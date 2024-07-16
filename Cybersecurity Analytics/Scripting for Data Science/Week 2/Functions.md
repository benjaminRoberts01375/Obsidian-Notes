Functions allows the programmer to reuse and compartmentalize code to prevent writing the same code over and over. Over time, programming languages have been able to improve the usage of functions by allowing them to be combined with objects, functions becoming first class to use as types and values (Sundell, 2018), and closures (Swift Foundation, n.d.). While these features are appreciated, the core functionality and reason of functions remain: breaking code into smaller pieces for readability, and for code reuse. Here's an example:

```python
def onGuestList(guestCheck: str):
	guestList = ["Ben", "Sally", "Steve", "Emily"]
	for guest in guestList:
		if guest == guestCheck:
			return True
	return False

def greetGuest(guest: str):
	print(f"Hello, {guest}")
	print("You may come right this way!")

def denyGuest(person: str):
	print(f"I'm sorry {person}, but you need to be on the list.")
	print("Feel free to sign up for next time.")

if __name__ == "__main__":
	guest = "Ryan"
	if onGuestList(guest):
		greetGuest(guest)
	else:
		denyGuest(guest)
```

This example attempts to greet guests who have been invited, while informing those not intended to arrive to sign up. What this example accomplishes is made easy to read by grouping code into functions, check if the guest is on the guest list, if they are then greet them, otherwise deny them. The complexity of the functions have been abstracted away, and only the relevant details are present within each of the functions. 

Functions are even capable of calling functions which includes themselves, and while convenient, when calling functions from other functions too many times may result in a stack overflow. When a function returns, the instruction pointer goes back to the point in memory where it last was before it had jumped to the function, but the computer needs to remember what memory was created by the function, and where. To do this, the computer uses a stack to order what functions where called in order, popping the last item added when the function returns. However if that stack grows too large (such as when a function accidentally calls itself thousands or millions of times), a stack overflow error is thrown, and the program typically crashes (Sheldon 2022).

_First class functions in Swift | Swift by Sundell_. (n.d.). Swift by Sundell. https://www.swiftbysundell.com/articles/first-class-functions-in-swift/#:~:text=Languages%20that%20support%20first%20class,as%20%22first%20class%20citizens%22.

Sheldon, R. (2022, July). _Stack overflow_. WhatIs. Retrieved July 10, 2024, from https://www.techtarget.com/whatis/definition/stack-overflow

Swift Foundation. (n.d.). _Closures_. Retrieved July 10, 2024, from https://docs.swift.org/swift-book/documentation/the-swift-programming-language/closures/