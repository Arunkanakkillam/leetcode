QN no:217   
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

Ans:
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
   const set=new Set(nums)
   if(set.size==nums.length){
    return false
   }
   return true
    }



QN no:137

Given an integer array nums where every element appears three times except for one, which appears exactly once. Find the single element and return it.

You must implement a solution with a linear runtime complexity and use only constant extra space.

Ans:


 * @param {number[]} nums
 * @return {number}
var singleNumber = function(nums) {
   for(let i=0;i<nums.length;i++){
        let flag=0
        for(let j=0;j<nums.length;j++){
            if(nums[i]==nums[j]&&i!=j){
                flag=1
                continue
            }
        }
        if(flag==0){
            return nums[i]
        }
    }

};



Qn no:41
Given an unsorted integer array nums. Return the smallest positive integer that is not present in nums.

You must implement an algorithm that runs in O(n) time and uses O(1) auxiliary space.



Ans:
/**
 * @param {number[]} nums
 * @return {number}
 */
var firstMissingPositive = function(nums) {
    const a=new Set(nums)
    for(let i=1;i<=nums.length+1;i++){
        if(!a.has(i)){
            return i
        }
    }
};



Qn No:73
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.

Ans:
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var setZeroes = function(matrix) {
    let a=[]
    let b=[]
   for(let i=0;i<matrix.length;i++){
    for(let j=0;j<matrix[0].length;j++){
        if(matrix[i][j]==0){
            a.push(i)
            b.push(j)
        }
    }
   } 


   for(let c=0;c<matrix.length;c++){
    for(let d=0;d<matrix[0].length;d++){
        if(a.includes(c)||b.includes(d)){
            matrix[c][d]=0
        }
    }
   }
};



Qn No:2665
Write a function createCounter. It should accept an initial integer init. It should return an object with three functions.

The three functions are:

    increment() increases the current value by 1 and then returns it.
    decrement() reduces the current value by 1 and then returns it.
    reset() sets the current value to init and then returns it.

Ans:
var createCounter = function(init) {
    let count=init
    return {
        increment:()=>{ count++; return count},
        reset:()=>{count=init;return count},
        decrement:()=>{ count--; return count}
   
    }
};


Qn no:3194

You have an array of floating point numbers averages which is initially empty. You are given an array nums of n integers where n is even.

You repeat the following procedure n / 2 times:

    Remove the smallest element, minElement, and the largest element maxElement, from nums.
    Add (minElement + maxElement) / 2 to averages.

Return the minimum element in averages.


Ans:
var minimumAverage = function(nums) {
    let b=[]
   if(nums.length>=nums.length/2){
        nums.sort((a,b)=>a-b);
        
        while (nums.length>1) {
            let a = (nums[0] + nums[nums.length - 1])/2
            nums.shift();  
            nums.pop();  
            b.push(a);  
        }
    }
    return b.sort((a,b)=>a-b)[0]
};


Qn no:575 Distribute Candies
Alice has n candies, where the ith candy is of type candyType[i]. Alice noticed that she started to gain weight, so she visited a doctor.

The doctor advised Alice to only eat n / 2 of the candies she has (n is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice.

Given the integer array candyType of length n, return the maximum number of different types of candies she can eat if she only eats n / 2 of them.

Ans:

var distributeCandies = function(candyType) {
    const a= new Set(candyType)
    if(candyType.length/2>a.size){
        return a.size
    }
    else{
        return candyType.length/2
    }
};

Qn no:500
Given an array of strings words, return the words that can be typed using letters of the alphabet on only one row of American keyboard like the image below.

In the American keyboard:

    the first row consists of the characters "qwertyuiop",
    the second row consists of the characters "asdfghjkl", and
    the third row consists of the characters "zxcvbnm".

Ans:
var findWords = function(words) {
    let a=[]
    for(i=0;i<words.length;i++){
        let flag1=false
        let flag2=false
        let flag3=false

        for(x of words[i]){
            if('qwertyuiop'.includes(x.toLowerCase())){
                flag1=true
            }
            else if('asdfghjkl'.includes(x.toLowerCase())){
                flag2=true
            }
            else if('zxcvbnm'.includes(x.toLowerCase())){
                flag3=true
            }
        }
        if(!(flag1&&flag2||flag1&&flag3||flag3&&flag2)){

                a.push(words[i])
        }
     
    }
    return a
};

Qn no: 7. Reverse Integer
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

Ans:
var reverse = function(x) {
    let b=2147483648;
    let a=x.toString().split('')
     if(a[0]=='-'){
        a.splice(0,1)
        let reversed = -(Number(a.reverse().join('')))
        return (reversed < -b || reversed >= b) ? 0 : reversed
     }
    
         let reversed = Number(a.reverse().join(''));
      return (reversed < -b || reversed >= b) ? 0 : reversed
};


Qn no:35. Search Insert Position
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.
Ans:
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    
    for(i=0;i<nums.length;i++){
        if(target==nums[i]){return i}
        else if(target<nums[i]){return i}
    }
    return nums.length
   
    
};