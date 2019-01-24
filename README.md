![Example-Logo](https://cdn.discordapp.com/attachments/452526740045037587/536261295305916418/OWO_MN_banner.png)

# One World Masternode Setup Guide (Ubuntu 16.04)
***
## Required
1) **100000 OWO coins**
2) **Local Wallet https://github.com/OneWorldCoin/owo/releases**
3) **VPS with UBUNTU 16.04**
4) **Putty https://www.putty.org/**
5) **Text editor on your local pc to save data for copy/paste**
***

***On your Local Wallet***
* Create an address with a label MN1 and send exactly 100000 OWO to it. Wait to complete 6 confirmations on “ Payment to yourself “ created.

* Open the Debug Console ( Tools – Debug Console ) and type ***masternode genkey***.
You will then receive your private key, save it in a txt to use it later.
  ```
  Example:
          masternode genkey
          w8723KqiiqtiLH6y2ktjfwzuSrNucGAbagpmTmCn1KnNEeQTJKf
* Still at Debug Console type ***masternode outputs*** and save txhash and outputidx on a txt
  ```
  Exemple:
          "txhash" : "12fce79c1a5623aa5b5830abff1a9feb6a682b75ee9fe22c647725a3gef42saa",
		         "outputidx" : 0

***On Putty***

* Once logged in your vps, *copy/past* each line one by one with *Enter*

	:arrow_forward: `wget -q https://github.com/OneWorldCoin/owo/releases/download/initial/owo-mn.sh`

	:arrow_forward: `bash owo-mn.sh`


* Let this run, and when it ask you to install dependencies, if you're not sure press ***y*** and then enter

* It will take some time and then will ask to compile the Daemon, press ***y*** and then enter 

* Last thing script will ask you is to provide Masternode Genkey. Copy the one you got previously (masternode genkey) and press enter.

Remember to do `oneworld-cli getblockcount` to check if VPS synced with chain

Do not close your terminal/ command prompt window at this point.

***Go back to your Local Wallet***

* Open the Masternode Configuration file (tools – open masternode configuration file) and add a new line (without #) using this template (bold needs to be changed) in the final save it and close the editor

**ALIAS VPS_IP**:32112 **masternodeprivkey TXhash Output**

		Example:
		MN1 125.67.32.10:29711 w8723KqiiqtiLH6y2ktjfwzuSrNucGAbagpmTmCn1KnNEeQTJKf
		12fce79c1a5623aa5b5830abff1a9feb6a682b75ee9fe22c647725a3gef42saa 0

* Close and Re-open Local Wallet, and at Masternode Tab you will find your MN with status MISSING

***(For the next steps you need to have already 21 confirmation on “Payment to yourself “ created in first step)***

* Go to Debug Console type the following: ***startmasternode alias 0 (mymnalias)***

		Example:
		startmasternode alias 0 MN1
***

***Go back to Putty***

   :arrow_forward: `oneworld-cli masternode status`

You need to get **"status" : 4**

## Congratulations your One World node it's running
