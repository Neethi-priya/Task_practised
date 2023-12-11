# 2. To check every element of a list is an integer or string 

`
data = [ "happy",1,"Birthday",2,"you"]
result = map(lambda x: type(x),data)
print(list(result))

`
# 3. Fibonacci series
 
 `
 def fibonacci_series(number):
    fibonacci = lambda x:x if x<=1 else fibonacci(x-1)+fibonacci(x-2)
    result = [fibonacci(i) for i in range(number)]
    return result
number = 20
result_1 = fibonacci_series(number)
print(result_1) 

fibonacci = lambda n, a=0, b=1: [a] + (fibonacci(n-1, b, a+b) if n > 1 else [])

# Generate Fibonacci series with 50 elements
fib_series = fibonacci(50)

print(fib_series)
  
 `

# 4. Validate the Regular expressions

`
import re

def email_address(email_id):
        pattern = "([a-z0-9_.])+\@+([a-z0-9])+(\.)+([a-z]{2,6})"
        if re.match(pattern, str(email_id)):
            return True 
        else:
            return False
    
def bangladesh_number(number_bangladesh):
        pattern = '^\+8801[3-9]\d{8}$'
        if re.match(pattern,str(number_bangladesh)):
            return True
        else:
            return False
    
def usa_number(number_usa):
        pattern = '^\+1\d{10}$'
        if re.match(pattern,str(number_usa)):
            return True
        else:
            return False
    
def alphanumeric_password(alpha_num):
       pattern = r"(^[A-Za-z0-9#?!@$%^/&*-]{16}$)"
       if re.match(pattern, str(alpha_num)):
           return True
       else:
           return False 
       
email_id = "neethu17@gmail.com"
number_bangladesh="+8801712345678"
number_usa= "+11234567890"
alpha_num = "abCDfh//22ij6781"
print("Email id is valid:", email_address(email_id))
print("Bangladesh number is valid:", bangladesh_number(number_bangladesh))
print("USA number is valid:", usa_number(number_usa))
print("Alphanumeric password is valid:", alphanumeric_password(alpha_num))

`