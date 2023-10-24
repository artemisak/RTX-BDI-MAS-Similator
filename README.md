# RTX-BDI-MAS Simulator

The general structure of the modelling process is outlined below. We use an exponential distribution with a scale of 1/lambda to generate the time between occurring events. An event is the appearance of a patient, which is characterised by several parameters: the time of the request appearance, the time of service provision, the task assigned and the selected doctor. A task is a certain MRI image to be decoded. The task, like the patient, is a named entity and has the following parameters: urgency and complexity. Urgency can take values from 1 to 3, where 1 is an urgent task (hospitalisation, severe condition), 2 is a task of medium urgency (the patient is conscious, injuries of no more than medium severity), 3 is the lowest priority (regular examinations, monitoring, minor injuries). Complexity is evaluated by a binary variable, either the task requires the highest qualification of a specialist or it does not. Complexity is a linear combination of technical complexity in image processing and urgency of the task. Thus, even tasks with the lowest priority can be considered as complex if they require more than usual processing time. The decision and complexity of the problem can be taken by a feed forward propagation neural network. For simulation purposes, its work is replaced by a random number generator. But in real RTX-BDI-MAS work, pre-scanning an image to assign it to one of two complexity categories has the potential to facilitate informed decision making in the process of matching available resources and agents in the clinic network. 

![Screenshot](Supplements/simulation-graph.svg)

It is worth mentioning that the available specialists are both agents and the main human resource of the clinic. Physicians are the specialists whose job it is to decipher the MRI image. They are assisted by interns who mark up the images. First of all, a doctor is characterised by his/her qualification, which can be assessed on a scale from 1 to 3, where 1 is a Doctor of Medical Sciences, 2 is a Candidate of Medical Sciences, and 3 is a specialist. During the simulation, the same doctor may receive several requests, similar to a live queue. The length of this queue is called the workload. From the point of view of RTX-BDI-MAS, this parameter can be used to predict the approximate waiting time before the start of a new task. And, consequently, optimisation of workload will reduce the average waiting time for the execution of a request in the network.
