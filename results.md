### Combined solution
```
Secret
    Mha4hOgMyAqP8ClvU1UJ63p1N04t0His/dDtffWM
    LVhDWhearQNW+SrIFmJsccII/1cqfaFrg9AMczJ4
    YjOeOc8sTefBd0K2bsFM1bMVM/hlQ2AKNJGo9NeT
    DoIfX6vXz7IqDAE5uxEtKUbD9Va7dukOcrZDq6hr
    f4vxBrRTuM5ZHdiiYftgfcJyAmLkQVSntDJH+yiA
    fJaOBOB6zy7O9gGxMIyCmkxLNjXz7qLtJ1s/OOrf
    SkCXsIRTXyKN2RZ/rn8PUcX3PfNuAov4CQsHZcaB
    874B8UkPsaG3whwkDZ6f0p4UN6YsIFX5nv4tZU+A
    kEghaGw6Js6mBu5kOZfudw==
    
Public key
    -----BEGIN PUBLIC KEY-----
    MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsmKOUWiNH0zavc2JJnrB
    uOXSA7eJkh7PTpaRREs6tHWw7K1GdDNQ3H2HHRHYLjlXRtJnPyhEdwTtlulPZsOB
    XEbQ92Rpc6PSU5vzJa4MAEMtUtQZ7uf+Jez9FP2b21evp32ktM6h1AD6C//2hNMm
    WLtfGX2O8fkbV3TDIMp7I/PHWEMhVw+8uMKpcrbJ0JD6/yEBEv7J1wFouYCH8wN6
    smsi2hEz5eahpn4LrpLWbkuT+Ifte4YnVU0/nTBz+c8SyojjX4MoTggt3C0LTGhe
    EqM+mmA5HwNWeABIH8KWNwd5JDM1gdkg3l/zFfdLlYvni8poXGHVnHt2ThFOe6p8
    1QIDAQAB
    -----END PUBLIC KEY-----
    
Private key
    -----BEGIN PRIVATE KEY-----
    MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCyYo5RaI0fTNq9
    [...]
    zQQpFsMZO0D2tw0fl2WrEqS0
    -----END PRIVATE KEY-----

1. zYkmesG45dIDt4mSHs9OlpFESzq0dbDsrUZ0M1DcfYcdEdguOVdG0mc/KER3BO2W
2. 6U9mw4FcRtD3ZGlzo9JTm/MlrgwAQy1S1Bnu5/4l7P0U/ZvbV6+nfaS0zqHUAPoL
3. 
4. I4TO/n3NdyXtF8JiCPjCsCq9hYzXDHlNTkNmosZUEk0lqzaPW8A3GwFLGBxg7b6u

End key
    -----BEGIN PRIVATE KEY-----
    MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCyYo5RaI0fTNq9
	 zYkmesG45dIDt4mSHs9OlpFESzq0dbDsrUZ0M1DcfYcdEdguOVdG0mc/KER3BO2W
	 6U9mw4FcRtD3ZGlzo9JTm/MlrgwAQy1S1Bnu5/4l7P0U/ZvbV6+nfaS0zqHUAPoL
	 ...
	 I4TO/n3NdyXtF8JiCPjCsCq9hYzXDHlNTkNmosZUEk0lqzaPW8A3GwFLGBxg7b6u
	 ...
    zQQpFsMZO0D2tw0fl2WrEqS0
    -----END PRIVATE KEY-----
```

### December 1st 
#### Solution 
Using telnet and asking xmas.rip for wishlist service on port 1 (adding random elements to the wishlist) returned the answer.

#### Command

```bash
telnet xmas.rip 1
```

#### Answer

```
zYkmesG45dIDt4mSHs9OlpFESzq0dbDsrUZ0M1DcfYcdEdguOVdG0mc/KER3BO2W
```

### December 2nd
##### Solution
Using given script to exploit heartbleed CVE-2014-0160 (`Last christmas I gave you my heart` referred to heartbleed vulnerability). 
##### Command
```bash
py python hb-test.py xmas.rip -p 2
```
##### Anwser
```
6U9mw4FcRtD3ZGlzo9JTm/MlrgwAQy1S1Bnu5/4l7P0U/ZvbV6+nfaS0zqHUAPoL
```

### December 3rd
##### Solution
Solution seems to be to manage to use HTTP over SCTP to get a response from xmas.rip:3, but I can't figure out how to install a HTTP over SCTP client on my mac :'(

### December 4th
##### Solution
Spent a lot of time trying to search for a convoluted SYN/ACK attack or a TLS vulnerability. The solution was much simpler however, it was a simple port-knocking pattern (knock on ports 42, 23, 16, 15, 8). Port 8 answers with the secret. However if you curl port 4 right after 8, it returns a message :

```bash
curl: (35) error:1400410B:SSL routines:CONNECT_CR_SRVR_HELLO:wrong version number
```

Might be worth looking into this a bit more
##### Command
```bash
curl https://xmas.rip:42
curl https://xmas.rip:23
curl https://xmas.rip:16
curl https://xmas.rip:15
curl https://xmas.rip:8
curl https://xmas.rip:4
```
##### Anwser
```
I4TO/n3NdyXtF8JiCPjCsCq9hYzXDHlNTkNmosZUEk0lqzaPW8A3GwFLGBxg7b6u
```

### Template
##### Solution
bla bla bla bla
##### Command
```bash
command
```
##### Anwser
```
token
```
