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


#### Validate US Telephone Numbers
function telephoneCheck(str) {
    let tF = /^1?\s?\d{3}-?\s?\d{3}-?\s?\d{4}$/.test(str);
    return tF || /^1?\s?[(]\d{3}[)]-?\s?\d{3}-?\s?\d{4}$/.test(str);
}


#### Record Collection
##### Old
function updateRecords(id, prop, value) {
  if (prop != 'tracks' && value != ''){
    collection[id][prop] = value;
  }
  else if (prop != 'tracks' && value == ''){
    delete collection[id][prop];
  }
  if (prop == 'tracks' && value == ''){
    delete collection[id][prop];
  }
  else if (prop == 'tracks' && !collection[id].hasOwnProperty(prop)){
    var tempA = [];
    tempA.push(value);
    collection[id][prop] = tempA;
  }
  else if (prop == 'tracks' && collection[id].hasOwnProperty(prop)){
    collection[id][prop].push(value);
  }
  return collection;
}

##### New
function updateRecords(id, prop, value) {
    if ( prop != 'tracks' ) collection[id][prop] = value
    if ( prop == 'tracks' && prop in collection[id] ) {
        collection[id][prop].push( value )
    }  
    if ( prop == 'tracks' && !(prop in collection[id]) ) {
        collection[id][prop] = [ value ]
    }
    if ( !value ) delete collection[id][prop]
    return collection;
}


#### Symmetric Difference
##### Old
function sym(args) {
  function flatten(arr){
  var cont = [];
    for (var i=0; i < arr.length; i++){
      if(cont.indexOf(arr[i]) == -1){
        cont.push(arr[i]);
      }
  }  return cont;
  }
  var sdContainer = flatten(args);   
  var delValue;
  function isDuplicate(value) {
    return value != delValue;
  }
  for (var k=1; k < arguments.length; k++){
    var tempCont = sdContainer.concat(flatten(arguments[k]));
    sdContainer = []; 
    for (var m=0; m < tempCont.length; m++){
      if(sdContainer.indexOf(tempCont[m]) == -1){
        sdContainer.push(tempCont[m]);
      }
      else
      {
        delValue = tempCont[m];
        sdContainer = sdContainer.filter(isDuplicate);
      }
    }
  }
return sdContainer.sort();
}

##### New
function sym(args) {
    for ( var i=1; i < arguments.length; i++) {
        let otherArg = [...arguments[i]], tmpArg = []
        args.forEach( x => {
            if ( !otherArg.includes(x) && !tmpArg.includes(x) ) tmpArg.push(x)
        })
        otherArg.forEach( x => {
            if ( !args.includes(x) && !tmpArg.includes(x) ) tmpArg.push(x)
        })
        args = tmpArg
    }
    return args;
}


#### Exact Change
##### Old
function checkCashRegister(price, cash, cid) {
  var change = [], drawerTotal = 0;
  var amntToReturn = cash * 100 - price * 100;
  var billValue = [10000,2000,1000,500,100,25,10,5,1];  // In Pennies.
  for (var i=0; i < billValue.length; i++) {
      var numOfBillsNeeded = Math.floor(amntToReturn / billValue[i]);
      var numOfBillsInDrawer = (cid[8-i][1] * 100) / billValue[i];
      var forChangeContainer = [];
      if (numOfBillsInDrawer == 0 || numOfBillsNeeded == 0) {
      }
      else if (numOfBillsInDrawer <= numOfBillsNeeded){
        forChangeContainer.push(cid[8-i][0]);
        forChangeContainer.push((numOfBillsInDrawer * billValue[i]) /100);
        change.push(forChangeContainer);
        amntToReturn -= numOfBillsInDrawer * billValue[i];
        cid[8-i][1] = 0;
      }
      else {
        forChangeContainer.push(cid[8-i][0]);
        forChangeContainer.push((numOfBillsNeeded * billValue[i]) /100);
        change.push(forChangeContainer);
        amntToReturn -= numOfBillsNeeded * billValue[i];
        cid[8-i][1] -= (numOfBillsNeeded * billValue[i]) / 100;
      }
    
      drawerTotal += cid[8-i][1] * 100;
    }
  if (amntToReturn > 0){
    return "Insufficient Funds";
  }
  if (drawerTotal == 0){
    return "Closed";
  }  
  return change;
}

##### New
function checkCashRegister(price, cash, cid) {
  var change = cash * 100 - price * 100;
  var centAmnts = [1,5,10,25,100,500,1000,2000,10000]
  var changeArr = [], cidTotal = 0
  for ( var i = cid.length - 1; i >= 0; i-- ) {
      let potential = Math.floor( change / centAmnts[i] )
      let reality = Math.floor( cid[i][1] * 100 / centAmnts[i] )
      if ( reality < potential ) {
          changeArr.push( cid[i] )
          change -= cid[i][1] * 100
      }
      else {
          changeArr.push( [cid[i][0], potential * centAmnts[i] / 100] )
          change -= potential * centAmnts[i]
          cidTotal = cid[i][1] * 100 - potential * centAmnts[i]
      }
  }
  return ( change > 0 ) ? "Insufficient Funds" : 
         ( !cidTotal ) ? "Closed" :
         changeArr.filter( e => e[1] )
}


