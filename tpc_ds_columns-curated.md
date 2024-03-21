-- Create table call_center
DROP TABLE IF EXISTS call_center;
CREATE TABLE call_center (
cc_call_center_sk AS call_center_sk,
cc_call_center_id AS call_center_id,
cc_rec_start_date AS rec_start_date,
cc_rec_end_date AS rec_end_date,
cc_closed_date_sk AS closed_date_sk,
cc_open_date_sk AS open_date_sk,
cc_name AS name,
cc_class AS class,
cc_employees AS employees,
cc_sq_ft AS sq_ft,
cc_hours AS hours,
cc_manager AS manager,
cc_mkt_id AS mkt_id,
cc_mkt_class AS mkt_class,
cc_mkt_desc AS mkt_desc,
cc_market_manager AS market_manager,
cc_division AS division,
cc_division_name AS division_name,
cc_company AS company,
cc_company_name AS company_name,
cc_street_number AS street_number,
cc_street_name AS street_name,
cc_street_type AS street_type,
cc_suite_number AS suite_number,
cc_city AS city,
cc_county AS county,
cc_state AS state,
cc_zip AS zip,
cc_country AS country,
cc_gmt_offset AS gmt_offset,
cc_tax_percentage AS tax_percentage
);

-- Create table catalog_page
DROP TABLE IF EXISTS catalog_page;
CREATE TABLE catalog_page (
cp_catalog_page_sk AS catalog_page_sk,
cp_catalog_page_id AS catalog_page_id,
cp_start_date_sk AS start_date_sk,
cp_end_date_sk AS end_date_sk,
cp_department AS department,
cp_catalog_number AS catalog_number,
cp_catalog_page_number AS catalog_page_number,
cp_description AS description,
cp_type AS type
);

-- Create table catalog_returns
DROP TABLE IF EXISTS catalog_returns;
CREATE TABLE catalog_returns (
cr_returned_date_sk AS returned_date_sk,
cr_returned_time_sk AS returned_time_sk,
cr_item_sk AS item_sk,
cr_refunded_customer_sk AS refunded_customer_sk,
cr_refunded_cdemo_sk AS refunded_cdemo_sk,
cr_refunded_hdemo_sk AS refunded_hdemo_sk,
cr_refunded_addr_sk AS refunded_addr_sk,
cr_returning_customer_sk AS returning_customer_sk,
cr_returning_cdemo_sk AS returning_cdemo_sk,
cr_returning_hdemo_sk AS returning_hdemo_sk,
cr_returning_addr_sk AS returning_addr_sk,
cr_call_center_sk AS call_center_sk,
cr_catalog_page_sk AS catalog_page_sk,
cr_ship_mode_sk AS ship_mode_sk,
cr_warehouse_sk AS warehouse_sk,
cr_reason_sk AS reason_sk,
cr_order_number AS order_number,
cr_return_quantity AS return_quantity,
cr_return_amount AS return_amount,
cr_return_tax AS return_tax,
cr_return_amt_inc_tax AS return_amt_inc_tax,
cr_fee AS fee,
cr_return_ship_cost AS return_ship_cost,
cr_refunded_cash AS refunded_cash,
cr_reversed_charge AS reversed_charge,
cr_store_credit AS store_credit,
cr_net_loss AS net_loss
);

