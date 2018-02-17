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


#### Something about palindromes
