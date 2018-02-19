### Functions created in Algorithm section


#### Reverse a string (done without higher order functions)

let reverseString = (str) => {
  let newStr = ''
  
  for(var i = str.length; i > 0; i--){
    newStr += str.charAt(i-1)
  }
  
  return newStr
}


#### Factorialize a Number (done using the turnary style for if / else statement)

let factorialize = (num) => num == 1 || !num ? 1 : num * factorialize(num-1)


#### Check for palindromes
let palindrome = (str) => {
    let str2 = ''
  
    str = str.replace(/_|\W+/g, '').toLowerCase()
    str2 = str.split('').reverse().join('')
  
    return str === str2
}


#### Find the Longest Word in a String
let findLongestWord = (str) => {
    return Math.max.apply(null, str.split(' ').map(x => x.length));
}


#### Title Case a Sentence
let titleCase = (str) => {
  return  str.toLowerCase()
              .split(' ')
               .map(x => {
                  x = x.split('')
                  x[0] = x[0].toUpperCase()
                  return x.join('')
                })
                .join(' ')
}


#### Return Largest Number in Arrays
let largestOfFour = (arr) => {
    return arr.map(x => Math.max.apply(null, x))
    }


#### No repeats please
	YT_watch?v=B5lUyJDkWzE
