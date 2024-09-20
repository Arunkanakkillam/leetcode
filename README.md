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
