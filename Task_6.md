# 1. To seperate Odd and even numbers in the given list

`
def odd_even(list_1):
    odd_list=[]
    even_list=[]
    for i in list_1:
        if i %2==0:
            even_list.append(i)
        else:
            odd_list.append(i) 
user_list = [10, 501, 22, 37, 100, 999, 87, 351]
odd_even(user_list)
print(f'Odd numbers in the list :{odd_list}')
print(f'even numbers in the list:{even_list}') 

` 
# 2. To count all the prime numbers in the new list

`
def prime_list(list_1):
    new_list=[]  

    if list_1 > 1:
        for i in range(2,list_1):
            if list_1% i == 0: 
                return False
            
        return True
    
user_list = [10, 501, 22, 37, 100, 999, 87, 351]
result=[num for num in user_list if prime_list(num)]
print("New list :", result)
print("Count of prime numbers in the list is",len(result))

`

# 3. Happy numbers

`
input_list = [10, 501, 22, 37, 100, 999, 87, 351]
happy_list = []
for i in input_list:
    x = i
    while x >= 10:
        sum_of_digits = 0
        while x > 0:
            rem = x % 10
            sum_of_digits += rem ** 2
            x = x//10
        if sum_of_digits == 1:
            happy_list.append(i)
print(happy_list)
length_of_happy_list = len(happy_list)
print(f"The count of happy numbers in the list is {length_of_happy_list}") 

`
# 4. Sum of first and last digit of an integer 

`
def sum_of_digits(number):
    new_string = str(number)
    return(int(number[0])+int(number[-1]))

user_input=input("Enter the number: ")
result = sum_of_digits(user_input)
print(result)

`

# 6. Duplicates in the three list

`
def duplicate_list(list_1,list_2,list_3):
    combined_list = list_1 + list_2 + list_3
    new_list = []
    for number in combined_list:
        if combined_list.count(number) > 1 and number not in new_list:
            new_list.append(number)
    return new_list

list_1 =  [int(item) for item in input("Enter the list_1 items : ").split()]
list_2 = [int(item) for item in input("Enter the list_2 items : ").split()]
list_3 = [int(item) for item in input("Enter the list_3 items : ").split()]
output = duplicate_list(list_1, list_2, list_3)
print(f"The duplicate element between the 3 list is {output}")

` 

# 7. First non repeating element in the list

`
def non_repeating(list_1):
    for i in list_1:
        if list_1.count(i) == 1:
            return i


user_input = [int(item) for item in input("Enter the list items : ").split()]
output = non_repeating(user_input)
print(f" The first non repeating element in the list is {output}")

` 
# 8. Minimum element in the rated and sorted list

`
def find_minimum_element(list_1):
    sorted_list = sorted(list_1)
    return sorted_list[0]

user_input_list = [int(number) for number in input("Enter the list :").split()]
result = find_minimum_element(user_input_list)
print("Minimum Element in the sorted list:", result)

`

# 9. Triplet in the list whose sum is equal to the given value

`
def triplet(list_1, target_sum):
    length = len(list_1)
    for i in range(length - 2):
        for j in range(i + 1, length - 1):
            for k in range(j + 1, length):
                if list_1[i] + list_1[j] + list_1[k] == int(target_sum):
                    return [list_1[i], list_1[j], list_1[k]]
    return None

user_list = [int(number) for number in input("Enter the list: ").split()]  
target_sum = input("enter the value :")
result = triplet(user_list, target_sum)

if result:
    print(f'Triplet with sum {target_sum}: {result}')
else:
    print('No triplet found with the given sum.')

`

# 10. To find if there is a sublist with zero

`
def sum_of_sublist(list_1):
    new_list = []
    for i in range(0, len(list_1)):
        for j in range(i+1, len(list_1)):
            new_list.append(list_1[i:j])
    for element in new_list:
        if sum(element) == 0:
            return element


input_list = [int(number) for number in input("Enter the list: ").split()]
result = sum_of_sublist(input_list)
if result:
    print(f" The sublist whose sum is zero is {result}") 
else:
    print(f"There is no sub-list with a sum of zero.")

`