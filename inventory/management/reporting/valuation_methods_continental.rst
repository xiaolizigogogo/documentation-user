:code-column:

==========================================================
How to do an inventory valuation? (Continental Accounting)
==========================================================

Every year your inventory valuation has to be recorded in your 
balance sheet. This implies two main choices:

- the way you compute the cost of your stored items 
  (Standard vs. Average vs. Real Price);

- the way you record the inventory value into your books 
  (periodic vs. Perpetual).

Costing Method
==============

.. rst-class:: alternatives doc-aside

Standard Price 
  .. rst-class:: values-table

  .. list-table::
     :widths: 28 18 18 18 18
     :header-rows: 1
     :stub-columns: 1

     * - Operation
       - Unit Cost
       - Qty On Hand
       - Delta Value
       - Inventory Value
     * -
       - €10
       - 0
       -
       - €0
     * - Receive 8 Products at €10
       - €10
       - 8
       - +8*€10
       - €80
     * - Receive 4 Products at €16
       - €10
       - 12
       - +4*€10
       - €120
     * - Deliver 10 Products
       - €10
       - 2
       - | -10*€10
         |
       - €20
     * - Receive 2 Products at €9
       - €10
       - 4
       - +2*€10
       - €40

  **Standard Price** means you estimate the cost price based 
  on direct materials, direct labor and manufacturing overhead 
  at the end of a specific period (usually once a year). You 
  enter this cost price in the product form.

Average Price
  .. rst-class:: values-table

  .. list-table::
     :widths: 28 18 18 18 18
     :header-rows: 1
     :stub-columns: 1

     * - Operation
       - Unit Cost
       - Qty On Hand
       - Delta Value
       - Inventory Value
     * -
       - €0
       - 0
       -
       - €0
     * - Receive 8 Products at €10
       - €10
       - 8
       - +8*€10
       - €80
     * - Receive 4 Products at €16
       - €12
       - 12
       - +4*€16
       - €144
     * - Deliver 10 Products
       - €12
       - 2
       - | -10*€12
         |
       - €24
     * - Receive 2 Products at €6
       - €9
       - 4
       - +2*€6
       - €36

  The **Average Price** method recomputes the cost price as a receipt order 
  has been processed, based on prices defined in tied purchase orders:
  FORMULA (see here attached)

  The average cost does not change when products leave the warehouse.

  From an accounting point of view, this method is mainly justified in 
  case of huge purchase price variations and is quite unusual due to its 
  operational complexity. Your actually need a software like Odoo to 
  easily keep this cost up-to-date.

  This method is dedicated to advanced users. It requires well established 
  business processes because the order in which you process receipt orders 
  matters in the cost computation.

FIFO
  .. rst-class:: values-table

  .. list-table::
     :widths: 28 18 18 18 18
     :header-rows: 1
     :stub-columns: 1

     * - Operation
       - Unit Cost
       - Qty On Hand
       - Delta Value
       - Inventory Value
     * -
       - €0
       - 0
       -
       - €0
     * - Receive 8 Products at €10
       - €10
       - 8
       - +8*€10
       - €80
     * - Receive 4 Products at €16
       - €12
       - 12
       - +4*€16
       - €144
     * - Deliver 10 Products
       - €16
       - 2
       - | -8*€10
         | -2*€16
       - €32
     * - Receive 2 Products at €6
       - €11
       - 4
       - +2*€6
       - €44

  For **Real Price** (FIFO, LIFO, FEFO, etc), the costing is further 
  refined by the removal strategy set on the warehouse location 
  or product's internal category. The default strategy is FIFO. With 
  such method, your inventory value is computed from the real cost 
  of your stored products (cfr. Quantitative Valuation) and not from 
  the cost price shown in the product form. Whenever you ship items, 
  the cost price is reset to the cost of the last item(s) shipped. 
  This cost price is used to value any product not received from a 
  purchase order (e.g. inventory adjustments).

  FIFO is advised if you manage all your workflow into Odoo (Sales, 
  Purchases, Inventory). It suits any kind of users.

