GITHUB MODE (current)
  The apps now load the data file from GitHub and save to GitHub (Save to GitHub button / Ctrl+S, one commit per save).
  See GITHUB_SETUP.md in the Happy_Hatch_Trading_System folder. The local-file instructions below still apply if you choose "Open a local Excel file instead".
  Works in any browser in GitHub mode.

Happy Hatch Trading System
--------------------------
FOLDER LAYOUT
  Happy_Hatch_Trading_System\
     Happy_Hatch_Trading_Forms_App.html        FULL: add / edit / delete / Admin page (PIN login)
     Happy_Hatch_Trading_Forms_User.html       USER: add records, search, invoices - no Edit / Delete / Admin
     Happy_Hatch_Trading_Forms_ViewOnly.html   VIEW ONLY: view + search - no add / edit / delete / Admin, never saves
     Happy_Hatch_Data\                         everything else
         Happy_Hatch_Trading_Inventory_Data.xlsx     <- your data file (the apps read and write this)
         Happy_Hatch_Trading_Inventory_Tracker.xlsx  Excel template (dashboard, invoice, formulas)
         Happy_Hatch_Logo.png, Product_Photos\       logo and product photos (name photos by product code, e.g. HH101.jpg)
         README.txt

HOW TO WORK (Chrome or Edge)
  When an app opens, a pop-up (blurred background) asks you to open the Excel data file first; the page content appears after you open it.
  1. Open an app (.html).
  2. Click "Open workbook".
     - First time only: choose the Happy_Hatch_Data folder (or the Happy_Hatch_Trading_System folder). The app remembers it.
     - After that the same click opens Happy_Hatch_Data\Happy_Hatch_Trading_Inventory_Data.xlsx straight away
       (the browser may ask once per session to allow editing - click Allow).
  3. Add / edit / delete as usual. Every change is written into that same Excel file (header shows "Saved to ... at hh:mm").
  - Close the data file in Excel while using the app (Excel locks it; the app saves as soon as it is closed).
  - If the header shows "NOT SAVED", no file is connected: click Open workbook.
  - Firefox / Safari cannot write into an opened file: there, Export Data downloads a copy instead.
  - The apps need internet to load the Excel library.
  - Do not connect the app to the Tracker template: it would be rewritten as a plain data file (the app warns you first).
  - Keep a backup copy of the data file now and then.

Start order: Products -> Customers -> Purchases -> Sales.  Quantities carry a Unit (Pcs, Kg or Ltr) on Purchase and Sales.
Purchase: enter the Unit Cost OR the Total Unit Price - the other is calculated (Total Unit Price = Unit Cost x Quantity; Unit Cost = Total Unit Price / Quantity). Total Cost = Total Unit Price + Freight Charges + Other Charges. Onboard Price/Unit = Total Cost / Quantity.
Products: Onboard Price = the Onboard Price/Unit of the product's latest purchase (0 until a purchase exists), so changing a purchase Unit Cost, Freight or Other Charges updates the product's Onboard Price, Net Price and Revenue.
Products: Net Price = Onboard Price + Profitability % x Onboard Price. Revenue = Net Price - Onboard Price. There is no Base Price column any more.
Suggested codes: Product HH101...  |  Order Number HH_S000101...
Sales (Changeset 001): a sales order is a header plus items.
  SALES       = order header: Order Number, date, customer and ONE Tax Code for the whole order (GST/CGST/SGST/IGST come from the TAX sheet), sub total, tax and total.
  SALES_ITEMS = the products on each order (sub-records linked by Order Number): product, MRP, quantity, unit, net amount.
  In the forms app, New Sale opens one order form with the items grid inside it - tax is set once per order, so it can never differ from product to product.
  Older workbooks with one flat Sales sheet are converted automatically when opened.
Tax: enter your tax rates once in the TAX sheet (Tax Code, GST / CGST / SGST / IGST %). On each sale pick the Tax Code; the four rates fill in from the TAX sheet and feed the invoice (one Tax Code per order). Enter only the taxes that apply to a code. Changing a rate in the TAX sheet changes it on every sale/invoice that uses that code.
Invoice: one per Order Number, printable as PDF. Confirm tax rates and invoice format with Finance.
Admin page (full app only): PIN login, change PIN, add columns (text, integer, decimal, currency, percent, date, yes/no, dropdown, email), required / unique / default, calculated columns.
Sales: MRP fills in automatically with the Product price (Net Price) and can be changed on any line; Net Amount = MRP x Quantity.

Export Data (header button) downloads a copy of all current data as a new Excel file in your Downloads folder; it does not change the connected data file.

Products: "Available Specifications" and "Available Colours" hold several values separated by commas (e.g. Red, Blue, Green).
Sales items: each item has a Colour chosen from the product's Available Colours (the choice list appears automatically for products that have colours).
Shipper: a separate sheet/tab for shipper details (Shipper Number, name, contact person, phone, e-mail, address, city). On each purchase pick the Shipper Number and the shipper name, contact and e-mail fill in automatically.
