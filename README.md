# CodeWars-Solutions
Questions and Answers for CodeWars

No point writing the level 8 and 7 kyu's as they are easy and do not require as much thought

# 6kyu

Q: Write a function toWeirdCase (weirdcase in Ruby) that accepts a string, and returns the same string with all even indexed characters in each word upper cased, and all odd indexed characters in each word lower cased. The indexing just explained is zero based, so the zero-ith index is even, therefore that character should be upper cased.

The passed in string will only consist of alphabetical characters and spaces(' '). Spaces will only be present if there are multiple words. Words will be separated by a single space(' ').

A: 
function toWeirdCase(string){
  var newArr = string.split(' ');
  var finalArr = [];
  for(var i=0; i < newArr.length; i++) {
      var newStr = newArr[i];
      finalArr.push([...newStr].map((x,i) => i%2 ? x : x.toUpperCase()).join(''));
  }
  return finalArr.join(' ');
}

_______________________________________________________________________________________________________________________________________

Q: Description:
Given an array (arr) as an argument complete the function countSmileys that should return the total number of smiling faces.
Rules for a smiling face:
-Each smiley face must contain a valid pair of eyes. Eyes can be marked as : or ;
-A smiley face can have a nose but it does not have to. Valid characters for a nose are - or ~
-Every smiling face must have a smiling mouth that should be marked with either ) or D.
No additional characters are allowed except for those mentioned.
Valid smiley face examples:
:) :D ;-D :~)
Invalid smiley faces:
;( :> :} :]

A:
function countSmileys(arr) {
var count = 0;
var possibleSmiley = [':D',':~)',';~D',':)',':-)',':-D',';-D',';D',';-)',';)',';~)',':~D'];
for(var i=0; i<arr.length; i++){
  for(var j=0; j<possibleSmiley.length; j++){
    if( arr[i] === possibleSmiley[j] ){
      count++;
    }
  }
}
return count;
}

_______________________________________________________________________________________________________________________________________

Q: #Srot the inner ctnnoet in dsnnieedcg oredr

You have to sort the inner content of every word of a string in descending order.
The inner content is the content of a word without first and the last char.

Some examples:

"sort the inner content in descending order" -> "srot the inner ctonnet in dsnnieedcg oredr"
"wait for me" -> "wiat for me"
"this kata is easy" -> "tihs ktaa is esay"

The string will never be null and will never be empty.
It will contain only lowercase-letters and whitespaces.

A:
function sortTheInnerContent(words){
  return words.split(" ").map( x => x.length < 3 ? x : x.charAt(0)+x.slice(1,-1).split("").sort((a,b)=>b>a).join("")+x.charAt(x.length-1)).join(" ");
}

_______________________________________________________________________________________________________________________________________

Q: Write a method that accepts a list of objects of type Animal, and returns a new list. The new list should be a copy of the original list, sorted first by the animal's number of legs, and then by its name.

If null is passed, the method should return null. If an empty list is passed, it should return an empty list back.

A: 
function sortAnimal(animal) {
    return Array.isArray(animal) ? animal.sort( (a,b)=> a.name > b.name).sort( (a,b)=> a.numberOfLegs - b.numberOfLegs) : null;
}

_______________________________________________________________________________________________________________________________________

Q: You are given a string of numbers between 0-9. Find the average of these numbers and return it as a floored whole number (ie: no decimal places) written out as a string. Eg:

"zero nine five two" -> "four"

If the string is empty or includes a number greater than 9, return "n/a"

A:
function averageString(str) {
  if( !str ) return "n/a";
  let count = 0;
  let numObj = {'zero' : 0, 'one' : 1, 'two' : 2, 'three' : 3, 'four' : 4, 'five' : 5, 'six' : 6, 'seven' : 7, 'eight' : 8, 'nine' : 9 };
  let arr = str.split(" ");
  for ( let i = 0; i < arr.length; i++ ){
    if ( numObj[ arr[i] ] == null ) {console.log("NO FIND "+arr[i]); return "n/a";}
    count += numObj[ arr[i] ];
  }
  return Object.keys(numObj)[ Math.floor(count/arr.length) ];
}

_______________________________________________________________________________________________________________________________________

