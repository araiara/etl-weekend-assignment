# Data Warehouse Design for an eCommerce site
## Business Requirements
The following are the business requirements of the system:
- The business domain is eCommerce.
- Analyze sales data to improve sales and find out trends among customers.
- Analyze sales data to invest more in products that are
  - Selling fast
  - Producing high profits
- Identify the products that are not doing well.

## Potential Area of Analysis
The following are the potential area of analysis:
- Identify the popular products among customers.
- Identify the least selling products.
- Analyze the customers based on their locations.
- Analyze the products based on their category.
- Analyze the products sold to customers.
- Analyze sales for a specific day.

## Possible Dimensions
The following are the possible dimensions:
- **dim_location** (*location_id*, town, country)
- **dim_customer** (*customer_id*, user_name, first_name, last_name, location_id*, active)
- **dim_category** (*category_id*, category)
- **dim_product** (*product_id*, product_name, product_description, price, mrp, pieces_per_case, weight_per_piece, uom, brand, category_id*, tax_percent, discount_pc, active, created_by, created_date, updated_by, updated_date)
- **dim_bill** (*bill_id*, bill_no, bill_date, bill_location, customer_id*, created_by, updated_by, created_date, updated_date)
- **fact_sales** (*sales_id*, bill_id*, product_id*, qty, gross_price, tax_amt, discount_amt, net_bill_amt)

## Possible Facts
The following are the possible facts:
- Product sales quantity
- Gross price for sales product
- Tax amount for a sold product
- The discount amount for a product
- Net bill amount for a sales product

## Identifying Attributes and Relationships between the Fact and Dimension Tables
### dim_location
Attributes | Description | Domain
---------- | ----------- | ------
location_id | The identifier for dim_location. | SERIAL, PK
town | The name of the town. | TEXT
country | The name of the country. | TEXT

### dim_customer
Attributes | Description | Domain
---------- | ----------- | ------
customer_id | The identifier for dim_customer. | SERIAL, PK
user_name | The preferred name while using the service. | TEXT, UNIQUE
first_name | First name of the customer. | TEXT
last_name | Last name of the customer. | TEXT
location_id | The ID of the location. | INT, FK
active | Active status of the customer. | CHAR(1)

### dim_category
Attributes | Description | Domain
---------- | ----------- | ------
category_id | The identifier for dim_category. | SERIAL, PK
category | The name of the category. | TEXT

### dim_product
Attributes | Description | Domain
---------- | ----------- | ------
product_id | The identifier for dim_product. | SERIAL, PK
product_name | The name of the product. | TEXT
product_description | The description of the product. | TEXT
price | The price of the product. | FLOAT
mrp | The maximum retail price of the product. | FLOAT
pieces_per_case | The total product pieces in a case. | INT
weight_per_piece | The weight of a single product piece. | FLOAT
uom | The unit of measure for a product. | CHAR(2)
brand | The brand of the product. | TEXT
category_id | The ID of the category. | INT, FK
tax_pc | The tax percent for a product. | FLOAT
discount_pc | The discount percent for a product. | FLOAT
active | The active status of the admin. | CHAR(1)
created_by | The name of the admin. | TEXT
created_date | The stocking date of the product. | DATE
updated_by | The name of the admin. | TEXT
updated_date | The recent stocking date of the product. | DATE

### dim_bill
Attributes | Description | Domain
---------- | ----------- | ------
bill_id | The identifier for dim_bill. | SERIAL, PK
bill_no | The number of the bill. | INT
bill_date | The date of bill generation. | TIMESTAMP
bill_location | The location where the bill was generated. | TEXT
customer_id | The ID of the customer. | INT, FK
created_by | The name of the staff that created the bill. | TEXT
updated_by | The name of the staff that updated the bill. | TEXT
created_date | The date and time of bill creation by staff. | DATE
updated_date | The date and time when the bill was updated by staff. | DATE

### fact_sales
Attributes | Description | Domain
---------- | ----------- | ------
sales_id | The identifier for fact_sales. | SERIAL, PK
bill_id | The ID of the bill. | INT, FK
product_id | The ID of the product. | INT, FK
qty | The sales quantity of a product. | INT
gross_price | The gross price of a sales product. | FLOAT
tax_amt | The tax amount for a sales product. | FLOAT
discount_amt | The discount amount for a sales product. | FLOAT
net_bill_amt | The total bill amount for a product. | FLOAT

## Logical Model
![](./img/logical-model.png)


[Link to the diagram](https://app.diagrams.net/#G1fz_FY-AXQpEv9yNQhccgYX-JzqJFtR_9)
