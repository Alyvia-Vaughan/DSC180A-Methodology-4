# Methodology Assignment 4

**Name:** Alyvia Ricketts  
**Email:** alvaughan@ucsd.edu  

**Section:** D45
**Mentor:** Prof. Soohyun Nam Liao

---

**What is the most interesting topic covered in your domain this quarter?**  
Whether LLMs can generate practice questions that test understanding instead of memorization. Students and instructors already use LLMs to make study material, but the output is unreliable. ContentGen reached 91% correctness with structured prompting, but only on two intro programming courses, using binary metrics, and at almost twice the token cost of a basic prompt. Lohr et al. found GPT-4 questions fit course material 93% of the time yet contained errors 36.7% of the time. What interests me most is that a question can look relevant while being wrong or repetitive, and that existing evaluations are not built to catch this.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**  
An adaptive practice tool for intro computing courses (DSC 10, DSC 30, DSC 80). The tool generates a question pool from uploaded course material and tags each question with a Bloom's Taxonomy level. A student starts at a low level and moves up after answering correctly, or moves down after repeated misses.

The research question: given course material for a topic, can an LLM generate questions whose intended Bloom's level matches the level assigned by human raters, and does that accuracy hold at higher levels (Apply, Analyze, Evaluate), where prior work shows generation is weakest? Success would be measured by agreement between the model's Bloom's tags and our manual tags (for example Cohen's kappa), and by our 1 to 3 rubric scores for correctness and answerability at each level.

The primary output would be a website (the adaptive tool) plus a report analyzing the generated question pools. Data comes from public course websites we already used in Quarter 1, and compute is API calls, which our token dashboard already tracks.

A backup investigation if the adaptive tool runs too long: skip the student-facing adaptation and run a controlled comparison of prompting strategies (structured, brainstorm-then-pick, Bloom's-level-specified) on variety and Bloom's fit, measuring variety with embedding similarity across a batch.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**  
Make the variety and Bloom's measurements more objective. In Quarter 1 we score everything manually on a 1 to 3 scale, which is slow and hard to compare across raters. I would add an automatic variety metric (average pairwise embedding similarity within a batch), check inter-rater agreement on a shared subset of questions, and put the target Bloom's level directly in the prompt so we can test whether the model actually hits it rather than scoring Bloom's fit after the fact.

**What other techniques would you be interested in using in your project?**  
Retrieval-augmented generation so each question is grounded in a specific section of lecture material; executing generated code to verify answers before they reach a student, since Chan et al. found this roughly doubled answer accuracy; using an LLM as a first-pass rubric grader and measuring how well it agrees with our manual scores; and a simple student model (such as a running mastery estimate per topic) to decide when to move a student up a Bloom's level.
