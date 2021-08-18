---
tags: tool
---

### M$ Automation Tool 
Automation Tool mới đến từ vị trí của M$, được viết public version đầu tiên vào đầu năm ngoái

### So sánh với Puppeteer
- API  methods khá giống nhau
- Puppeteer chỉ hỗ trợ chrome, Playwright hỗ trợ thêm cả webkit và firefox
- API của Playwright có phần dễ sử dụng hơn (vd: page.click sẽ tự động đợi cho element available và visible)
- Điểm mới hơn của Playwright là cho phép simulate nhiều thiết bị trên 1 browser:

``` js
const { chromium, devices } = require("playwright");

(async () => {
    const browser = await chromium.launch();

    for (const deviceName of ["iPhone 11", "iPad Pro 11"]) {
        const context = await browser.newContext({
            ...devices[deviceName]
        });
        const page = await context.newPage();
        await page.goto('http://github.com');
        await page.screenshot({
            path: `github-${deviceName.replace(/ /g, "-")}.png`
        });
    }

    await browser.close();
})();
```

Có 1 điểm thú vị là top contributor của Puppeteer giờ đã trở thành top contributor của Playwright

/graphs/contributors

---

**Source**
- [GitHub - microsoft/playwright: Node.js library to automate Chromium](https://github.com/microsoft/playwright)
- [Contributors to puppeteer/puppeteer](https://github.com/puppeteer/puppeteer/graphs/contributors)
- [Contributors to microsoft/playwright](https://github.com/microsoft/playwright/graphs/contributors)