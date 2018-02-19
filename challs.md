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


#### Factorialize a Number (done using the turnary style for if / else statement)

let factorialize = (num) => num == 1 || !num ? 1 : num * factorialize(num-1)

factorialize(5);



#### Check for palindromes
function palindrome(str) {
    let str2 = ''
  
    str = str.replace(/_|\W+/g, '').toLowerCase()
    str2 = str.split('').reverse().join('')
  
    return str === str2
}
palindrome("eye")


#### Find the Longest Word in a String
let findLongestWord = (str) => {
    return Math.max.apply(null, str.split(' ').map(x => x.length));
}

#### Title Case a Sentence
function titleCase(str) {
  return  str.toLowerCase()
              .split(' ')
               .map(x => {
                  x = x.split('')
                  x[0] = x[0].toUpperCase()
                  return x.join('')
                })
                .join(' ')
}

titleCase("I'm a little tea pot");


#### Return Largest Number in Arrays



#### No repeats please
	YT_watch?v=B5lUyJDkWzE
