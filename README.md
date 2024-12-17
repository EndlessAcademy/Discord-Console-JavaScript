<header>

<!--
  <<< Author notes: Course header >>>
  Include a 1280×640 image, course title in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Add your open source license, GitHub uses MIT license.
-->

# Discord Console

⚠️ **Note**: I'm not affiliated with Discord and do not encourage using any of these scripts. Use everything here at your own risk. This is meant for **educational purposes** only and using these codeblocks may result in your account being disabled/terminated.

# Inner workings of Discord

**Disclaimer**: The information provided in this section is obtained through reverse engineering and NOT verified for it's accuracy. Therefore it might be outdated as well.

# Console

As stated in my disclaimer, I don't promote using any kind of client modifications. Please don't use the code found here for illegal / hacking purposes, or you might risk seeing this error message:

![Ban Message](https://github.com/user-attachments/assets/cb423923-9a16-4fe0-b5b2-dc566924e006)
</header>


<details>
  <summary>Expand</summary>
  
# How to use these Javascript
It only works on web and desktop versions (Windows, Linux, MacOS), not on mobile.

1. Press CTRL + SHIFT + I to toggle Developer Tools (Discord is based on Electron, which is basically Google Chrome)
2. Click on "Console" if not already selected
3. Paste the script in the command field
4. Press enter
  
# Obtain Your Token
Copies your Token into the clipboard.

⚠️ **DO NOT GIVE THIS TO ANYONE. It grants full access to your account.**

<details>
<summary>Expand</summary>
  
Paste this into the console (while being logged in):
  ```js
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getToken !== undefined) {return copy(m.default.getToken())}if (m.getToken !== undefined) {return copy(m.getToken())}}}]); console.log("%cDone!", "font-size: 50px"); console.log(`%cYou now have your token in the clipboard!`, "font-size: 16px")
  ```
The token should be in your clipboard now.
Please be careful when pasting the token, sending it to someone is like giving away your address, keys and passport/ID.
Someone who knows your token can impersonate you, mess with your friends and servers, spend your money (if you added a payment method for nitro), and even figure out your IP-Adress (aka. probably your real-life home adress) using the new devices feature.


</details>
</footer>
