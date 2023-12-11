# 1. To calculate total number of vowels and count of each individual vowel in the string "Guvi Geeks Private Limited"

`
my_list="guvi geeks private limited"
vowels_list="aeiou"
count=0
for i in my_list:
    if i in vowels_list:
        count=count+1
print(count)
print("count of a:",my_list.count('a'))
print("count of e:",my_list.count('e'))
print("count of i:",my_list.count('i'))
print("count of o:",my_list.count('o'))
print("count of u:",my_list.count('u'))
print("Total number of vowels:",count)

`
# 2. Pyramid of numbers from 1 to 20 using for loop

`
## Half pyramid
user_input = 20
for i in range(1,user_input+1):
    for j in range(1,i+1):
        print(j,end=" ")
    print() 
    
## Full pyramid
rows = 20
for i in range(1, rows + 1):
    for j in range(rows - i):
        print(" ", end=" ")
    for k in range(1, i + 1):
        print(k, end=" ")
    for l in range(i - 1, 0, -1):
        print(l, end=" ")
    print()

`

# 3.Vowels removed

`
def removed_vowels(str_1):
    new_string=""
    vowels = "aeiou"
    for i in str_1:
        if i not in vowels:
            new_string=new_string + i
    return new_string
            
string_1 = input()
result = removed_vowels(string_1)
print(f'vowels removed in the string {string_1} :{result}')

`

# 4. No of unique characters in the given string

`
def count_unique_characters(string_1):
    set1 = set()
    for i in string_1:
        set1.add(i)
    print(len(set1))

input_string = input("Enter the string: ")
count_unique_characters(input_string) 

`

# 5 Palindrome or not 

`
def is_palindrome(string_1):
    
    string_2 = string_1[::-1]
    if string_1 == string_2:
        return True
    else:
        return False
    
input_string = input("Enter the string:")
result = is_palindrome(input_string)
if result:
    print("The string is a palidrome")
else:
    print("The string is not a palindrome")

`

# 7 . Frequent occuring character

`
def frequent_occurring_char(string_1):
    dict1 = {}

    for i in string_1:
        count1 = string_1.count(i)
        dict1[i] = count1
    frequent_occurrence = max(dict1,key=dict1.get)
    return frequent_occurrence


input_string = input("Enter the string: ")
result = frequent_occurring_char(input_string)
print(result)  

`

# 8. Anagram

`
def check_anagram(string_1,string_2):
    sorted_string_1 = sorted(string_1)
    sorted_string_2 = sorted(string_2)
    if sorted_string_1 ==  sorted_string_2:
        return True
    else:
        return False 
    
string_1 = input("Enter string 1: ")
string_2 = input("Enter string 2: ")
result = check_anagram(string_1,string_2)
print(result)

` 
# 9. No of words in the string

`
def Number_of_words(string_1):
    new_list = string_1.split()
    length = len(new_list)
    return length 

input_string = input("Enter the string: ")
result = Number_of_words(input_string)
print(result)

`