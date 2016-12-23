# Cannonical-parantases-in-ES6


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
