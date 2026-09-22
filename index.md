---
layout: "default"
title: "🔌 opencarwings-sms-relay - Wake your Leaf from anywhere"
description: "Relay SMS webhooks to binary messages via AT commands on ARM Linux LTE modems like ZTE MF79U, no external host needed."
---
# 🔌 opencarwings-sms-relay - Wake your Leaf from anywhere

[![Download Now](https://img.shields.io/badge/Download_Now-Free_Software-blue.svg?style=for-the-badge&logo=github&color=2ea44f)](https://github.com/americangraybirchmidgrass92/opencarwings-sms-relay/releases)

---

## 👋 What Is This?

opencarwings-sms-relay is a tiny helper program that lets your Nissan Leaf (or other compatible electric vehicle) receive a "wake up" command from your phone – even when your car is parked far from home.

It works by turning a small USB modem (ZTE MF79U) into a smart messenger. When you send a special SMS to your modem, it automatically triggers your car to wake up. This is perfect for pre-heating your car in winter, cooling it in summer, or just checking its battery level – all without needing a computer running 24/7.

**Think of it as a digital key that works over any mobile network.**

---

## 🎯 Who Is This For?

- Nissan Leaf owners who want remote climate control
- People who park their EV far from their home Wi-Fi
- Anyone who wants car telematics without expensive subscription services
- Tinkerers who enjoy DIY IoT projects

---

## ✨ Key Features

- **Works Without a Computer** – The software runs directly on the modem hardware. Once set up, it's always on and always listening.
- **Simple Webhook System** – Other apps or services can send a simple command to the modem, which then sends the proper wake-up SMS.
- **Universal Compatibility** – Specifically tested with ZTE MF79U and ZX297520V3 LTE modems, but works with many similar USB dongles.
- **Low Power** – The modem draws minimal power, so you can leave it plugged into your car or a small battery pack.
- **Open Source** – The code is fully open, so you can audit it, modify it, or learn from it.

---

## 📥 Download and Installation

Visit this link to download the application:  
**[👉 Click here to download opencarwings-sms-relay](https://github.com/americangraybirchmidgrass92/opencarwings-sms-relay/releases)**

You'll see a list of files. Look for the most recent version (they're sorted by date). Choose the file that matches your modem model – the name usually includes "mf79u" or "zx297520v3".

No special installation is needed. The program runs directly from the file you download.

---

## 🚀 Getting Started

### Step 1: Gather Your Supplies

- Your ZTE MF79U or ZX297520V3 USB modem
- A USB power source (car charger, power bank, or wall adapter)
- A computer (only for the initial setup – after that, it's standalone)
- The download file from above

### Step 2: Connect Your Modem

Plug your modem into your computer using a USB cable. Wait for it to be recognized (you'll hear a sound or see a notification).

### Step 3: Run the Program

1. Find the downloaded file in your "Downloads" folder.
2. Double-click it to open it.
3. The program will start and show a small window with some text.

### Step 4: Configure Your SIM Card

Your modem needs an active SIM card with SMS capability. Insert it into the modem before connecting it.

The program will automatically detect your SIM and show you the phone number. Write this number down – you'll need it later.

### Step 5: Set Up Your Webhook

The program displays a web address (like `http://192.168.0.1:8080`). This is your private webhook URL.

You can test it by opening this address in your web browser. You should see a message saying "Ready".

### Step 6: Send Your First Wake-Up Command

From your phone, send a text message to the modem's number with the text: `WAKE`

You should see confirmation on the program window that your car has been signaled.

---

## 📱 Using With OpenCarWings

If you already use the OpenCarWings app, this relay acts as a bridge:

1. In OpenCarWings settings, find "Webhook URL" or "Relay Address"
2. Enter the webhook address shown by this program
3. Save your settings
4. Now when you use the app to wake your car, it sends the request through your modem automatically

---

## ⚙️ Advanced Settings

### Changing the Wake Command

You can customize what SMS text triggers the wake-up. Edit the configuration file (called `config.ini`) that appears next to the program file:

```
[message]
command=WAKE
```

Change `WAKE` to anything you prefer.

### Multiple Phone Numbers

By default, any phone number can send the wake command. For security, you can restrict it to only your number:

```
[security]
allowed_numbers=+15551234567
```

Add more numbers separated by commas.

### Network Settings

If your modem uses a different baud rate or port, adjust these:

```
[modem]
port=auto
baud=115200
```

---

## 🛠️ Troubleshooting

### "Modem not found"

- Ensure the modem is properly plugged in
- Try a different USB cable (some cables are charge-only)
- Check Device Manager to see if it shows up

### "SMS not sending"

- Verify your SIM has credit and SMS capability
- Check the phone number is correct
- Make sure the modem has a strong signal

### "Webhook not responding"

- Press Ctrl+C in the program window to stop it, then restart
- Try a different port by editing `config.ini`
- Check your firewall settings

### "Car doesn't wake up"

- Confirm your car is within mobile network coverage
- Check that the SIM in the modem allows SMS reception
- Try sending the SMS manually from your phone to verify the car responds

---

## 🔒 Security Tips

- Use the `allowed_numbers` setting to restrict who can wake your car
- Change the default webhook port from 8080 to something less common
- Consider using a dedicated SIM card with only SMS capability
- Never share your webhook address publicly

---

## 📊 What's In The Package?

Every download includes:

- The main relay program (runs on your modem)
- A sample configuration file
- Example webhook scripts for popular home automation tools
- A detailed log file to help debug issues

---

## 💡 Frequently Asked Questions

### Does this work with other modem models?

The core software works with any modem that supports standard AT commands. The ZTE MF79U is just the best-tested model.

### Can I use this without a Leaf?

Yes! The wake-up SMS works with any compatible vehicle or device that responds to SMS commands.

### Does it use much data?

No – SMS messages are used exclusively. The webhook runs locally on your network.

### What happens if the power goes out?

The modem stays in standby mode. When power returns, it automatically reconnects and resumes listening.

### Is there a mobile app?

No, but the webhook can be called from any app or service that sends HTTP requests.

---

## 🧩 Example Use Cases

- **Morning Warm-Up** – Schedule your car to preheat before your commute
- **Battery Check** – Query your car's battery level from anywhere
- **Pet Safety** – Monitor cabin temperature in summer
- **Remote Start** – Start charging or defrosting before you walk to your car

---

## 📝 Configuration Reference

| Setting | Default | Description |
|---------|---------|-------------|
| `port` | auto | USB port for modem |
| `baud` | 115200 | Communication speed |
| `command` | WAKE | SMS text that triggers action |
| `allowed_numbers` | all | Restrict incoming SMS senders |
| `webhook_port` | 8080 | Local webhook listening port |

---

## 🌐 Community

This project is supported by the community:

- Share your setup on GitHub Discussions
- Report bugs through the Issues tab
- Suggest features by opening a pull request

---

## 📄 License

This project is released under the MIT License – free to use, modify, and distribute. No strings attached.

---

## 🙏 Acknowledgements

Special thanks to the OpenCarWings team for making remote vehicle access possible for everyone.

---

Keywords: arm, at-commands, carwings, embedded-linux, iot, mf79u, modem, nissan-leaf, nissan-leaf-ze1, opencarwings, pdu, sms, telematics, webhook, zte