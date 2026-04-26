- **Open-world (continual) learning (OWL)**: *CIL+*
	- 1) Detect novel / new objects (OOD detection)
	- 2) acquire he ground-truth labels of the OOD objects
	- 3) incrementally learn the new objects (online CIL+)
- Theoretical result for CIL+:
	- *WP* (w/ task prediction) OOD detection are necessary conditions
	- *Online or streaming CIL+*: Data from any old and new class can come at any time.
![[Pasted image 20260422101102.png]]
- Try to expand what we had before (blue lines)
- ~={orange}Learning on the job=~
- ~={blue}Learning after model deployment=~
- Need to discover new tasks to learn *in* the application
## Ex: Greeting a bot in a hotel
- See an existing guest:
	- "Hello X how are you"
- See a new guest - recognize that they are new
	- Bot should welcome the new guest and ask for information
- See the new guest again:
	- Bot remembers the guest
- This is completely done by the model itself
- ***This is not trivial!***
	- ~={red}In a real hotel, the situation is much more complex=~
	- How does the bot know that the novel object is a new guest?
		- Object could be anything....
	- Different characterizations require different responses (~={blue}adaption or accommodation=~ strategies)
		- Does it look like an animal? report to staff
		- Does it look like a policeman? Do nothing
		- Does it look like a hotel guest w/ luggage? Ask for their name & learn to recognize
		- What strategies does the bot deploy to cope with situations?
	- We need a shit load of knowledge to do simple things
	  
## Autonomous (online) learning after development
- PLDA - example method, using a pre-trained model![[Pasted image 20260422102004.png]]

## Novelty Characterization and Adaptation
- *Characterization*: A description of the novel object based on the agent's existing knowledge
	- Different levels of detail -> more or less precise responses
	- Done based on *similarity*:
		- E.g. looks like an animal (generic), or looks like a dog (specific)
	- ***Attributes / properties***: e.g. a moving object, speed and direction of moving
- *Adapting to novelty*: a pair (Characterization, Response)
	- Response: According to characterization, formulate a specific course of actions to respond to the new novelty
		- Default action if cannot characterize
	- Enable continual learning
- *Risk assessment*: each decision carries risks

## Adaptation enabled continual learning
- ___Ask a human and learn___
	- Ask human using interactive module $I$ for natural language to get ground-truth data and incrementally learn
	- ~={blue}Self-sufficient bots need to be able to interact with humans=~
- ___Imitation learning___
	- On seeing a novel object by a self-driving car, if a car drives through with no issue, car may choose the same course of action
	- ~={blue}Self-sufficient bots should be able to take their own actions based on the what others do, without needing to directly ask=~
- ___Perform limited reinforcement learning___
	- Trial-and-error exploration

## SOLA: Self-initiated Open-world Continual Learning & Adaptation
![[Pasted image 20260422102939.png]]
- Natural language interface (NLI)
	- *Performance Task*: user asks the system (CML, like siri or alexa) to perform a task in NL, the system does it via API actions
	- CML builds NLIs for API-driven applications semi-automatically
	- To build a new NLI (or add a new skill)
		- Application dev writes set $S_i$ of seed commands (SC) in NL to represent each API action $i$
		- Adapts an learns new paraphrased SC from users interactively and continually
- **Novelty detection**: when CML cannot ground a user command
	- e.g. it can't understand how to perform a specified action by breaking apart the natural language command
- **Novelty Characterization**: which part of the command it understands and which part it has difficulty based on similarity
	- e.g. "Turn off light" -> Turn off might be novel
- **Adaptation**: 
	- Response: as the user by providing some options to collect ground-truth data
	- Continual learning: learn a new seed command
- **Risk Consideration**
	- Do not ask user too many questions
	- When not confident -> take the default action
		- Say the command in another way
		- Options can be annoying -> user loses confidence in the system

# Some controversial statements
- Do humans learn representations or features?
	- Who knowssssssssss
- e.g. Mother teaching a baby to recognize Apple and Banana
	- Does the baby already have an internal representation of the apple and banana and know they are different?
- Learning need not or should not learn representations
- AIs most important task is still training or building a good foundation or world model