---
layout: post
title: Cybersecurity Incident Report
subtitle: Analyzing network layer communication
excerpt_image: https://github.com/jeffreytse/jekyll-theme-yat/assets/9413601/2ed22d49-90b1-4f7e-8e8f-b77b21dee505
categories: markdown
tags: [incident report, cybersecurity analysts, network traffic, security risks, malicious traffic]
top: 2
---

![banner](https://github.com/jeffreytse/jekyll-theme-yat/assets/9413601/2ed22d49-90b1-4f7e-8e8f-b77b21dee505)

**INCIDENT OVERVIEW**

Safespace is a company that specializes in providing IT services for clients. The company received a notification that Several customers of their clients reported that they were not able to access the client company website **www.yummyrecipesforme.com,** and saw the error **“destination port unreachable”** after waiting for the page to load. 

**RESPONDING TO THE SECURITY INCIDENT:**

**STEP 1: Analyse the incident with the Network Analyzer Tool**

As a security analyst, tasked with analyzing the situation and determining which network protocol was affected during this incident. First, I visited the website and also received the error “destination port unreachable.” To troubleshoot the issue, I load the network analyzer tool, **tcpdump,** and attempt to load the webpage again. 
To load the webpage, My browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. My browser then uses this IP address as the destination IP for sending an HTTPS request to the webserver to display the webpage. The analyzer shows that when I send UDP packets to the DNS server, I receive **ICMP** packets containing the error message: “udp port 53 unreachable.” 


tcpdump log
------------

In the tcpdump log, you find the following information:

        13:24:32.192571 IP 192.51.100.15.52444 › 203.0.113.2. domain: 35084+ A?
        yummyrecipesforme.com. (24)
        13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2
        udp port 53 unreachable length 254

        
        13:26:32.192571 IP 192.51.100.15.52444 › 203.0.113.2.domain: 35084+ A?
        yummyrecipesforme.com. (24)
        13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2
        udp port 53 unreachable length 320

        13:28:32.192571 IP 192.51.100.15.52444 › 203.0.113.2.domain: 35084+ A?
        yummyrecipesforme.com. (24)
        13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2
        udp port 53 unreachable length 150
        
      

Here's a numbered list:

 1. first item
 2. second item
 3. third item

Paragraphs are separated by a blank line.

2nd paragraph. *Italic*, **bold**, and `monospace`. Itemized lists
look like:

  * this one
  * that one
  * the other one

Note that --- not considering the asterisk --- the actual text
content starts at 4-columns in.

> Block quotes are
> written like so.
>
> They can span multiple paragraphs,
> if you like.

Use 3 dashes for an em-dash. Use 2 dashes for ranges (ex., "it's all
in chapters 12--14"). Three dots ... will be converted to an ellipsis.
Unicode is supported. ☺



An h2 header
------------

Here's a numbered list:

 1. first item
 2. second item
 3. third item
    

Note again how the actual text starts at 4 columns in (4 characters
from the left side). Here's a code sample:

    # Let me re-iterate ...
    for i in 1 .. 10 { do-something(i) }


As you probably guessed, indented 4 spaces. By the way, instead of
indenting the block, you can use delimited blocks, if you like:

~~~
define foobar() {
    print "Welcome to flavor country!";
}
~~~

(which makes copying & pasting easier). You can optionally mark the
delimited block for Pandoc to syntax highlight it:

~~~python
import time
# Quick, count to ten!
for i in range(10):
    # (but not *too* quick)
    time.sleep(0.5)
    print(i)
~~~



### An h3 header ###

Now a nested list:

 1. First, get these ingredients:

      * carrots
      * celery
      * lentils

 2. Boil some water.

 3. Dump everything in the pot and follow
    this algorithm:

        find wooden spoon
        uncover pot
        stir
        cover pot
        balance wooden spoon precariously on pot handle
        wait 10 minutes
        goto first step (or shut off burner when done)

    Do not bump wooden spoon or it will fall.

Notice again how text always lines up on 4-space indents (including
that last line which continues item 3 above).

Here's a link to [a website](http://foo.bar), to a [local
doc](local-doc.html), and to a [section heading in the current
doc](#an-h2-header). Here's a footnote [^1].

[^1]: Some footnote text.

Tables can look like this:

Name           Size  Material      Color
------------- -----  ------------  ------------
All Business      9  leather       brown
Roundabout       10  hemp canvas   natural
Cinderella       11  glass         transparent

Table: Shoes sizes, materials, and colors.

(The above is the caption for the table.) Pandoc also supports
multi-line tables:

--------  -----------------------
Keyword   Text
--------  -----------------------
red       Sunsets, apples, and
          other red or reddish
          things.

green     Leaves, grass, frogs
          and other things it's
          not easy being.
--------  -----------------------

A horizontal rule follows.

***

Here's a definition list:

apples
  : Good for making applesauce.

oranges
  : Citrus!

tomatoes
  : There's no "e" in tomatoe.

Again, text is indented 4 spaces. (Put a blank line between each
term and  its definition to spread things out more.)

Here's a "line block" (note how whitespace is honored):

| Line one
|   Line too
| Line tree

and images can be specified like so:

![example image](https://user-images.githubusercontent.com/9413601/123900693-1d9ebd00-d99c-11eb-8e9e-cf7879187606.png "An exemplary image")

Inline math equation: $\omega = d\phi / dt$. Display
math should get its own line like so:

$$I = \int \rho R^{2} dV$$

And note that you can backslash-escape any punctuation characters
which you wish to be displayed literally, ex.: \`foo\`, \*bar\*, etc.
