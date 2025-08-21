# Testing

Basic: could use std::time and compute the difference between the start and end of a function or an entire program

Unit Testing:
Arrange, Act, Assert
Arrange: Setup the test case like the variables, objects, dependencies, only test one change (isolate from other changes)
Act: Execute some state change
Assert: Assert that the result is what we expect

A unit test makes sure that a specific component works as intended

Integration tests combining unit tests within a program into a group and tets that group. used to find interface defects between the modules

System: whole application/build test

```
public class TodoListTests:
{
  [Fact]
  public void Add_SavesTodoItem()
  {
    // arrange  
    var list = new TodoList();
    

    //act
    list.Add(new("Test Content");

    //assert
    var savedItem = Assert.Single(list.All);
    Assert.NotNull(savedItem);
    Assert.Equal("Test Content", savedItem.Content);
  }
}
