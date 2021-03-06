#Task 2: IoC with Microsoft Unity

## IoC Container

* IoC Container keeps track of implementations of interfaces (services, 
  components).
* It helps you wire objects together without doing so explicitly and writing 
  your own infrastructure.
* It can provide even more - for example lifetime management.
* When registering and consuming dependencies as interfaces you do not have to
  worry who the implementor is and how to construct it - container takes the 
  responsibility and does things for you.
* Dependencies defined as interfaces have some benefits:
  * Classes are much easier to unit test.
  * Changing the implementation (strategy) is just matter of different 
    registration into IoC container.
* Adding a new dependency to any of classes is as simple as adding a new 
  interface parameter to constructor (or respectively as a parameter to an 
  injection method or dependency property - see next tasks).

## How to start?

1. The project is currently using constructor injection.
2. Get familiar with project 020_IoCWithUnity.
3. Identify all interfaces and their implementors.
4. Find the ```Bootstrapper``` class.
  * It is good practice to extract all dependency registrations into a single
    place (bootstrapper is a common name).
  * Properly implement its ```SetupContainer()``` method.
  * Alternative to ```Bootstrapper``` class could be XML config file. 
    Benefit of config file is ability to change dependencies as part of 
	deployment.
	Downside is that the config file is more verbose, harder to maintain. ReSharper
	doesn't have full powers there.

## Extras

* Feel free to modify the solution by providing new implementations of interface
  IOperation, e.g. Minus.
* Try implement another ```IResultWriter``` which will write result to a file 
  name and configure Unity to start using it instead of ```ConsoleResultWriter```.

## Sample solution

* ```Bootstrapper``` class now registers properly all the dependencies as 
  needed.
* We have added ```Minus``` class and ```IOperationMinus``` to get minus 
  operation working.
* Also there is an alternative implementation of ```IResultWriter```. See 
  ```Bootstrapper``` class for comment on usage.
  * Actually this demonstrates one of the IoC container benefits - you can 
  quickly change an implementation of an interface to a different one.

## Solution

* For more info about the sample solution please see IoCTaskSolutions, project 
  020_IoCWithUnity.
* Read the comments throughout the code carefully, they contain important 
  informations in regards inversion of control and dependency injection.
