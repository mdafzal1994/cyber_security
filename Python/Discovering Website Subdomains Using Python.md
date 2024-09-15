
#!usr/bin/env python

import requests


def request(url):
    try:
        request= requests.get("http://" + url)
        print(request)
        return request
    except requests.exceptions.ConnectionError:
        pass


target_url="google.com"  # base url

with open("/file_patha/word_list.txt","r") as wordlist_file:
     for line in wordlist_file:
         word=line.strip()  # will remove \n form word
         test_url =word + "." + target_url
         response = request(test_url)
         if response:
             print("[+] discover subdomain --> " + test_url)
