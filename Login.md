# openSNS
A test project(Open source)
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import Select
from selenium.common.exceptions import NoSuchElementException
from selenium.common.exceptions import NoAlertPresentException
import unittest, re
from time import sleep
from HTMLTestRunner import HTMLTestRunner

class Login(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Firefox()
        self.driver.implicitly_wait(10000)
        self.base_url = "http://10.10.10.127/"
        # driver = self.driver
        # driver.get(self.base_url + "/agileone/")
        # self.verificationErrors = []
        # self.accept_next_alert = True

    def tearDown(self):
        self.driver.quit()
    
    def test_login1(self):
        # driver = self.driver
        # driver.get(self.base_url + "/agileone/")
        #1.用户名为空 密码为空
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")

    def test_login2(self):
        # #2.用户名为空 密码不为空
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("123456")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login3(self):
        # #3.用户名不为空 密码为空
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("123456")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login4(self):
        # #4.用户名和密码相同
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("abcde")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("abcde")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login5(self):
         # #5.用户名和密码相同
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("123456")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("123456")
        driver.find_element_by_id("login").click()
        sleep(2)
        title = driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login6(self):
        # #6.用户名错误 密码正确
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("abcde")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("admin")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login7(self):
        # #7.用户名正确 密码错误
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("admin")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("abcde")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title, "AgileOne - Power to Agile Development")
    def test_login8(self):
        #8.用户名正确 密码正确
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("admin")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("admin")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title,"AgileOne - Power to Agile Development" )
    def test_login9(self):
        #9.用户名正确 密码正确
        driver = self.driver
        driver.get(self.base_url + "/agileone/")
        driver.find_element_by_id("username").clear()
        driver.find_element_by_id("username").send_keys("denny")
        driver.find_element_by_id("password").clear()
        driver.find_element_by_id("password").send_keys("denny")
        driver.find_element_by_id("login").click()
        sleep(2)
        title=driver.title
        self.assertEqual(title,"AgileOne - Power to Agile Development")
    


if __name__ == "__main__":
    # unittest.main(
    testunit = unittest.TestSuite()
    testunit.addTest(Login("test_login1"))
    testunit.addTest(Login("test_login2"))
    testunit.addTest(Login("test_login3"))
    testunit.addTest(Login("test_login4"))
    testunit.addTest(Login("test_login5"))
    testunit.addTest(Login("test_login6"))
    testunit.addTest(Login("test_login7"))
    testunit.addTest(Login("test_login8"))
    testunit.addTest(Login("test_login9"))
    # now = time.strftime("%Y-%m-%d %H_%M_%S")
    # filename ='C:/Users/Administrator/Desktop/agileone/'+now + 'result.html'
    fp = open('C:/Users/Administrator/Desktop/agileone/result.html', 'wb')
    runner = HTMLTestRunner(stream=fp, title='openSNS登录模块', description='用例执行情况:')
    runner.run(testunit)
    fp.close()

