# HTB_TornadoService
Hack The Box Challenge (Tornado Web Service)

# CHALLENGE DESCRIPTION
You have found a portal of the recently arising tornado malware, it appears to have some protections implemented but a bet was made between your peers that they are not enough. Will you win this bet?

# Tornado Dashboard
http://94.237.49.36:49193/
![image](https://github.com/user-attachments/assets/f981f194-77b2-4782-8d93-493925ac98ad)


# Tools Used
- BurpSuite
- CURL
- Python for Web Server listener
- OS: Kali Linux

# Attempts
- 1st Attempt: IP Scanning using BurpSuite. #### UNSUCCESSFUL
- 2nd Attempt: SQL Injection. #### UNSUCCESSFUL
- 3rd Attempt: CSRF Attack. # SUCCESSFUL #

# Approach used for CSRF attack
1. Download the 
   ![image](https://github.com/user-attachments/assets/b26ef7fd-1109-4f23-959b-fd852996624a)

2. Create a CSRF Payload file.
   Setup http server (Listener) on port 1337
   python -m http.server 1337 
   ![image](https://github.com/user-attachments/assets/d03d0f9b-342a-485b-839a-62045be8b9ed)

3. Trigger CSRF Payload (using CURL)
   Host the HTML file through the browser to trigger the CSRF payload

4. Report Tornado on HTB Server
   curl "http://94.237.59.207:47563/report_tornado?ip=127.0.0.1"

5. Use CURL commands to automate and to create a random user
   curl -X POST "http://94.237.59.207:47563/login" \
   -H "Content-Type: application/json" \
   -d '{"username": "kittykat", "password": "kittykat"}' \
   -c cookie.txt 

6. Extract the cookies to a file (cookie.txt)
   curl -X GET "http://94.237.59.207:47563/stats" -b cookie.txt

# CAPTURED FLAG
- # HTB{s1mpl3_stuff_but_w1th_4_tw15t!}

7. Submitted flag on Hack The Box
   ![image](https://github.com/user-attachments/assets/232baf85-ba3a-475f-93ef-65023aec4ae9)

Challenge Completed
![image](https://github.com/user-attachments/assets/cc652c48-3e97-4053-b061-de20221c3c7f)

