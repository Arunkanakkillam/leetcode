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



Qn no:180. Consecutive Numbers

Table: Logs

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| num         | varchar |
+-------------+---------+
In SQL, id is the primary key for this table.
id is an autoincrement column starting from 1.

Find all numbers that appear at least three times consecutively.
Return the result table in any order.The result format is in the following example.

Ans:
select distinct l1.num as ConsecutiveNums from logs as l1 join logs as l2 on l1.id = l2.id + 1  
join logs as l3 on l1.id = l3.id - 1  where l1.num = l2.num and l1.num = l3.num;




Qn no:596. Classes More Than 5 Students
Table: Courses

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| student     | varchar |
| class       | varchar |
+-------------+---------+
(student, class) is the primary key (combination of columns with unique values) for this table.
Each row of this table indicates the name of a student and the class in which they are enrolled.

Write a solution to find all the classes that have at least five students.Return the result table in any order.
The result format is in the following example.


Ans:
select class
from Courses
group by class
having count(class) >= 5;


Qn no:1527. Patients With a Condition

Table: Patients

+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| patient_id   | int     |
| patient_name | varchar |
| conditions   | varchar |
+--------------+---------+
patient_id is the primary key (column with unique values) for this table.
'conditions' contains 0 or more code separated by spaces. 
This table contains information of the patients in the hospital.

 

Write a solution to find the patient_id, patient_name, and conditions of the patients who have Type I Diabetes. Type I Diabetes always starts with DIAB1 prefix.

Return the result table in any order.

The result format is in the following example.

Ans:
select patient_id, patient_name, conditions  
from Patients
where conditions like 'DIAB1%' or conditions like '% DIAB1%';


Qn no:1045. Customers Who Bought All Products
Table: Customer

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| customer_id | int     |
| product_key | int     |
+-------------+---------+
This table may contain duplicates rows. 
customer_id is not NULL.
product_key is a foreign key (reference column) to Product table.

 

Table: Product

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_key | int     |
+-------------+---------+
product_key is the primary key (column with unique values) for this table.

Ans:select distinct customer_id 
from customer
group by customer_id
having count(distinct product_key )=(select count (distinct product_key)from Product)


Qn no:4. Median of Two Sorted Arrays

Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
The overall run time complexity should be O(log (m+n)).

Ans:
public class Solution {
    public double FindMedianSortedArrays(int[] nums1, int[] nums2) {
        int [] a=nums1.Concat(nums2).ToArray();
        Array.Sort(a);
        int n=a.Length;
        if(n%2==1){
            return a[n/2];
        }
        else{
            return (a[(n/2)-1]+a[(n/2)])/2.00;
        }


    }
}

Qn no:1661. Average Time of Process per Machine

Table: Activity

+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| machine_id     | int     |
| process_id     | int     |
| activity_type  | enum    |
| timestamp      | float   |
+----------------+---------+
The table shows the user activities for a factory website.
(machine_id, process_id, activity_type) is the primary key (combination of columns with unique values) of this table.
machine_id is the ID of a machine.
process_id is the ID of a process running on the machine with ID machine_id.
activity_type is an ENUM (category) of type ('start', 'end').
timestamp is a float representing the current time in seconds.
'start' means the machine starts the process at the given timestamp and 'end' means the machine ends the process at the given timestamp.
The 'start' timestamp will always be before the 'end' timestamp for every (machine_id, process_id) pair.
It is guaranteed that each (machine_id, process_id) pair has a 'start' and 'end' timestamp.

 

There is a factory website that has several machines each running the same number of processes. Write a solution to find the average time each machine takes to complete a process.

The time to complete a process is the 'end' timestamp minus the 'start' timestamp. The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run.

The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places.

Return the result table in any order.

The result format is in the following example.

Ans:
select act.Machine_id,round(avg(act2.timestamp-act.timestamp),3) as processing_time
from activity act
join activity act2
on act.Machine_id=act2.Machine_id and act.process_id =act2.process_id and act.activity_type ="start" and act2.activity_type ="end"
group by act.Machine_id;

Qn no:3024 type of triangle
You are given a 0-indexed integer array nums of size 3 which can form the sides of a triangle.

    A triangle is called equilateral if it has all sides of equal length.
    A triangle is called isosceles if it has exactly two sides of equal length.
    A triangle is called scalene if all its sides are of different lengths.

