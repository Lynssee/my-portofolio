# Deployment Guide

## Deploy ke GitHub Pages dengan Custom Domain menggunakan Cloudflare Tunnel

### Prerequisites
1. GitHub Account
2. Cloudflare Account
3. Domain yang sudah terdaftar di Cloudflare

---

## 1. Setup GitHub Repository

### Push ke GitHub:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/REPO-NAME.git
git push -u origin main
```

### Enable GitHub Pages:
1. Buka Repository Settings
2. Pilih **Pages** di sidebar
3. Source: **GitHub Actions**
4. Simpan

---

## 2. Build Project Locally

```bash
# Install dependencies
npm install

# Build project
npm run build

# Preview build (optional)
npm run preview
```

Output akan ada di folder `build/`

---

## 3. Deploy ke GitHub Pages

### Otomatis via GitHub Actions:
Setiap push ke branch `main` akan otomatis trigger deployment.

```bash
git add .
git commit -m "Update website"
git push
```

### Manual Deploy:
```bash
npm run deploy
```

---

## 4. Setup Cloudflare Tunnel untuk Custom Domain

### Install Cloudflared:

**Windows:**
```powershell
# Download cloudflared
winget install --id Cloudflare.cloudflare
```

**Linux/Mac:**
```bash
# Download cloudflared
curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -o cloudflared
chmod +x cloudflared
sudo mv cloudflared /usr/local/bin/
```

### Login ke Cloudflare:
```bash
cloudflared tunnel login
```

### Buat Tunnel:
```bash
# Ganti 'my-website-tunnel' dengan nama tunnel Anda
cloudflared tunnel create my-website-tunnel
```

### Dapatkan Tunnel ID:
```bash
cloudflared tunnel list
```
Copy **Tunnel ID** yang muncul.

---

## 5. Konfigurasi Tunnel

Buat file `config.yml` di:
- **Windows:** `C:\Users\YOUR_USERNAME\.cloudflared\config.yml`
- **Linux/Mac:** `~/.cloudflared/config.yml`

```yaml
tunnel: YOUR_TUNNEL_ID
credentials-file: C:\Users\YOUR_USERNAME\.cloudflared\YOUR_TUNNEL_ID.json

ingress:
  - hostname: yourdomain.com
    service: https://yourusername.github.io/your-repo-name
  - hostname: www.yourdomain.com
    service: https://yourusername.github.io/your-repo-name
  - service: http_status:404
```

**Ganti:**
- `YOUR_TUNNEL_ID` dengan Tunnel ID dari step sebelumnya
- `yourdomain.com` dengan domain Anda
- `yourusername.github.io/your-repo-name` dengan URL GitHub Pages Anda

---

## 6. Setup DNS di Cloudflare

### Via Command Line:
```bash
# Root domain
cloudflared tunnel route dns my-website-tunnel yourdomain.com

# WWW subdomain
cloudflared tunnel route dns my-website-tunnel www.yourdomain.com
```

### Via Cloudflare Dashboard:
1. Login ke [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Pilih domain Anda
3. Buka **DNS** → **Records**
4. Tambahkan CNAME records:
   - **Name:** `@` atau `yourdomain.com`
   - **Target:** `YOUR_TUNNEL_ID.cfargotunnel.com`
   - **Proxy status:** Proxied (Orange cloud)
   - Save

   - **Name:** `www`
   - **Target:** `YOUR_TUNNEL_ID.cfargotunnel.com`
   - **Proxy status:** Proxied (Orange cloud)
   - Save

---

## 7. Jalankan Tunnel

### Test Tunnel:
```bash
cloudflared tunnel run my-website-tunnel
```

### Jalankan sebagai Service (Windows):
```powershell
cloudflared service install
cloudflared service start
```

### Jalankan sebagai Service (Linux/Mac):
```bash
sudo cloudflared service install
sudo systemctl start cloudflared
sudo systemctl enable cloudflared
```

---

## 8. Verifikasi Deployment

1. Buka browser dan akses:
   - `https://yourdomain.com`
   - `https://www.yourdomain.com`
   - `https://yourusername.github.io/your-repo-name`

2. Pastikan semua URL menampilkan website Anda dengan benar

---

## Troubleshooting

### Build Error:
```bash
# Clear cache dan reinstall
rm -rf node_modules package-lock.json
npm install
npm run build
```

### Tunnel tidak jalan:
```bash
# Check tunnel status
cloudflared tunnel info my-website-tunnel

# Check logs
cloudflared tunnel run my-website-tunnel --loglevel debug
```

### DNS tidak resolve:
- Tunggu 5-10 menit untuk DNS propagation
- Clear browser cache
- Check di [DNS Checker](https://dnschecker.org)

---

## Update Website

Setiap kali ada perubahan:

```bash
# Commit changes
git add .
git commit -m "Update content"
git push

# GitHub Actions akan otomatis build dan deploy
# Cloudflare Tunnel akan otomatis serve versi terbaru
```

---

## Commands Cheat Sheet

```bash
# Development
npm run dev              # Start dev server
npm run build            # Build for production
npm run preview          # Preview production build

# Deployment
git push                 # Auto deploy via GitHub Actions
npm run deploy           # Manual deploy to GitHub Pages

# Cloudflare Tunnel
cloudflared tunnel list                    # List all tunnels
cloudflared tunnel info my-website-tunnel  # Get tunnel info
cloudflared tunnel run my-website-tunnel   # Run tunnel
cloudflared service start                  # Start tunnel service
cloudflared service stop                   # Stop tunnel service
```

---

## Resources

- [SvelteKit Documentation](https://kit.svelte.dev/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Cloudflare Tunnel Documentation](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)

