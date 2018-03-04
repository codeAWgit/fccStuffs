### Functions created in Algorithm section


#### Reverse a string (done without higher order functions)
let reverseString = (str) => {
    let newStr = ''
    for(var i = str.length; i > 0; i--){
        newStr += str.charAt(i-1)
    }
    return newStr
}


#### Factorialize a Number 
##### First way I learned to make this function.
function factorialize(num) {
    let result = 1
	for (let i = 1; i <= num ; i++){
		result *= i;
	}
	return result;
} 
##### Second way I learned to make this function.
function factorialize(num) {		 
	if (num == 1 || !num){
      return 1}
	return num * factorialize(num-1)
}

##### (done using the ternary style for if / else statement)
let factorialize = (num) => num == 1 || !num ? 1 : num * factorialize(num-1)

##### or for tail call optimization
let factorialize = (num, acc = 1 ) {
    if (num < 2 ) return acc
    return factorialize(num - 1, num * acc)
}


#### Check for palindromes
let palindrome = (str) => {
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


#### Confirm the Ending
let confirmEnding = (str, target) => {
    let len = target.length
    return target === str.substr(0-len,len)
}


#### Repeat a String Repeat a String
let repeatStringNumTimes = (str, num) => {
    if(num < 1) num = 0
    return str.repeat(num);
}


#### Truncate a String
let truncateString = (str, num) => {
    return (num <= 3) ? str.slice(0,num) + '...' :
        (str.length <= num) ? str.slice(0,num) :
        str.slice(0,num - 3) + '...'
}


#### Chunky Monkey
let chunkArrayInGroups = ( arr, size, newRay = [] ) => {
    while( arr.length ) { 
        newRay.push( arr.splice( 0,size ))
    }
    return newRay
}


#### Slasher Flick
let slasher = (arr, howMany) => {
    return arr.slice(howMany);
}


#### Mutations
let mutation = (arr) => {
    arr[1].toLowerCase().split('').forEach( x => {
        if (arr[0].toLowerCase().indexOf(x) === -1) arr[0] = ''
    })
    return Boolean(arr[0]);
}


#### Falsy Bouncer
let bouncer = (arr) => {
    return arr.filter( x => x )
}


#### Seek and Destroy
function destroyer(arr) {
    let i = arguments.length;
    while( i-- ){
        arr = arr.filter(x => x !== arguments[i])
    }
    return arr;
}


#### Where Do I Belong?
let getIndexToIns = (arr, num) => {
  arr.push(num)
  return arr.sort((a, b) => a - b).indexOf(num)
}


#### Caesar's Cipher
let rot13 = (str) => { // LBH QVQ VG!
    let deCodeROT13 = m => {
        return String.fromCharCode(m.charCodeAt() + 
            (/[A-M]/.test(m) ? 13 : -13))
    }
    return str.replace(/\w/g, deCodeROT13)
}


#### Sum All Numbers in a Range
let sumAll = (arr, rslt = 0) => {
        arr.sort( (a,b) => a - b)
        do{
            rslt += arr[0]  
        } while (arr[1] > arr[0]++)
    return rslt
}


#### Diff Two Arrays
function diffArray(arr1, arr2) {
    return [...arr1,...arr2]
        .filter( x => arr1.indexOf(x) == -1 || arr2.indexOf(x) == -1)
}


#### Roman Numeral Converter
function convertToRoman(num) {
    num = '0'.repeat(4 - String(num).length) + String(num)
    let fStr = ''

    for(let i = 0, len = num.length ; i < len ; i++){
        if (+num[i] === 0) continue
        let lettersToUse = [['_X','_V','M'],['M','D','C'],['C','L','X'],['X','V','I']]                 
        fStr += buildRoman(+num[i], ...lettersToUse[i])
    }

    function buildRoman(digit, t, f, o){
        return (digit === 9) ? o + t :
                (digit === 4) ? o + f :
                (digit === 5) ? f :
                (digit < 4) ? o.repeat(digit) :
                f + o.repeat(digit - 5)
    }
    return fStr
}


#### Wherefore Art Thou
function whatIsInAName(collection, source) {
    var arr = [];
    for ( let element of collection) {
        let inElement = true
        for ( let prop in source) {
            if ( !(prop in element) || source[prop] !== element[prop] && inElement) {
                inElement = false
            }
        }
        if (inElement) arr.push(element)
    }
    return arr;
}


#### Search and Replace
function myReplace(str, before, after) {
    return str.replace(before, preverveCase())

    function preverveCase() {
        if ( before.charCodeAt(0) < 91 ) {
            return after.charAt(0).toUpperCase() + after.slice(1)
        }
        return after
    }
}


#### Pig Latin
function translatePigLatin(str) {
    str = str.replace(/(\b[aeiou]\w+)/, '$1way')
    return str.replace(/(\b[^aeiou]+)(\w+)/, '$2$1ay')
}


#### 





#### No repeats please
	YT_watch?v=B5lUyJDkWzE