Q: Write simple .camelCase method (camel_case function in PHP, CamelCase in C# or camelCase in Java) for strings. All words must have their first letter capitalized without spaces.

A:
String.prototype.camelCase=function(){
  return this.split(" ").map( x => x.charAt(0).toUpperCase()+x.substring(1,x.length) ).join("");
}

_______________________________________________________________________________________________________________________________________

Q: If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

Note: If the number is a multiple of both 3 and 5, only count it once.

A: 
function solution(number){
  var num = 0;
  
  for(var i = 0; i<number ; i++){
    if( (i%3==0) || (i%5==0) ){
      num+=i;
    }
  }
  return num;
}

_______________________________________________________________________________________________________________________________________

Q: You get an array of arrays.
If you sort the arrays by their length, you will see, that their length-values are consecutive.
But one array is missing!


You have to write a method, that return the length of the missing array.

Example:
[[1, 2], [4, 5, 1, 1], [1], [5, 6, 7, 8, 9]] --> 3

If the array of arrays is null/nil or empty, the method should return 0.

When an array in the array is null or empty, the method should return 0 too!
There will always be a missing element and its length will be always between the given arrays.

A:
function getLengthOfMissingArray(arrayOfArrays) {
   return !arrayOfArrays||(arr=arrayOfArrays.map((x,y)=>x?x.length:0).sort((a,b)=>a-b)).indexOf(0)>-1
         ?0:arr.filter((x,y)=>x!=y+arr[0]).concat([1])[0]-1;
}

_______________________________________________________________________________________________________________________________________

Q: Polycarpus works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, he has decided to take a couple of old songs and make dubstep remixes from them.

Let's assume that a song consists of some number of words (that don't contain WUB). To make the dubstep remix of this song, Polycarpus inserts a certain number of words "WUB" before the first word of the song (the number may be zero), after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), and then the boy glues together all the words, including "WUB", in one string and plays the song at the club.

For example, a song with words "I AM X" can transform into a dubstep remix as "WUBWUBIWUBAMWUBWUBX" and cannot transform into "WUBWUBIAMWUBX".

Recently, Jonny has heard Polycarpus's new dubstep track, but since he isn't into modern music, he decided to find out what was the initial song that Polycarpus remixed. Help Jonny restore the original song.

Input
The input consists of a single non-empty string, consisting only of uppercase English letters, the string's length doesn't exceed 200 characters

Output
Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.

Examples
songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB")
  // =>  WE ARE THE CHAMPIONS MY FRIEND
  
  
A: 
function songDecoder(song){
 return song.split("WUB").filter(x=>x!='').join(" ");
}

_______________________________________________________________________________________________________________________________________

Q: Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

Examples: spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" spinWords( "This is a test") => returns "This is a test" spinWords( "This is another test" )=> returns "This is rehtona test"

A: 
function spinWords(str){
  return str.split(" ").map((x)=>{return x.length>4? x.split("").reverse().join("") :x; }).join(" ");
}

______________________________________________________________________________________________________________________________________

Q: In this kata you have to write a simple Morse code decoder. While the Morse code is now mostly superceded by voice and digital data communication channels, it still has its use in some applications around the world.
The Morse code encodes every character as a sequence of "dots" and "dashes". For example, the letter A is coded as ·−, letter Q is coded as −−·−, and digit 1 is coded as ·−−−−. The Morse code is case-insensitive, traditionally capital letters are used. When the message is written in Morse code, a single space is used to separate the character codes and 3 spaces are used to separate words. For example, the message HEY JUDE in Morse code is ···· · −·−−   ·−−− ··− −·· ·.

NOTE: Extra spaces before or after the code have no meaning and should be ignored.

In addition to letters, digits and some punctuation, there are some special service codes, the most notorious of those is the international distress signal SOS (that was first issued by Titanic), that is coded as ···−−−···. These special codes are treated as single special characters, and usually are transmitted as separate words.

Your task is to implement a function that would take the morse code as input and return a decoded human-readable string.

A: 
decodeMorse = function(morseCode){
  return morseCode.split("   ").map(y=>{y=y.split(" ").map(x=>{return MORSE_CODE[x];}).join("");return y;}).join(" ").trim();
}

_______________________________________________________________________________________________________________________________________

Q: Cara is applying for several different jobs. The online application forms ask her to respond within a specific character count. Cara needs to check that her answers fit into the character limit.

Annoyingly, some application forms count spaces as a character, and some don't.

Your challenge:

Write Cara a function charCheck() with the arguments:

"text": a string containing Cara's answer for the question
"max": a number equal to the maximum number of characters allowed in the answer
"spaces": a boolean which is True if spaces are included in the character count and False if they are not
The function charCheck() should return an array: [True, "Answer"] , where "Answer" is equal to the original text, if Cara's answer is short enough.

