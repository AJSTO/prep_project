-- Create table call_center
DROP TABLE IF EXISTS call_center;
CREATE TABLE call_center (
    cc_call_center_sk STRING,
    cc_call_center_id STRING,
    cc_rec_start_date STRING,
    cc_rec_end_date STRING,
    cc_closed_date_sk STRING,
    cc_open_date_sk STRING,
    cc_name STRING,
    cc_class STRING,
    cc_employees STRING,
    cc_sq_ft STRING,
    cc_hours STRING,
    cc_manager STRING,
    cc_mkt_id STRING,
    cc_mkt_class STRING,
    cc_mkt_desc STRING,
    cc_market_manager STRING,
    cc_division STRING,
    cc_division_name STRING,
    cc_company STRING,
    cc_company_name STRING,
    cc_street_number STRING,
    cc_street_name STRING,
    cc_street_type STRING,
    cc_suite_number STRING,
    cc_city STRING,
    cc_county STRING,
    cc_state STRING,
    cc_zip STRING,
    cc_country STRING,
    cc_gmt_offset STRING,
    cc_tax_percentage STRING
);

-- Create table catalog_page
DROP TABLE IF EXISTS catalog_page;
CREATE TABLE catalog_page (
    cp_catalog_page_sk STRING,
    cp_catalog_page_id STRING,
    cp_start_date_sk STRING,
    cp_end_date_sk STRING,
    cp_department STRING,
    cp_catalog_number STRING,
    cp_catalog_page_number STRING,
    cp_description STRING,
    cp_type STRING
);

-- Create table catalog_returns
DROP TABLE IF EXISTS catalog_returns;
CREATE TABLE catalog_returns (
    cr_returned_date_sk STRING,
    cr_returned_time_sk STRING,
    cr_item_sk STRING,
    cr_refunded_customer_sk STRING,
    cr_refunded_cdemo_sk STRING,
    cr_refunded_hdemo_sk STRING,
    cr_refunded_addr_sk STRING,
    cr_returning_customer_sk STRING,
    cr_returning_cdemo_sk STRING,
    cr_returning_hdemo_sk STRING,
    cr_returning_addr_sk STRING,
    cr_call_center_sk STRING,
    cr_catalog_page_sk STRING,
    cr_ship_mode_sk STRING,
    cr_warehouse_sk STRING,
    cr_reason_sk STRING,
    cr_order_number STRING,
    cr_return_quantity STRING,
    cr_return_amount STRING,
    cr_return_tax STRING,
    cr_return_amt_inc_tax STRING,
    cr_fee STRING,
    cr_return_ship_cost STRING,
    cr_refunded_cash STRING,
    cr_reversed_charge STRING,
    cr_store_credit STRING,
    cr_net_loss STRING
);

-- Create table catalog_sales
DROP TABLE IF EXISTS catalog_sales;
CREATE TABLE catalog_sales (
    cs_sold_date_sk STRING,
    cs_sold_time_sk STRING,
    cs_ship_date_sk STRING,
    cs_bill_customer_sk STRING,
    cs_bill_cdemo_sk STRING,
    cs_bill_hdemo_sk STRING,
    cs_bill_addr_sk STRING,
    cs_ship_customer_sk STRING,
    cs_ship_cdemo_sk STRING,
    cs_ship_hdemo_sk STRING,
    cs_ship_addr_sk STRING,
    cs_call_center_sk STRING,
    cs_catalog_page_sk STRING,
    cs_ship_mode_sk STRING,
    cs_warehouse_sk STRING,
    cs_item_sk STRING,
    cs_promo_sk STRING,
    cs_order_number STRING,
    cs_quantity STRING,
    cs_wholesale_cost STRING,
    cs_list_price STRING,
    cs_sales_price STRING,
    cs_ext_discount_amt STRING,
    cs_ext_sales_price STRING,
    cs_ext_wholesale_cost STRING,
    cs_ext_list_price STRING,
    cs_ext_tax STRING,
    cs_coupon_amt STRING,
    cs_ext_ship_cost STRING,
    cs_net_paid STRING,
    cs_net_paid_inc_tax STRING,
    cs_net_paid_inc_ship STRING,
    cs_net_paid_inc_ship_tax STRING,
    cs_net_profit STRING
);

-- Create table customer
DROP TABLE IF EXISTS customer;
CREATE TABLE customer (
    c_customer_sk STRING,
    c_customer_id STRING,
    c_current_cdemo_sk STRING,
    c_current_hdemo_sk STRING,
    c_current_addr_sk STRING,
    c_first_shipto_date_sk STRING,
    c_first_sales_date_sk STRING,
    c_salutation STRING,
    c_first_name STRING,
    c_last_name STRING,
    c_preferred_cust_flag STRING,
    c_birth_day STRING,
    c_birth_month STRING,
    c_birth_year STRING,
    c_birth_country STRING,
    c_login STRING,
    c_email_address STRING,
    c_last_review_date STRING
);

