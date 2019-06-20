import time
from datetime import datetime as dt


hosts_path=r"C:\Windows\System32\drivers\etc\hosts"
redirect="127.0.0.1"

website_list1='www.cam4.in www.darering.com www.drtuber.com www.babosas.com www.89.com www.xvideos.com www.pinkworld.com'
website_list=website_list1.split()

with open(hosts_path,'r+') as file:
    content=file.read()
    for new in website_list:
        if new in content:
            pass
        else:
            file.write(redirect+" "+ new+"\n")

first=input("\nEnter the link\n")

link=first.split(sep=',')

"\n"

s_hour,s_min=input("\nBlocking Time:\n").split(sep=':')

"\n"

e_hour,e_min=input("\nUnblocking Time:\n").split(sep=':')


while True:
    if dt(dt.now().year,dt.now().month,dt.now().day,int(s_hour),int(s_min)) < dt.now() < dt(dt.now().year,dt.now().month,dt.now().day,int(e_hour),int(e_min)):
        print("\nWebsite Blocked...\n\n")
        with open(hosts_path,'r+') as file:
            content=file.read()
            for website in link:
                if website in content:
                    pass
                else:
                    file.write(redirect+" "+ website+"\n")
    else:
        with open(hosts_path,'r+') as file:
            content=file.readlines()
            file.seek(0)
            for line in content:
                if not any(website in line for website in link):
                    file.write(line)
            file.truncate()
        print("\n Website Unblocked...\n")
    time.sleep(5)
