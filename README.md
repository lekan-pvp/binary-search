# Binary Search by Iteration and Recursion

    package main

    import "fmt"

    var mid int

    // Brutforce method
    func LinearSearch(data []int, target int) bool {
      for i := 0; i < len(data); i++ {
        if data[i] == target {
          return true
        }
      }
      return false
    }

    // Binary iterative search
    func BinarySearchIterative(data []int, target int) bool {
      low := 0
      high := len(data) - 1

      for low <= high {
        mid = (low + high) / 2
        if target == data[mid] {
          return true
        } else if target < data[mid] {
          high = mid - 1
        } else if target > data[mid] {
          low = mid + 1
        }
      }
      return false
    }

    func BinarySearchRecursive(data []int, target int, low int, high int) bool {

      if low > high {
        return false
      } else {
        mid = (low + high) / 2
        if target == data[mid] {
          return true
        } else if target < data[mid] {
          return BinarySearchRecursive(data, target, low, mid-1)
        } else {
          return BinarySearchRecursive(data, target, mid+1, high)
        }
      }
    }

    func main() {
      data := []int{2, 4, 5, 7, 8, 9, 12, 14, 17, 19, 22, 25, 27, 28, 33, 37}
      target := 37
      result1 := BinarySearchIterative(data, target)
      fmt.Println(result1)
      result2 := BinarySearchRecursive(data, target, 0, len(data)-1)
      fmt.Println(result2)
    }
