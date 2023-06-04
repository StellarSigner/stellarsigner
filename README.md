# Build an offline, airgapped Stellar signing device for less than $50!

**The project is currently in development and is not yet ready for use with real funds. Please check back soon!**

![Image of LumenSigners in Open Pill Enclosures](docs/img/Open_Pill_Star.JPG)

---------------

* [Project Summary](#project-summary)
* [Shopping List](#shopping-list)
* [Software Installation](#software-installation)
  * [Verifying the Software](#verifying-the-software)
* [Enclosure Designs](#enclosure-designs)
* [SeedQR Printable Templates](#seedqr-printable-templates)
* [Manual Installation Instructions](#manual-installation-instructions)


---------------

# Project Summary

The goal of LumenSigner is to enhance the security of users' Stellar accounts. To accomplish this goal, LumenSigner offers anyone the opportunity to build a verifiable air-gapped, stateless Stellar signing device using inexpensive, publicly available hardware components (usually < $50).

LumenSigner is built on top of SeedSigner, and we are grateful for the contributions made by SeedSigner contributors.

If you have specific questions about the project, our [Discord server](https://discord.gg/ZYjnz2fVYN) is a great place to ask them.

### Feature Highlights:
* Calculate word 12/24 of a BIP-39 seed phrase
* Create a 24-word BIP-39 seed phrase with 99 dice rolls
* Create a 24-word BIP-39 seed phrase by taking a digital photo
* Temporarily store up to 3 seed phrases while device is powered
* Guided interface to manually create a SeedQR for instant input [(demo video here)](https://youtu.be/c1-PqTNx1vc)
* BIP-39 passphrase / word 25 support
* Scan and parse transaction data from animated QR codes
* Review transaction information and sign it.
* Live preview during photo-to-seed and QR scanning UX
* Optimized seed word entry interface
* Responsive, event-driven user interface

---------------

# Shopping List

To build a LumenSigner, you will need:

* Raspberry Pi Zero (preferably version 1.3 with no WiFi/Bluetooth capability, but any Raspberry Pi 2/3/4 or Zero model will work, Raspberry Pi 1 devices will require a hardware modification to the Waveshare LCD Hat, as per the [instructions here](./docs/legacy_hardware.md))
* Waveshare 1.3" 240x240 pxl LCD (correct pixel count is important, more info at https://www.waveshare.com/wiki/1.3inch_LCD_HAT)
* Pi Zero-compatible camera (tested to work with the Aokin / AuviPal 5MP 1080p with OV5647 Sensor)

Notes:
* You will need to solder the 40 GPIO pins (20 pins per row) to the Raspberry Pi Zero board. If you don't want to solder, purchase "GPIO Hammer Headers" for a solderless experience.
* Other cameras with the above sensor module should work, but may not fit in the Orange Pill enclosure
* Choose the Waveshare screen carefully; make sure to purchase the model that has a resolution of 240x240 pixels

LumenSigner owes its existence to the hard work of SeedSigner contributors, you can support them by purchasing hardware [here](https://btc-hardware-solutions.square.site/).

---------------

# Software Installation

## A Special Note On Minimizing Trust
As is the nature of pre-packaged software downloads, downloading and using the prepared LumenSigner release images means implicitly placing trust in the individual preparing those images; in our project the release images are prepared and signed by the eponymous creator of the project, [@overcat](https://github.com/overcat) "the person". That individual is additionally the only person in possession of the PGP keys that are used to sign the release images.

However, one of the many advantages of the open source software model is that the need for this kind of trust can be negated by our users' ability to (1) review the project's source code and (2) assemble the operating image necessary to use the software themselves. From our project's inception, instructions to build a LumenSigner operating image (using precisely the same process that is used to create the prepared release images) have been made availabile. We have put a lot of thought and work into making these instructions easy to understand and follow, even for less technical users. These instructions can be found [here](docs/manual_installation.md).

## Downloading the Software

   
Download the current Version (0.1.0.dev0) software image that is compatible with your  Raspberry Pi Hardware. The Pi Zero 1.3 is the most common and recommended board.
| Board                 | Download Image Link/Name          |
| --------------------- | --------------------------------- |
|**[Raspberry Pi Zero 1.3](https://www.raspberrypi.com/products/raspberry-pi-zero/)**      |[`lumensigner_os.0.1.0.dev0.pi0.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi0.img)      |
|[Raspberry Pi Zero W](https://www.raspberrypi.com/products/raspberry-pi-zero-w/)    |[`lumensigner_os.0.1.0.dev0.pi0.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi0.img)      |
|[Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/)  |[`lumensigner_os.0.1.0.dev0.pi02w.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi02w.img)    |
|[Raspberry Pi 2 Model B](https://www.raspberrypi.com/products/raspberry-pi-2-model-b/) |[`lumensigner_os.0.1.0.dev0.pi2.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi2.img)      |
|[Raspberry Pi 3 Model B](https://www.raspberrypi.com/products/raspberry-pi-3-model-b/) |[`lumensigner_os.0.1.0.dev0.pi02w.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi02w.img)    |
|[Raspberry Pi 4 Model B](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) |[`lumensigner_os.0.1.0.dev0.pi4.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi4.img)      |
|[Raspberry Pi 400](https://www.raspberrypi.com/products/raspberry-pi-400-unit/) |[`lumensigner_os.0.1.0.dev0.pi4.img`](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.pi4.img)      |

Note: If you have physically removed the WiFi component from your board, you will still use the image file of the original(un-modified) hardware. (Our files are compiled/based on the *processor* architecture). Although it is better to spend a few minutes upfront to determine which specific Pi hardware/model you have, if you are still unsure which hardware you have, you can try using the pi0.img file. Making an incorrect choice here will not ruin your board, because this is software, not firmware. 

**also download** these 2 signature verification files to the same folder  
[The Plaintext manifest file](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.sha256)  
[The Signature of the manifest file](https://github.com/LumenSigner/lumensigner/releases/download/0.1.0.dev0/lumensigner_os.0.1.0.dev0.sha256.sig)

Once the files have all finished downloading, follow the steps below to verify the download before continuing on to write the software onto a MicroSD card. Next, insert the MicroSD into your assembled hardware and connect the USB power. Allow about 45 seconds for our logo to appear, and then you can begin using your LumenSigner! 

[Our previous software versions are available here](https://github.com/LumenSigner/lumensigner/releases). Choose a specific version and then expand the *Assets* sub-heading to display the .img file binary and also the 2 associated signature files. **Note:** The prior version files will have lower numbers than the scripts and examples provided in this document, but the naming format will be the same, so you can edit them as required for signature verification etc.   


## Verifying that the downloaded files are authentic (optional but highly recommended!)

You can quickly verify that the software you just downloaded is both authentic and unaltered, by following these instructions.
We assume you are running the commands from a computer where both [GPG](https://gnupg.org/download/index.html) and [shasum](https://command-not-found.com/shasum) are already installed, and that you also know [how to navigate on a terminal](https://terminalcheatsheet.com/guides/navigate-terminal). 


### Step 1. Verify that the signature (.sig) file is genuine:

Run GPG's *fetch-keys* command to import the LumenSigner projects public key from the popular online keyserver called *Keybase.io*, into your computer's *keychain*. 


```
gpg --fetch-keys https://keybase.io/overcat/pgp_keys.asc?fingerprint=a78bca78b9c468db2b6f8a1493323c9ec6769086
```
The result should confirm that 1 key was *either* imported or updated. *Ignore* any key ID's or email addresses shown.

![SS - Fetchkeys-Keybase PubKey import with Fingerprint shown (New import or update of the key)v3-100pct](./docs/img/fetch_gpg_key.png)  

Next, you will run the *verify* command on the signature (.sig) file. (*Verify* must be run from inside the same folder that you downloaded the files into earlier. The `*`'s in this command will auto-fill the version from your current folder, so it should be copied and pasted as-is.)   
```
gpg --verify lumensigner_os.0.1.0.dev0.sha256.sig
```

When the verify command completes successfully, it should display output like this:
<BR>
![SS - Verify Command - GPG on Linux - Masked_v4-100pct](./docs/img/verify_signature.png)  
The result must display "**Good signature**".  Ignore any email addresses - *only*  matching Key fingerprints count here. Stop immediately if it displays "*Bad signature*"!
<BR> 

On the *last* output line, look at your *rightmost* 16 characters (the 4 blocks of 4).  
**Crucially, we must now check WHO that Primary key fingerprint /ID belongs to.** We will start by looking at Keybase.io to see if it is the *LumenSigner project* 's public key or not.

<details><summary> About the warning message:</summary>
<p>  Since you are about to match the outputted fingerprint/ID against the proofs at keybase.io/overcat, and thereby confirm who the pubkey really belongs to-, you can safely ignore this warning message:

```
> WARNING: This key is not certified with a trusted signature!  
> There is no indication that the signature belongs to the owner.
 ```
</p>
</details>
<br>

<details><summary> More about how the verify command works:</summary>
<p>  
The verify command will attempt to decrypt the signature file (sha256.sig) by trying each public key already imported into your computer. If the public key we just imported (via fetch-keys), manages to: (a) successfully decrypt the .sig file , and (b), that result matches exactly to the clear-text equivalent (.sha256) of the .sig file, then its "a good signature"!   

Crucially, we must still manually check who *exactly* owns the Key ID which gave us that "Good signature". Thats what the warning message means- Who does the matching key really belong to? We will start by looking at keybase.io to see if it is "The LumenSigner project"'s public Key or not. 
Note that it is the file hashes of .sig and .sha256 that *verify* compares, not their raw contents.

</p>
</details>
<br>

Now to determine ***who*** the Public key ID belongs to: Goto [keybase.io/overcat](https://keybase.io/overcat)  
<BR>
![SS - Keybase Website PubKey visual matching1_Cropped-80pct](./docs/img/keybase.png)



**You must now *manually* compare: The 16 character fingerprint ID (as circled in red above) to, those *rightmost* 16 characters from your *verify* command.** 

**If they match exactly, then you have successfully confirmed that your .sig file is authentically from the LumenSigner Project!**
<BR>

<details><summary>Learn more about how keybase.io helps you check that someone (online) is who they say they are:</summary>
<p>
Keybase.io allows you to independently verify that the public key saved on Keybase.io, is both authentic and that it belongs to the organization it claims to represent.  
 Keybase has already checked the three pubkey file locations  cryptographically when they were saved there. You can further verify the key publications if you would like:  
 
 - *via Keybase*: By clicking on any of the three blue badges to see that the "proof" was published at that location. (The blue badge marked as tweet, is in the most human-readable form and it is also a bi-directional link on Twitter)     

Once you have used the above method, you will know if the Public Key stored on Keybase, is genuinely from the LumenSinger Project or not.
</p>
</details>
<br>

If the two ID's do *not* match, then you must stop here immediately. Do not continue. Contact us for assistance in the Telegram group address above.

<br>

### Step 2. Verifying that the *software images/binaries* are genuine

Now that you have confirmed that you do have the real LumenSigner Project's Public Key (ie the 16 characters match) - you can return to your terminal window. Running  the *shasum* command, is the final verification step and will confirm (via file hashing) that the software code/image files, were also not altered since publication, or even during your download process.  

 **On Linux or OSX:** Run this command
```
shasum -a 256 --ignore-missing --check lumensigner.0.1.*.sha256  
```

**On Windows (inside Powershell):** Run this command
```
CertUtil -hashfile gpg --verify lumensigner_os.0.1.0.dev0.Insert_Your_Pi_Models_binary_here_For_Example_pi02w.img SHA256 
```
On Windows, you must then manually compare the resulting file hash value to the corresponding hash value shown inside the .SHA256 cleartext file.
 <BR>

Wait up to 30 seconds for the command to complete, and it should display:
```
lumensigner_os.0.1.0.dev0.[Your_Pi_Model_For_Example:pi02w].img: OK
```
**If you receive the "OK" message** for your **lumensigner.0.1.x.[Your_Pi_Model_For_Example:pi02w].img file**, as shown above, then your verification is fully complete!  
**All of your downloaded files have now been confirmed as both authentic and unaltered!** You can proceed to create/write your MicroSD card😄😄 !!     

If your file result shows "FAILED", then you must stop here immediately. Do not continue. Contact us for assistance at  the Telegram group address above.

<BR>

Please recognize that this process can only validate the software to the extent that the entity that first published the key is an honest actor, and their private key is not compromised or somehow being used by a malicious actor.
<BR>
<BR>


## Writing the software onto your MicroSD card

To write the LumenSigner software onto your MicroSD card, there are a few options available:   
| Application              | Description                                                                                                                                                  | Platform and official Source                                                         |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Balena Etcher            | The application is called Etcher, and the company that wrote it is called Balena.  Hence *Etcher by Balena* or *Balena Etcher*                                                  | [Available for Windows, Mac and Linux](https://www.balena.io/etcher#download-etcher) |
| Raspberry Pi Imager      | Produced by the Raspberry Pi organization.                                                                                                                   | [Available for Windows, Mac and Linux](https://www.raspberrypi.com/software/)        |
| DD Command Line Utility  | Built-in to Linux and MacOS, the DD (Data Duplicator) is a tool for advanced users.  If not used carefully it can accidentally format the incorrect disk!   | Built-in to Linux and MacOS                                                        |

Be sure to download the software from the genuine publisher.  
Either of the Etcher or Pi Imager software is recommended.  Some users have reported a better experience with one or the other. So, if the one application doesn't work well for your particular machine, then please try the other one. 
<BR>
### **General Considerations:** 
The writing and verify steps are very quick from version 0.1.0 upwards, so please pay close attention to your screen. 
Make sure to set any write-protection physical slider on the MicroSD Card Adapter to UN-locked.  
You also don't need to pre-format the MicroSD beforehand.  You *dont* need to unzip any .zip file beforehand.
Current Etcher and Pi Imager software will perform a verify action (by default) to make sure the card was written successfully! Watching for that verify step to complete successfully, can save you a lot of headaches if you later need to troubleshoot issues where your LumenSigner device doesn't boot up at power on.   
Writing the MicroSd card is also known as flashing.  
It will overwrite everything on the MicroSD card.  
If the one application fails for you, then please try again using our other recommended application.  
Advanced users may want to try the Linux/MacOS *DD* command instead of using Etcher or Pi Imager, however, a reminder is given that DD can overwrite the wrong disk if you are not careful !
#### **Specific considerations for Windows users:**
Use the Pi imager software as your first choice on Windows. Windows can sometimes flag the writing of a MicroSD as risky behaviour and hence it may prevent this activity. If this happens, your writing/flashing will fail, hang or won't even begin, in which case you should to try to run the Etcher/Pi-Imager app "As administrator", (right-click and choose that option). It can also be blocked by windows security in some cases, so If you have the (non-default) *Controlled Folder Access* option set to active, try turning that *off* temporarily. 




---------------

# Enclosure Designs

### Open Pill

The Open Pill enclosure design is all about quick, simple and inexpensive deployment of a LumenSigner device. The design does not require any additional hardware and can be printed using a standard FDM 3D printer in about 2 hours, no supports necessary. A video demonstrating the assembly process can be found [here](https://youtu.be/gXPFJygZobEa). To access the design file and printable model, click [here](https://github.com/LumenSigner/lumensigner/tree/dev/enclosures/open_pill).

### Orange Pill

The Orange Pill enclosure design offers a more finished look that includes button covers and a joystick topper. You'll also need the following additional hardware to assemble it:

* 4 x F-F M2.5 spacers, 10mm length
* 4 x M2.5 pan head screws, 6mm length
* 4 x M2.5 pan head screws, 12mm length

The upper and lower portions of the enclosure can be printed using a standard FDM 3D printer, no supports necessary. The buttons and joystick nub should ideally be produced with a SLA/resin printer. An overview of the entire assembly process can be found [here](https://youtu.be/aIIc2DiZYcI). To access the design files and printable models, click [here](https://github.com/LumenSigner/lumensigner/tree/dev/enclosures/orange_pill).

### Community Designs

* [Lil Pill](https://cults3d.com/en/3d-model/gadget/lil-pill-seedsigner-case) by @_CyberNomad
* [OrangeSurf Case](https://github.com/orangesurf/orangesurf-seedsigner-case) by @OrangeSurfBTC
* [PS4 SeedSigner](https://www.thingiverse.com/thing:5363525) by @Silexperience
* [OpenPill Faceplate](https://www.printables.com/en/model/179924-seedsigner-open-pill-cover-plates-digital-cross-jo) by @Revetuzo 
* [Waveshare CoverPlate](https://cults3d.com/en/3d-model/various/seedsigner-coverplate-for-waveshare-1-3-inch-lcd-hat-with-240x240-pixel-display) by @Adathome1

---------------

# SeedQR Printable Templates
You can use LumenSigner to export your seed to a hand-transcribed SeedQR format that enables you to instantly load your seed back into LumenSigner.

[More information about SeedQRs](docs/seed_qr/README.md)

<table align="center">
    <tr><td><img src="docs/seed_qr/img/handmade_qr.jpg"></td></tr>
</table>

Standard SeedQR templates:
* [12-word SeedQR template dots (25x25)](docs/seed_qr/printable_templates/dots_25x25.pdf)
* [24-word SeedQR template dots (29x29)](docs/seed_qr/printable_templates/dots_29x29.pdf)
* [12-word SeedQR template grid (25x25)](docs/seed_qr/printable_templates/grid_25x25.pdf)
* [24-word SeedQR template grid (29x29)](docs/seed_qr/printable_templates/grid_29x29.pdf)
* [Baseball card template: 24-word SeedQR (29x29)](docs/seed_qr/printable_templates/trading_card_29x29_w24words.pdf)

CompactSeedQR templates:
* [12-word CompactSeedQR template dots (21x21)](docs/seed_qr/printable_templates/dots_21x21.pdf)
* [24-word CompactSeedQR template dots (25x25)](docs/seed_qr/printable_templates/dots_25x25.pdf)
* [12-word CompactSeedQR template grid (21x21)](docs/seed_qr/printable_templates/grid_21x21.pdf)
* [24-word CompactSeedQR template grid (25x25)](docs/seed_qr/printable_templates/grid_25x25.pdf)
* [Baseball card template: 12-word Compact SeedQR (21x21)](docs/seed_qr/printable_templates/trading_card_21x21_w12words.pdf)
* [Baseball card template: 24-word Compact SeedQR (25x25)](docs/seed_qr/printable_templates/trading_card_25x25_w24words.pdf)



2-sided SeedQR templates - 8 per sheet
Printing settings - (2-sided)("flip on long edge")("Actual Size")
If printing on cardstock, adjust your printer settings via its control panel

A4 templates(210mm * 297mm):
* [21x21 - stores 12-word seeds ONLY in CompactSeedQR format ONLY](docs/seed_qr/printable_templates/21x21_A4_trading_card_2sided.pdf)
* [25x25 - stores 12-word or 24 word seeds depending on SeedQR format](docs/seed_qr/printable_templates/25x25_A4_trading_card_2sided.pdf)
* [29x29 - stores 24-word seeds ONLY as plaintext SeedQR format ONLY](docs/seed_qr/printable_templates/29x29_A4_trading_card_2sided.pdf)

Letter templates(8.5in * 11in):
* [21x21 - stores 12-word seeds ONLY in CompactSeedQR format ONLY](docs/seed_qr/printable_templates/21x21_letter_trading_card_2sided.pdf)
* [25x25 - stores 12-word or 24 word seeds depending on format](docs/seed_qr/printable_templates/25x25_letter_trading_card_2sided.pdf)
* [29x29 - stores 24-word seeds ONLY as plaintext SeedQR format ONLY](docs/seed_qr/printable_templates/29x29_letter_trading_card_2sided.pdf)
---------------

# Manual Installation Instructions
see the docs: [Manual Installation Instructions](docs/manual_installation.md)
