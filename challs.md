### Functions created in Algorithm section


#### Reverse a string (done without higher order functions)
function reverseString(str) {
  let newStr = ''
  
  for(var i = str.length; i > 0; i--){
    newStr += str.charAt(i-1)
  }
  
  return newStr
}
reverseString("hello");


#### Factorialize a Number

function factorialize(num) {		
	return (num == 1 || !num ? 1 : num * factorialize(num-1))
}


#### Check for palindromes
function palindrome(str) {
    let str2 = ''
  
    str = str.replace(/_|\W+/g, '').toLowerCase()
    str2 = str.split('').reverse().join('')
  
    return str === str2
}
palindrome("_eye")


#### Find the Longest Word in a String



#### No repeats please
	YT_watch?v=B5lUyJDkWzE
