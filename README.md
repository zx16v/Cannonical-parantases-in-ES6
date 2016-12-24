# Cannonical-parantases-in-ES6

The program flow:
1) creat a Map object to holding right bracket as key and left bracket as value.
2) looping over the input string char by char checking by using regualr expression to avoid the
   cumbersum switch-case. 
   a) using regOpen regex i check if the current char is left bracket, if so it is pushed to the stack.
   if not
   b) i check whther the current char is right bracket, if so i'll pop the last left bracket from the stack,
      the i use as a key input for GET method of the Map object, i'll execert the value of it's matching left bracket
      now i van compare, if it's identical then i can move on in the loop, if not i exit the function with false return value.
  3)  out of the loop i'm checking whtere the stack is empty, if so the input string is bracket cannonical, so it's
      return value is true otherwise false.
   


function verify(text)
{
   'use strict';
    let  stack =  new Array();
    let myMap = new Map([  ['[', ']'], ['(',')'], ['<','>'] ]);
    let regOpen   =  /[([<"]/ ;
    let regClose  = /[\)\]\>"]/ ;
    let length  =  text.length-1;
    var pop;
    var currentChar;
    for (var i=0;i<=length; i++ )
    {
        currentChar = text.charAt(i);
        if(  currentChar.match(regOpen)  )
            stack.push(  currentChar);
        else if(   currentChar.match(regClose)  )
        {
            pop =  myMap.get(stack.pop());
            if( pop!=  currentChar )   return 0;
        }
    }
    return (stack.length==0 ? 1:0);
