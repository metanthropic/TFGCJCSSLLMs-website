# Wibes Check — Web Intelligence Engine

![Wibes Check Banner](public/assets/landing-preview.png)

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-indigo.svg)](https://opensource.org/licenses/MIT)
[![Framework: Next.js](https://img.shields.io/badge/Framework-Next.js_15-black.svg?logo=next.js)](https://nextjs.org/)
[![Styling: Tailwind](https://img.shields.io/badge/Styling-Tailwind_CSS-38bdf8.svg?logo=tailwind-css)](https://tailwindcss.com/)
[![Deployed on Vercel](https://img.shields.io/badge/Deployment-Vercel-black.svg?logo=vercel)](https://vercel.com/)

**[Live Demo](https://wibescheck.ekjot.me)** · **[Report Bug](https://github.com/ekjotsinghmakhija/wibes-check/issues)** · **[Request Feature](https://github.com/ekjotsinghmakhija/wibes-check/issues)**

</div>

---

## ⚡️ Overview

**Wibes Check** is a developer-first OSINT (Open Source Intelligence) tool designed to instantly analyze any website's infrastructure. It aggregates data from over 30 distinct sources to provide a comprehensive security and performance report in seconds.

Unlike heavy enterprise tools, Wibes Check is built for speed and visual clarity. It runs entirely on **Next.js Edge Runtime** and Node.js serverless functions, performing real-time DNS resolution, SSL handshakes, and header analysis without requiring a heavy backend database.

## 📸 Intelligence Dashboard

![Dashboard Preview](public/assets/dashboard-preview.jpg)

## 🔮 Capabilities

Wibes Check is divided into four intelligence modules:

### 🛡️ Security Intelligence
* **SSL/TLS Analysis:** Detailed handshake inspection, certificate issuer, validity, and protocol versions.
* **Security Headers:** Checks for HSTS, CSP, X-Frame-Options, and other critical security policies.
* **Firewall Detection:** Identifies WAFs like Cloudflare, AWS CloudFront, Akamai, or Vercel Firewall.
* **Email Security:** Validates SPF and DMARC records to prevent email spoofing.
* **DNSSEC:** Verifies the existence of cryptographic signatures (DNSKEY/DS records).

### 🏗️ Infrastructure Recon
* **Tech Stack Detection:** Fingerprints server types (Express, Vercel), CMS (WordPress, Drupal), and frameworks (React, Next.js).
* **Geo-Location:** Pinpoints server physical location, ISP, and Autonomous System (AS) organization.
* **DNS Records:** Full resolution of A, AAAA, MX, TXT, and NS records.
* **Redirect Chains:** Traces HTTP redirect paths to detect loops or insecure hops.

### 🌍 SEO & Content
* **Global Rank:** Fetches domain authority and ranking via Open PageRank.
* **Bot Configuration:** Analyzes `robots.txt` rules and Sitemap availability.
* **Social Graph:** Previews how the site appears when shared on social media (OG Tags, Twitter Cards).
* **Archive History:** Retrieves historical snapshots from the Wayback Machine.

### 📊 Performance & Green Web
* **Carbon Footprint:** Estimates the CO2 emissions per page view based on data transfer size.
* **Server Status:** Checks uptime and response latency.

## 🛠️ Tech Stack

* **Framework:** [Next.js 15 (App Router)](https://nextjs.org/)
* **Language:** TypeScript
* **Styling:** Tailwind CSS (v4)
* **Animation:** Framer Motion
* **Data Fetching:** SWR
* **Icons:** Lucide React
* **Utilities:** `node:dns` (Native DNS), `cheerio` (HTML Parsing)

## 🚀 Getting Started

Follow these steps to run Wibes Check locally.

### Prerequisites
* Node.js 18+
* npm or pnpm

### Installation

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/ekjotsinghmakhija/wibes-check.git](https://github.com/ekjotsinghmakhija/wibes-check.git)
    cd wibes-check
    ```

2.  **Install dependencies**
    ```bash
    npm install
    ```

3.  **Configure Environment Variables**
    Create a `.env.local` file in the root directory:
    ```env
    # Optional: For Global Rank data (free key from OpenPageRank.com)
    OPEN_PAGERANK_KEY=your_api_key_here
    ```

4.  **Run the development server**
    ```bash
    npm run dev
    ```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## 📂 Project Structure

```bash
src/
├── app/
│   ├── api/              # Serverless functions (DNS, SSL, Whois, etc.)
│   ├── check/[domain]/   # Results dashboard page
│   └── opengraph-image.tsx # Dynamic OG image generator
├── components/
│   ├── homepage/         # Landing page components
│   ├── results/          # Data visualization cards (SSLCard, DnsCard...)
│   └── ui/               # Shared UI elements (Logo, SpotlightCard)
└── lib/                  # Utilities
```

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## ✍️ Author

**Ekjot Singh**

* Website: [ekjot.me](https://ekjot.me)
* GitHub: [@ekjotsinghmakhija](https://github.com/ekjotsinghmakhija)
* LinkedIn: [Ekjot Singh](https://www.linkedin.com/in/ekjot-singh-thefirst/)

---
<div align="center">
  <p>Built with ❤️  and Next.js</p>
</div>