-- Create table customer_address
DROP TABLE IF EXISTS customer_address;
CREATE TABLE customer_address (
    ca_address_sk STRING,
    ca_address_id STRING,
    ca_street_number STRING,
    ca_street_name STRING,
    ca_street_type STRING,
    ca_suite_number STRING,
    ca_city STRING,
    ca_county STRING,
    ca_state STRING,
    ca_zip STRING,
    ca_country STRING,
    ca_gmt_offset STRING,
    ca_location_type STRING
);

drop table if exists customer_demographics;
create table customer_demographics
(
cd_demo_sk STRING,
cd_gender STRING,
cd_marital_status STRING,
cd_education_status STRING,
cd_purchase_estimate STRING,
cd_credit_rating STRING,
cd_dep_count STRING,
cd_dep_employed_count STRING,
cd_dep_college_count STRING
);

drop table if exists date_dim;
create table date_dim
(
d_date_sk STRING,
d_date_id STRING,
d_date STRING,
d_month_seq STRING,
d_week_seq STRING,
d_quarter_seq STRING,
d_year STRING,
d_dow STRING,
d_moy STRING,
d_dom STRING,
d_qoy STRING,
d_fy_year STRING,
d_fy_quarter_seq STRING,
d_fy_week_seq STRING,
d_day_name STRING,
d_quarter_name STRING,
d_holiday STRING,
d_weekend STRING,
d_following_holiday STRING,
d_first_dom STRING,
d_last_dom STRING,
d_same_day_ly STRING,
d_same_day_lq STRING,
d_current_day STRING,
d_current_week STRING,
d_current_month STRING,
d_current_quarter STRING,
d_current_year STRING
);

drop table if exists household_demographics;
create table household_demographics
(
hd_demo_sk STRING,
hd_income_band_sk STRING,
hd_buy_potential STRING,
hd_dep_count STRING,
hd_vehicle_count STRING
);

drop table if exists income_band;
create table income_band
(
ib_income_band_sk STRING,
ib_lower_bound STRING,
ib_upper_bound STRING
);

drop table if exists inventory;
create table inventory
(
inv_date_sk STRING,
inv_item_sk STRING,
inv_warehouse_sk STRING,
inv_quantity_on_hand STRING
);

drop table if exists item;
create table item
(
i_item_sk STRING,
i_item_id STRING,
i_rec_start_date STRING,
i_rec_end_date STRING,
i_item_desc STRING,
i_current_price STRING,
i_wholesale_cost STRING,
i_brand_id STRING,
i_brand STRING,
i_class_id STRING,
i_class STRING,
i_category_id STRING,
i_category STRING,
i_manufact_id STRING,
i_manufact STRING,
i_size STRING,
i_formulation STRING,
i_color STRING,
i_units STRING,
i_container STRING,
i_manager_id STRING,
i_product_name STRING
);

drop table if exists promotion;
create table promotion
(
p_promo_sk STRING,
p_promo_id STRING,
p_start_date_sk STRING,
p_end_date_sk STRING,
p_item_sk STRING,
p_cost STRING,
p_response_target STRING,
p_promo_name STRING,
p_channel_dmail STRING,
p_channel_email STRING,
p_channel_catalog STRING,
p_channel_tv STRING,
p_channel_radio STRING,
p_channel_press STRING,
p_channel_event STRING,
p_channel_demo STRING,
p_channel_details STRING,
p_purpose STRING,
p_discount_active STRING
);

drop table if exists reason;
create table reason
(
r_reason_sk STRING,
r_reason_id STRING,
r_reason_desc STRING
);

drop table if exists ship_mode;
create table ship_mode
(
sm_ship_mode_sk STRING,
sm_ship_mode_id STRING,
sm_type STRING,
sm_code STRING,
sm_carrier STRING,
sm_contract STRING
);

drop table if exists store;
create table store
(
s_store_sk STRING,
s_store_id STRING,
s_rec_start_date STRING,
s_rec_end_date STRING,
s_closed_date_sk STRING,
s_store_name STRING,
s_number_employees STRING,
s_floor_space STRING,
s_hours STRING,
s_manager STRING,
s_market_id STRING,
s_geography_class STRING,
s_market_desc STRING,
s_market_manager STRING,
s_division_id STRING,
s_division_name STRING,
s_company_id STRING,
s_company_name STRING,
s_street_number STRING,
s_street_name STRING,
s_street_type STRING,
s_suite_number STRING,
s_city STRING,
s_county STRING,
s_state STRING,
s_zip STRING,
s_country STRING,
s_gmt_offset STRING,
s_tax_precentage STRING
);

drop table if exists store_returns;
create table store_returns
(
sr_returned_date_sk STRING,
sr_return_time_sk STRING,
sr_item_sk STRING,
sr_customer_sk STRING,
sr_cdemo_sk STRING,
sr_hdemo_sk STRING,
sr_addr_sk STRING,
sr_store_sk STRING,
sr_reason_sk STRING,
sr_ticket_number STRING,
sr_return_quantity STRING,
sr_return_amt STRING,
sr_return_tax STRING,
sr_return_amt_inc_tax STRING,
sr_fee STRING,
sr_return_ship_cost STRING,
sr_refunded_cash STRING,
sr_reversed_charge STRING,
sr_store_credit STRING,
sr_net_loss STRING
);