If her answer "text" is too long, return an array: [False, "Answer"]. The second element should be the original "text" string truncated to the length of the limit.

When the "spaces" argument is False, you should remove the spaces from the "Answer".

For example:

charCheck("Cara Hertz", 10, True) should return [ True, "Cara Hertz" ]
charCheck("Cara Hertz", 9, False) should return [ True, "CaraHertz" ]
charCheck("Cara Hertz", 5, True) should return [ False, "Cara " ]
charCheck("Cara Hertz", 5, False) should return [ False, "CaraH" ]

A: 
function charCheck(text, max, spaces){
  if(!spaces){
    text = text.replace(/ /g,"");  
  };
  return [text.length<=max ? true : false,text.slice(0,max)];
};

_______________________________________________________________________________________________________________________________________
_______________________________________________________________________________________________________________________________________

# 5Kyu

Q: Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

A: 
var moveZeros = function (arr) {
  var zeros = [];
  var newArr = [];
  for(var i=0;i<arr.length;i++){
    if( (Number.isInteger(arr[i])) && (arr[i]==0) ){
      zeros.push(0);
    }else{
      newArr.push(arr[i]);
    }
  }
  return newArr.concat(zeros);
}

_______________________________________________________________________________________________________________________________________

# 4Kyu

Q: Given the string representations of two integers, return the string representation of the sum of those integers.

A:
function sumStrings(a,b) {
  let str1a = a.split('').reverse();
  let str2a = b.split('').reverse();
  let output = '';
  let longer = Math.max(a.length, b.length);
  let carry = false;
  for (let i = 0; i < longer; i++) {
    let result = 0;
    if (str1a[i] && str2a[i]) {
      result = parseInt(str1a[i]) + parseInt(str2a[i]);

    } else if (str1a[i] && !str2a[i]) {
      result = parseInt(str1a[i]);

    } else if (!str1a[i] && str2a[i]) {
      result = parseInt(str2a[i]);
    }

    if (carry) {
        result += 1;
        carry = false;
    }
    if(result >= 10) {
      carry = true;
      output += result.toString()[1];
    }else {
      output += result.toString();
    }
  }
  output = output.split('').reverse().join('');

  if(carry) {
    output = '1' + output;
  }
  return output.replace(/^0+/, '');

}

_______________________________________________________________________________________________________________________________________

Q: Write a function that, given a string of text (possibly with punctuation and line-breaks), returns an array of the top-3 most occurring words, in descending order of the number of occurrences.

Assumptions:
A word is a string of letters (A to Z) optionally containing one or more apostrophes (') in ASCII. (No need to handle fancy punctuation.)
Matches should be case-insensitive, and the words in the result should be lowercased.
Ties may be broken arbitrarily.
If a text contains fewer than three unique words, then either the top-2 or top-1 words should be returned, or an empty array if a text contains no words.
Examples:
top_3_words("In a village of La Mancha, the name of which I have no desire to call to
mind, there lived not long since one of those gentlemen that keep a lance
in the lance-rack, an old buckler, a lean hack, and a greyhound for
coursing. An olla of rather more beef than mutton, a salad on most
nights, scraps on Saturdays, lentils on Fridays, and a pigeon or so extra
on Sundays, made away with three-quarters of his income.")
# => ["a", "of", "on"]

top_3_words("e e e e DDD ddd DdD: ddd ddd aa aA Aa, bb cc cC e e e")
# => ["e", "ddd", "aa"]

top_3_words("  //wont won't won't")
# => ["won't", "wont"]

A: 
function topThreeWords(text) {
  var filters = ['.',',','\"'];
  var newArr = text.split(' ').map(x => x.toLowerCase().replace(/^\/|\/$/gi, '').replace(/^\/|\/$/gi, '')).sort().filter( (x)=> {
  if( x.includes(filters[0]) || x.includes(filters[1]) || x.includes(filters[2])){ 
      return false;    
  }return x;
  });
  
  var newObj = [];
  var currentCount = 1;
  for(var i=0; i<newArr.length; i++){    
    var currentLetter = newArr[i];       
    if(currentLetter == newArr[i+1]){
      currentCount++;
    }else{
      newObj.push({letter: currentLetter, count: currentCount});
      currentCount=1;
    }   
  }
  newObj = newObj.sort( (a,b)=> { return b.count - a.count } );
  if(newObj[0] === undefined || newObj[0].letter=='\''){
    return [];
  }else return [...newObj].map( (x,i)=>{ return i<3 ? x.letter : false  } ).slice(0,3);
}

_______________________________________________________________________________________________________________________________________





































