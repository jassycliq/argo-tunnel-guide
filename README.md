# Argo Tunnel guide
How I personally setup Cloudflare's Argo Tunnel for my personal unraid server without using a reverse proxy.


From my understanding, this creates a "tunnel" to Cloudflare servers which then points to a specific device and port in my network. I don't need to worry about opening ports up on my router, setting up some reverse proxy, nor setting up a dynamic dns service AND I don't have to worry about double NAT.  
&nbsp;  
Unfortunately, I can't figure out if this is a paid product or not. It's technically a part of the Argo suite which IS a paid product but there have been reports that Argo tunnels at some point became free. Everything on Cloudflare's website points to it being a paid product but a week later and there aren't any extra charges yet in the billing area. So YMMV.  
&nbsp;  
If you're willing to try it out though I've got a basic setup that works for Unraid.  
* [Download the binary that works for your personal computer](https://developers.cloudflare.com/argo-tunnel/downloads)  
* ![Still on your personal computer enter the command `cloudflared tunnel login`](https://is.gd/oAphCd)  
This will open a new webpage where you log into your cloudflare account.  
* Choose the zone that you want to use  
![This will save a `cert.pem` somewhere on your computer](https://is.gd/qGrEZg)  
* Grab said file and save it onto your Unraid server somewhere, preferably where you want containers to have access (appdata?)  
* Go to your Docker tab and scroll to the bottom  
* Add container  
![Use the following container I found to start using the argo tunnel](https://is.gd/PzFKhX)  
* That docker isn't set in stone, it can be adjusted for your own setup but it'll work to get you going. The first key is the domain you want to setup for said service (plex), second key is the local ip for said service with said port. Then the last two are just my way of getting the container to use our cert.  
* Rinse and repeat for any other services you want. I saw a tutorial somewhere where they also use Cloudflare Access to add some sort of Auth in front of their services but I don't open anything else up so I didn't go that far.  
&nbsp;  
If there's a better way to do this, or even another way to get around my future dynamic DNS and double NAT issue, I'll gladly take it.  
I also wasn't able to figure how to keep my traefik setup to work with this so if there's a way to do that I would love to keep using it.
