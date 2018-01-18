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

class Fabu(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Firefox()
        self.driver.implicitly_wait(300)
        self.base_url = "http://10.10.10.127/"
        self.verificationErrors = []
        self.accept_next_alert = True
        driver = self.driver
        driver.get(self.base_url + "/opensns/index.php?s=/ucenter/member/register.html")
        driver.maximize_window()
        driver.find_element_by_css_selector("p.p2").click()
        driver.find_element_by_id("inputEmail").clear()
        driver.find_element_by_id("inputEmail").send_keys("294865774@qq.com")
        driver.find_element_by_id("inputPassword").clear()
        driver.find_element_by_id("inputPassword").send_keys("********")
        driver.find_element_by_name("remember").click()
        driver.find_element_by_css_selector("button.login-btn").click()
        driver.find_element_by_xpath("//li[2]/a/span").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div[3]/div").click()
        driver.find_element_by_class_name("icon-zs").click()
    def tearDown(self):
        self.driver.refresh()
        self.driver.quit()

    #  内容小于140个字
    def test_fabu1(self):
        driver = self.driver
        driver.find_element_by_id("weibo_content").clear()
        driver.find_element_by_id("weibo_content").send_keys("hello world")
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        driver.implicitly_wait(30)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")

    #  内容多于140个字
    def test_fabu2(self):
        driver = self.driver
        driver.find_element_by_id("weibo_content").clear()
        driver.find_element_by_id("weibo_content").send_keys("f someone loves a flower, of which just one single blossom grows in all the millions and millions of stars, it is enough to make him happy just to look at the stars. He can say to himself, Somewhere, my flower is there… But if the sheep eats the flower, in one moment all his stars will be darkened… And you think that is not important! ")
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        self.driver.implicitly_wait(30)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()

    # 内容为空
    def test_fabu3(self):
        driver = self.driver
        driver.find_element_by_id("weibo_content").clear()
        driver.find_element_by_id("weibo_content").send_keys("")
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        self.driver.implicitly_wait(30)
        sleep(2)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()

    # 添加表情
    def test_fabu4(self):
        driver = self.driver
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div/a/i").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div/div/div/div/div[2]/a[103]/img").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div/div/div/div/div/a").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div[2]/a/i").click()
        self.driver.implicitly_wait(30)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()

    # 添加图片
    def test_fabu5(self):
        driver = self.driver
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div/a[2]/i").click()
        driver.find_element_by_xpath("/html/body/div[4]/div/div/div/div/div/div[3]/div/div[2]/div/div/div[3]/div/div/div[2]/label").click()
        self.driver.implicitly_wait(30)
        sleep(1)
        title = driver.title
        self.assertEqual(title, "微博-OpenSNS v5开源社群系统")
        driver.refresh()


if __name__ == "__main__":
    testunit = unittest.TestSuite()
    testunit.addTest(Fabu("test_fabu1"))
    testunit.addTest(Fabu("test_fabu2"))
    testunit.addTest(Fabu("test_fabu3"))
    testunit.addTest(Fabu("test_fabu4"))
    testunit.addTest(Fabu("test_fabu5"))
    now = strftime("%Y-%m-%d %H_%M_%S")
    fp = open('C:/Users/Administrator/Desktop/agileone/'+now+'result_fabu.html', 'wb')
    runner = HTMLTestRunner(stream=fp, title='openSNS发布微博', description='用例执行情况:')
    runner.run(testunit)
    fp.close()
