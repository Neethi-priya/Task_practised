# drag and drop

`

from selenium import webdriver
from time import sleep
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC



class Drag_drop:

    def __init__(self,web_url):
        self.url = web_url
        self.driver = webdriver.Edge()

    def draggable(self):
        try:
            self.driver.maximize_window()
            self.driver.get(self.url)
            sleep(6)
            #wait =WebDriverWait(self.driver, 10)
            frame = self.driver.find_element(By.CLASS_NAME, value='demo-frame')
            self.driver.switch_to.frame(frame)
            drag =self.driver.find_element(by=By.XPATH, value="/html/body/div[1]")
            drop =self.driver.find_element(by=By.XPATH, value="/html/body/div[2]")
            ActionChains(self.driver).drag_and_drop(drag,drop).perform()
            sleep(5)
        except NoSuchElementException as selenium_error:
            print("Element Not Found",selenium_error)


url = "https://jqueryui.com/droppable/"
x = Drag_drop(url)
x.draggable()


`

`
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from time import sleep

class dragdrop:

    def __init__(self, web_url):
        self.url = web_url
        self.driver = webdriver.Edge()
        self.actions = ActionChains(self.driver)

    def logging(self):
        self.driver.maximize_window()
        self.driver.get(self.url)

    def drag_drop(self):
        try:
            wait = WebDriverWait(self.driver, 10)
            frame = self.driver.find_element(By.CLASS_NAME, value='demo-frame')
            self.driver.switch_to.frame(frame)
            drag_obj = wait.until(EC.presence_of_element_located((By.XPATH, "//p[text()='Drag me to my target']")))
            drop_destinee = wait.until(EC.visibility_of_element_located((By.XPATH, "//p[text()='Drop here']")))
            self.actions.drag_and_drop(drag_obj, drop_destinee).perform()
            sleep(2)
        except :
            print("unable to drop the box")
        finally:
            self.driver.quit()

url = "https://jqueryui.com/droppable/"
dd = dragdrop(url)
dd.logging()
dd.drag_drop()

`