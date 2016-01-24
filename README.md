# Stamped, the game framework

Stamped goal is to provide a modular environment for JS game development based on Stamp{it} by Eric Elliot.

## Dependency

Stamp{it} doesn't provide a dependency mechanism. For example, if I create a MoveWithArrows Stamp, objects stamped with MoveWithArrows should have a Placeable Stamp which provide a X/Y/Z coordinate system.

So, each Stamp should store the stamps they rely on, so we can fire errors easily.

## Architecture example

	PlayableCharacter
		<- MoveWithArrows { Dep : Placeable }
		<- Character
			<- Placeable
			<- Renderable

	PNJ
		<- Character
			<- Placeable
			<- Renderable
		<- Actionnable
		<- Clickable { Dep : Actionnable }

### Discussion

#### Why dependencies ?

We could simply Stamp MoveWithArrows with Placeable. Architecture could be :

PlayableCharacter
	<- MoveWithArrows
		<- Placeable
	<- Character
		<- Renderable
			<- Placeable

Pros : we avoid a complex dependencies management implementation.

Cons : we over-Stamp some objects

It's a good question to ask once some development is on the road.

## Tooling

We use NPM as package-manager.

## TODOS

* Init NPM (OK)
* Install Stamp{it}
* Improve Stamp{it} with a dependencies mechanism
* Create a Stamp for Canvas and at least one famous rendering library (Three.js for example)
* Create a 'Hello world' game, like a Manic shooter for example, to demonstrate the usability