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

Qn no:2704. To Be Or Not To Be

Write a function expect that helps developers test their code. It should take in any value val and return an object with the following two functions.

    toBe(val) accepts another value and returns true if the two values === each other. If they are not equal, it should throw an error "Not Equal".
    notToBe(val) accepts another value and returns true if the two values !== each other. If they are equal, it should throw an error "Equal".

Ans:
var expect = function(val) {
  return{   toBe:function(v){ 
        if(v===val){
            return true
        }
        else{
          throw new Error("Not Equal");
        }
    },
     notToBe:function(v){
        if(v!==val){return true}
        else{
            throw new Error("Equal");
        }
    }
  }
};

Qn no: 1662. Check If Two String Arrays are Equivalent

Given two string arrays word1 and word2, return true if the two arrays represent the same string, and false otherwise.

A string is represented by an array if the array elements concatenated in order forms the string.

Ans:
var arrayStringsAreEqual = function(word1, word2) {
    let a
    let b
  for( i=0;i<word1.length;i++){
    a+=word1[i]
  }
  for( i=0;i<word2.length;i++){
    b+=word2[i]
  }
  if(a==b){return true }
    return false
};

Qn no: 2000. Reverse Prefix of Word
Given a 0-indexed string word and a character ch, reverse the segment of word that starts at index 0 and ends at the index of the first occurrence of ch (inclusive). If the character ch does not exist in word, do nothing.

    For example, if word = "abcdefd" and ch = "d", then you should reverse the segment that starts at 0 and ends at 3 (inclusive). The resulting string will be "dcbaefd".

Return the resulting string.
Ans:
var reversePrefix = function(word, ch) {
   x= word.split("")
   c=''
   for(i=0;i<x.length;i++){
       c+=x[i]
       if(x[i]==ch){
                   return c.split("").reverse().join("")+word.slice(i+1)
       }
   }
   return word
};

Qn No:43. Multiply Strings
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.
Ans:
var multiply = function(num1, num2) {

 return String(BigInt(num1)*BigInt(num2))
};


Qn no:2469. Convert the Temperature
You are given a non-negative floating point number rounded to two decimal places celsius, that denotes the temperature in Celsius.

You should convert Celsius into Kelvin and Fahrenheit and return it as an array ans = [kelvin, fahrenheit].

Return the array ans. Answers within 10-5 of the actual answer will be accepted.
Ans;
var convertTemperature = function(celsius) {
    return [celsius+273.15,celsius * 1.80 + 32.00]
};


Qn no:1346. Check If N and Its Double Exist
Given an array arr of integers, check if there exist two indices i and j such that :

    i != j
    0 <= i, j < arr.length
    arr[i] == 2 * arr[j]
Ans:
var checkIfExist = function(arr) {
    for(i=0;i<arr.length;i++){
        for(j=0;j<arr.length;j++){
            if(i!=j&&arr[j]==2*arr[i]){
                return true
            }
        }
    }
    return false
};

Qn no:136. Single Number
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.
Ans:
public class Solution {
    public int SingleNumber(int[] nums) {
       int res=0;
    foreach(var n in nums){
        res^=n;
    }

        return res; 
    }
}

Qn no:2974. Minimum Number Game
You are given a 0-indexed integer array nums of even length and there is also an empty array arr. Alice and Bob decided to play a game where in every round Alice and Bob will do one move. The rules of the game are as follows:

    Every round, first Alice will remove the minimum element from nums, and then Bob does the same.
    Now, first Bob will append the removed element in the array arr, and then Alice does the same.
    The game continues until nums becomes empty.

Return the resulting array arr.
Ans:
var numberGame = function(nums) {
    nums.sort((a,b)=>b-a)
    let f=[]
    let i=nums.length-1
    while(i>0){
        let c=nums.pop()
        let d=nums.pop()
        f.push(d)
        f.push(c)
    }
    return f
};

Qn No:771. Jewels and Stones
You're given strings jewels representing the types of stones that are jewels, and stones representing the stones you have. Each character in stones is a type of stone you have. You want to know how many of the stones you have are also jewels.

Letters are case sensitive, so "a" is considered a different type of stone from "A".

Ans:
var numJewelsInStones = function(jewels, stones) {
    count=0
    for(i=0;i<jewels.length;i++){
        for(j=0;j<stones.length;j++){
            if(jewels[i]==stones[j]){
                count++
            }
        }
    }
    return count
};

Qn no: 2621 Sleep
Given a positive integer millis, write an asynchronous function that sleeps for millis milliseconds. It can resolve any value.
Ans:
async function sleep(millis) {
    return new Promise((res,rej)=>{
        setTimeout(()=>{console.log(millis)
              res()
        },millis)
    })
}

Qn no:648. Replace Words

