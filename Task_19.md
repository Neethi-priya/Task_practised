# sauce_demo

`
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time


class Priya:
    def __init__(self,url,username,password):
        self.url =url
        self.username=username
        self.password=password
    
    def login(self):
        self.driver = webdriver.Edge()
        self.driver.maximize_window()
        
        self.driver.get(self.url)
        self.driver.find_element(by=By.ID, value="user-name").send_keys(self.username)
        time.sleep(2)
        self.driver.find_element(by=By.XPATH, value="//*[@id='password']").send_keys(self.password) 
        time.sleep(2)
        self.driver.find_element(by=By.XPATH, value="//*[@id='login-button']").click()
        time.sleep(2) 
        
        get_title = self.driver.title 
        print(get_title)
        get_current_url =  self.driver.current_url 
        print(get_current_url)
        
        page_content = self.driver.page_source 
        f = open("Webpage_task_11.txt","w")
        f.write(page_content) 
        f.close()
        print("Entire content of the page has written")

url = "https://www.saucedemo.com/"
username="standard_user"
password="secret_sauce"
data = Priya(url,username,password)
data.login()


`