-- Create table catalog_sales
DROP TABLE IF EXISTS catalog_sales;
CREATE TABLE catalog_sales (
cs_sold_date_sk AS sold_date_sk,
cs_sold_time_sk AS sold_time_sk,
cs_ship_date_sk AS ship_date_sk,
cs_bill_customer_sk AS bill_customer_sk,
cs_bill_cdemo_sk AS bill_cdemo_sk,
cs_bill_hdemo_sk AS bill_hdemo_sk,
cs_bill_addr_sk AS bill_addr_sk,
cs_ship_customer_sk AS ship_customer_sk,
cs_ship_cdemo_sk AS ship_cdemo_sk,
cs_ship_hdemo_sk AS ship_hdemo_sk,
cs_ship_addr_sk AS ship_addr_sk,
cs_call_center_sk AS call_center_sk,
cs_catalog_page_sk AS catalog_page_sk,
cs_ship_mode_sk AS ship_mode_sk,
cs_warehouse_sk AS warehouse_sk,
cs_item_sk AS item_sk,
cs_promo_sk AS promo_sk,
cs_order_number AS order_number,
cs_quantity AS quantity,
cs_wholesale_cost AS wholesale_cost,
cs_list_price AS list_price,
cs_sales_price AS sales_price,
cs_ext_discount_amt AS ext_discount_amt,
cs_ext_sales_price AS ext_sales_price,
cs_ext_wholesale_cost AS ext_wholesale_cost,
cs_ext_list_price AS ext_list_price,
cs_ext_tax AS ext_tax,
cs_coupon_amt AS coupon_amt,
cs_ext_ship_cost AS ext_ship_cost,
cs_net_paid AS net_paid,
cs_net_paid_inc_tax AS net_paid_inc_tax,
cs_net_paid_inc_ship AS net_paid_inc_ship,
cs_net_paid_inc_ship_tax AS net_paid_inc_ship_tax,
cs_net_profit AS net_profit
);

-- Create table customer
DROP TABLE IF EXISTS customer;
CREATE TABLE customer (
c_customer_sk AS customer_sk,
c_customer_id AS customer_id,
c_current_cdemo_sk AS current_cdemo_sk,
c_current_hdemo_sk AS current_hdemo_sk,
c_current_addr_sk AS current_addr_sk,
c_first_shipto_date_sk AS first_shipto_date_sk,
c_first_sales_date_sk AS first_sales_date_sk,
c_salutation AS salutation,
c_first_name AS first_name,
c_last_name AS last_name,
c_preferred_cust_flag AS preferred_cust_flag,
c_birth_day AS birth_day,
c_birth_month AS birth_month,
c_birth_year AS birth_year,
c_birth_country AS birth_country,
c_login AS login,
c_email_address AS email_address,
c_last_review_date AS last_review_date
);

-- Create table customer_address
DROP TABLE IF EXISTS customer_address;
CREATE TABLE customer_address (
ca_address_sk AS address_sk,
ca_address_id AS address_id,
ca_street_number AS street_number,
ca_street_name AS street_name,
ca_street_type AS street_type,
ca_suite_number AS suite_number,
ca_city AS city,
ca_county AS county,
ca_state AS state,
ca_zip AS zip,
ca_country AS country,
ca_gmt_offset AS gmt_offset,
ca_location_type AS location_type
);

-- Create table customer_demographics
DROP TABLE IF EXISTS customer_demographics;
CREATE TABLE customer_demographics (
cd_demo_sk AS demo_sk,
cd_gender AS gender,
cd_marital_status AS marital_status,
cd_education_status AS education_status,
cd_purchase_estimate AS purchase_estimate,
cd_credit_rating AS credit_rating,
cd_dep_count AS dep_count,
cd_dep_employed_count AS dep_employed_count,
cd_dep_college_count AS dep_college_count
);

-- Create table date_dim
DROP TABLE IF EXISTS date_dim;
CREATE TABLE date_dim (
d_date_sk AS date_sk,
d_date_id AS date_id,
d_date AS date,
d_month_seq AS month_seq,
d_week_seq AS week_seq,
d_quarter_seq AS quarter_seq,
d_year AS year,
d_dow AS dow,
d_moy AS moy,
d_dom AS dom,
d_qoy AS qoy,
d_fy_year AS fy_year,
d_fy_quarter_seq AS fy_quarter_seq,
d_fy_week_seq AS fy_week_seq,
d_day_name AS day_name,
d_quarter_name AS quarter_name,
d_holiday AS holiday,
d_weekend AS weekend,
d_following_holiday AS following_holiday,
d_first_dom AS first_dom,
d_last_dom AS last_dom,
d_same_day_ly AS same_day_ly,
d_same_day_lq AS same_day_lq,
d_current_day AS current_day,
d_current_week AS current_week,
d_current_month AS current_month,
d_current_quarter AS current_quarter,
d_current_year AS current_year
);