In English, we have a concept called root, which can be followed by some other word to form another longer word - let's call this word derivative. For example, when the root "help" is followed by the word "ful", we can form a derivative "helpful".
Given a dictionary consisting of many roots and a sentence consisting of words separated by spaces, replace all the derivatives in the sentence with the root forming it. If a derivative can be replaced by more than one root, replace it with the root that has the shortest length.
Return the sentence after the replacement.

Ans:
var replaceWords = function(dictionary, sentence) {
    dictionary.sort((a, b) => a.length - b.length); 
    
    const words = sentence.split(' '); 
    
    for (let i = 0; i < words.length; i++) { 
        for (let j = 0; j < dictionary.length; j++) { 
            if (words[i].startsWith(dictionary[j])) { 
                words[i] = dictionary[j]; 
                break; 
            }
        }
    }
    return words.join(' ');
};

Qn no:1672. Richest Customer Wealth
You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the i​​​​​​​​​​​th​​​​ customer has in the j​​​​​​​​​​​th​​​​ bank. Return the wealth that the richest customer has.
A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

Ans:
var maximumWealth = function(accounts) {
   
    wealth=[]
    for(i=0;i<accounts.length;i++){
        sum=0
        for(j=0;j<accounts[i].length;j++){
            sum =sum+accounts[i][j]
        }
        wealth.push(sum)
    }
   return Math.max(...wealth)
};

Qn no:2396. Strictly Palindromic Number
An integer n is strictly palindromic if, for every base b between 2 and n - 2 (inclusive), the string representation of the integer n in base b is palindromic.

Given an integer n, return true if n is strictly palindromic and false otherwise.

A string is palindromic if it reads the same forward and backward.

Ans:
var isStrictlyPalindromic = function(n) {
  for(let i=2;i<n;i++){
    a=n.toString(i)
if(a.split('').reverse().join('')!=a){
    return false
}
  }  
  return true
};

Qn no:283. Move Zeroes
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
Note that you must do this in-place without making a copy of the array.
Ans:
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let start = 0;  
    let current = 0;  
    while (current < nums.length) {
        if (nums[current] !== 0) {
            let temp = nums[start];
            nums[start] = nums[current];
            nums[current] = temp;
            start++;
        }
        current++
    }
};

Qn no:2520. Count the Digits That Divide a Number
Given an integer num, return the number of digits in num that divide num.
An integer val divides nums if nums % val == 0.
Ans:
/**
 * @param {number} num
 * @return {number}
 */
var countDigits = function(num) {
    let a=num.toString()
    count=0
    for(i=0;i<a.length;i++){
        if(num%a[i]==0){
             count++
        }
           
    
    }
    return count
};

Qn No:1757. Recyclable and Low Fat Products
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.
Write a solution to find the ids of products that are both low fat and recyclable.
Return the result table in any order.
The result format is in the following example.

Ans:
/* Write your T-SQL query statement below */
select product_id
from products
where low_fats = 'y' AND recyclable = 'y'


Qn no:584. Find Customer Referee
Table: Customer

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
Find the names of the customer that are not referred by the customer with id = 2.
Return the result table in any order.
The result format is in the following example.

Example 1:

Input: 
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
Output: 
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+


Ans:
select name from customer
where referee_id != 2 or referee_id is null;




Qn no:175. Combine Two Tables

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| personId    | int     |
| lastName    | varchar |
| firstName   | varchar |
+-------------+---------+
personId is the primary key (column with unique values) for this table.
This table contains information about the ID of some persons and their first and last names.

Table: Address

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| addressId   | int     |
| personId    | int     |
| city        | varchar |
| state       | varchar |
+-------------+---------+
addressId is the primary key (column with unique values) for this table.
Each row of this table contains information about the city and state of one person with ID = PersonId.

Write a solution to report the first name, last name, city, and state of each person in the Person table. If the address of a personId is not present in the Address table, report null instead.
Return the result table in any order.The result format is in the following example.

Ans:
Select person.firstname,person.lastname,address.city,address.state
from person
left Join address
on person.personid=address.personid;


Qn no:595. Big Countries

Table: World
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |
+-------------+---------+
name is the primary key (column with unique values) for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.
A country is big if:
it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.
Return the result table in any order.
The result format is in the following example.

Ans:
select name,population,area from world
where area>=3000000 or population >=25000000;

Qn No: 197. Rising Temperature

Weather

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.
Write a solution to find all dates' id with higher temperatures compared to its previous dates (yesterday).
Return the result table in any order.The result format is in the following example.

Ans: 
select w1.id as Id
from Weather w1
join Weather w2 on w1.recordDate=DATEADD(day, 1, w2.recordDate)
where w1.temperature>w2.temperature;

Qn no:570. Managers with at Least 5 Direct Reports

Table: Employee

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table indicates the name of an employee, their department, and the id of their manager.
If managerId is null, then the employee does not have a manager.
No employee will be the manager of themself.

