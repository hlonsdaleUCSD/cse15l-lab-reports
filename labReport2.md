# CSE15L Lab Report 2
## Harry Lonsdale

## Part 1: StringServer and localhost
![Image](StringServerCode.png)
**This was the code for my StringServer**
<br/><br/>
![Image](add%20this.png)
<br/>
![Image](andThisToo.png)
<br/>
**And here are some screenshots of it in use**. 

For the **first** screenshot:
- Which methods in your code are called?

  My code would first run the `main` method of the class StringServer which calls `server.start` with a new instantiation of the Handler class. When a new url is typed in, the Handler's `handleRequest` method is called.
- What are the relevant arguments to those methods, and the values of any relevant fields of the class?

  The argument to the `main` method of StringServer is the port number, which is relevant as it is used to decide the localhost port number on which the server will run. The arguments for `server.start` are important because they determine the port number (passed in from main) and the Handler that it will use, which is a new instantiation of the class I wrote. The argument passed into `handleRequest` is the url that is typed in, which determines the function of the program. The value of `String str` is "add this\n" after this screenshot.
- How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why

  The value of `String str` was changed by this specific request because "add this\n" was concatenated to `str`. Before this was run, `str` was just the empty String "".

For the **second** screenshot:
- Which methods in your code are called?

 My code would first run the `main` method of the class StringServer which calls `server.start` with a new instantiation of the Handler class. When a new url is typed in, the Handler's `handleRequest` method is called.
 
 - What are the relevant arguments to those methods, and the values of any relevant fields of the class?

  The argument to the `main` method of StringServer is the port number, which is relevant as it is used to decide the localhost port number on which the server will run. The arguments for `server.start` are important because they determine the port number (passed in from main) and the Handler that it will use, which is a new instantiation of the class I wrote. The argument passed into `handleRequest` is the url that is typed in, which determines the function of the program. The value of `String str` is `"add this\nandThisToo\n"` after this screenshot.
  
 - How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why

  The value of `String str` was changed by this specific request because "andThisToo\n" was concatenated to `str`. Before this was run, `str` was `add this\n`.
  
## Part 2: Bug Hunting

The bug that I'm choosing to report on is the bug in `averageWithoutLowest`.

Here's a failure-inducing jUnit test for this method.
```
  @Test
  public void testAverageWithoutLowest(){
    double[] input = new double[]{1.2, 1.2, 1.2, 1.2, 1.2};
    double output = ArrayExamples.averageWithoutLowest(input);
    assertEquals(1.2,output,0.0);
  }
```

- The expected output of this code is 1.2, because even if you drop the single lowest value (one of the 1.2s), the other four 1.2s will still cause the average to be 1.2.
- However, the output for that jUnit test is the following:
```
1) testAverageWithoutLowest(ArrayTests)
java.lang.AssertionError: expected:<1.2> but was:<0.0>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:555)
	at org.junit.Assert.assertEquals(Assert.java:685)
	at ArrayTests.testAverageWithoutLowest(ArrayTests.java:33)
```

As you can see, the returned value was **0.0**, not what we expected!