-- Create table household_demographics
DROP TABLE IF EXISTS household_demographics;
CREATE TABLE household_demographics (
hd_demo_sk AS demo_sk,
hd_income_band_sk AS income_band_sk,
hd_buy_potential AS buy_potential,
hd_dep_count AS dep_count,
hd_vehicle_count AS vehicle_count
);

-- Create table income_band
DROP TABLE IF EXISTS income_band;
CREATE TABLE income_band (
ib_income_band_sk AS income_band_sk,
ib_lower_bound AS lower_bound,
ib_upper_bound AS upper_bound
);

-- Create table inventory
DROP TABLE IF EXISTS inventory;
CREATE TABLE inventory (
inv_date_sk AS date_sk,
inv_item_sk AS item_sk,
inv_warehouse_sk AS warehouse_sk,
inv_quantity_on_hand AS quantity_on_hand
);

-- Create table item
DROP TABLE IF EXISTS item;
CREATE TABLE item (
i_item_sk AS item_sk,
i_item_id AS item_id,
i_rec_start_date AS rec_start_date,
i_rec_end_date AS rec_end_date,
i_item_desc AS item_desc,
i_current_price AS current_price,
i_wholesale_cost AS wholesale_cost,
i_brand_id AS brand_id,
i_brand AS brand,
i_class_id AS class_id,
i_class AS class,
i_category_id AS category_id,
i_category AS category,
i_manufact_id AS manufact_id,
i_manufact AS manufact,
i_size AS size,
i_formulation AS formulation,
i_color AS color,
i_units AS units,
i_container AS container,
i_manager_id AS manager_id,
i_product_name AS product_name
);

-- Create table promotion
DROP TABLE IF EXISTS promotion;
CREATE TABLE promotion (
p_promo_sk AS promo_sk,
p_promo_id AS promo_id,
p_start_date_sk AS start_date_sk,
p_end_date_sk AS end_date_sk,
p_item_sk AS item_sk,
p_cost AS cost,
p_response_target AS response_target,
p_promo_name AS promo_name,
p_channel_dmail AS channel_dmail,
p_channel_email AS channel_email,
p_channel_catalog AS channel_catalog,
p_channel_tv AS channel_tv,
p_channel_radio AS channel_radio,
p_channel_press AS channel_press,
p_channel_event AS channel_event,
p_channel_demo AS channel_demo,
p_channel_details AS channel_details,
p_purpose AS purpose,
p_discount_active AS discount_active
);

-- Create table reason
DROP TABLE IF EXISTS reason;
CREATE TABLE reason (
r_reason_sk AS reason_sk,
r_reason_id AS reason_id,
r_reason_desc AS reason_desc
);


-- Create table ship_mode
DROP TABLE IF EXISTS ship_mode;
CREATE TABLE ship_mode (
sm_ship_mode_sk AS ship_mode_sk,
sm_ship_mode_id AS ship_mode_id,
sm_type AS type,
sm_code AS code,
sm_carrier AS carrier,
sm_contract AS contract
);

-- Create table store
DROP TABLE IF EXISTS store;
CREATE TABLE store (
s_store_sk AS store_sk,
s_store_id AS store_id,
s_rec_start_date AS rec_start_date,
s_rec_end_date AS rec_end_date,
s_closed_date_sk AS closed_date_sk,
s_store_name AS store_name,
s_number_employees AS number_employees,
s_floor_space AS floor_space,
s_hours AS hours,
s_manager AS manager,
s_market_id AS market_id,
s_geography_class AS geography_class,
s_market_desc AS market_desc,
s_market_manager AS market_manager,
s_division_id AS division_id,
s_division_name AS division_name,
s_company_id AS company_id,
s_company_name AS company_name,
s_street_number AS street_number,
s_street_name AS street_name,
s_street_type AS street_type,
s_suite_number AS suite_number,
s_city AS city,
s_county AS county,
s_state AS state,
s_zip AS zip,
s_country AS country,
s_gmt_offset AS gmt_offset,
s_tax_precentage AS tax_precentage
);

