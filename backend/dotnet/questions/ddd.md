# DDD

* What's Problem-Domain?
* What's Solution-Domain?
* Strategic Design
	* What's Ubiquitous Language?
	* What's Bounded Context?
	* What are DDD sub-domains?
		* What's Core domain?
		* What's Generic domain?
		* What's Supporting domain?
* Tactical Design
	* What's Aggregate?
	* What's Value-Object?
		* Can we use C# 9 records as Value-Objects?
		* Ask for some examples of Value-Objects
		* How can we persist Value-Objects?
	* Domain Services
		* What's a domain-service?
		* How it's different from application-services?
	* Domain Events
		* What is domain-event?
		* Where we use them?
		* How to raise them?
	* Context Mapping
		* What is context-mapping?
		* What are the different context-mapping patterns?
			* Open/Host Service
			* Conformist
			* Anticorruption-Layer
			* Shared-Kernel
			* Customer/Supplier
			* Patnership
			* Published Language
			* Separate Ways
		* What's Upstream and Downstream?
	* Integration between BCs (messaging, RPC, ...)
	* Entity Persistence
		* What's persistence-ignorance?
* Patterns 
	* Factories
	* Repositories
		* What's repository?
		* What's unit-of-work?
		* Generic repository or Explicit repositories?
	* Event Sourcing
		* What's event-sourcing?
		* What are streams in event-sourcing?
		* When should we delete events from the stream?
	* CQRS
		* What's CQRS?
		* When should we do that?
		* How to synchronize Command and Query databases?