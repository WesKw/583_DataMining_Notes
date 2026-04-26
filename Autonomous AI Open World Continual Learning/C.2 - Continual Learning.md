- Learn a sequence of tasks $T_1, T_2, ... T_n$ incrementally
- Each task has training dataset $D_t={(x_i,y_i)}^n_{i=1}$
- Goal: learn each new task $T_{n+1}$ incrementally
	- 1) without __catastrophic forgetting (CF)__ - Learning of the new task should not result in accuracy degradation for any previous $N$ tasks
	- 2) with __knowledge transfer (KT)__ - leveraging knowledge from previous tasks to learn the new task better
- Assumption: Once a task is learned its data is not longer accessible, at least a majority of it
	- New task $T_{N+1}$ and its training data $D_{N+1}$ are given by the user.
- In supervised ML, a task is a set of classes to learn
- We assume that the task and its training data are given
  ![[Pasted image 20260426104226.png]]
## Two Popular CL Settings
- **Task incremental Learning (TIL)** - train a separate model for each task and task-id provided during testing
	- e.g.: Task1 -> Recognize dog breeds, task 2 -> recognize different animals, task 3 -> recognize different types of fish
	- Goal: Construct a predictor $f: X\times T \rightarrow Y$ to identify the class label $y \in Y_k$ for $(x,k)$ given the test instance $x$ from task $k$. $T$ is a sequence of tasks, each has a training data set $D_k$, $X$ is the set of input samples, $Y$ is the set of class labels
- **Class Incremental Learning (CIL)** - Produce a single model from all tasks and classify all classes during testing
	- e.g.: Task 1 -> learn to recognize pig and cat, task 2 -> sheep, task 3 -> chicken and dog
	- Goal is to build a single classifier for all tasks $f : X\rightarrow Y$
	- inter-task class separation challenge - how do we establish the decision boundaries b/w the classes of the new task and those of old tasks?
