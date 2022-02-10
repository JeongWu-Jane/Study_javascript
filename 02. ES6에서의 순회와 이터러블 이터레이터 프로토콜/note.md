## for.. of 순회방법 
> 내장 이터러블: arr, map, set
- Map
``` const map = new Map([["a", 1], ["b", 2], ["c", 3],]);  
//map[0] -> undefined
//map[1] -> undefined
//map[2] -> undefined
--> 기존 순회방식이 x
 ```
- Set
 ``` const set = new Set([1, 2, 3]); 
 //set[0] -> undefined
//set[1] -> undefined
//set[2] -> undefined
--> 기존 순회방식이 x
 
 ```
 
- Symbol: 객체의 키가 될수 있음   
arr[Symbol.iterator] -> function 출력   
arr[Symbol.iterator] -> null로 해서   
for of 돌리면 오류  -> arr는 iterable 아니다 라고 오류   
   
arr->이터러블   
let iterator=arr[Symbol.iterator](); //interator 리턴   
iterator.next() //{value:1, done:false}   
iterator.next() //{value:1, done:false}   
iterator.next() //{value:1, done:false}   
iterator.next() //{value:undefined, done:true}   //done이 true면 빠져나옴    

var a=map[Symbol.iterator]();
a.next(); // {value:Array(2),done:false}  Array(2) ->["a",1]
a.next(); // {value:Array(2),done:false}
a.next(); // {value:Array(2),done:false}
a.next(); // {value:undefined,done:true}

var it=map.values(); //MapIterator [1,2,3]
it[Symbol.iterator] //iterator return
//map.entires 또다시 순회
var it2=it[Symbol.iterator]();
it2.next(); //{value:1, done:false}

-"well-formed iterator" : iterator가 자기자신을 반환하는 symbol iterator 메서드 가질때