---
layout: post
title: Forensic CTF for new college students
---

## Introduction

Some time ago I was entrusted with the task of designing some exercises to be part of a CTF. Which aim was to introduce information security concepts to university first years students without previous experience in that field. I found this task quite difficult as striking a balance in the difficulty of the exercises turned out not to be as easy as I thought. I decided to focus on the forensics area because it was direct for me to draw a parallel with what a police detective would have to do and at the same time allow students to learn about protocols like TCP HTTP, tools like wireshark, scapy, hexdump etc. I hope you enjoy them as much as I do creating them, good luck.

### **Challenge 1:** Mobs chat

The International Comitee of Investigations is trying to catch a well known argentinian mobster named Mario. Last week one of Mario's minion was captured along with a list of future victims. However, the list is encrypted and only with the password (the flag) will be able to decrypted. Acording to Mario's psychological profile, he usually uses the same password pattern; a master password plus the name of any of his pets. We paid a group of hackers who provide us with a traffic capture of Mario's computer.
Will you be able to find the flag?

[Mario network traffic pcap][1]

[1]:{{ site.url }}/downloads/mario-network-traffic.tar.gz

**Hint:** Mario frequents unsafe chat sites.  
**MD5 Flag:** df5738a7e288813c2c0e84de74749f9e

### **Challenge 2:** Urgent data leak

It is suspected that the security of a computer has been compromised and the attackers are subtracting information in some way towards their server, therefore we proceed to capture network traffic from this computer and try to analyze what is happening. The objective is to find the flag that the attackers are stealing.

[Network traffic pcap][2]

[2]:{{ site.url }}/downloads/dump-network-traffic.tar.gz

**Hint:** There are some task that you have to do urgently.  
**MD5 Flag:** 03a0788654dbf801bb3d84bb252cd67c

### **Challenge 3:** PDF rfc

The famous conclave of people who designed the pdf format on a leisurely afternoon decided to write a small rfc briefly describing the format itself. Bored with this task and knowing in detail how it works they decided to hide a little message somewhere in the file. Can you find it?

[Rfc37778 pdf][3]

[3]:{{ site.url }}/downloads/rfc37778.pdf

**MD5 Flag:** 522bbad8370d66c1ed001c5a104593f8