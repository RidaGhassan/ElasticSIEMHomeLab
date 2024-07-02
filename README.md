![SIEMLAB1](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/8694009c-c7e2-4ec9-ab47-94887f8e55de)

1. To start, create an Elastic account, and configure Kalilinux on your preferred hypervisor.

![SIEMLAB2](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/9bc45c7a-2a5c-4132-9bbc-550f3c382bc5)

2. Click on the Hamburger menu on the top left, click on add integration, then click on Elastic Defend.

![SIEMLAB3](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/e068501d-882e-4414-8f3b-60433d6f3cef)

3. Follow these Configurations.

![SIEMLAB4](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/2a1558b7-8f61-4366-9037-6a050e257618)

![SIEMLAB5](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/b6f1b01d-6e0e-448a-bb79-da6e49296d80)

4. Click " Add Elastic Agents to your host ".

![SIEMLAB6](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/c410fbe4-f39c-464d-8958-1b509b2fcd9f)

5. You should then be redirected to this screen, copy the given linux command, then open a KaliLinux Terminal.

![SIEMLAB7](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/595b75e2-8d39-40a6-987a-c5931faf002c)

6. Input the command into the terminal, this will install the SIEM into your VM

![SIEMLAB8](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/c234e727-c83c-4d47-8e37-f8be95312015)

7. Input the command " sudo systemctl status elastic-agent.service " in order to confirm if installation was a success

 ![SIEMLAB9](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/6ca3c304-8d2b-4f74-b961-412e490b6397)

8. After confirming success, input the command " nmap -p- localhost ". This essentially will preform an nmap scan for the machine.

![SIEMLAB10](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/2cbd4cb6-d119-4e58-a0e9-be0519bd822e)

9. Return to the Elastic manager, Click on the Hamburger menu on the top left, under Observability, hit logs. Here you will find the nmap log from when you preformed an nmap scan earlier on your machine.
   
![SIEMLAB11](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/809d38de-4fb3-4c75-b807-3c696127fab5)

10. In order to visualize the logs, you will place them on a graph. first, open the hamburger menu again, and click on dashboards, then create a new dashboard.

Afterwards, select a method of observation of your choice, I selected the " Bar Vertical Stacked " display. On the Horizontal Axis, select " timestamp " and on the vertical axis, select " count of records ".

![SIEMLAB12](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/9fbee96c-d504-4c39-9c63-d2c8ad934b85)

It should look like this.

![SIEMLAB13](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/74dc8d5b-cc6b-4d8f-aa72-a0e665f34ae9)

11. Now that we have the graph, put in another command of your choice into the KaliLinux terminal such as " sudo ps "
and " nmap sV localhost ".

![SIEMLAB14](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/11aaf9c3-033a-47e9-aa20-2ba418f1f90e)

After a brief wait, your SIEM should detect it in the log system, as well as present it visually in the graph you made.
Notice that the terminal requests were made at 7:14EDT which is why the graph spikes up so high during that exact time.

![SIEMLAB15](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/466fd1ad-f799-4ee9-b39f-dec0d107fe31)

12. Finally, we will create a rule to notify us whenever an nmap scan is done.

Click on the hamburger icon again, and navigate to security, then to alerts.

![SIEMLAB16](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/a72db202-20a5-4059-afd2-d29d04c8b3cf)

13. Select " Manage rules " then " Create new rule " after that, route the alert system to detect nmap scans by typing " event.action:"nmap_scan " in the custom query field.

![SIEMLab17](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/761bacd0-91bf-4e14-a201-44f7f62100a3)

14. Name your rule and describe it so that it is easy to understand and track if someone else is on the SIEM.

![SIEMLAB18](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/b86c7155-c5a7-417d-9be9-c15e78824383)

15. Route your alert to your method of communication. I chose E-mail since this is my home SIEM.

![SIEMLAB19](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/bb9dadaa-5f79-4839-b1df-2ed7a6244174)

Let's test to see if the alert system was successful. Let's nmap scan my github at " nmap www.github.com/ridaghassan "

![SIEMLAB20](https://github.com/RidaGhassan/ElasticSIEMHomeLab/assets/174221510/4efa27ee-6f2e-4b24-af4c-f76f7a3e9652)

As you can see, the log system detected my nmap scan and reported it back to the SIEM.
