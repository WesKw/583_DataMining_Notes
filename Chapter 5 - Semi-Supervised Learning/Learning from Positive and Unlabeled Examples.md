- [[PU Learning]]
- **Positive examples**: One has a set of examples of a class $P$
- **Unlabeled set**: Also has a set $U$ of unlabeled (or mixed) examples w/ instances from $P$ and also not from $P$ (**negative examples**)
- Build a classifier to classify the examples in $U$ and/or future (test) data
- Key feature of the problem: No labeled negative training data
- This problem is called [[PU Learning]]
- # Direct Marketing
	- Company has a DB w/ details of its customers (positive examples), but no information about non-customers (negative examples)
	- We want to find people who are similar to their customers for marketing
	- Get a database of people (unlabeled data) who *may* be customers
	- Are unlabeled examples helpful?
		- We do not know where our decision boundaries are
- ## Theoretical foundation
	- $(X, Y): X$ - Input vector, $Y \in \{1, -1\}$ - class label
	- $f$ classification function
	- We write the probability of error:
	  $Pr[f(X) \ne Y)] = Pr[f(X) = 1 \& Y = -1] + Pr[f(X) = -1 \& Y=1]$
	- ...more stuff...
	- The point is that PU Learning is a constrained optimization problem
		- We want to minimize the number of unlabeled examples labeled as positive
			- subject to the constraint that the fraction of errors on the positive examples is no more than 1-$r$ ($r$ is recall, in practice we do not need to set this)
- ## Algorithms
	- 2 step learning
		- Step 1: Identify a set of reliable negative documents from the unlabeled set
		- Step 2: Build a sequence of classifiers by iteratively applying a classification algorithm and then selecting a good classifier
	- Can be done with naive bayes or SVM!
	- How do we find reliable negatives?
		- [[Spy Technique]]
			- Sample a certain % of positive examples and put them into unlabeled set to act as "spies"
			- Run classification algo assuming all unlabeled examples are negative 
			- We then extract reliable negative examples from the unlabeled set more accurately
		- [[1-DNF method]]
			- For text documents
			- Find set of words $W$ that occur in the positive documents more frequently than in the unlabeled set
			- Extract those documents from the unlabeled set that does not contain any word in $W$, these form the reliable negative documents
		- [[Rocchio method]] from information retrieval
		- [[Naive Bayesian method]]
	- Heuristic methods
		- Step 1 tries to find some initial reliable negative examples from the unlabeled set
		- Step 2 tried to identify more and more negative examples iteratively
		- These two steps for the strategy increase the number of unlabeled examples classed as negative while maintaining the number of correctly classed positive examples
	- We can use [[3.8 - Support Vector Machines]] to deal with the problem directly (without 2 steps)
		- Remember, we don't have negative data, we have unlabeled data!
	- ## How do we apply SVM?
		- We can used [[Biased SVM]], we assume the first $k-1$ examples are labeled positive, and the rest are unlabeled examples, labeled negative
		- We regard unlabeled data as negative but there is a lot of error or noise!
		- We can make mistakes on the unlabeled data set
		- ### Noisy case
			- If we allow the positive set to have noisy negative examples, then:$$
\text{Minimize}: \frac{1}{2}w^{T}w+C_+\sum^{k-1}_{i=1}\epsilon_i + C_-\sum^{n}_{i=k}\epsilon_i \\
\text{Subject to:}$$
			* This turns out to e the same as the asymmetric cost SVM for dealing w/ unbalanced data
			* However, we don't have negative data, so we can't do accuracy. 
			* Normally we use f-scores, but we have no negative data so we cannot measure the precision.
			* We also can't tune the parameters because we have no negative data
		* ### Estimating performance
			* We need to estimate performance in order to select parameters.
			* Learning from positive and negative examples often arise in retrieval situations, we use F score as the classification performance measure:
			  $F=2pr / (p+r)$ where $p$ is [[precision]] and $r$ is [[recall]].
			* Remember, to get a high [[F-score]], both precision and recall need to be high. But remember we do not have negative examples, so we can't find the F-score.
			* We can use performance criteria $pr/Pr[Y=1]$: It can be estimated directly from the validation set as $r^2/Pr[f(X)=1]$
				* Recall: $r=Pr[f(X)=1|Y=1]$
				* Precision: $p=Pr[Y=1 | f(X)=1]$
				* This behavior is similar to the F-score.
				* These are the probabilistic definitions of precision and recall.
			* $r^2/Pr[f(X)=1]$ - classify the unlabeled data as positive, so we want Pr to be small and r to be large
			* $Pr[f(X)=1]$ can be obtained using the full validation set.
			* criterion reflects the theory well
			* This is commonly used in text classification and natural language processing
			* Understand the idea behind this (this is on the quizzes and exams)
* # Summary
	* Learning w/ positive and unlabeled examples
	* 2 step learning strategy
	* biased SVM formulation
	* Performance measures that can be estimated from data
	* Biased SVM performs better
* ## One class learning
	* Learning with a single class
		* What if we have no unlabeled data? Only positive data?
		* No negative or unlabeled data
		* Used for anomaly detection or novelty detection
	* Traditional techniques based on SVM
	* New techniques are all based on deep learning