Ans:
select e.name from employee e
where (select count(*) from employee where managerid=e.id)>=5 ;



Qn no:176. Second Highest Salary

Table: Employee

+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key (column with unique values) for this table.
Each row of this table contains information about the salary of an employee.

Write a solution to find the second highest distinct salary from the Employee table. If there is no second highest salary, return null (return None in Pandas).
The result format is in the following example.

Ans:
SELECT(SELECT DISTINCT salary 
FROM employee
ORDER BY salary DESC
OFFSET 1 ROWS 
FETCH NEXT 1 ROWS ONLY)
AS SecondHighestSalary;




QN NO:619. Biggest Single Number

Table: MyNumbers

+-------------+------+
| Column Name | Type |
+-------------+------+
| num         | int  |
+-------------+------+
This table may contain duplicates (In other words, there is no primary key for this table in SQL).
Each row of this table contains an integer.

A single number is a number that appeared only once in the MyNumbers table.
Find the largest single number. If there is no single number, report null.
The result format is in the following example.

Ans:
select (select num from mynumbers
group by num
having count(num)=1
order by num desc
offset 0 rows
fetch next 1 rows only)
as num;


Qn no:1280. Students and Examinations

Table: Students

+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| student_id    | int     |
| student_name  | varchar |
+---------------+---------+
student_id is the primary key (column with unique values) for this table.
Each row of this table contains the ID and the name of one student in the school.

 

Table: Subjects

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| subject_name | varchar |
+--------------+---------+
subject_name is the primary key (column with unique values) for this table.
Each row of this table contains the name of one subject in the school.

 

Table: Examinations

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | int     |
| subject_name | varchar |
+--------------+---------+
There is no primary key (column with unique values) for this table. It may contain duplicates.
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.

 

Write a solution to find the number of times each student attended each exam.

Return the result table ordered by student_id and subject_name.

The result format is in the following example.

Ans:
select 
    Students.student_id,
    Students.student_name,
    Subjects.subject_name,
    (select 
         count(examinations.subject_name) from examinations 
     where examinations.student_id = Students.student_id and examinations.subject_name = Subjects.subject_name) as attended_exams
from Students
cross join Subjects
group by   Students.student_id,Students.student_name,Subjects.subject_name;



Qn no:2356. Number of Unique Subjects Taught by Each Teacher

Table: Teacher

+-------------+------+
| Column Name | Type |
+-------------+------+
| teacher_id  | int  |
| subject_id  | int  |
| dept_id     | int  |
+-------------+------+
(subject_id, dept_id) is the primary key (combinations of columns with unique values) of this table.
Each row in this table indicates that the teacher with teacher_id teaches the subject subject_id in the department dept_id.

Write a solution to calculate the number of unique subjects each teacher teaches in the university.
Return the result table in any order.The result format is shown in the following example.

Ans:
select teacher_id,count(Distinct subject_id) as cnt 
from teacher
group by teacher_id;



Qn no:1934. Confirmation Rate

Table: Signups

+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| user_id        | int      |
| time_stamp     | datetime |
+----------------+----------+
user_id is the column of unique values for this table.
Each row contains information about the signup time for the user with ID user_id.

Table: Confirmations

+----------------+----------+
| Column Name    | Type     |
+----------------+----------+
| user_id        | int      |
| time_stamp     | datetime |
| action         | ENUM     |
+----------------+----------+
(user_id, time_stamp) is the primary key (combination of columns with unique values) for this table.
user_id is a foreign key (reference column) to the Signups table.
action is an ENUM (category) of the type ('confirmed', 'timeout')
Each row of this table indicates that the user with ID user_id requested a confirmation message at time_stamp and that confirmation message was either confirmed ('confirmed') or expired without confirming ('timeout').
The confirmation rate of a user is the number of 'confirmed' messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. Round the confirmation rate to two decimal places.Write a solution to find the confirmation rate of each user.Return the result table in any order.The result format is in the following example.


Ans:
select 
signups.user_id,round(count(case when confirmations.action = 'confirmed' then 1 end) * 1.0/ count(*),2) as confirmation_rate
from signups
left join confirmations 
on signups.user_id = confirmations.user_id
group by 
signups.user_id;


Qn no:1729. Find Followers Count
Table: Followers

+-------------+------+
| Column Name | Type |
+-------------+------+
| user_id     | int  |
| follower_id | int  |
+-------------+------+
(user_id, follower_id) is the primary key (combination of columns with unique values) for this table.
This table contains the IDs of a user and a follower in a social media app where the follower follows the user.

Write a solution that will, for each user, return the number of followers.
Return the result table ordered by user_id in ascending order.The result format is in the following example.

Ans:
select user_id, count(user_id) as followers_count
from Followers
group by user_id
order by user_id asc;