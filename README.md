**Problem Statement**

Consider a function that squares all elements of a list and returns a list with the results. Complete the following two equivalent definitions of
squareList

def squareList(list: List[Int]): List[Int] =
 list match {
   case Nil => ??
   case  h:: t => ??
}

def squareList(list: List[Int]): List[Int] =
list map ??


**Solution**


**Code For the Problem**

```
package com.knoldus.square

case class SquareOfList(userList: List[Int]) {

  // Function to square the elements of the list using map() function.
  def squaredListUsingMap(): List[Int] = {
    val newSquaredList = userList.map(element => element * element)
    newSquaredList
  }

  // Function to square the elements of the list using Pattern Matching.
  def squaredListUsingPatternMatching(list: List[Int]): List[Int] = {
    list match {
      case Nil => Nil
      case head :: tail => head * head :: squaredListUsingPatternMatching(tail)
    }
  }
}
```


**Code For Test Cases**

```
package com.knoldus.square

import org.scalatest.funsuite.AnyFunSuite

class SquareOfListTest extends AnyFunSuite {

  test("SquareOfList.squaredListUsingMap should return the squared list using map") {
    val inputList = List(1, 2, 3, 4)
    val expectedOutput = List(1, 4, 9, 16)
    assert(SquareOfList(inputList).squaredListUsingMap() == expectedOutput)
  }

  test("SquareOfList.squaredListUsingMap should turn the negative list in positive squared list using map") {
    val inputList = List(-3, -4, -8, -9)
    val expectedOutput = List(9, 16, 64, 81)
    assert(SquareOfList(inputList).squaredListUsingMap() == expectedOutput)
  }

  test("SquareOfList.squaredListUsingPatternMatching should return the squared list using pattern matching") {
    val inputList = List(1, 2, 3, 4)
    val expectedOutput = List(1, 4, 9, 16)
    assert(SquareOfList(inputList).squaredListUsingPatternMatching(inputList) == expectedOutput)
  }

  test("SquareOfList.squaredListUsingPatternMatching should turn the negative list in positive squared list using pattern matching") {
    val inputList = List(-3, -4, -8, -9)
    val expectedOutput = List(9, 16, 64, 81)
    assert(SquareOfList(inputList).squaredListUsingPatternMatching(inputList) == expectedOutput)
  }

  test("SquareOfList.squaredListUsingMap should return an empty list for an empty input list") {
    val inputList = List.empty[Int]
    val expectedOutput = List.empty[Int]
    assert(SquareOfList(inputList).squaredListUsingMap() == expectedOutput)
  }

  test("SquareOfList.squaredListUsingPatternMatching should return an empty list for an empty input list") {
    val inputList = List.empty[Int]
    val expectedOutput = List.empty[Int]
    assert(SquareOfList(inputList).squaredListUsingPatternMatching(inputList) == expectedOutput)
  }

}
```

