# cowin

`
from selenium import webdriver
from selenium.webdriver.common.by import By
import time
class Priya:
    url = "https://www.cowin.gov.in/"
    driver = webdriver.Edge()
    faq_xpath = "//*[@id='navbar']/div[4]/div/div[1]/div/nav/div[3]/div/ul/li[4]/a"
    partners_xpath = "/html/body/app-root/app-header/header/div[4]/div/div[1]/div/nav/div[3]/div/ul/li[5]/a"
    
    def window_handles_data(self):
        self.driver.get(self.url)
        self.driver.maximize_window()
        time.sleep(2)
        parent_window =  self.driver.current_window_handle 
        print("windowId for cowin portal",parent_window)
        self.driver.find_element(by=By.XPATH, value=self.faq_xpath).click()
        time.sleep(5)
        self.driver.find_element(by=By.XPATH, value=self.partners_xpath).click()
        time.sleep(5)
        window_1 = self.driver.window_handles 
        print(window_1)
        for window_data in window_1:
            
            if window_data != parent_window:
                self.driver.switch_to.window(window_data)
                time.sleep(2)
                self.driver.close()
                time.sleep(5)
                 
            
p= Priya()
p.window_handles_data()
`

# labour

`
from selenium import webdriver
from selenium.webdriver.common.by import By
import time
from selenium.webdriver.common.action_chains import ActionChains
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.common.keys import Keys
import os  
import urllib
class Priya:
    url = "https://labour.gov.in/"
    driver = webdriver.Edge()
    
    def documents_download(self):
      try:
        self.driver.maximize_window()
        self.driver.get(self.url)
        time.sleep(10)
        elementToHover = self.driver.find_element(by=By.LINK_TEXT, value ="Documents")
        hover = ActionChains(self.driver).move_to_element(hover)
        hover.perform()
        time.sleep(3)
        self.driver.find_element(by=By.ID, value="//*[@id='nav']/li[7]/ul/li[2]/a").click()
        time.sleep(7)
        self.driver.find_element(by=By.ID, value="//*[@id='fontSize']/div/div/div[3]/div[2]/div[1]/div/div/div/div/div/div/div/div/div/div[2]/div[2]/table/tbody/tr[2]/td[2]/a").click()
        time.sleep(7)
        alert = self.driver.switch_to.alert
        alert.accept()
        time.sleep(6)
        handles = self.driver.window_handles
        for handle in handles:
            self.driver.switch_to.window(handle)
            if self.driver.current_url=="https://labour.gov.in/sites/default/files/mpr_october_2023.pdf":
                self.driver.find_element(by=By.ID, value="//*[@id='icon']/iron-icon")
                print("downloaded")
            elif self.driver.current_url == "https://labour.gov.in/monthly-progress-report":
                pass
                
      except NoSuchElementException as e:
          print(e)
      finally:
          self.driver.quit()
          
    def download_media(self):
        directory = "python_task_20"
        parent_dir = "D:\\new"
        path = os.path.join(parent_dir, directory)    
        os.mkdir(path)  
        print("Directory created") 
        try:
           self.driver.maximize_window()  
           self.driver.get(self.url)
           time.sleep(7)
           elementTo_hover= self.driver.find_element(by=By.XPATH, value="//a[text()='Media']")
           hover = ActionChains(self.driver).move_to_element(elementTo_hover)
           hover.perform()
           time.sleep(2)
           self.driver.find_element(by=By.XPATH, value="//*[@id='nav']/li[10]/ul/li[2]/a").click()
           time.sleep(3)
           hover_1 = self.driver.find_element(by=By.XPATH, value="//img[@title='Swachhata Hi Seva']").get_attribute('src')
           hover_2 = self.driver.find_element(by=By.XPATH, value="//img[@title='LEMM']").get_attribute('src')
           #ActionChains(self.driver).move_to_element(hover_1).key_down(Keys.Control).send_keys("s")​‌
           print(hover_1)
           time.sleep(10)
           """src_1 = []
           for img in hover_1:
                src_1.append(img.get_attribute('src'))
                # Retrieve and download the images.
                for i in range(10):    
                    urllib.request.urlretrieve(str(src[i]),"sample_data/pets{}.jpg".format(i)) """
           
           
           
           time.sleep(10)
           print("downloaded")
        except NoSuchElementException as error:
            print(error)
        finally:
            self.driver.quit()
           
    
    
p= Priya()
p.download_media()



`