LIFO (not accepted in IFRS)
  .. rst-class:: values-table

  .. list-table::
     :widths: 28 18 18 18 18
     :header-rows: 1
     :stub-columns: 1

     * - Operation
       - Unit Cost
       - Qty On Hand
       - Delta Value
       - Inventory Value
     * -
       - €0
       - 0
       -
       - €0
     * - Receive 8 Products at €10
       - €10
       - 8
       - +8*€10
       - €80
     * - Receive 4 Products at €16
       - €12
       - 12
       - +4*€16
       - €144
     * - Deliver 10 Products
       - €10
       - 2
       - | -4*€16
         | -6*€10
       - €20
     * - Receive 2 Products at €6
       - €8
       - 4
       - +2*€6
       - €32

  For **Real Price** (FIFO, LIFO, FEFO, etc), the costing is further 
  refined by the removal strategy set on the warehouse location 
  or product's internal category. The default strategy is FIFO. 
  With such method, your inventory value is computed from the 
  real cost of your stored products (cfr. Quantitative Valuation) 
  and not from the cost price shown in the product form. Whenever 
  you ship items, the cost price is reset to the cost of the last 
  item(s) shipped. This cost price is used to value any product 
  not received from a purchase order (e.g. inventory adjustments).

  LIFO is not permitted outside the United States.

Odoo allows any method. The default one is **Standard Price**. 
To change it, check **Use a 'Fixed', 'Real' or 'Average' price 
costing method** in Purchase settings. Then set the costing 
method from products' internal categories. Categories show up 
in the Inventory tab of the product form.

Whatever the method is, Odoo provides a full inventory valuation
in :menuselection:`Inventory --> Reports --> Inventory Valuation` 
(i.e. current quantity in stock * cost price).

Periodic Inventory Valuation
============================

In a periodic inventory valuation, goods reception and 
outgoing shipments have no direct impact in the accounting. 
At the end of the month or year, the accountant posts one 
journal entry representing the value of the physical inventory. 

This is the default configuration in Odoo and it works 
out-of-the-box. Check following operations and find out how 
Odoo is managing the accounting postings.

.. rst-class:: alternatives doc-aside

Vendor Bill
  .. rst-class:: values-table

  ============================= ===== ======
  \                             Debit Credit
  ============================= ===== ======
  Assets: Inventory                50
  Assets: Deferred Tax Assets    4.68
  Liabilities: Accounts Payable	       54.68
  ============================= ===== ======

  Configuration:
    * Purchased Goods: defined on the product or on the internal category of related product (Expense Account field)
    * Deferred Tax Assets: defined on the tax used on the purchase order line
    * Accounts Payable: defined on the vendor related to the bill
Goods Receptions
  No Journal Entry
Customer Invoice
  .. rst-class:: values-table

  ===================================== ===== ======
  \                                     Debit Credit
  ===================================== ===== ======
  Revenues: Sold Goods                           100
  Liabilities: Deferred Tax Liabilities            9
  Assets: Accounts Receivable             109
  ===================================== ===== ======

  Configuration:
    * Revenues: defined on the product or on the internal category of related product (Income Account field)
    * Deferred Tax Liabilities: defined on the tax used on the invoice line
    * Accounts Receivable: defined on the customer (Receivable Account)

  The fiscal position used on the invoice may have a rule that replaces the
  Income Account or the tax defined on the product by another one.
Customer Shipping
  No Journal Entry
Manufacturing Orders
  No Journal Entry

.. raw:: html

   <hr style="float: none; visibility: hidden; margin: 0;">

At the end of the month/year, your company does a physical inventory 
or just relies on the inventory in Odoo to value the stock into your books.

Create a journal entry to move the stock variation value from your 
Profit&Loss section to your assets. 

.. h:div:: doc-aside

  .. rst-class:: values-table

  ===================================== ===== ======
  \                                     Debit Credit
  ===================================== ===== ======
  Assets: Inventory                         X     
  Expenses: Inventory Variations                   X            
  ===================================== ===== ======

  If the stock value decreased, the **Inventory** account is credited
  and te **Inventory Variations** debited.
   
.. raw:: html

   <hr style="float: none; visibility: hidden; margin: 0;">

Perpetual Inventory Valuation
=============================

In a perpetual inventory valuation, goods receptions and 
outgoing shipments are posted in your books in real time. 
The books are therefore always up-to-date. This mode is 
dedicated to expert accountants and advanced users only. 
As opposed to periodic valuation, it requires some extra 
configuration & testing.

Let's take the case of a reseller.

