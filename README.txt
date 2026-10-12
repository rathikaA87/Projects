Happy Hatch Trading System
--------------------------
Happy_Hatch_Trading_Inventory_Tracker.xlsx  - main workbook (products, sales, purchase, customers, dashboard, invoice)
Happy_Hatch_Trading_Forms_App.html          - data-entry forms (open in a browser; use Open/Save workbook buttons)
Product_Photos\                             - one photo per product, named by product code (e.g. HH000101.jpg)

Keep all three together in the same folder.
Products: the "Photo File" column/field holds each product's image path (Product_Photos/<ProductCode>.jpg).
Sales: each sale row carries an Order Number (HH_S000101 ...). One order can have many product rows.
Sales tax columns: GST (%), CGST (%), SGST (%), IGST (%) - same rates on every row of an order; enter only those that apply.
Invoice: one per Order Number; labels like "CGST (9%)" show the order rate; each amount = rate x Subtotal; Total = Subtotal + the four amounts. Printable as PDF.
Sample tax rates are illustrative - confirm with Finance.
