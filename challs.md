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


#### DNA Pairing
function pairElement(str) {
    return str.split('').map( x => {
        return ( x == 'G') ? ['G','C'] :
            ( x == 'C') ? ['C','G'] : 
            ( x == 'A') ? ['A','T'] :
            ( x == 'T') ? ['T','A'] : "Not a DNA character" 
    })
}


#### Missing Letters
function fearNotLetter(str) {
    let len = str.length, i = 1
    for ( ; i < len; i++) {
        if ( str.charCodeAt( i - 1 ) !== ( str.charCodeAt( i ) - 1 )) {
          return String.fromCharCode(str.charCodeAt( i ) - 1 )
        }
    }
    return undefined
}


#### Boo Who
function booWho(bool) {
  return bool === true || bool === false;
}


#### Sorted Union
function uniteUnique(arr) {
    let tmpArr  
    [arr, ...tmpArr] = arguments
    tmpArr.forEach( x => {
        arr = arr.concat(x.filter( y => !(arr.includes(y))))
    })
    return arr
}


#### Convert HTML Entities
function convertHTML(str) {
  str = str.replace(/&/g, "&amp;")
  str = str.replace(/"/g, "&quot;")
  str = str.replace(/'/g, "&apos;")
  str = str.replace(/</g, "&lt;")
  return str.replace(/>/g, "&gt;")
}


#### Spinal Tap Case
function spinalCase(str) {
    return str.replace(/(\S)\s+(\S)|([a-z]+)_?([A-Z]{1})/g, '$1$3-$2$4').toLowerCase();
}


#### Sum All Odd Fibonacci Numbers
function sumFibs(num) {
    let o = 1, o2 = 1, next = 2, sum = 2;
    while ( next <= num ) {
        o2 = o; o = next;
        next = o + o2
        sum += o % 2 && o
    }
    return sum;
}


#### Sum All Primes
function sumPrimes(num) {
    let sum = 0
    for ( let i = 2; i <= num; i++) {
        let quot = 0
        for (let k = 1; k <= i; k++) {
            if ( i % k === 0 ) quot += k
        }
        if ( i + 1 === quot ) sum += i
    }
    return sum
}


#### Smallest Common Multiple
function smallestCommons(arr) {    Shorter code.
    arr.sort((a,b) => a - b )
    let potentialSCM = arr[1], loopCount = 1
    while (true) {
        let remainder = 0
        for (let i = arr[0]; i <= arr[1]; i++) {
            remainder += ( potentialSCM % i )
        }
        if (!remainder) return potentialSCM;
        loopCount++
        potentialSCM = loopCount * arr[1]
    }
}

function smallestCommons(arr) {   Likely faster code.
    arr.sort((a,b) => a - b )
    let potentialSCM = arr[1], loopCount = 1, fullArr = [] 
    for (let i = arr[0]; i <= arr[1]; i++) {
        fullArr.push(i)
    }
    while (true) {
        let remainder = 0
        fullArr.forEach( x => {
            remainder += potentialSCM % x
        })
        if (!remainder) return potentialSCM;
        loopCount++
        potentialSCM = loopCount * arr[1]
    }
}


#### Finders Keepers
function findElement(arr, func) {
    return arr.find(func);
}


#### Drop It
function dropElements(arr, func) {
    let sliceFrom = arr.reduce( (rslt, cur, i) => {
        return rslt === arr.length && func(cur) ? i : rslt
    }, arr.length)
    return arr.slice(sliceFrom);
}


#### Steamroller
function steamrollArray(arr) {
    let rsltArr = []
    arr.forEach( x => {
        ( Array.isArray( x ) ) ? (
            steamrollArray( x ).forEach( y => rsltArr.push( y ) )
        ) : (
            rsltArr.push( x )
        )
    })
    return rsltArr
}


#### Binary Agents
function binaryAgent(str) {
    return str.split(' ').map( x => String.fromCharCode( parseInt( x, 2 )) ).join('')
}


#### Everything Be True
function truthCheck(collection, pre) {
    return collection.every( x => Boolean(x[pre]));
}


#### Arguments Optional
function addTogether() { 
    let sum = 0
    for ( let i =0; i < arguments.length; i++) {
        typeof arguments[i] !== 'number' ? sum = undefined : sum += arguments[i]
    }
    if ( arguments.length > 1 || sum === undefined ) {
        return sum
    }
    else {   
        return function needNum( secondNum ) {
            return ( typeof secondNum !== 'number' ) ? undefined : sum + secondNum
        }
    }        
}


#### No repeats please
	YT_watch?v=B5lUyJDkWzE
