# 1. The function will create a text file with the current timestamp and that file should have the content of current time stamp

`
import datetime

def create_timestamp_file():
    current_time = datetime.datetime.now().strftime("%Y-%m-%d_%H-%M-%S")
    file_name = f"timestamp_{current_time}.txt"
    with open(file_name, 'w') as file:
        file.write(current_time)
    
    print(f"File '{file_name}' with timestamp content has been created.")
create_timestamp_file()

`

# 2.Read a textfile and display the content 

`
def readtextfile(newfile):
    try:
        with open (newfile,"r") as file:
            storagefile = file.read()
            print(storagefile)
    except:
            print(f"error:{newfile}")
user_file = input("Enter the filename:")
readtextfile(user_file) 

`