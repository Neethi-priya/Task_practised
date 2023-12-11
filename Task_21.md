# cookies

`
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time 
class Priya:
    url ="https://www.saucedemo.com/"
    driver =webdriver.Edge()
    def login(self):
        self.driver.maximize_window()
        self.driver.get(self.url)
        time.sleep(4)
        cookie_befor_login=self.driver.get_cookies()
        #cookie_home_page = cookies[0]['value']
        print('Initial Value of Cookie Before Login # ', cookie_befor_login)
        self.driver.find_element(by=By.ID, value ="user-name").send_keys("standard_user")
        time.sleep(2)
        self.driver.find_element(by=By.ID, value="password").send_keys("secret_sauce")
        time.sleep(2)
        self.driver.find_element(by=By.XPATH, value="//*[@id='login-button']").click()
        print("logged in")
        time.sleep(3)
        cookies_after_login =self.driver.get_cookies()
        #cookie_after_login = cookies_after_login[0]['value']
        print('Initial Value of Cookie After Login # ', cookies_after_login) 
        self.driver.find_element(by=By.XPATH, value="//*[@id='react-burger-menu-btn']").click()
        time.sleep(3)
        self.driver.find_element(by=By.ID, value="logout_sidebar_link").click()
        time.sleep(3)
        if(cookie_befor_login != cookies_after_login):
            print("SUCCESS # Login Success. Previous Cookie ID before Login is {a} and after login Cookie ID is {b}".format(a=cookie_befor_login, b=cookies_after_login))

p = Priya()
p.login()


`