Return a string representing the type of triangle that can be formed or "none" if it cannot form a triangle.

Ans:
var triangleType = function(nums) {
    
    if (nums[0]==nums[1]&&nums[1]==nums[2]){
        return "equilateral"
    }
    else if(
        nums[0] + nums[1]>nums[2]&&
        nums[0] + nums[2]>nums[1]&&
        nums[1] + nums[2]>nums[0]

    ) {

if(nums[1]==nums[2]||nums[1]==nums[0]||nums[0]==nums[2]){
    return "isosceles"
}
return "scalene" 
    }
    return "none"
};


Qn no:1978. Employees Whose Manager Left the Company
Table: Employees

+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| employee_id | int      |
| name        | varchar  |
| manager_id  | int      |
| salary      | int      |
+-------------+----------+
In SQL, employee_id is the primary key for this table.
This table contains information about the employees, their salary, and the ID of their manager. Some employees do not have a manager (manager_id is null). 
Find the IDs of the employees whose salary is strictly less than $30000 and whose manager left the company. When a manager leaves the company, their information is deleted from the Employees table, but the reports still have their manager_id set to the manager that left.
Return the result table ordered by employee_id.The result format is in the following example.

Ans:

select employee_id 
from Employees
where salary<30000 and manager_id not in (select employee_id from Employees) 
order by employee_id asc;

Qn no:1281. Subtract the Product and Sum of Digits of an Integer
Given an integer number n, return the difference between the product of its digits and the sum of its digits. 
Ans:
public class Solution {
    public int SubtractProductAndSum(int n) {
     string a=n.ToString();
     int mul=1;
     int sum=0;
     for(int i=0;i<a.Length;i++){
        int digit = int.Parse(a[i].ToString());
            mul*=digit;
            sum+=digit;
     }
     return mul-sum;   
    }

}

Qn no:66. Plus One
You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.Increment the large integer by one and return the resulting array of digits.

Ans:
public class Solution {
    public int[] PlusOne(int[] digits) {
        for (int i = digits.Length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        int[] newDigits = new int[digits.Length + 1];
        newDigits[0] = 1;
        
        return newDigits;
    }
}




Qn no:1211. Queries Quality and Percentage

Table: Queries

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| query_name  | varchar |
| result      | varchar |
| position    | int     |
| rating      | int     |
+-------------+---------+
This table may have duplicate rows.
This table contains information collected from some queries on a database.
The position column has a value from 1 to 500.
The rating column has a value from 1 to 5. Query with rating less than 3 is a poor query.

 

We define query quality as:

    The average of the ratio between query rating and its position.

We also define poor query percentage as:

