# Elastic-setup

Alright, here's the premise: I was told to prove that I can set up an Elastic cluster in Docker and make it so it can grab logs, but where's the fun in just doing just that on any random old machine/virtual machine(VM) and point another machine/VM at the elastic ports?  
So here's my super overkill and impractical(?) way of going about that task. Lol.  

## The Beginning

So, I'm not gonna lie. When I was handed that task, I was completely ready to just spin up my main linux VM(Kali Linux), install an Elastic cluster in Docker there, then point another VM's logs at the ports and call it a day. I got as far as installing the Elastic cluster before I thought: Who would actually use an Elastic cluster that way? In freaking KALI. Nobody.  
So, I went back and started from scratch. If you're gonna do something, might as well do it properly, eh? Even if this is homework.  

## The setup

Ok, with all that talk, what is it we are actually trying to achieve with an Elastic cluster? Elastic is just a Security Information and Event Management(SIEM), of course. It's a place to aggregate logs and monitor network and client activity, depending on how you set it up. What's it useful in? Enterprise and production environments. You won't set up a SIEM at home, unless you're a homelabber(sometimes you guys are weirdos, but still, respect).  
So, let's set up a basic simulated environment where you would use a SIEM.  

### How would the setup look like?

A SIEM is not gonna be of any use if it's just sitting out in the open, where anyone can go in, read, write, and do anything with it. So, it needs to be isolated. I achieved this by putting it in its own isolated network, behind a firewall. The clients would need to access the outside internet at large, so I would put them also behind the firewall, in their own network called a De-militarized Zone(DMZ). Yeah, don't ask me why that name, I didn't choose it. The analogy still works, though.  

Anyways, here's what I want the setup to look like and do:  

<img width="721" height="771" alt="image" src="https://github.com/user-attachments/assets/86796633-a069-4308-a88f-3877af4f3cdb" />

