## KLDA: Kernel Linear Discriminant Analysis
- Using only *large foundation models (LFM)* as feature extractors, no training or fine-tuning
- For each sample, we obtain its features from LFM
	- Extracted features are kernelled using RBF kernel and random Fourier features 
	- Training / learning
		- Compute a *feature mean for each class* and a *shared covariance matrix*
	- Testing: using linear discriminant analysis (LDA)
		- We do expansion do ensure data is more linearly separable
	- This method does pretty well
- Upper-bound technique - We learn every thing together instead of incrementally
	  
## AnaCP: Analytic Contrastive Projection
- several *CIL* methods based on analytic (closed-form) solutions over a pre-trained model have been proposed
	- SLDA, KLDA, RanPC, GACL
- ***Limitation***: they only use features from the frozen PTM, cannot fine-tune or adapt features
	- Suboptimal performance
- **AnaCP** - novel approach that can adapt features through analytic contrastive learning
	- based on *Extreme Learning Machine (ELM)*![[Pasted image 20260422100229.png]]
- Main idea:
	- Achieve the effect of *contrastive learning*
	- Positive Alignment via Prototype Regression
		- Use mean vectors as the target of ridge regression for prediction
	- Negative Repulsion via target-prototype separation
		- Shifting the means of the classes
			- Apply SVD on the class means and change singular values
