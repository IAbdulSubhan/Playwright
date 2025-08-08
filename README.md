# Playwright Python Tutorial

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive guide to using Playwright with Python for browser automation, web scraping, and testing with detailed examples and explanations.

## 📌 Table of Contents

- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Usage](#-usage)
- [Interactive REPL Mode](#-interactive-repl-mode)
- [Locator Strategies](#-locator-strategies)
- [Mouse Actions](#-mouse-actions)
- [Input Handling](#-input-handling)
- [File Uploads](#-file-uploads)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

## 🌟 Features

- Complete Playwright Python tutorial from basics to advanced
- Sync and async API examples
- Multiple element locator strategies
- Form handling examples
- File upload techniques
- Interactive REPL mode for real-time debugging
- Dark-themed documentation with copy-paste ready code
- Practical examples for common web automation tasks

## 📋 Prerequisites

- Python 3.7+
- pip package manager
- Basic understanding of Python

## 🛠 Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/playwright-python-tutorial.git
cd playwright-python-tutorial
```

2. Install Playwright:
```bash
pip install playwright
```

3. Install browsers:
```bash
playwright install
```

## 🚀 Usage

### Basic Sync Playwright
```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=False, slow_mo=500)
    page = browser.new_page()
    page.goto("https://example.com")
    print(page.title())
    browser.close()
```

### Async Playwright (for concurrency)
```python
import asyncio
from playwright.async_api import async_playwright

async def main():
    async with async_playwright() as p:
        browser = await p.chromium.launch()
        page = await browser.new_page()
        await page.goto("https://example.com")
        print(await page.title())
        await browser.close()

asyncio.run(main())
```

## 💻 Interactive REPL Mode

To keep the browser open for interactive work:

1. Run your script in interactive mode:
```bash
python -i your_script.py
```

2. Or use IPython for better experience:
```bash
pip install ipython
ipython -i your_script.py
```

3. You can also add this to your script:
```python
input("Press Enter to close browser...")
browser.close()
```

## 🔍 Locator Strategies

### By Role
```python
page.get_by_role('link', name="linkname").click()
```

### By Text
```python
page.get_by_text('Submit').click()
page.get_by_text('Welcome', exact=True).highlight()
```

### CSS Selectors
```python
page.locator('button.btn-primary').click()
page.locator('div > ul.list-group').highlight()
```

### XPath
```python
page.locator('//input[@value="submit"]').click()
```

## 🖱 Mouse Actions

```python
# Double click
element.dblclick()

# Right click
element.click(button='right')

# Click with modifier keys
element.click(modifiers=['Shift', 'Ctrl'])

# Hover
element.hover()
```

## ⌨ Input Handling

```python
# Fill input
page.get_by_label('Username').fill('user123')

# Type with delay
page.get_by_placeholder('Password').type('secret', delay=100)

# Checkboxes
page.get_by_label('Agree').check()
page.get_by_label('Subscribe').uncheck()
```

## 📁 File Uploads

### Standard Input
```python
page.get_by_label('Upload file').set_input_files('file.txt')
```

### Button-triggered Upload
```python
with page.expect_file_chooser() as fc_info:
    page.get_by_text('Select file').click()
file_chooser = fc_info.value
file_chooser.set_files('file.txt')
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

## 🙏 Acknowledgements

- [Playwright Documentation](https://playwright.dev/python/docs/intro)
- [Python Official Documentation](https://docs.python.org/3/)
```

This README includes:

1. **Badges** - For license information
2. **Table of Contents** - Easy navigation
3. **Features** - Highlighting what the tutorial covers
4. **Installation Instructions** - Step-by-step setup
5. **Usage Examples** - Both sync and async basic examples
6. **Interactive REPL Mode** - Special section as requested
7. **Locator Strategies** - Various ways to find elements
8. **Mouse Actions** - Different interaction methods
9. **Input Handling** - Form interaction examples
10. **File Uploads** - Both standard and special cases
11. **Contributing Guidelines** - For community contributions
12. **License Information** - MIT license
13. **Acknowledgements** - Credit to resources used

The markdown is formatted for good readability on GitHub and includes code blocks with proper syntax highlighting. You can customize the repository links and your personal information as needed.