-- Create table store_returns
DROP TABLE IF EXISTS store_returns;
CREATE TABLE store_returns (
sr_returned_date_sk AS returned_date_sk,
sr_return_time_sk AS return_time_sk,
sr_item_sk AS item_sk,
sr_customer_sk AS customer_sk,
sr_cdemo_sk AS cdemo_sk,
sr_hdemo_sk AS hdemo_sk,
sr_addr_sk AS addr_sk,
sr_store_sk AS store_sk,
sr_reason_sk AS reason_sk,
sr_ticket_number AS ticket_number,
sr_return_quantity AS return_quantity,
sr_return_amt AS return_amt,
sr_return_tax AS return_tax,
sr_return_amt_inc_tax AS return_amt_inc_tax,
sr_fee AS fee,
sr_return_ship_cost AS return_ship_cost,
sr_refunded_cash AS refunded_cash,
sr_reversed_charge AS reversed_charge,
sr_store_credit AS store_credit,
sr_net_loss AS net_loss
);


-- Create table store_sales
DROP TABLE IF EXISTS store_sales;
CREATE TABLE store_sales (
ss_sold_date_sk AS sold_date_sk,
ss_sold_time_sk AS sold_time_sk,
ss_item_sk AS item_sk,
ss_customer_sk AS customer_sk,
ss_cdemo_sk AS cdemo_sk,
ss_hdemo_sk AS hdemo_sk,
ss_addr_sk AS addr_sk,
ss_store_sk AS store_sk,
ss_promo_sk AS promo_sk,
ss_ticket_number AS ticket_number,
ss_quantity AS quantity,
ss_wholesale_cost AS wholesale_cost,
ss_list_price AS list_price,
ss_sales_price AS sales_price,
ss_ext_discount_amt AS ext_discount_amt,
ss_ext_sales_price AS ext_sales_price,
ss_ext_wholesale_cost AS ext_wholesale_cost,
ss_ext_list_price AS ext_list_price,
ss_ext_tax AS ext_tax,
ss_coupon_amt AS coupon_amt,
ss_net_paid AS net_paid,
ss_net_paid_inc_tax AS net_paid_inc_tax,
ss_net_profit AS net_profit
);

-- Create table time_dim
DROP TABLE IF EXISTS time_dim;
CREATE TABLE time_dim (
t_time_sk AS time_sk,
t_time_id AS time_id,
t_time AS time,
t_hour AS hour,
t_minute AS minute,
t_second AS second,
t_am_pm AS am_pm,
t_shift AS shift,
t_sub_shift AS sub_shift,
t_meal_time AS meal_time
);

-- Create table warehouse
DROP TABLE IF EXISTS warehouse;
CREATE TABLE warehouse (
w_warehouse_sk AS warehouse_sk,
w_warehouse_id AS warehouse_id,
w_warehouse_name AS warehouse_name,
w_warehouse_sq_ft AS warehouse_sq_ft,
w_street_number AS street_number,
w_street_name AS street_name,
w_street_type AS street_type,
w_suite_number AS suite_number,
w_city AS city,
w_county AS county,
w_state AS state,
w_zip AS zip,
w_country AS country,
w_gmt_offset AS gmt_offset
);

-- Create table web_page
DROP TABLE IF EXISTS web_page;
CREATE TABLE web_page (
wp_web_page_sk AS web_page_sk,
wp_web_page_id AS web_page_id,
wp_rec_start_date AS rec_start_date,
wp_rec_end_date AS rec_end_date,
wp_creation_date_sk AS creation_date_sk,
wp_access_date_sk AS access_date_sk,
wp_autogen_flag AS autogen_flag,
wp_customer_sk AS customer_sk,
wp_url AS url,
wp_type AS type,
wp_char_count AS char_count,
wp_link_count AS link_count,
wp_image_count AS image_count,
wp_max_ad_count AS max_ad_count
);

