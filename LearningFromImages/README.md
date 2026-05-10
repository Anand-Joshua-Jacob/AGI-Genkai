- Research shows that the human brain processes visuals 60,000 times faster than text.[link](https://oit.williams.edu/files/2010/02/using-images-effectively.pdf)
- LLMs are bad at spatial reasoning
- I want to add a benchmark in a place where AI is not able to perform well so that we can make improvements in that area moving forward.
- This task isolates learning as there is no element of Metacogniton, executive functions or social cognition.(also attention?)
- For many current systems, learning occurs only during training or in-context. However, for truly robust and adaptive behavior, AI systems should be able to learn (and retain) new knowledge and skills over time (e.g., as part of a continuous
learning process). In this benchmark we will be testing in-context learning. But the context will contain (Choices the AI made and the outcomes??)
- Task 1 (_1, _2(1,2 and 1, 3), _3)
  - Has to learn initial and final from the first 2 images.
- Task 2 (_1, _2, _3)
  - Has to learn initial and final and arrows.
  - We have provided arrows in the first 2 images but expect the LLM to learn to understand even without the arrows in the later images.
- Task 3 (_1, _2, _3)
  - The scale of the stick figures are different
  - The stick figure has to move down by 2 units.
- Task 4, 5, 6 (_1, _2, _3)
  - No scale provided, just intuition


- LLMs know about inertia but have they seen it in action (very little image training compared to text) (assume)


### Problem Statement
- Research shows that the human brain processes visuals 60,000 times faster than text.[link](https://oit.williams.edu/files/2010/02/using-images-effectively.pdf) whereas LLMs are bad at spatial reasoning.
- I want to add a benchmark in a place where AI is not able to perform well so that we can make improvements in that area moving forward.
- In this benchmark we will be testing in-context learning of LLMs from images.

### Dataset and Task
The benchmark consists of 3 Kaggle tasks corresponding to 3 Kaggle datasets. All the images in the datasets are drawn by me so we can be sure that the LLMs have never seen them while training.

<img src="database/task1/task1_1/4.jpg" alt="Sample Image" width="350">

#### [Dataset 1](https://www.kaggle.com/datasets/anandjoshuajacob/task-jumping) and Task 1
- Consists of 5 sub tasks named task1_1, task1_2, task1_3, task1_4 and task1_5
- Each sub task consists of 4 images and each image consists of 2 stickmen, a grey stickman denoting initial position and a black stickman denoting final position.
- The 1st, 2nd and 3rd images show movement of the stickman to the right, left and upwards. The LLM is given these 3 images as option A, option B and option C
- Then it is given a target image which is the 4th image that shows initial stickman on the left and final stickman on the right with a red region in between. 
- The target image (4th image) is same across all the tasks. The LLM is told to avoid the red, and that normal rules of physics apply. It is now tasked with finding the shortest sequence of moves to achieve what is shown in the target image.
- Since the stickman will immediately hit the red block if it moves right first, the correct sequence is to jump first and then move right after which it will come down due to gravity. Hence the correct answer is "CA".
- In task1_1 the 3 images showing movement have labels denoting initial and final position and an arrow indicating the direction of movement, but the target image just contains the gray stickman and black stickman. The LLM is tested on it's ability to learn the conventions and understand that gray stickman represents initial position and black stickman represents final position.
- In the other tasks only the first image contains labels and arrows and these are gradually removed in images 2 and 3. The target image does not contain labels or arrows in any task. I want to test how fast the LLM can learn the conventions of the labels and arrows. In task 1_5 only the first image has labels and arrows, the 2 remaining images showing stickman movement and the final target image contain only a gray stickman and black stickman(initial and final position).
- The LLM has to **learn** these conventions and understand what each image represents and what it has to do in the final image. Then it has to come up with the correct sequence that achieves what is shown in the final image.
- As tasks progress the LLM gets fewer examples to learn the conventions from.
- The LLM is asked to output a reasoning field and final answer sequence. If the final answer sequence is right the LLM passes the task.
- A reference scale is shown in the X and Y direction for the LLM to see that the stickman has moved from this position to that.

#### [Dataset 2](https://www.kaggle.com/datasets/anandjoshuajacob/stickfigures-without-explicit-scale) and Task 2
- Consists of 5 sub tasks named task2_1, task2_2, task2_3, task2_4 and task2_5
- All tasks are the same as Task 1 but without a scales in the X and Y directions.
- Most LLMs reasoned saying the Stick figure moved x units to the right from this coordinate to that one. So I wanted to see how they would perform if no explicit scale was provided for the LLMs to make these calculations. They have to internally form representations of the stickman moving up or sideways by some units and roughly compare them to the target image movement before coming up with the final answer sequence.
- The Correct sequence like in Task1 is to Jump and move right i.e. "CA".

#### [Dataset 3](https://www.kaggle.com/datasets/anandjoshuajacob/visual-learning-3) and Task 3
- Consists of 5 sub tasks named task3_1, task3_2, task3_3, task3_4 and task3_5
- All tasks are the same as Task 1 but the sequence of the options is changed to option A - up, option B - left, option C - right. 
- Right and left are just opposites of each other, so it is easy for the LLM to understand and relate the labels and arrows present in the Right image to the left image and so on.
- I now want to test if the LLM can relate labels and arrows in an "up" image to lateral movement images and target image.
- The Correct sequence is again to Jump and move right i.e. "AC" in this case.


### Task & benchmark construction
- I have created 3 Kaggle tasks corresponding to the 3 Kaggle Datasets above. Each kaggle task has 5 sub tasks.
- For scoring, Each subtask is run for 5 trials and each time the LLM gets the sequence right, it gets 1 point and 0 otherwise. The final score is the average of the 25 runs (5 subtasks * 5 trials)
- The Kaggle benchmark score is an average of the score on the 3 Kaggle tasks.

### Technical details 
- This task isolates learning and reasoning as there is no element of Metacogniton, executive functions or social cognition. It may contain some attention too as to which part of the image to focus on, but all LLMs are very good at this and it does not affect the final score.


### Results, insights, and conclusions
- For the task, I modified the prompt to make it easier for the LLM to get a reasonable score. But during this I was using google/gemini 3 flash preview. It seems to have fine-tuned the task to be easy for this particular model and so gemini 3 flash preview perform consistently well. 
- Also when I ran the task on a text only model, it guessed the right answer simply by guessing what the each image and the final task would be simply based on my prompt. So maybe the LLMs are not learning purely based on what they see in the images.



### Organizational affiliations
Working in a Japanese Automobile company, nothing crazy. 

### References & citations
https://oit.williams.edu/files/2010/02/using-images-effectively.pdf