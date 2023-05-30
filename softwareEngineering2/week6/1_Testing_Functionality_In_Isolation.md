# Testing Functionality In Isolation
![[Pasted image 20230530013353.png]]
* Unit tests should be isolated to test the functionality of a single component.
* This can be difficult as aspects of a system usually depend on other systems.
* To break these connections in testing, `test doubles` can be used, there are many types such as:
	* `Dummies`: Data that is passed around but never used.
	* `Fakes`: Generally works as expected but has shortcuts unsuitable for full production like using an in-memory database.
	* `Stub`: Provides a canned answer to a particular invocation
	* `Mock`: Has pre-programmed expectations of how it will be called and what will happen internally when it is called. This is an extension of stubs wherein more complex interactions can be programmed in (eg returning a different result from the same function based on how many times it has been called).