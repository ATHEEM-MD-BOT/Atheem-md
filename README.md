

# ATHEEM MD BOT



> Powerful WhatsApp Multi-Device Bot built with **Baileys MD**.  

> Easy to use, fast, and packed with 300+ commands!



![Atheem Logo](_c9a1b1b2-752c-4ffb-a6c4-d1cd88861998.jpeg)


click here to get session id 
const { default: makeWASocket, useMultiFileAuthState } = require('@whiskeysockets/baileys');
const { Boom } = require('@hapi/boom');
const fs = require('fs');

async function connectBot() {
    const { state, saveCreds } = await useMultiFileAuthState('session');
    const sock = makeWASocket({
        auth: state,
        printQRInTerminal: false, // Hatutaki QR image, tutatumia base64 string
    });

    sock.ev.on('creds.update', saveCreds);

    sock.ev.on('connection.update', (update) => {
        const { connection, lastDisconnect, qr } = update;

        if (qr) {
            console.log('\nPAIRING CODE (Scan in WhatsApp):');
            console.log(qr); // Hii ni base64 string
        }

        if (connection === 'close') {
            const reason = new Boom(lastDisconnect?.error)?.output?.statusCode;
            if (reason === DisconnectReason.loggedOut) {
                console.log('Logged out. Deleting session...');
                fs.rmSync('session', { recursive: true, force: true });
                connectBot();
            } else {
                console.log('Connection closed. Reconnecting...');
                connectBot();
            }
        } else if (connection === 'open') {
            console.log('BOT CONNECTED SUCCESSFULLY!');
        }
    });
}

connectBot();
---




### 🚀 Deploy Now



[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/PJvpgT?referralCode=ATHEEMMD)  

[![Deploy on Koyeb](https://www.koyeb.com/static/images/deploy/button.svg)](https://app.koyeb.com/deploy?type=git&repository=github.com/ATHEEM-MD-BOT/Atheem-md)  

[![Deploy on Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)  

[![Deploy on Replit](https://replit.com/badge/github/ATHEEM-MD-BOT/Atheem-md)](https://replit.com/@ATHEEM-TECH/AtheemPairing)



---



### ✅ Pairing Your WhatsApp




### ⚙️ Features



- 300+ Powerful Commands

- Group Tools (antilink, welcome, admin)

- Downloader, AI Chat, Logo Maker

- Music & Video, Anime, Modding, Pranks

- Auto Typing, Auto Record, and more!



---



### 👑 Developer



**Owner:** [ATHEEM TECH](https://github.com/ATHEEM-MD-BOT)  

**WhatsApp:** [+255742233117](https://wa.me/255742233117)

"""



# Save the README as a .md file

readme_path = Path("/mnt/data/README_ATHEEM_MD_BOT.md")

readme_path.write_text(readme_content)



readme_path