    The percentage of all queries with rating less than 3.

Write a solution to find each query_name, the quality and poor_query_percentage.

Both quality and poor_query_percentage should be rounded to 2 decimal places.

Return the result table in any order.

The result format is in the following example.


Ans:
select  query_name ,round( cast(avg(cast(rating as float)/position ) as float),2) as quality  , 
round((cast(cast(sum(case when rating < 3 then 1 else 0 end) * 100 as float)/count(*)as float)) ,2) as poor_query_percentage
from Queries
where query_name is not null
group by query_name
order by quality desc;



Qn no:1633. Percentage of Users Attended a Contest

Table: Users

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| user_id     | int     |
| user_name   | varchar |
+-------------+---------+
user_id is the primary key (column with unique values) for this table.
Each row of this table contains the name and the id of a user.
Table: Register
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| contest_id  | int     |
| user_id     | int     |
+-------------+---------+
(contest_id, user_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id of a user and the contest they registered into.
Write a solution to find the percentage of the users registered in each contest rounded to two decimals.
Return the result table ordered by percentage in descending order. In case of a tie, order it by contest_id in ascending order.
The result format is in the following example.

Ans:
select distinct Register.contest_id, round(count(register.user_id)*cast(100 as float)/(select cast (count(distinct user_id)as float) from Users),2)  as percentage
from Register
group by register.contest_id
order by  percentage desc,Register.contest_id asc ;


Qn no:1832. Check if the Sentence Is Pangram
A pangram is a sentence where every letter of the English alphabet appears at least once.

Given a string sentence containing only lowercase English letters, return true if sentence is a pangram, or false otherwise.

Ans:
public class Solution {
    public bool CheckIfPangram(string sentence) {
        HashSet<char> sent=new HashSet<char>();
        foreach(var leter in sentence){
            if(leter>='a' || leter<='z'){
                sent.Add(leter);
            }
        }

        return sent.Count==26;
    }
}

Qn no:704. Binary Search
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.
You must write an algorithm with O(log n) runtime complexity.

Ans:
public class Solution {
    public int Search(int[] nums, int target) {
        
int left=0;
int right=nums.Length-1;
while(left<=right){
    int middle=left+(right-left)/2;
    if(nums[middle]==target){
        return middle;
    }
    else if(nums[middle]<target){
        left=middle+1;
    }
    else{
        right=middle-1;
    }
}
return-1;
    }
}

Qn no:1342. Number of Steps to Reduce a Number to Zero

Given an integer num, return the number of steps to reduce it to zero.

In one step, if the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

Ans:
public class Solution {
    public int NumberOfSteps(int num) {
        int count=0;
        while(num>0){
               if(num%2==0){
            num=num/2;
            count++;
        }
        else{num=num-1;
        count++;
         }
    }
    return count;
        }
     
}

Qn no:627. Swap Salary

Table: Salary

+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| id          | int      |
| name        | varchar  |
| sex         | ENUM     |
| salary      | int      |
+-------------+----------+
id is the primary key (column with unique values) for this table.
The sex column is ENUM (category) value of type ('m', 'f').
The table contains information about an employee.

 

Write a solution to swap all 'f' and 'm' values (i.e., change all 'f' values to 'm' and vice versa) with a single update statement and no intermediate temporary tables.

Note that you must write a single update statement, do not write any select statement for this problem.

The result format is in the following example.

Ans:
update salary
set sex=case 
when sex='m' then 'f'
when sex='f' then 'm'
end;

Qn no:1920. Build Array from Permutation
Given a zero-based permutation nums (0-indexed), build an array ans of the same length where ans[i] = nums[nums[i]] for each 0 <= i < nums.length and return it.

Ans:
public class Solution {
    public int[] BuildArray(int[] nums) {
        int[]ans=new int[ nums.Length];
        for(int i=0;i< nums.Length ;i++){
            ans[i]=nums[nums[i]];
        }
        return ans;
    }
}

Qn no:49. Group Anagrams
Given an array of strings strs, group the
anagrams together. You can return the answer in any order.

Ans:
public class Solution {
    public IList<IList<string>> GroupAnagrams(string[] strs) {

       return strs.GroupBy(c=>new string(c.OrderBy(b=>b).ToArray()))
                   .Select(p=>p.ToList() as IList<string>).ToList();
        
    }
}

Qn no: 414. Third Maximum Number
Given an integer array nums, return the third distinct maximum number in this array. If the third maximum does not exist, return the maximum number.
ans:
public class Solution {
    public int ThirdMax(int[] nums) {
   var data=nums.Distinct().OrderByDescending(x=>x).
                    ToList();
                    if(data.Count()<3){
                        return data[0];
                    }
                    return data[2];
    }
}


Qn no:1089. Duplicate Zeros
Given a fixed-length integer array arr, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything.

Ans:
public class Solution {
    public void DuplicateZeros(int[] arr) {
        var ar=arr.ToList();
        for(int i=0;i<ar.Count;i++){
            if(ar[i]==0){
                ar.Insert(i,0);
                ar.RemoveAt(ar.Count-1);
                i++;
            }
        }
        for(int j=0;j<arr.Length;j++){
            arr[j]=ar[j];
        }
    }
}


Qn no:1295. Find Numbers with Even Number of Digits
Given an array nums of integers, return how many of them contain an even number of digits.

Ans:
public class Solution {
    public int FindNumbers(int[] nums) {
        int count=0;
        for(int i=0;i<nums.Length;i++){
            if(nums[i].ToString().Length%2==0){
                    count++;
            }
        }
        return count;
    }
}

Qn no:278. First Bad Version
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.
Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.
You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

/* The isBadVersion API is defined in the parent class VersionControl.
      bool IsBadVersion(int version); */

public class Solution : VersionControl {
    public int FirstBadVersion(int n) {
        for(int i=n;i>0;i--){
            if(IsBadVersion(i)){
                for(int j=i-1;j>0;j--){
                    if(IsBadVersion(j)==false){
                        return j+1;
                    }
                }
                return 1;
            }
        }
        return -1;
        
    }
}

Qn No:176. Second Highest Salary
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

Ans:
select max(salary) as SecondHighestSalary 
from employee
where salary not in (select max(salary) from Employee )


Qn no:682. Baseball Game
You are keeping the scores for a baseball game with strange rules. At the beginning of the game, you start with an empty record.
You are given a list of strings operations, where operations[i] is the ith operation you must apply to the record and is one of the following:
An integer x.Record a new score of x.'+'.Record a new score that is the sum of the previous two scores.'D'.
Record a new score that is the double of the previous score.
'C'.Invalidate the previous score, removing it from the record.
Return the sum of all the scores on the record after applying all the operations.
The test cases are generated such that the answer and all intermediate calculations fit in a 32-bit integer and that all operations are valid.

Ans:


public class Solution {
    public int CalPoints(string[] operations) {
        List<int> sum = new List<int>();

        foreach (string op in operations) {
            if (op == "+") {
      
                if (sum.Count >= 2) {
                    sum.Add(sum[sum.Count - 1] + sum[sum.Count - 2]);
                }
            }
            else if (op == "D") {
              
                if (sum.Count >= 1) {
                    sum.Add(2 * sum[sum.Count - 1]);
                }
            }
            else if (op == "C") {
               
                if (sum.Count > 0) {
                    sum.RemoveAt(sum.Count - 1);
                }
            }
            else {
              
                sum.Add(int.Parse(op));
            }
        }

        return sum.Sum();  
    }
}

Qn No: 1389. Create Target Array in the Given Order
Given two arrays of integers nums and index. Your task is to create target array under the following rules:
Initially target array is empty.From left to right read nums[i] and index[i], insert at index index[i] the value nums[i] in target array.
Repeat the previous step until there are no elements to read in nums and index.
Return the target array.It is guaranteed that the insertion operations will be valid.

Ans:
public class Solution {
    public int[] CreateTargetArray(int[] nums, int[] index) {
        List<int> numbers=new List <int>();
        for(int i=0;i<nums.Length;i++){
            numbers.Insert(index[i],nums[i]);
        }
        return numbers.ToArray();
    }
}

Qn no:800. Maximum Ascending Subarray Sum
Given an array of positive integers nums, return the maximum possible sum of an ascending subarray in nums.
A subarray is defined as a contiguous sequence of numbers in an array.A subarray [numsl, numsl+1, ..., numsr-1, numsr] is ascending if for all i where l <= i < r, numsi  < numsi+1. Note that a subarray of size 1 is ascending.


Ans:
public class Solution {
    public int MaxAscendingSum(int[] nums) {
        List<int> list=new List<int>();
        for(int i=0;i<nums.Length;i++){
            int sum=nums[i];
            for(int j=i+1;j<nums.Length;j++){
                if(nums[j]>nums[j-1]){
                    sum+=nums[j];
                }else
                {
                     break;
                }
               
            }
            list.Add(sum);
        }
        return list.Max();
    }
}


Qn No:1790. Check if One String Swap Can Make Strings Equal
You are given two strings s1 and s2 of equal length. A string swap is an operation where you choose two indices in a string (not necessarily different) and swap the characters at these indices.
Return true if it is possible to make both strings equal by performing at most one string swap on exactly one of the strings. Otherwise, return false.

Ans:
public class Solution {
    public bool AreAlmostEqual(string s1, string s2) {
        if (s1 == s2) return true;  
        List<int> diffIndices = new List<int>();

        for (int i = 0; i < s1.Length; i++) {
            if (s1[i] != s2[i]) {
                diffIndices.Add(i);
                if (diffIndices.Count > 2) return false; 
            }
        }
         if (diffIndices.Count != 2) return false;
        int i1 = diffIndices[0], i2 = diffIndices[1];
        return s1[i1] == s2[i2] && s1[i2] == s2[i1];
    }
}
qn No:2706. Buy Two Chocolates
You are given an integer array prices representing the prices of various chocolates in a store. You are also given a single integer money, which represents your initial amount of money.
You must buy exactly two chocolates in such a way that you still have some non-negative leftover money. You would like to minimize the sum of the prices of the two chocolates you buy.
Return the amount of money you will have leftover after buying the two chocolates. If there is no way for you to buy two chocolates without ending up in debt, return money. Note that the leftover must be non-negative.

ans:
public class Solution {
    public int BuyChoco(int[] prices, int money) {
         int minCost = int.MaxValue;
        for(int i=0;i<prices.Length;i++){
            for(int j=i+1;j<prices.Length;j++){
                if(prices[i]+prices[j]>money){
                    continue;
                }
               minCost = Math.Min(minCost, prices[i]+prices[j]); 
            }
        }
      if (minCost == int.MaxValue) {
            return money;
        } else {
            return money - minCost;
        }
    }
}


Qn no:2595. Number of Even and Odd Bits
You are given a positive integer n.
Let even denote the number of even indices in the binary representation of n with value 1.
Let odd denote the number of odd indices in the binary representation of n with value 1.
Note that bits are indexed from right to left in the binary representation of a number.
Return the array [even, odd].

Ans:
public class Solution {
    public int[] EvenOddBit(int n) {
       string b = Convert.ToString(n, 2);
        int even=0;
        int odd=0;
        for(int i=0;i<b.Length;i++){
           int c = b[b.Length - 1 - i] - '0';
            if(c==1&&i%2==0){
                even++;
            }
            if(c==1&&i%2!=0){
                odd++;
            }
        }
        return new int[]{even,odd};
    }
}

Qn no:2656. Maximum Sum With Exactly K Elements 

You are given a 0-indexed integer array nums and an integer k. Your task is to perform the following operation exactly k times in order to maximize your score:

Select an element m from nums.
Remove the selected element m from the array.
Add a new element with a value of m + 1 to the array.
Increase your score by m.
Return the maximum score you can achieve after performing the operation exactly k times.

Ans:
public class Solution {
    public int MaximizeSum(int[] nums, int k) {
        Array.Sort(nums);
       int sum=nums[nums.Length-1];
        for (int i = 0;i<k;i++){
            nums[nums.Length-1]=nums[nums.Length-1]+1;
            if(i<k-1){
            sum +=(nums[nums.Length-1]);
            }
        }
        return sum;
        
    }
}

Qn no:3174. Clear Digits
You are given a string s.

Your task is to remove all digits by doing this operation repeatedly:

Delete the first digit and the closest non-digit character to its left.
Return the resulting string after removing all digits.
Ans:
public class Solution {
    public string ClearDigits(string s) {
        List<char> result = s.ToList(); 

        for (int i = 0; i < result.Count;) {
            if (int.TryParse(result[i].ToString(), out _)) {
                result.RemoveAt(i); 

                if (i > 0) { 
                    result.RemoveAt(i - 1);
                    i--;
                }
            } else {
                i++; 
            }
        }

        return new string(result.ToArray());
    }
}

Qn no:1910. Remove All Occurrences of a Substring
Given two strings s and part, perform the following operation on s until all occurrences of the substring part are removed:

Find the leftmost occurrence of the substring part and remove it from s.
Return s after removing all occurrences of part.

A substring is a contiguous sequence of characters in a string.

Ans:
public class Solution {
    public string RemoveOccurrences(string s, string part) {
       
         while (s.Contains(part)) {
           s=s.Remove(s.IndexOf(part),part.Length);
        }
        return s;
        
    }
}

Qn no:1980. Find Unique Binary String
Given an array of strings nums containing n unique binary strings each of length n, return a binary string of length n that does not appear in nums. If there are multiple answers, you may return any of them.

Ans:

public class Solution {
    public string FindDifferentBinaryString(string[] nums) {
        int n = nums.Length;
        Random random = new Random();

        while (true) {
            string randomBinary = GenerateRandomBinary(n, random);
            
            if (!nums.Contains(randomBinary)) {
                return randomBinary;
            }
        }
    }

    private string GenerateRandomBinary(int length, Random random) {
        char[] binaryString = new char[length];

        for (int i = 0; i < length; i++) {
            binaryString[i] = random.Next(2) == 0 ? '0' : '1';
        }

        return new string(binaryString);
    }
}