-- Create table web_returns
DROP TABLE IF EXISTS web_returns;
CREATE TABLE web_returns (
wr_returned_date_sk AS returned_date_sk,
wr_returned_time_sk AS returned_time_sk,
wr_item_sk AS item_sk,
wr_refunded_customer_sk AS refunded_customer_sk,
wr_refunded_cdemo_sk AS refunded_cdemo_sk,
wr_refunded_hdemo_sk AS refunded_hdemo_sk,
wr_refunded_addr_sk AS refunded_addr_sk,
wr_returning_customer_sk AS returning_customer_sk,
wr_returning_cdemo_sk AS returning_cdemo_sk,
wr_returning_hdemo_sk AS returning_hdemo_sk,
wr_returning_addr_sk AS returning_addr_sk,
wr_web_page_sk AS web_page_sk,
wr_reason_sk AS reason_sk,
wr_order_number AS order_number,
wr_return_quantity AS return_quantity,
wr_return_amt AS return_amt,
wr_return_tax AS return_tax,
wr_return_amt_inc_tax AS return_amt_inc_tax,
wr_fee AS fee,
wr_return_ship_cost AS return_ship_cost,
wr_refunded_cash AS refunded_cash,
wr_reversed_charge AS reversed_charge,
wr_account_credit AS account_credit,
wr_net_loss AS net_loss
);


-- Create table web_sales
DROP TABLE IF EXISTS web_sales;
CREATE TABLE web_sales (
ws_sold_date_sk AS sold_date_sk,
ws_sold_time_sk AS sold_time_sk,
ws_ship_date_sk AS ship_date_sk,
ws_item_sk AS item_sk,
ws_bill_customer_sk AS bill_customer_sk,
ws_bill_cdemo_sk AS bill_cdemo_sk,
ws_bill_hdemo_sk AS bill_hdemo_sk,
ws_bill_addr_sk AS bill_addr_sk,
ws_ship_customer_sk AS ship_customer_sk,
ws_ship_cdemo_sk AS ship_cdemo_sk,
ws_ship_hdemo_sk AS ship_hdemo_sk,
ws_ship_addr_sk AS ship_addr_sk,
ws_web_page_sk AS web_page_sk,
ws_web_site_sk AS web_site_sk,
ws_ship_mode_sk AS ship_mode_sk,
ws_warehouse_sk AS warehouse_sk,
ws_promo_sk AS promo_sk,
ws_order_number AS order_number,
ws_quantity AS quantity,
ws_wholesale_cost AS wholesale_cost,
ws_list_price AS list_price,
ws_sales_price AS sales_price,
ws_ext_discount_amt AS ext_discount_amt,
ws_ext_sales_price AS ext_sales_price,
ws_ext_wholesale_cost AS ext_wholesale_cost,
ws_ext_list_price AS ext_list_price,
ws_ext_tax AS ext_tax,
ws_coupon_amt AS coupon_amt,
ws_ext_ship_cost AS ext_ship_cost,
ws_net_paid AS net_paid,
ws_net_paid_inc_tax AS net_paid_inc_tax,
ws_net_paid_inc_ship AS net_paid_inc_ship,
ws_net_paid_inc_ship_tax AS net_paid_inc_ship_tax,
ws_net_profit AS net_profit
);

-- Create table web_site
DROP TABLE IF EXISTS web_site;
CREATE TABLE web_site (
web_site_sk AS site_sk,
web_site_id AS site_id,
web_rec_start_date AS rec_start_date,
web_rec_end_date AS rec_end_date,
web_name AS name,
web_open_date_sk AS open_date_sk,
web_close_date_sk AS close_date_sk,
web_class AS class,
web_manager AS manager,
web_mkt_id AS mkt_id,
web_mkt_class AS mkt_class,
web_mkt_desc AS mkt_desc,
web_market_manager AS market_manager,
web_company_id AS company_id,
web_company_name AS company_name,
web_street_number AS street_number,
web_street_name AS street_name,
web_street_type AS street_type,
web_suite_number AS suite_number,
web_city AS city,
web_county AS county,
web_state AS state,
web_zip AS zip,
web_country AS country,
web_gmt_offset AS gmt_offset,
web_tax_percentage AS tax_percentage
);
