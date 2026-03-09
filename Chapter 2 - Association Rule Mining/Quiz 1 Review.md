1) [[Association Rule Mining]] w/ multiple minimum supports
	1) sdc tries to prevent too frequent and too infrequent items from appearing in the same itemset
2) For mining association rules w/ multiple minimum supports
	1) [[tail count]] is used for rule generation
		1) Tail counting is __not__ used for candidate generation or pruning.
3) Given I = {1, 2, 3, 4}, MIS(1) = .15, MIS(2) = 0.08, MIS(3) = 0.07, MIS(4) = 0.05, len(T) = 100, first pass gives supports {1}.count = 25, {2}.count = 7, {3}.count = 6, {4}.count = 6, find L.
	1) sup(1) = .25, sup(2) = .07, sup(3) = 0.06, sup(4) = 0.06. If we sort by the MIS values, the first item that would be found is 4. Since MIS(4) is 0.05, and its the first item we've found, then all subsequent items must have a support $\ge$ MIS(4) = 0.05. So, the resulting L would be {4, 3, 2, 1}.
4) Deleting anomalies is a step of...
	1) [[Data cleaning]]
		1) [[Data integration]] is combining data from multiple sources
		2) [[Data reduction]] reduces dimensionality of the data
		3) [[Data transformation]] changes existing data
5) For [[Class Association Rule Mining]] (CAR) mining
	1) items that can appear on the rhs cannot appear on the lhs
		1) Remember for CAR we are looking for rules for specific classes (fixed targets), find out correlations with a specific class
6) F3 = {{1, 2, 5}, {1, 2, 3}, {1, 3, 7}, {1, 3, 4}, {3, 4, 7}, {1, 3, 5} {1, 4, 7}}, what are the candidate 4-itemsets after joining and pruning (using [[Apriori]])
	1) Candidates after joining are {1, 2, 5, 3}, {1, 3, 7, 4}, {1, 3, 7, 5}, {1, 3, 5, 4}
	2) then we have to prune them by removing any subsets of all candidates that are not found in F3.
	3) {1, 2, 5, 3} is removed because {2, 5, 3} is not in F3
	4) {1, 3, 7, 4} is kept because all 3 subsets are in F3
	5) {1, 3, 7, 5} is removed because {3, 7, 5} is not in F3
	6) {1, 3, 5, 4} is removed because {3, 5, 4} is not in F3
	7) So the answer was none of the above
	8) Remember, for this type of question think about the [[Downward Closure]] property
7) For [[Sequential Mining]]
	1) <{2, 3}{3, 4, 5, 6}> is a super sequence of <{2}{3}>
		1) <{2, 3}{3, 4, 5, 6}> is not a super sequence of <{4}{5}> because 4 and 5 appear in the same dataset
8) Association rule mining is
	1) A form of [[Unsupervised]] learning
9) For mining association rules w/ multiple min supports
	1) We can set the same minimum support for multiple items
10) Given frequent 3-sequences: <{3, 4} {6}>, <{3, 4} {5}>, <{3, 5} {7}>, <{3} {5, 6}>, <{4} {5, 6}> and <{4} {5} {7}>, what are the candidate 4-sequences?
	1) <{3, 4}{5, 6}> is the only candidate that appears
11) Complexity of minimum item support frequency mining is exponential
12) Given a dataset, min sup, and min conf
	1) Association rule mining has a unique solution
13) What is dimensionality reduction of data?
	1) To reduce the number of attributes in a given data set
14) What is attribute construction?
	1) The process of creating new attributes in a data set given existing attributes
15) Requirements of association rule mining
	1) Sparse data, minimum supports, minimum confidence
		1) Tabular data is not required because we can convert it to transactional data
		2) Association rule mining only works with categorical data
		3) Dense data means that rule mining would be extremely slow!
16) MS Apriori algorithm is a generalization of Apriori
	1) If we set every minimum support of every item to be the same, MS Apriori reduces to Apriori
17) Data cleaning is a major pre-processing step of data mining
18) Given the user-specified MIS values for the three items 1, 2, and 3: MIS(1) = 2%, MIS(2) = 0.1%, MIS(3) = 0.3%. Which of the following rules satisfies its minsup?
	1) 1 -> 2 sup = 0.15, conf = 70%
		1) This is the only rule where {1, 2} actually works, because the minimum support for 2 is 0.1%, meaning that if this rule exists the support for 2 must be $\ge$ 0.1%.
			1) Ex: 1 -> 3 sup = 0.15% does not work because the smallest minimum support in the rule is 0.3%, so the rule cannot have a support of 0.15%.
			2) 1 -> 2 implies that {1,2} is a frequent itemset, which means that it has a support of at least 0.1%.
19) In association rule mining with multiple minimum supports, if we do not want an item to appear as the first item in any frequent pattern, what can we do?
	1) We set the minimum item support for that item to 120%, that way it always appears in the back.
20) Let F3 = {{1, 2, 3}, {1, 3, 4}, {1, 2, 5}, {1, 3, 5} {1, 3, 7}, {1, 4, 7}, {3, 4, 7}}. Using the Apriori candidate generation algorithm, we obtain the following the candidate 4-itemsets after the join step and the pruning step
	1) {1,2,3,5} - {2,3,5} does not appear, removed
	2) {1,3,4,5} - {3,4,5} does not appear, removed
	3) {1,3,5,7} - {3,5,7} does not appear, removed
	4) {1,3,4,7} - All subsets appear, we keep this candidate <- only one we keep
	5) {1,2,3,4} - {2,3,4} does not appear, removed
21) [[Data integration]] combines data from multiple sources
22) Minimum support is the most important parameter for association rule mining