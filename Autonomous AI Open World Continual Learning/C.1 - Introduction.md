- Can robots continuously learn by themselves
- Human brains are hardwired to learn!
- AI agents must be able to:
	- 1) Learn continually in the open and dynamic world that i full of unknowns on its own initiative with self-motivation
	- 2) Must interact with humans, other agents in the environment
- Classic machine learning: Isolated single-task learning
	- Task T -> input D -> Learning (ML algorithm) -> Model -> Application
	- *Weaknesses*
		- _Closed-world assumption_
			- Open world: with unknowns or novelties that are out-of-distribution (OOD)
		- *No continual learning*
		- *No learning after deployment*
		  
- ## Novelty Detection & Continual Learning
	- Traditional ML makes close world-assumption
		- (test classes) $Y^{test}$ $\subset$ $Y^{train}$ (training classes)
	- *Open World* - with unknowns or novelties
		- ___A system unable to detect new things cannot learn by itself___
	- Autonomy involves connecting *novelty detection* and *continual/life-long learning*
	- **Self-initiated Open-world continual Learning and Adaptation** (SOLA) connects both
## Autonomous Learning Agent
- World is full of *unknowns*
- Need to learn on the job & be autonomous
	- continuous self-motivated and self-supervised manner to improve over time
- *Self-motivation*: detect novel or unknown objects to learn
	- Novelties are intrinsic motivations for human learning
- *Self-supervision*: collect ground-truth training data by agent itself via
	- Interaction or communication w/ other humans or agents
	- Perception, internal evaluation, environmental feedback
- ### Ex: Self-driving cars need to learn continuously
	- Cannot reach human-level driving with only rules and offline training
	- Too many edge cases! World is mysterious
	- Needs to adapt in the *open world* with many *unknowns*
	- Need to learn on the flyyyyyyyyyy
	  
## Chatbots should learn continually after deployment
- Chatbot: human users may say things a chatbot does not understand
	- Learn new knowledge and new language expressions during chatting 
	- Humans learn a lot in daily conversations
- Chatbots should not solely rely on offline training