.. h:div:: valuation-chart-continental doc-aside

   .. placeholder

.. raw:: html

   <hr style="float: none; visibility: hidden; margin: 0;">

.. h:div:: doc-aside
  
   **Configuration:**

   - Accounts Receivable/Payable: defined on the partner (Accounting tab)

   - Deferred Tax Assets/Liabilities: defined on the tax used on the invoice line

   - Revenues/Expenses: defined by default on product's internal category; can be 
     also set in product form (Accounting tab) as a replacement value.

   - Inventory Variations: to set as Stock Input/Output Account in product's internal 
     category
     
   - Inventory: to set as Stock Valuation Account in product's internal category


More Technically ...
======================

The following chapter is more technical and explains how specific elements are computed.
Basically the elements below are computed for a product.product not for a product.template.
When calculated for different elements, it may differs.

On Hand quantities
^^^^^^^^^^^^^^^^^^^
- For product.product
  TODO:
- For product.template
  TODO:

Inventory Valuation (Current Inventory)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This is specified in odoo/addons/stock_account/models/product.py mostly in the method _compute_stock_value()

- Fifo Manual
  TODO:
- Fifo Automated
  The quantity is the sum of the quantity for stock.move of this product with a specific domain.
  The value is the sum of the quantity for stock.move of this product with a specific domain.

  The domain is defined in odoo/addons/stock_account/models/stock.py in the method _get_all_base_domain and basically looks like

  - Odoo style:
  ```
          domain = [
            ('state', '=', 'done'),
            '|',
                '&',
                    '|',
                        ('location_id.company_id', '=', False),
                        '&',
                            ('location_id.usage', 'in', ['inventory', 'production']),
                            ('location_id.company_id', '=', company_id or self.env.user.company_id.id),
                    ('location_dest_id.company_id', '=', company_id or self.env.user.company_id.id),
                '&',
                    ('location_id.company_id', '=', company_id or self.env.user.company_id.id),
                    '|',
                        ('location_dest_id.company_id', '=', False),
                        '&',
                            ('location_dest_id.usage', '=', 'inventory'),
                            ('location_dest_id.company_id', '=', company_id or self.env.user.company_id.id),
  ```

  - SQL style: (need double check)
  ```
  SELECT stock_move.product_id,SUM(COALESCE(stock_move.qty)), SUM(COALESCE(stock_move.remaining_value, 0.0)), ARRAY_AGG(stock_move.id)
	            FROM "stock_location" as "stock_move__location_id","stock_location" as "stock_move__location_dest_id","stock_move"
	            WHERE ("stock_move"."location_dest_id"="stock_move__location_dest_id"."id" AND "stock_move"."location_id"="stock_move__location_id"."id") AND 
	            (
		            	(
			            	("stock_move"."product_id" in (34189))  AND
				            ("stock_move"."state" = 'done')
				        )
				     AND
		            (
		            	(
		            		("stock_move__location_id"."company_id" IS NULL   OR
				            	(	("stock_move__location_id"."usage" in ('inventory','production'))  AND  ("stock_move__location_id"."company_id" = 1))
		            		)  AND
		            		("stock_move__location_dest_id"."company_id" = 1)
		            	)
		            	OR
		            	(
		            		("stock_move__location_id"."company_id" = 1)  AND ("stock_move__location_dest_id"."company_id" IS NULL
		            			OR
		            		(("stock_move__location_dest_id"."usage" = 'inventory')  AND  ("stock_move__location_dest_id"."company_id" = 1)))
		            	)
	            	)
	            )
	            AND ("stock_move"."company_id" IS NULL   OR  ("stock_move"."company_id" in (1)))
	            GROUP BY stock_move.product_id

  ```
Inventory Valuation (At a Specific Date)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This is specified in odoo/addons/stock_account/models/product.py mostly in the method _compute_stock_value()
- Fifo Manual:
  TODO:
- Fifo Automated:
  The quantity is computed from the Inventory Valuation (Current Inventory). If the quantity is negative or null the line is not displayed.
  The value is computed from the account.move.lines and is simply the sum balances of all the account.move.lines where the account is the valuation account of the product.

.. seealso::

  * :doc:`../../routes/strategies/removal`
  * :doc:`../../../accounting/others/inventory/avg_price_valuation`
  * :doc:`../../routes/costing/landed_costs`