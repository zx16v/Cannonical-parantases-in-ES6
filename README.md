# Cannonical-parantases-in-ES6
goto https://raw.githubusercontent.com/zx16v/Cannonical-parantases-in-ES6/master/README.md

The program flow:
1) creat a Map object to hold  the right brackets as a key and left brackets as value.
2) looping over the input string char by char checking by using regualr expression to avoid cumbersum switch-case structure. 
   a) using regOpen regex i check if the current char is left a bracket type, if i push it into the stack.
      if not
   b) i check whether the current char is right bracket type, if so i'll pop the last left bracket from the stack,
      and use it as a key input for GET method of the Map object(" myMap.get(stack.pop()"),
      i'll execert the value of it's matching left bracket
      now i compare: (currentChar != myMap.get(stack.pop() ),
      if it's identical then i can move on in the loop, if not i exit the function with false return value.
 
3)  out of the loop i'm checking whether the stack is empty, if so the input string is bracket cannonical, so it's
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
