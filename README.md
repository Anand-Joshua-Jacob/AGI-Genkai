# AGI-Genkai

> The term AGI is often used as a shorthand to describe various kinds of highly capable AI systems. [1]

- This repository contains experiments designed to probe the current limits of state‑of‑the‑art AI systems and to map out their cognitive profiles, with the goal of informing and guiding future research.
- Based on research in psychology, neuroscience and cognitive science, general intelligence can deconstructed into 10 key cognitive faculties. These are Perception, Generation, Attention, Learning, Memory, Reasoning, Metacognition, Executive functions, Problem solving and Social cognition. [1]
- Out of the 10 cognitive faculties mentioned above, there a special need for high quality benchmarks in the fields of learning, metacognition, attention, executive functions, and social cognition. [2]
- This repository presents exploratory benchmarks and experiments targeting several of these under‑served cognitive faculties.

## Learning

> The ability to acquire new knowledge, skills, or behaviors through experience, study, or instruction. [1]
1. **Learning from images** evaluates how well LLMs can learn conventions from images and apply them to reason about a target image. See the detailed tasks and report in the [Learning from Images directory](https://github.com/Anand-Joshua-Jacob/AGI-Genkai/tree/main/LearningFromImages).

2. **Learned Helplessness** refers to a phenomenon in which humans and animals stop trying when they believe their efforts have no effect. Do LLMs exhibit similar behavior? See the additional details in [Learned Helplessness directory](https://github.com/Anand-Joshua-Jacob/AGI-Genkai/tree/main/LearnedHelplessness)

3. **Cognitive Maps in Rats and Men** [3], published in Psychological Review 1948, discusses how rats form cognitive maps of mazes after exploring them a few times. It shows that among other things rats can learn the layout of a map by exploring it. SOTA AI systems were also tested on their ability to learn maze structures in the paper titled **MazeEval: A Benchmark for Testing Sequential Decision-Making in Language Models (2025)** [4]. This paper shows that LLMs fail for large mazes and that performance significantly degrades when the language used is changed to Icelandic. It suggests that spatial reasoning in LLMs emerges from linguistic patterns rather than language-agnostic mechanisms.

4. **ARC-AGI-3** [5] challenges AI systems with navigating simulated environments to reach specified goals when provided with a discrete set of actions at each step—shifting from static benchmarks to interactive reasoning environments. It introduces a suite of tasks that are designed to be highly challenging for current AI systems while remaining solvable by humans.



## Metacognition - thinking about thinking

Confidence calibration done during testing itseems - [Reasoning models get higher scores.](https://arxiv.org/abs/2505.14489)

1. So how about putting the bullshit benchmark questions and testing whether the AI agrees, if it does, how much is it's confidence score.
2. How about adding the prompt like - "Answer only if you are 100 percent sure" or "Make sure what you are saying makes sense" and then evaluating the system.

## References

1. [Measuring Progress Toward AGI: A Cognitive Framework](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/measuring-progress-toward-agi/measuring-progress-toward-agi-a-cognitive-framework.pdf) (Google DeepMind, 2026)

2. [Kaggle Hackathon conducted by Google Deepmind](https://www.kaggle.com/competitions/kaggle-measuring-agi)

3. [Cognitive Maps in Rats and Men (1948)](https://psychclassics.yorku.ca/Tolman/Maps/maps.htm)

4. [MazeEval: A Benchmark for Testing Sequential Decision-Making in Language Models (2025)](https://arxiv.org/abs/2507.20395)

5. [ARC-AGI-3](https://arcprize.org/arc-agi/3)