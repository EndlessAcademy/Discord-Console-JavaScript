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

# Easy Edit Mode
You can use this to make fake screenshots without having to use Inspect Element (CTRL + SHIFT + I) each time.

<details>
  <summary>Expand</summary>
  
  ```
  document.designMode = 'on'
  ```
</details>

# Spotify "Listen Along" Spoofer
Makes it possible to use the "Listen Along" feature without needing Spotify Premium.

<details>
  <summary>Expand</summary>
  
  ```
(webpackChunkdiscord_app.push([[''],{},e=>{m=[];for(let c in e.c)m.push(e.c[c])}]),m).find(m => m?.exports?.Z?.getAccounts).exports.Z.getAccounts().forEach((conn) => conn.type === "spotify" && (webpackChunkdiscord_app.push([[''],{},e=>{m=[];for(let c in e.c)m.push(e.c[c])}]),m).find(m => m?.exports?.Z?.isDispatching).exports.Z.dispatch({type: "SPOTIFY_PROFILE_UPDATE", accountId: conn.id, isPremium: true}))  
  ```
</details>

# Enter NSFW Channels
Grants access to channels marked as NSFW on an under-18 account.

**Only use this script if you are 18+! There is a reason those channels are marked as NSFW.**

<details>
  <summary>Expand</summary>
  
This script is intended for people (>18) whose accounts have been wrongfully marked as underage. Don't use it for other purposes.
  ```
  var findModule=(item)=>window.webpackChunkdiscord_app.push([[Math.random()],{},(req)=>{for(const m of Object.keys(req.c).map((x)=>req.c[x].exports).filter((x)=>x)){if(m.default&&m.default[item]!==undefined)return m.default}}])
findModule('getCurrentUser').getCurrentUser().nsfwAllowed = true
  ```

![No Access](https://github.com/user-attachments/assets/172def80-4310-42ae-94e8-9652568b345f)

 ![Can Access](https://github.com/user-attachments/assets/f7d00a7a-0ccc-4027-9b50-fac4c94e4ab9)
</details>

# Get Hidden Channel IDs
Displays the ID's of channels that you can't see without client modifications.

<details>
  <summary>Expand</summary>

  ```
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getPrivateChannelIds !== undefined) {return console.log(m.default.getPrivateChannelIds())}if (m.getPrivateChannelIds !== undefined) {return console.log(m.getPrivateChannelIds())}}}]);  
  ```

![Get Hidden Channel ID](https://github.com/user-attachments/assets/16101d91-a53d-4cef-936c-cc4a055716d7)
</details>

# Change Password
Changes the password of the account that is currently logged in.
**Only use this on your own account! Stealing accounts is a crime in most countries.**

<details>
  <summary>Expand</summary>

  ```
let oldpassword = "";
let newpassword = "";

window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getToken !== undefined) {fetch("https://discord.com/api/v9/users/@me", { "credentials": "include", "body": "{\"password\":\"" + oldpassword + "\",\"new_password\":\"" + newpassword + "\"}", "method": "PATCH", "headers": { "Authorization": m.default.getToken(), "Content-Type":"application/json" }}); return}if (m.getToken !== undefined) {fetch("https://discord.com/api/v9/users/@me", {"credentials": "include","body": "{\"password\":\"" + oldpassword + "\",\"new_password\":\"" + newpassword + "\"}","method":"PATCH","headers": {"Authorization": m.getToken(), "Content-Type":"application/json"}});return}}}]);
```
</details>

# Add Guild Features
Enables server features (like having a partnered / verified server, or some boost-only features) locally, meaning everything is purely visual.

<details>
  <summary>Expand</summary>
  
 ![Normal Community](https://github.com/user-attachments/assets/f218b17f-f3db-4aca-893a-ca59414c75c2)   ![Verified Community](https://github.com/user-attachments/assets/4709a3c5-85c9-4cb0-8fc0-10e4f6ec9585)   ![Partnered Community](https://github.com/user-attachments/assets/322d5ef8-c37a-418e-acde-88c3e9018cec)
 
  Valid features are `PARTNERED` and `VERIFIED`.

  ```
let serverid = "";
let feature = "";

window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getGuilds !== undefined) {return m.default.getGuild(serverid).features.add(feature)}if (m.getGuilds !== undefined) {return m.getGuild(serverid).features.add(feature)}}}]); 
  ```
</details>

# Delete Webhook
Deletes a webhook using it's webhook URL.
You could use this to delete the webhook of some scammers trying to token-grab you. :)

<details>
  <summary>Expand</summary>

  ```
let webhookURL = "PUT_WEBHOOK_URL_HERE";

await fetch(webhookURL, {
  "method": "DELETE",
});
  ```
</details>

# E-mail Address & Phone Number Verification Bypass
Bypasses e-mail address and phone number verification in servers. This does not let you send messages, but you can connect and talk in voice channels.

<details>
  <summary>Expand</summary>

  ```
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().phone = '+1234567890';}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().phone = '+1234567890'}}}]);
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().email = 'email@email.com';}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().email = 'email@email.com'}}}]);
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getCurrentUser !== undefined) {return m.default.getCurrentUser().verified = true;}if (m.getCurrentUser !== undefined) {return m.getCurrentUser().verified = true}}}]);
  ```
</details>

# Discord Activities
Adds the Activities button in the voice channel you're in.

<details>
  <summary>Expand</summary>

  ```
var AppIds = ["755600276941176913", "880218394199220334", "755827207812677713", "773336526917861400", "814288819477020702", "832012774040141894", "879864070101172255", "879863881349087252", "832012854282158180", "878067389634314250", "902271654783242291", "879863686565621790", "879863976006127627", "852509694341283871", "832013003968348200", "832025144389533716", "763133495793942528", "880218832743055411", "878067427668275241", "879864010126786570", "879864104980979792", "891001866073296967", "832012586023256104", "832012682520428625", "832013108234289153", "763116274876022855", "832012730599735326", "832012938398400562", "832025061657280566", "801133024841957428", "832012815819604009", "832012894068801636", "832025114077298718", "832025993019260929"]
window.webpackChunkdiscord_app.push([[Math.random()], {}, (req) => {for (const m of Object.keys(req.c).map((x) => req.c[x].exports).filter((x) => x)) {if (m.default && m.default.getEnabledAppIds !== undefined) {return m.default.getEnabledAppIds = () => AppIds}}}]);
  ```

![Activities](https://github.com/user-attachments/assets/d301123f-8a8e-4d26-96b2-44a847bfbbb9)
</details>

# Change Client Color
Changes your client's color to your liking.

<details>
  <summary>Expand</summary>

  ```
__SECRET_EMOTION__.injectGlobal(`
    * {
--background-primary: #000000;
    --background-secondary: #000000;
--background-secondary-alt: #070707ff;
--background-accent: #252525;
--background-floating: #242424ff;
    --scrollbar-thin-track: #000000;
    --channeltextarea-background: #151515;
    }
`)
  ```
</details>

# AMOLED Theme on Desktop & Web
Activates the AMOLED theme from mobile on desktop and web, which uses darker colors than the normal theme and is better on the eyes.

<details>
  <summary>Expand</summary>
  
  ```
document.body.classList.add("theme-amoled"); 
  ```
</details>


</footer>
