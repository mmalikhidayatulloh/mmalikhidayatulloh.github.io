
# How to Send
```
~ >>> telnet 192.168.43.224 25                                                                                                                           
Trying 192.168.43.224...
Connected to malik.local.
Escape character is '^]'.
220 localhost ESMTP
helo test.local
250 localhost
mail from: test@test.local
250 2.1.0 Ok
rcpt to: malik@malik.local
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
from: test@test.local
to: malik@malik.local
subject: test

test
.
250 2.0.0 Ok: queued as B636B16077E
quit
221 2.0.0 Bye
Connection closed by foreign host.
You have new mail.
```

# How to Read

```
~ >>> telnet 192.168.43.224 pop3                                                                                                                      
Trying 192.168.43.224...
Connected to 192.168.43.224.
Escape character is '^]'.
+OK Dovecot ready.
user malik
+OK
pass ******
+OK Logged in.
retr 2
+OK 438 octets
Return-Path: <test@test.local>
X-Original-To: malik@malik.local
Delivered-To: malik@malik.local
Received: from test.local (malik.local [192.168.43.224])
	by localhost (Postfix) with SMTP id B636B16077E
	for <malik@malik.local>; Fri, 13 Aug 2021 04:41:34 +0700 (WIB)
from: test@test.local
to: malik@malik.local
subject: test
Message-Id: <20210812214201.B636B16077E@localhost>
Date: Fri, 13 Aug 2021 04:41:34 +0700 (WIB)

test
.
quit
+OK Logging out.
Connection closed by foreign host.
```