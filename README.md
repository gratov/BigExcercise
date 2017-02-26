# Big Excercise
## Papa Smurf's potion store
Papa Smurf is a well known potions brewer. Smurfs from all over the world travel to our small town, in order to buy his potions.
As his evergrowing fame keeps on growing, papa smurf's workload grows with it. He's been brewing potions non stop lately and with barely enough time to eat and sleep.
But then disaster strikes: Papa smurf is running low on troll's toe cheese and in his desperation he turns to us for help.
This is what he needs:


![grotesmurf](grotesmurf.jpg)
> **UserStories**
>
1. Papa smurf needs a service to keep track of all the ingredients he has left in his closet, without having to count them himself.
2. His closet contains 5 shelves, each shelf for a category of ingredients: -liquid ingredients -herbs & spices -special types of rock -rare ingredients -miscelanious ingredients
3. Ingredients should have a name, description, price and a gathering date as some products tent to expire rather quickly.
4. Papa smurf would like to see these lists, in 2 ways: -all categories side by side, displaying only ingredient name & amount. -a page for each category displaying all ingredients of that category in detail. Details of the same products but with different gathering date should be grouped by gathering date. 
5. Liquid ingredients generally expire after a month, herbs after 1 week,rocks don't expire,rare & miscelanious items have a item specific expiery time
6. 










xx. Papa smurf also needs a service to order new ingredients when his supply is running low. This should be possible either by the click of a button or even better, automatically when the supply of a product reaches the tresshold of 3 pieces.
xx. Each category of ingredients is delivered by a different smurf company.


```java
try{
	double calculation = 5/0;
} catch(Exception ex){
	System.out.println(ex.getMessage());
    ex.printStackTrace();
}
``` 
There are diffent kinds of exceptions we could catch:

![polymorphism](img/classdiagramException.png)

**Throwable:**
Common superclass for all exceptions. This ensures that we can throw errors within the JVM.
**Error:**
Grave system errors. Most of the time you shouldn't try to recover from these kinds of errors. For instance it's not usefull to catch an OutOfMemoryError since the only possible thing we could do is kill the program, something that is done automaticly by the JVM.
**Exceptions**
Common superclass for all exceptions you should handle.

You may catch muliple exceptions at the same time, but you should consider the order of the catch blocks.

```java
int[] intArray = new intArray[5];
try{
	intArray[6] = 5;
}catch(Throwable e){
	System.out.println("Throwable");
}catch(Exception e){
	System.out.println("Exception");
}catch(RuntimeException e){
	System.out.println("RuntimeException");
}catch(IndexOutOfBoundsException | ArrayIndexOutOfBoundsException e){
	System.out.println("IndexOutOfBoundsException or ArrayIndexOutOfBoundsException");
}
```

> **EXCERCISE 17.2**
>
1. What do you think the previous block of code will print ?
2. How can we fix it ?

Somethimes you want to ensure a code block will be excecuted with or without failures . For instance if you are working with files you don't want to keep them connected when you encountered an error. The finally code block is designed for situations like this.
It will be excecuted eventough an error occured.

```java
try{
	intArray[6] = 5;
}catch(Throwable e){
	System.out.println("Throwable");
}finally {
	System.out.println("We executed the code");
}
```

> **EXCERCISE 17.3**
>
1. What would happen if an error occured whitin the finally block?
2. What is the difference between a ```finally``` block and just adding some code after the ```catch``` block ?

> **Lab 1:**
>
1. Create a method that takes in 2 numbers and divides them.
2. Make sure no error blocks the program.
3. If it is a divided by zero or not a number exception you should print a specific message: "Please do not divide by zero."
4. Make sure you print out a suffix.

## Difference checked and unchecked exceptions
You may already have noticed that some exceptions can be thrown and you don't need a try catch block and for other exceptions your compiler complains that you should catch or throw the exception. 

This is called between checked or unchecked exceptions.

**Unchecked**
These are all exceptions that have RuntimeException as a supperclass. 
You aren't obliged to handle these errors, but you should handle them somewhere in your code. You will use this a lot for throwing the exception to the front end without having to put throw on every method.

**Checked**
You have to handle these exceptions. You could use a try catch block or use the throws keyword. This will forward the exception to the next method.

```java
public void printFileContents() {
	try{
    	System.out.println(getFileContents());
    } catch(IOException e){
    	e.printStackTrace();
    }
}

public String getFileContents() throws IOExceptions {
	BufferedReader br = new BufferedReader(new FileReader("foo.txt"));
    StringBuilder result = new StringBuilder();
	String line = null;
    while ((line = br.readLine()) != null) {
		result.append(line);
        result.append("\n")
 	}
    return result.toString();
}
```

> **Excercise 17.4**
>
1. What is missing in the previous code block ?
2. Is the ArthemeticException checked or unchecked ?
3. When creating your own exception, why would you use a checked exception, why an unchecked?

## Creating your own exception
**Throwing an exception**
You can always throw any new exception. This is done by instantiating the exception and using the keyword throw.
```java
throw new UnsuportedOperationException("implement me after the test");
```

**Creating an exception**
You can create your own exception by extending one of the Throwable supperclasses.

```java
public class NoTeacherFoundException extends RuntimeException {

}
```

> **Lab 2**
>
1. Create your own exception KittyDiedException where you can add a message.
2. Throw this exception with the message "Another one bites the dust"
3. Why should you create your own exceptions ?
4. Did you make this a checked or unchecked exception ?

## Labs
### Lab 3

1. Create your own validation exception
2. Create a new account with following validation rules, you should return a validation error:
	1. Person should be at least 18 years old
	2. Person should have a first and last name
	3. Person should have an adress
	4. Bank account should have a starting amount
	5. Bank accout should never go under 0
3. What will happen if you have 2 validation errors? Try to figure out how to solve this. 

### Lab 4
1. Try to figure out how you can save some text to a file.
2. Does this throw checked or unchecked exceptions ?
3. Why should you use a finally block?
4. Can you replace this by something?
<details><summary>Hint</summary>
Search for something called try with resource.
</details>
5. Try to explain to a colleague what this is.
