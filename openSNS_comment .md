# openSNS
A test project(Open source)
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import Select
from selenium.common.exceptions import NoSuchElementException
from selenium.common.exceptions import NoAlertPresentException
from HTMLTestRunner import HTMLTestRunner
from time import *
import unittest,re

class Pinglun(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Firefox()
        self.driver.implicitly_wait(30)
        self.base_url = "http://10.10.10.127/"
        self.verificationErrors = []
        self.accept_next_alert = True

    def tearDown(self):
        self.driver.refresh()
        self.driver.quit()

    def test_pinglun1(self):
        driver = self.driver
        driver.get(self.base_url + "/opensns/index.php?s=/ucenter/member/register.html")
        driver.maximize_window()
        driver.find_element_by_css_selector("p.p2").click()
        driver.find_element_by_id("inputEmail").clear()
        driver.find_element_by_id("inputEmail").send_keys("294865774@qq.com")
        driver.find_element_by_id("inputPassword").clear()
        driver.find_element_by_id("inputPassword").send_keys("abcd1234")
        driver.find_element_by_css_selector("button.login-btn").click()
        self.driver.implicitly_wait(10)
        driver.find_element_by_xpath("/html/body/div[2]/div[2]/div/div/ul/li[2]/a/span").click()
        sleep(1)
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div/div/div[2]/div[2]/div[2]/div[2]").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div/div/div[2]/div[2]/div[2]/div[2]").click()
        self.driver.implicitly_wait(10)
        driver.find_element_by_id("text_317").send_keys("good")
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div[2]/div[4]/div/div/div/p/a[2]/i").click()
        river.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        self.driver.implicitly_wait(10)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()

    def test_pinglun2(self):
        driver = self.driver
        driver.get(self.base_url + "/opensns/index.php?s=/ucenter/member/register.html")
        driver.maximize_window()
        driver.find_element_by_css_selector("p.p2").click()
        driver.find_element_by_id("inputEmail").clear()
        driver.find_element_by_id("inputEmail").send_keys("294865774@qq.com")
        driver.find_element_by_id("inputPassword").clear()
        driver.find_element_by_id("inputPassword").send_keys("abcd1234")
        driver.find_element_by_css_selector("button.login-btn").click()
        self.driver.implicitly_wait(10)
        driver.find_element_by_xpath("//li[2]/a/span").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div/div/div[2]/div[2]/div[2]/div[2]").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div/div/div[2]/div[2]/div[2]/div[2]").click()
        self.driver.implicitly_wait(10)
        driver.find_element_by_id("text_317").send_keys("5555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555555")
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[6]/div/div[2]/div[4]/div/div/div/p/a[2]/i").click()
        iver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        self.driver.implicitly_wait(10)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()

if __name__ == "__main__":
    testunit = unittest.TestSuite()
    testunit.addTest(Pinglun("test_pinglun1"))
    testunit.addTest(Pinglun("test_pinglun2"))
    now = strftime("%Y-%m-%d %H_%M_%S")
    fp = open('C:/Users/Administrator/Desktop/agileone/'+now+'result_pinglun.html', 'wb')
    runner = HTMLTestRunner(stream=fp, title='openSNS微博评论', description='用例执行情况:')
    runner.run(testunit)
    fp.close()
