# 💧 Automated Debt Checker - Aguas Cordobesas

A Python automation script with a graphical user interface (GUI) that allows for bulk checking of debt status for multiple Billing Units (UF - Unidad de Facturación) on the Aguas Cordobesas portal. Ideal for streamlining administrative tasks in real estate agencies and property management.

## 🚀 How it works

The program takes an Excel file containing a list of properties, extracts the Billing Unit (UF) number for each one, and uses **Playwright** to automatically navigate the Aguas Cordobesas website. It checks if the account has "past due bills" (*comprobantes vencidos*) and then updates the same Excel file, writing a `"SI"` (Yes) or `"NO"` accordingly.

## 📊 Excel Structure

The script is designed to read and write using a specific column layout. Your Excel file must have the following columns (the program starts processing from row 2):

| Nº | Landlord Name | Address | UF | Debt |
| :---: | :--- | :--- | :--- | :---: |
| 1 | John Doe | Main St 123 | 01234567 | *(The script writes here)* |
| 2 | Jane Smith | Park Ave 456 | 09876543 | *(The script writes here)* |

* **Organizational columns (`Nº`, `Landlord Name`, `Address`):** The script ignores these entirely. They are meant strictly for your own visual organization so you know which property each account belongs to.
* **Key column (`UF` - Column D):** This is the only data the bot reads to perform the search on the website.
* **Result column (`Debt` - Column E):** The bot will automatically write **"SI"** (if it detects past due bills) or **"NO"** (if the account is up to date).

## ⚙️ Key Features

- **Graphical User Interface (GUI):** Includes an intuitive window built with `Tkinter` to easily select your Excel file.
- **Background Execution:** Implements `threading` to prevent the interface from freezing while the bot is actively working.
- **Headless Mode:** Lets you choose whether to watch the web browser perform the queries in real-time or run it hidden in the background so it doesn't interrupt your workflow.
- **Fault Tolerance:** If a UF is not numeric or the website takes too long to respond, the script logs the error in the console and seamlessly moves on to the next row without crashing.

## 🛠️ Prerequisites

Make sure you have Python installed on your system. You will also need to install the following Python libraries:

- `playwright`
- `openpyxl`

## 📦 Installation

1. Clone this repository or download the source code.
2. Open your terminal or command prompt and install the required dependencies:
   ```bash
   pip install playwright openpyxl
   playwright install chromium
   python main.py```