# Elastic-setup

Alright, here's the premise: I was told to prove that I can set up an Elastic instance in Docker and make it so it can grab logs, but where's the fun in just doing just that on any random old machine/virtual machine(VM) and point another machine/VM at the elastic ports?  
So here's my super overkill and impractical(?) way of going about that task. Lol.  

## The Beginning

So, I'm not gonna lie. When I was handed that task, I was completely ready to just spin up my main linux VM(Kali Linux), install an Elastic instance in Docker there, then point another VM's logs at the ports and call it a day. I got as far as installing Elastic before I thought: Who would actually use Elastic that way? In freaking KALI. Nobody.  
So, I went back and started from scratch. If you're gonna do something, might as well do it properly, eh? Even if this is homework.  

## The setup

Ok, with all that talk, what is it we are actually trying to achieve with Elastic? Elastic is a Security Information and Event Management(SIEM), of course. It's a place to aggregate logs and monitor network and client activity, depending on how you set it up. What's it useful in? Enterprise and production environments. You won't set up a SIEM at home, unless you're a homelabber(sometimes you guys are weirdos, but still, respect).  
So, let's set up a basic simulated environment where you would use a SIEM.  

### How would the setup look like?

A SIEM is not gonna be of any use if it's just sitting out in the open, where anyone can go in, read, write, and do anything with it. So, it needs to be isolated. I achieved this by putting it in its own isolated network, behind a firewall. The clients would need to access the outside internet at large, so I would put them also behind the firewall, in their own network called a De-militarized Zone(DMZ). Yeah, don't ask me why that name, I didn't choose it. The analogy still works, though.  

Anyways, here's what I want the setup to look like and do:  

<img width="727" height="768" alt="image" src="https://github.com/user-attachments/assets/42483b71-3fbb-43d9-a46f-87e554b3dd3a" />

So, why this setup? One step at a time.  

These are the three zones we've established:  
1. Untrusted Zone: WAN(Internet) is basically the wild west. Anything and everything can happen here. As such, we don't trust this zone easily.  
2. Neutral Zone: DMZ is able to access WAN regularly. It's still internal, but we would be much more cautious of it.  
3. Internal Zone: LAN is our internal, secure zone.  

But the SIEM still can talk with some parts of the internet! And what about the DMZ clients being able to send logs to Elastic? Yes, yes, I know. If we are truly gonna harden a LAN node, we shouldn't allow any clients from the DMZ to blast data so recklessly at the LAN. Nor allow it to talk with anything on the internet directly.  
I chose to do it this way for a few reasons:
1. I'm not pro, bro. Lemme start small and build up. Both in the red and blue team sides. I'm aiming for this to be my long term playground. It's all hosted in VMs anyway.
2. This is actually a relatively plausible setup to encounter in the real world. All the tools I chose to use(OPNsense, elastic, docker) may be free, but they are also pretty much industry standard.
3. If setup properly, this setup is actually still really resilient. Let's just pray I have the skills to set it up properly.
4. I actually wanna take a break from setting up excessive VMs for now(More details to follow in future updates as I progress further into writing this report ~~for prosperity~~).

Anyways, for now, I'll throw the setup files I used for kali before I decided to abandon that approach, and the firewall setup files onto here. Firewall's still not completely done. I'm still setting up the elastic machine, so that's gonna have to wait for a future update. Along with me documenting my setup process. Lol.