drop table if exists store_sales;
create table store_sales
(
ss_sold_date_sk STRING,
ss_sold_time_sk STRING,
ss_item_sk STRING,
ss_customer_sk STRING,
ss_cdemo_sk STRING,
ss_hdemo_sk STRING,
ss_addr_sk STRING,
ss_store_sk STRING,
ss_promo_sk STRING,
ss_ticket_number STRING,
ss_quantity STRING,
ss_wholesale_cost STRING,
ss_list_price STRING,
ss_sales_price STRING,
ss_ext_discount_amt STRING,
ss_ext_sales_price STRING,
ss_ext_wholesale_cost STRING,
ss_ext_list_price STRING,
ss_ext_tax STRING,
ss_coupon_amt STRING,
ss_net_paid STRING,
ss_net_paid_inc_tax STRING,
ss_net_profit STRING
);

drop table if exists time_dim;
create table time_dim
(
t_time_sk STRING,
t_time_id STRING,
t_time STRING,
t_hour STRING,
t_minute STRING,
t_second STRING,
t_am_pm STRING,
t_shift STRING,
t_sub_shift STRING,
t_meal_time STRING
);

drop table if exists warehouse;
create table warehouse
(
w_warehouse_sk STRING,
w_warehouse_id STRING,
w_warehouse_name STRING,
w_warehouse_sq_ft STRING,
w_street_number STRING,
w_street_name STRING,
w_street_type STRING,
w_suite_number STRING,
w_city STRING,
w_county STRING,
w_state STRING,
w_zip STRING,
w_country STRING,
w_gmt_offset STRING
);

drop table if exists web_page;
create table web_page
(
wp_web_page_sk STRING,
wp_web_page_id STRING,
wp_rec_start_date STRING,
wp_rec_end_date STRING,
wp_creation_date_sk STRING,
wp_access_date_sk STRING,
wp_autogen_flag STRING,
wp_customer_sk STRING,
wp_url STRING,
wp_type STRING,
wp_char_count STRING,
wp_link_count STRING,
wp_image_count STRING,
wp_max_ad_count STRING
);

drop table if exists web_returns;
create table web_returns
(
wr_returned_date_sk STRING,
wr_returned_time_sk STRING,
wr_item_sk STRING,
wr_refunded_customer_sk STRING,
wr_refunded_cdemo_sk STRING,
wr_refunded_hdemo_sk STRING,
wr_refunded_addr_sk STRING,
wr_returning_customer_sk STRING,
wr_returning_cdemo_sk STRING,
wr_returning_hdemo_sk STRING,
wr_returning_addr_sk STRING,
wr_web_page_sk STRING,
wr_reason_sk STRING,
wr_order_number STRING,
wr_return_quantity STRING,
wr_return_amt STRING,
wr_return_tax STRING,
wr_return_amt_inc_tax STRING,
wr_fee STRING,
wr_return_ship_cost STRING,
wr_refunded_cash STRING,
wr_reversed_charge STRING,
wr_account_credit STRING,
wr_net_loss STRING
);

drop table if exists web_sales;
create table web_sales
(
ws_sold_date_sk STRING,
ws_sold_time_sk STRING,
ws_ship_date_sk STRING,
ws_item_sk STRING,
ws_bill_customer_sk STRING,
ws_bill_cdemo_sk STRING,
ws_bill_hdemo_sk STRING,
ws_bill_addr_sk STRING,
ws_ship_customer_sk STRING,
ws_ship_cdemo_sk STRING,
ws_ship_hdemo_sk STRING,
ws_ship_addr_sk STRING,
ws_web_page_sk STRING,
ws_web_site_sk STRING,
ws_ship_mode_sk STRING,
ws_warehouse_sk STRING,
ws_promo_sk STRING,
ws_order_number STRING,
ws_quantity STRING,
ws_wholesale_cost STRING,
ws_list_price STRING,
ws_sales_price STRING,
ws_ext_discount_amt STRING,
ws_ext_sales_price STRING,
ws_ext_wholesale_cost STRING,
ws_ext_list_price STRING,
ws_ext_tax STRING,
ws_coupon_amt STRING,
ws_ext_ship_cost STRING,
ws_net_paid STRING,
ws_net_paid_inc_tax STRING,
ws_net_paid_inc_ship STRING,
ws_net_paid_inc_ship_tax STRING,
ws_net_profit STRING
);

drop table if exists web_site;
create table web_site
(
web_site_sk STRING,
web_site_id STRING,
web_rec_start_date STRING,
web_rec_end_date STRING,
web_name STRING,
web_open_date_sk STRING,
web_close_date_sk STRING,
web_class STRING,
web_manager STRING,
web_mkt_id STRING,
web_mkt_class STRING,
web_mkt_desc STRING,
web_market_manager STRING,
web_company_id STRING,
web_company_name STRING,
web_street_number STRING,
web_street_name STRING,
web_street_type STRING,
web_suite_number STRING,
web_city STRING,
web_county STRING,
web_state STRING,
web_zip STRING,
web_country STRING,
web_gmt_offset STRING,
web_tax_percentage STRING
);
