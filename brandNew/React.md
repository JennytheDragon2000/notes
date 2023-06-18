- How virtual Dom is different from actual dom in the browser?
	- ![[Pasted image 20230521202520.png]]
	- its a lightweight in memory representation of component tree. where each node reperesent a comonent and its properties
	- when the state or data of a component changes, react update it in the virtual dom. after that it compares current virtual dom with previous virtual dom to identify the nodes that should be updated
	- ![[Pasted image 20230521202840.png]]
	- it'll then update those nodes in the actual dom.
	- technically updateding the dom is not done by react itself. it's done by companion library called react dom.
		![[Pasted image 20230521203006.png]]
	

- What is the difference between framework and library?
	- ![[Pasted image 20230521190210.png]]
	- ![[Pasted image 20230521190456.png]]
	- react is a library to create interactive, dynamic user interfaces
	- ![[Pasted image 20230521190911.png]]
	- we can use whatever tool for other things.
![[Pasted image 20230522085012.png]]

we use ReactDOM to render this component tree inside an element with the id `'root'`
![[Pasted image 20230522085026.png]]
we use ReactNative render this in mobile applications
![[Pasted image 20230522104838.png]]
we need to change the import 
![[Pasted image 20230522105241.png]]
![[Pasted image 20230522105210.png]]

- In react a component can not return more than one element
	- ![[Pasted image 20230522155412.png]]
	- to Solve this problem we have two ways
		1. wrap those element with a div
			- ![[Pasted image 20230522155942.png]]
		2.wrap element with a Fragment
		
			![[Pasted image 20230522161218.png]]
		3. just an empyt angle brackets. (you don't have to import anything)
			 ![[Pasted image 20230522161550.png]]
			 
- Render List of Icons dynamically
	- ![[Pasted image 20230522163006.png]]
	- in JSX we don't have a for loop. so we can't write a for loop. 
	- Instead we have to use map function (in javascript arrays have a method called map)
	- ![[Pasted image 20230522163236.png]]
	- we get a compilation error when we do this. cuz this expression is not allowed in the middle of jsx markup.
	- in jsx we can only use html elements or other react components.
	- so to render data dynamically we need to wrap this expression in braces
	- ![[Pasted image 20230522163445.png]]
	- but we have a warning 
	- ![[Pasted image 20230522163636.png]]
	- each list item should have a key property to uniquely identifies that item.
	- react needs this to keep track of our item.
	- so later when we add or remove items dynamically react knows what part of the page should be updated.
	- ![[Pasted image 20230522164002.png]]
	- we use item name cuz it's unique here. 
	- but in a real world application where we retrieve items from an api quite often each item have a property like id.
	- ![[Pasted image 20230522164201.png]]
	- warning is gone now 
	- ![[Pasted image 20230522164225.png]]

- Conditional Statements
	- ![[Pasted image 20230522172522.png]]
	- ![[Pasted image 20230523105015.png]]
	- but our heading is gone.
	- ![[Pasted image 20230523105129.png]]
	- ![[Pasted image 20230523105148.png]]
	- but there's duplication. how we can reduce it?
	- but insdie jsx expression we cannot write if statements. we can only write 
		- html elements
		- other react components
		- curly braces {}
	- so instead of if we can use ternary operator here 
	- ![[Pasted image 20230523105531.png]]
	- with this we can have the same result as before 
	- ![[Pasted image 20230523105705.png]]
	- sometimes this logic can get a little bit too complicated and it can pollute our jfx markup. in those cases we can always extract this logic and store it in a seperate  variable or constant .
	- ![[Pasted image 20230523121448.png]]
	- ![[Pasted image 20230523121455.png]]
	- we can also move this logic inside a function
	- ![[Pasted image 20230523121628.png]]
	- benefit of using a function here is our function can have parameters.
	- ![[Pasted image 20230523122330.png]]
	- but here it returns null with turnery operator. how to avoid it?
	- ![[Pasted image 20230523122544.png]]
	- ![[Pasted image 20230523122614.png]]
	- 
### Handling events

- let's see how to handle click events 
- here he forgot something to add before . he forgot to add one of the bootstrap classes to item.
- ![[Pasted image 20230523124648.png]]
- ![[Pasted image 20230523124700.png]]
- ![[Pasted image 20230523124706.png]]
- now we want be able to click on each item and see it on console.
- in react each element has a property/prop called on click 
- ![[Pasted image 20230523124909.png]]
- ![[Pasted image 20230523124926.png]]
- ![[Pasted image 20230523124608.png]]




































































