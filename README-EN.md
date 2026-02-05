<div align="center">

# Katelya-TGBed

> 🖼️ Free Image/File Hosting Solution, based on Cloudflare Pages and Telegram

**English** | [中文](README.md)

<br>

![GitHub stars](https://img.shields.io/github/stars/katelya77/Katelya-TGBed?style=flat-square)
![GitHub forks](https://img.shields.io/github/forks/katelya77/Katelya-TGBed?style=flat-square)
![GitHub license](https://img.shields.io/github/license/katelya77/Katelya-TGBed?style=flat-square)

[![Deploy to Cloudflare Pages](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/katelya77/Katelya-TGBed)

</div>

---

## 📸 Screenshots

<table>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/bfdd1fa0-e3e8-44d7-8379-f54a3d6a048b" alt="Upload Page" style="width:100%">
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/20c8dad5-cf7b-4e65-a662-ccc21deef03a" alt="Gallery View" style="width:100%">
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/4c3e32b0-1acd-4152-a51f-d9d44d27a2a9" alt="Admin Dashboard" style="width:100%">
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/0da27a87-111c-429b-8071-b11d3202bca2" alt="File Details" style="width:100%">
    </td>
  </tr>
</table>

## ✨ Features

- 📦 **Unlimited Storage** - Upload an unlimited number of images and files.
- 💰 **Completely Free** - Hosted on Cloudflare, zero cost within free tier limits.
- 🌐 **Free Domain** - Uses `*.pages.dev` subdomain, supports custom domains.
- 🔒 **Content Moderation** - Optional image moderation API to automatically block inappropriate content.
- 📁 **Multi-format Support** - Supports images, videos, audio, documents, archives, etc.
- 👁️ **Online Preview** - Supports previewing images, videos, audio, and documents (pdf, docx, txt).
- 🚀 **Multipart Upload** - Supports files up to 100MB (requires R2).
- 🎨 **Multiple Views** - Grid, list, and waterfall layout management interfaces.
- 🗂️ **Storage Classification** - Visually distinguish between Telegram and R2 stored files.

---

## 🚀 Quick Deployment

### Prerequisites

- Cloudflare Account
- Telegram Account

### Step 1: Get Telegram Credentials

1. **Get Bot Token**
   - Send `/newbot` to [@BotFather](https://t.me/BotFather).
   - Follow the prompts to create a bot and get the `BOT_TOKEN`.

2. **Create Channel & Add Bot**
   - Create a new Telegram Channel.
   - Add your bot to the channel as an **Administrator**.

3. **Get Chat ID**
   - Send a message to [@VersaToolsBot](https://t.me/VersaToolsBot) or [@GetTheirIDBot](https://t.me/GetTheirIDBot) to get your Channel ID.

### Step 2: Deploy to Cloudflare

1. **Fork this Repository**

2. **Create Pages Project**
   - Log in to [Cloudflare Dashboard](https://dash.cloudflare.com).
   - Go to `Workers & Pages` → `Create Application` → `Pages` → `Connect to Git`.
   - Select the forked repository and click **Begin setup**.

3. **Configure Environment Variables**
   - Go to Project `Settings` → `Environment variables`.
   - Add the required variables:

| Variable Name | Description | Required |
| :--- | :--- | :---: |
| `TG_Bot_Token` | Telegram Bot Token | ✅ |
| `TG_Chat_ID` | Telegram Channel ID | ✅ |
| `BASIC_USER` | Admin Username | Optional |
| `BASIC_PASS` | Admin Password | Optional |

**Redeploy** - You must redeploy the project after adding environment variables for them to take effect.

---

## 📦 Storage Configuration

### KV Storage (Image Management)

To enable the gallery and management features, you must configure KV:

1. Cloudflare Dashboard → `Workers & Pages` → `KV`.
2. Click `Create a Namespace`, name it `katelya-tgbed`.
3. Go to Pages Project → `Settings` → `Functions` → `KV namespace bindings`.
4. Add binding: Variable name `img_url`, select the namespace you created.
5. Redeploy the project.

### R2 Storage (Large File Support, Optional)

Configure R2 to support file uploads up to 100MB:

1. **Create Bucket
