### Instructions for Designing Your Experiments and Creating a Motivation Example

### General Instructions for All Teams:
Your next priority is setting up the **evaluation environment**. The key deliverable is to present a **clear, well-motivated challenge** that your project aims to solve, supported by **experimental results**. The experiment should produce results that you can include directly in your final report/paper.

- Think of a Jupyter notebook-style setup: you start an experiment, and after a while, it generates some results—**your own data**, not fake or borrowed from other papers.
- These results should motivate why this problem matters and show that you’re making progress on a solution.
  
Each project will have slightly different needs, so here’s how to structure the task for each one. I start off by discussing the general instructions in the context of the two projects intended to extend IPA framework in details and then I discuss customized examples for other projects who currently submitted their proposals in their project repository.

**Objective:**
Your next key deliverable is to present a **clear and concrete motivation example** for one of the main challenges your project aims to solve. This should be supported by **your own experimental results**. To help you structure your efforts, use the following guidelines.

### 1. **Prioritize Evaluation Setup**
The most critical step right now is to focus on setting up your evaluation environment. This environment will allow you to run experiments, collect data, and generate initial results that demonstrate the importance of the challenge you're tackling.

- Think of this like a Jupyter notebook setup where you can run your experiments and plot the results.
  - For example, if you are working with the IPA system, try replicating an experiment and plotting the results (check out IPA’s repo for inspiration).
  - Your goal should be to create a plot or result that could eventually go into your final report or paper.

- **Offline plots** are acceptable if you can’t use a live setup, but the data **must come from your own experiments**—no using data from other papers or making up numbers.

### 2. **Collaborate on Experiment Design**
Each team should:
- Meet and **discuss the key challenge** you’re trying to address in your project. 
- Brainstorm what kind of **initial experiment** you can run to demonstrate the importance of this challenge.
- Think about the **metrics** you need to show. For instance:
  - If you’re working on energy efficiency, focus on energy consumption, latency, and performance trade-offs.
  - If your project is about resource optimization, consider metrics like resource utilization, cost, and scaling efficiency.
  
  Remember, the goal is to motivate why this challenge matters. You may want to work on a couple of challenges, fine, but start with one core challenge and only one for the motivation example you need to deliver soon.


### 3. **Design of Experiments (DOE)**
When designing your experiment, focus on:
- **Independent Variables:** What are the factors you’re changing? (e.g., model size, batch size, hardware configuration).
- **Dependent Variables:** What are the outcomes you’re measuring? (e.g., energy consumption, accuracy, latency).
- **Control Variables:** What will stay constant to make sure the results are valid?

### 4. **Examples of Solid Motivation Experiments**
To get a sense of what a strong motivation example looks like, refer to the following papers:
- **MLSys 2023 Papers:** These often contain experiments that showcase the relevance of the problem they address.
- **IPA’s experiments in the replication repo** (check out their GitHub).
  
  **Specific Examples:**
  - Papers that measure energy efficiency in distributed ML systems (you can find these in MLSys and Systems conference papers). For example, how does adjusting the hardware or algorithm parameters change energy consumption?
  - Papers that deal with **scalability challenges** in ML pipelines, where they show clear trade-offs between performance and resource usage.

### 5. **Deliverable:**
- A short presentation with **your own experimental results**. This should clearly motivate the challenge you’re addressing.
  - Show a **plot** or **figure** generated from your experiment.
  - Explain why these results matter and how they inform the next steps in your project.
  
### General Tips:
- **Collaborate but Focus:** Discuss experiment design with your teammates and other teams if relevant. However, only focus on **one task at a time** to avoid being overwhelmed.
- **Use GitHub:** Leverage GitHub’s project management features to assign tasks, track your progress, and ensure the team stays on target.
- **Create Plots from Real Data:** The results you generate should be based on your own data and serve as the foundation for the final project report.
- **Leverage each other's strengths:** If your team is struggling with certain aspects (e.g., setting up the environment or plotting results), consider reaching out to other teams who might be working on similar problems for advice, but focus on **one collaborative task at a time**.
- **Keep it simple:** Start with a small, manageable experiment that can grow as you refine your project. The point is to **show progress**, not to complete everything in one go.


Good luck, and remember to stay focused on the next step: generating **real experimental results**!
