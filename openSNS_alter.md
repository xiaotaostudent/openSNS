# openSNS
A test project(Open source)
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import Select
from selenium.common.exceptions import NoSuchElementException
from selenium.common.exceptions import NoAlertPresentException
import unittest, time, re

class OpenSNS(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Firefox()
        self.driver.implicitly_wait(30)
        self.base_url = "http://10.10.10.127/"
        self.verificationErrors = []
        self.accept_next_alert = True
    
    def test_open_s_n_s(self):
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
        above=driver.find_element_by_xpath("/html/body/div[2]/div[3]/li[4]/a/img")
        # ActionChains(driver).move_to_element(above).perform()
        # driver.find_element_by_xpath("/html/body/div[2]/div[3]/li[4]/ul/li/a").click()
        # driver.find_element_by_xpath("/html/body/div[2]/div[3]/li[3]/a/span[2]")
        ab=driver.find_element_by_xpath("/html/body/div[2]/div[3]/li[3]/a/span[2]")
        ActionChains(driver).move_to_element(ab).perform()
        driver.find_element_by_xpath("/html/body/div[2]/div[3]/li[3]/ul/div[4]/div[2]/a/div").click()
        driver.find_element_by_xpath("/html/body/div/div[2]/div[3]/li[4]").click()
        Select(driver.find_element_by_id("J_province")).select_by_visible_text(u"山东省")
        Select(driver.find_element_by_id("J_city")).select_by_visible_text(u"青岛市")
        Select(driver.find_element_by_id("J_district")).select_by_visible_text(u"市南区")
        driver.find_element_by_id("signature").clear()

        driver.find_element_by_id("signature").send_keys("hello everybody")
        driver.find_element_by_css_selector("button.btn.btn-primary").click()
        driver.find_element_by_link_text(u"个人资料").click()
        driver.find_element_by_id("expand_1").clear()
        driver.find_element_by_id("expand_1").send_keys("123456789")
        driver.find_element_by_id("expand_2").click()
        driver.find_element_by_xpath("/html/body/div/div[4]/div/div[2]/div/div/div/div/div/div/div[2]/div[2]/form/div/div/div/div/dl[2]/div/div/input").clear()
        driver.find_element_by_xpath("/html/body/div/div[4]/div/div[2]/div/div/div/div/div/div/div[2]/div[2]/form/div/div/div/div/dl[2]/div/div/input").send_keys("2017-01-01")
        driver.find_element_by_id("submit_btn").click()
        driver.find_element_by_link_text(u"开发者资料").click()
        Select(driver.find_element_by_id("expand_3")).select_by_visible_text("ruby")
        driver.find_element_by_xpath("(//input[@name='expand_4'])[2]").click()
        driver.find_element_by_id("expand_5").clear()
        driver.find_element_by_id("expand_5").send_keys("hello world")
        driver.find_element_by_css_selector("#expand_tab_2 > form.ajax-form > div.with-padding > div.row > div.col-xs-8 > #submit_btn").click()
        driver.find_element_by_link_text(u"开源中国资料").click()
        driver.find_element_by_id("expand_7").clear()
        driver.find_element_by_id("expand_7").send_keys("Michael"
                                                        "")
        driver.find_element_by_css_selector("#expand_tab_3 > form.ajax-form > div.with-padding > div.row > div.col-xs-8 > #submit_btn").click()
        driver.find_element_by_link_text(u"资料设置").click()
        assertEqual(u"编辑资料", driver.title)

    
    # def is_element_present(self, how, what):
    #     try: self.driver.find_element(by=how, value=what)
    #     except NoSuchElementException, e: return False
    #     return True
    #
    # def is_alert_present(self):
    #     try: self.driver.switch_to_alert()
    #     except NoAlertPresentException, e: return False
    #     return True
    #
    # def close_alert_and_get_its_text(self):
    #     try:
    #         alert = self.driver.switch_to_alert()
    #         alert_text = alert.text
    #         if self.accept_next_alert:
    #             alert.accept()
    #         else:
    #             alert.dismiss()
    #         return alert_text
    #     finally: self.accept_next_alert = True
    #
    # def tearDown(self):
    #     self.driver.quit()
    #     self.assertEqual([], self.verificationErrors)

if __name__ == "__main__":
    unittest.main()