#### Inventory Update
##### Old
function updateInventory(arr1, arr2) {
  var alphArr = [];
  var bothArr = arr1.concat(arr2);  //This puts both the inventories into one array.
  var finalArr = [];          //finalArr is the updated inventory from two previous.
  for (var i=0; i < bothArr.length; i++){    
    if (alphArr.indexOf(bothArr[i][1]) == -1){
        alphArr.push(bothArr[i][1]);
  }
  }  
  alphArr.sort();       //All unique inventory item names put in alphabetical order.
  for (var m=0; m< alphArr.length; m++){
    var itemTotal = 0;
    var loopArr = [];    
    for (var n=0; n< bothArr.length; n++){
      if (alphArr[m] == bothArr[n][1]){
        itemTotal += bothArr[n][0];
        }
      }
    loopArr.push(itemTotal);
    loopArr.push(alphArr[m]);
    finalArr.push(loopArr);
  }
  return finalArr;
}

##### New
function updateInventory(arr1, arr2) {
    let arr1Names = []
    arr1.forEach( e => arr1Names.push( e[1] ))
    arr2.forEach( e => {
        if ( !arr1Names.includes( e[1] ) ) arr1.push( e )
        else {
            arr1[ arr1Names.indexOf( e[1] ) ][0] += e[0]
        }
    })
    return arr1.sort( (a, b) => a[1] < b[1] ? -1 : 1 )
}

#### Newer Still
function updateInventory(arr1, arr2) {
    arr2.forEach( e => {
        var i = arr1.findIndex( x => x[1] === e[1] );
        i === -1 ? arr1.push( e ) : arr1[ i ][0] += e[0];
    })
    return arr1.sort( (a, b) => a[1] < b[1] ? -1 : 1 )
}


#### No repeats please
##### Old


##### New
	YT_watch?v=B5lUyJDkWzE


#### Make a Person
##### Old
var Person = function(firstAndLast) {
    // Complete the method below and implement the others similarly
  this.setFirstName = function(first){
    if(!this.fullName){
           this.fullName = firstAndLast;
    }     
    this.fullName = this.fullName.replace(/\w+/, first);  //To replace first name.
  };

  this.setLastName = function(last){
    if(!this.fullName){
           this.fullName = firstAndLast;
    }     
    this.fullName = this.fullName.replace(/(\w+\s+)(\w+)/, '$1' + last);  //Replace last name.
  };

  this.setFullName = function(firstAndLast2){
    this.fullName = firstAndLast2;
  };
  
  this.getFirstName = function() {
    if(!this.fullName){
           this.fullName = firstAndLast;
    }
      return this.fullName.replace(/(\w+)(\s+\w+)/, '$1');
    };

  this.getLastName = function() {
    if(!this.fullName){
           this.fullName = firstAndLast;
    }    
      return this.fullName.replace(/(\w+\s+)(\w+)/, '$2');
    };
  
  this.getFullName = function() {   
      return this.fullName;
    };  
};

##### New
var Person = function(firstAndLast) {
    this.getFullName = function() {
      return firstAndLast;
    };
    this.getFirstName = function() {
      return firstAndLast.split(' ')[0];
    };
    this.getLastName = function() {
      return firstAndLast.split(' ')[1];
    };
    this.setFullName = function(newFull) {
      firstAndLast = newFull; 
    };
    this.setFirstName = function(newFirst) {
      firstAndLast = `${newFirst} ${this.getLastName()}`;
    };
    this.setLastName = function(newLast) {
      firstAndLast = `${this.getFirstName()} ${newLast}`;
    };
};


#### Map the Debris
function orbitalPeriod(arr) {
    var GM = 398600.4418;
    var earthRadius = 6367.4447;
    arr = arr.map( function (x) {
      x.orbitalPeriod = Math.round( 2 * Math.PI * Math.sqrt( Math.pow(
                          x.avgAlt + earthRadius, 3 ) / GM ));
      delete x.avgAlt;
      return x;
    });
    return arr;
}


#### Pairwise
##### Old
function pairwise(arr, arg) {
  arr = arr.reduce(function(accOrI, curr, index, array){
    
    array.find(function(x, index2){
      if(arg - curr == x && accOrI.indexOf(index) == -1 && accOrI.indexOf(index2) == -1 && index != index2){
        accOrI.push(index2);
        accOrI.push(index);
      }
    });
    return accOrI;
  }
  return arr.reduce(function(sum, curVal){
    return sum + curVal;
  }, 0);
}, []);
  
  

##### New
function pairwise(arr, arg, total = 0) {
    for ( let k=0; k < arr.length; k++) {
        for ( let i = k+1; i < arr.length; i++) {
            if ( arr[k] + arr[i] === arg) {
                total += k + i
                arr[k] = undefined; arr[i] = undefined
            }
        }
    }
    return total
}
