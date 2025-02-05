# 🚀 Scraping Browser by Bright Data  
*A fully automated headless browser solution for dynamic web scraping with Puppeteer, Selenium, and Playwright. The Scraping Browser is opened as a GUI on Bright Data's Infrastructure.*  

[![Promo](https://github.com/luminati-io/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.com/products/scraping-browser) 

🔗 **[Get Started for Free](https://brightdata.com/products/scraping-browser)** | 📖 **[Official Documentation](https://docs.brightdata.com/scraping-automation/scraping-browser/introduction)**  

---

## 🔹 Overview  
Scraping Browser is a fully-hosted **browser-based scraping solution** that automates **multi-step data collection** with **built-in proxy management**, **CAPTCHA solving**, and **advanced website unblocking**. It supports **Puppeteer, Playwright, and Selenium**, enabling effortless web automation at an **unlimited scale**.  

## ✅ Why Use Scraping Browser?  
- **No Infrastructure Overhead** – Run and scale browser sessions via API without maintaining browser infrastructure.  
- **Built-in Unlocking** – Auto-handles **CAPTCHAs, fingerprinting, retries, and JS rendering** under the hood.  
- **Multi-Step Navigation** – Automate clicks, scrolling, form submissions, and hover interactions.  
- **Unlimited Scaling** – Launch **thousands of concurrent browser sessions** without rate limits.  
- **Global Geo-Access** – Unlock localized content with [**72M+ residential IPs across 195 countries**](https://brightdata.com/proxy-types/residential-proxies).  
- **Seamless Debugging** – Monitor sessions in real-time with **Chrome DevTools integration**.  

---

## 🚀 Getting Started  

### 📌 Install Dependencies  
Ensure you have **Node.js**, **Python**, or **C#** installed along with your preferred web automation library:  

```sh
# Install Puppeteer
npm install puppeteer-core

# Install Playwright
npm install playwright

# Install Selenium
pip install selenium
```

## 🔧 Usage Examples

### 1️⃣ Puppeteer Example (JavaScript)

```js
const puppeteer = require('puppeteer-core');

const SBR_WS_ENDPOINT = 'wss://brd-customer-<YOUR-USERNAME>-zone-<YOUR-ZONE-NAME>:<YOUR-PASSWORD>@brd.superproxy.io:9222';

async function main() {
    console.log('Connecting to Scraping Browser...');
    const browser = await puppeteer.connect({ browserWSEndpoint: SBR_WS_ENDPOINT });
    try {
        const page = await browser.newPage();
        console.log('Connected! Navigating to example.com...');
        await page.goto('https://example.com');
        console.log('Scraping page content...');
        const html = await page.content();
        console.log(html);
    } finally {
        await browser.close();
    }
}

main().catch(err => console.error(err.stack || err));
```

> **💡 Learn more about [web scraping with Puppeteer](https://brightdata.com/blog/how-tos/web-scraping-puppeteer)**

### 2️⃣ Playwright Example (Python)

```python
import asyncio
from playwright.async_api import async_playwright

SBR_WS_CDP = 'wss://brd-customer-<YOUR-USERNAME>-zone-<YOUR-ZONE-NAME>:<YOUR-PASSWORD>@brd.superproxy.io:9222'

async def run(pw):
    print('Connecting to Scraping Browser...')
    browser = await pw.chromium.connect_over_cdp(SBR_WS_CDP)
    try:
        page = await browser.new_page()
        print('Connected! Navigating to example.com...')
        await page.goto('https://example.com')
        print('Scraping page content...')
        html = await page.content()
        print(html)
    finally:
        await browser.close()

async def main():
    async with async_playwright() as playwright:
        await run(playwright)

if __name__ == '__main__':
    asyncio.run(main())
```

> **💡 Learn more about [web scraping with Playwright](https://brightdata.com/blog/how-tos/playwright-web-scraping)**

### 3️⃣ Selenium Example (JavaScript)

```js
const { Builder, Browser } = require('selenium-webdriver');

const SBR_WEBDRIVER = 'https://brd-customer-<YOUR-USERNAME>-zone-<YOUR-ZONE-NAME>:<YOUR-PASSWORD>@brd.superproxy.io:9515';

async function main() {
    console.log('Connecting to Scraping Browser...');
    const driver = await new Builder().forBrowser(Browser.CHROME).usingServer(SBR_WEBDRIVER).build();
    try {
        console.log('Connected! Navigating to example.com...');
        await driver.get('https://example.com');
        console.log('Scraping page content...');
        const html = await driver.getPageSource();
        console.log(html);
    } finally {
        driver.quit();
    }
}

main().catch(err => console.error(err.stack || err));
```

> **💡 Learn more about [web scraping with Selenium](https://brightdata.com/blog/how-tos/using-selenium-for-web-scraping)**

## 🔥 Advanced Features

### 🛠️ Debugging with Chrome DevTools

Monitor browser sessions in real-time:

```js
const { exec } = require('child_process');

const chromeExecutable = 'google-chrome';
const openDevtools = async (page, client) => {
    const frameId = page.mainFrame()._id;
    const { url: inspectUrl } = await client.send('Page.inspect', { frameId });
    exec(`"${chromeExecutable}" "${inspectUrl}"`, error => {
        if (error) throw new Error('Unable to open devtools: ' + error);
    });
};
```

### 🧩 CAPTCHA Solving

```js
const client = await page.target().createCDPSession();
const { status } = await client.send('Captcha.solve', { detectTimeout: 30000 }); # change the time according to your needs
console.log(`CAPTCHA solve status: ${status}`);
```

> 🤖 Check out our [CAPTCHA Solver](https://github.com/luminati-io/Captcha-solver).

## 🔄 Automatic IP Rotation & Unlocking  
Scraping Browser automatically rotates IPs thanks to the integrated [rotating proxies](https://brightdata.com/solutions/rotating-proxies) and handles retries for seamless data collection. 

## 💰 Pricing  

### 💳 Flexible Plans  
- **Pay-As-You-Go:** $8.40/GB – No commitment.  
- **Growth Plan:** $7.14/GB – Ideal for teams.  
- **Business Plan:** $6.30/GB – For scaling operations.  
- **Enterprise:** Custom pricing for high-volume needs.  

📌 **Sign up now and get your first deposit matched up to $500!**  

[💰 View Pricing](https://brightdata.com/pricing/scraping-browser)  

## ❓ Frequently Asked Questions  

### 🤔 What makes Scraping Browser different from a standard headless browser?  
Scraping Browser is a fully managed, GUI-based browser that runs on Bright Data's infrastructure and automatically unlocks even the most protected sites.  

### 🛡️ How does Scraping Browser handle bot detection?  
It automates fingerprinting, CAPTCHA solving, retries, and mimics real user behavior to prevent detection.  

### 🔌 Is Scraping Browser compatible with Puppeteer, Playwright, and Selenium?  
Yes! It seamlessly integrates with all major web automation tools.  

### 🔍 When should I use Scraping Browser instead of a proxy?  
Use Scraping Browser when you need JavaScript rendering, interactive actions (clicks, scrolls), and multi-step navigation.  
