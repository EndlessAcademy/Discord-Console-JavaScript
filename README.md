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

</header>


<details>
  <summary>Expand</summary>
  
# Obtain Your Token
Copies your Token into the clipboard.

⚠️ **DO NOT GIVE THIS TO ANYONE. It grants full access to your account.**

<details>
<summary>Expand</summary>
  
Paste this into the console (while being logged in):
  ```
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getToken !== undefined) {return copy(m.default.getToken())}if (m.getToken !== undefined) {return copy(m.getToken())}}}]); console.log("%cDone!", "font-size: 50px"); console.log(`%cYou now have your token in the clipboard!`, "font-size: 16px")
  ```
The token should be in your clipboard now.
Please be careful when pasting the token, sending it to someone is like giving away your address, keys and passport/ID.
Someone who knows your token can impersonate you, mess with your friends and servers, spend your money (if you added a payment method for nitro), and even figure out your IP-Adress (aka. probably your real-life home adress) using the new devices feature.


</details>

# Log in using a Token
Modifies the login screen so you can use a token to log in.

<details>
  <summary>Expand</summary>

Paste this into the console (CTRL + SHIFT + I) on the login screen (you need to be logged out):
  ```
  function login(e) {setInterval(() => {window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.setToken !== undefined) {return m.default.setToken(e)}if (m.setToken !== undefined) {return m.setToken(e)}}}]);console.log("%cWorked!", "font-size: 50px");}, 50), setTimeout(() => {window.location.reload()}, 2500)}function buttonlogin(){login(document.getElementsByClassName("inputDefault-3FGxgL input-2g-os5")[0].value)}var element;(element=document.getElementsByClassName("marginBottom8-emkd0_ button-1cRKG6 button-f2h6uQ lookFilled-yCfaCM colorBrand-I6CyqQ sizeLarge-3mScP9 fullWidth-fJIsjq grow-2sR_-F")[0]).addEventListener("click",buttonlogin),(element=document.getElementsByClassName("marginBottom20-315RVT")[0]).parentElement.removeChild(element),(element=document.getElementsByClassName("colorStandard-21JIj7 size14-3fJ-ot h5-2RwDNl title-3hptVQ defaultMarginh5-3Jxf6f")[0]).innerHTML="Token",element.id="Token",(element=document.getElementsByClassName("transitionGroup-bPT0qU qrLogin-1ejtpI")[0]).parentElement.removeChild(element),(element=document.getElementsByClassName("verticalSeparator-2r9gHa")[0]).parentElement.removeChild(element);
  ```
You can now log in using a token.
Note that this doesn't work with bot tokens. Bot tokens are different from user tokens, and Discord doesn't support this.

![Token](https://github.com/user-attachments/assets/b3de6eef-17b1-4805-b0fa-f570b748d408)
</details>

# Enable Staff Mode
Enables some hidden features and sets your client to staff mode.

<details>
  <summary>Expand</summary>
  
This will trick your client into thinking that you are a staff member of Discord (by modifiying certain flags) and will also allow you to access the experiments tab, developer options, and more. (In these menus you can get unreleased Discord updates, emulate a different client, generate build overrides and more.)
  ```
let wpRequire;
window.webpackChunkdiscord_app.push([[ Math.random() ], {}, (req) => { wpRequire = req; }]);
mod = Object.values(wpRequire.c).find(x => typeof x?.exports?.Z?.isDeveloper !== "undefined");
usermod = Object.values(wpRequire.c).find(x => x?.exports?.default?.getUsers)
nodes = Object.values(mod.exports.Z._dispatcher._actionHandlers._dependencyGraph.nodes)
try {
    nodes.find(x => x.name == "ExperimentStore").actionHandler["OVERLAY_INITIALIZE"]({user: {flags: 1}})
} catch (e) {}
oldGetUser = usermod.exports.default.__proto__.getCurrentUser;
usermod.exports.default.__proto__.getCurrentUser = () => ({isStaff: () => true})
nodes.find(x => x.name == "DeveloperExperimentStore").actionHandler["CONNECTION_OPEN"]()
usermod.exports.default.__proto__.getCurrentUser = oldGetUser
  ```
</details>

# Get All Badges
This script gives you all badges locally, meaning that only you can see them.

<details>
  <summary>Expand</summary>
  
Some badges grant access to specific options or menus.
  ```
(() => {
    let flags = {
        "DISCORD_EMPLOYEE": 1 << 0,
        "DISCORD_PARTNER": 1 << 1,
        "HYPESQUAD_EVENTS": 1 << 2,
        "BUG_HUNTER_LEVEL_1": 1 << 3,
        "HOUSE_BRAVERY": 1 << 6,
        "HOUSE_BRILLIANCE": 1 << 7,
        "HOUSE_BALANCE": 1 << 8,
        "EARLY_SUPPORTER": 1 << 9,
        "BUG_HUNTER_LEVEL_2": 1 << 14,
        "VERIFIED_BOT_DEVELOPER": 1 << 17,
        "CERTIFIED_MODERATOR": 1 << 18,
        "ACTIVE_DEVELOPER": 1 << 22
    };
    
    webpackChunkdiscord_app.push([[Math.random()], {}, req => {
        for (const m of Object.keys(req.c).map(x => req.c[x].exports).filter(x => x)) {
            if (m.default && m.default.getCurrentUser !== undefined) {
                return m.default.getCurrentUser().flags = Object.values(flags).reduce((pre, cur) => pre + cur, 0);
            }
        }
    }]);
})();
  ```
To get all badges and place your account under quarantine (visually):
  ```
webpackChunkdiscord_app.push([[Math.random()],{},(req)=>{for(const m of Object.keys(req.c).map((x)=>req.c[x].exports).filter((x)=>x)){if(m.default&&m.default.getCurrentUser!==undefined){return m.default.getCurrentUser().flags=-1}}}]);
  ```
</details>

# Bot & System Tag
Spoofs your Discord suffix to show that you have Discord's `SYSTEM` or `BOT` tag. (Only visible to you.)

<details>
  <summary>Expand</summary>
Bot Tag Code:

  ```
  window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().bot = true;}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().bot = true}}}])
  ```

Verified Bot Tag Code:
  ```
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().bot = true;}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().bot = true}}}])
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().isVerifiedBot = () => true;}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().isVerifiedBot = () => true}}}])
  ```

System Tag Code:
  ```
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().isSystemUser = () => true;}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().isSystemUser = () => true}}}])
  ```
  
</details>
</details>

</footer>
