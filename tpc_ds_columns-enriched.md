--Create table
drop table if exists call_center;
create table call_center
(
CAST(cc_call_center_sk AS INTEGER) AS cc_call_center_sk,
CAST(cc_call_center_id AS STRING) AS cc_call_center_id,
CAST(cc_rec_start_date AS DATE) AS cc_rec_start_date,
CAST(cc_rec_end_date AS DATE) AS cc_rec_end_date,
CAST(cc_closed_date_sk AS INTEGER) AS cc_closed_date_sk,
CAST(cc_open_date_sk AS INTEGER) AS cc_open_date_sk,
CAST(cc_name AS STRING) AS cc_name,
CAST(cc_class AS STRING) AS cc_class,
CAST(cc_employees AS INTEGER) AS cc_employees,
CAST(cc_sq_ft AS INTEGER) AS cc_sq_ft,
CAST(cc_hours AS STRING) AS cc_hours,
CAST(cc_manager AS STRING) AS cc_manager,
CAST(cc_mkt_id AS INTEGER) AS cc_mkt_id,
CAST(cc_mkt_class AS STRING) AS cc_mkt_class,
CAST(cc_mkt_desc AS STRING) AS cc_mkt_desc,
CAST(cc_market_manager AS STRING) AS cc_market_manager,
CAST(cc_division AS INTEGER) AS cc_division,
CAST(cc_division_name AS STRING) AS cc_division_name,
CAST(cc_company AS INTEGER) AS cc_company,
CAST(cc_company_name AS STRING) AS cc_company_name,
CAST(cc_street_number AS STRING) AS cc_street_number,
CAST(cc_street_name AS STRING) AS cc_street_name,
CAST(cc_street_type AS STRING) AS cc_street_type,
CAST(cc_suite_number AS STRING) AS cc_suite_number,
CAST(cc_city AS STRING) AS cc_city,
CAST(cc_county AS STRING) AS cc_county,
CAST(cc_state AS STRING) AS cc_state,
CAST(cc_zip AS STRING) AS cc_zip,
CAST(cc_country AS STRING) AS cc_country,
CAST(cc_gmt_offset AS NUMERIC) AS cc_gmt_offset,
CAST(cc_tax_percentage AS NUMERIC) AS cc_tax_percentage

);

drop table if exists catalog_page;
create table catalog_page
(
CAST(cp_catalog_page_sk AS INTEGER) AS cp_catalog_page_sk,
CAST(cp_catalog_page_id AS STRING) AS cp_catalog_page_id,
CAST(cp_start_date_sk AS INTEGER) AS cp_start_date_sk,
CAST(cp_end_date_sk AS INTEGER) AS cp_end_date_sk,
CAST(cp_department AS STRING) AS cp_department,
CAST(cp_catalog_number AS INTEGER) AS cp_catalog_number,
CAST(cp_catalog_page_number AS INTEGER) AS cp_catalog_page_number,
CAST(cp_description AS STRING) AS cp_description,
CAST(cp_type AS STRING) AS cp_type

);

drop table if exists catalog_returns;
create table catalog_returns
(
CAST(cr_returned_date_sk AS INTEGER) AS cr_returned_date_sk,
CAST(cr_returned_time_sk AS INTEGER) AS cr_returned_time_sk,
CAST(cr_item_sk AS INTEGER) AS cr_item_sk,
CAST(cr_refunded_customer_sk AS INTEGER) AS cr_refunded_customer_sk,
CAST(cr_refunded_cdemo_sk AS INTEGER) AS cr_refunded_cdemo_sk,
CAST(cr_refunded_hdemo_sk AS INTEGER) AS cr_refunded_hdemo_sk,
CAST(cr_refunded_addr_sk AS INTEGER) AS cr_refunded_addr_sk,
CAST(cr_returning_customer_sk AS INTEGER) AS cr_returning_customer_sk,
CAST(cr_returning_cdemo_sk AS INTEGER) AS cr_returning_cdemo_sk,
CAST(cr_returning_hdemo_sk AS INTEGER) AS cr_returning_hdemo_sk,
CAST(cr_returning_addr_sk AS INTEGER) AS cr_returning_addr_sk,
CAST(cr_call_center_sk AS INTEGER) AS cr_call_center_sk,
CAST(cr_catalog_page_sk AS INTEGER) AS cr_catalog_page_sk,
CAST(cr_ship_mode_sk AS INTEGER) AS cr_ship_mode_sk,
CAST(cr_warehouse_sk AS INTEGER) AS cr_warehouse_sk,
CAST(cr_reason_sk AS INTEGER) AS cr_reason_sk,
CAST(cr_order_number AS INTEGER) AS cr_order_number,
CAST(cr_return_quantity AS INTEGER) AS cr_return_quantity,
CAST(cr_return_amount AS NUMERIC) AS cr_return_amount,
CAST(cr_return_tax AS NUMERIC) AS cr_return_tax,
CAST(cr_return_amt_inc_tax AS NUMERIC) AS cr_return_amt_inc_tax,
CAST(cr_fee AS NUMERIC) AS cr_fee,
CAST(cr_return_ship_cost AS NUMERIC) AS cr_return_ship_cost,
CAST(cr_refunded_cash AS NUMERIC) AS cr_refunded_cash,
CAST(cr_reversed_charge AS NUMERIC) AS cr_reversed_charge,
CAST(cr_store_credit AS NUMERIC) AS cr_store_credit,
CAST(cr_net_loss AS NUMERIC) AS cr_net_loss

);


drop table if exists catalog_sales;
create table catalog_sales
(
CAST(cs_sold_date_sk AS INTEGER) AS cs_sold_date_sk,
CAST(cs_sold_time_sk AS INTEGER) AS cs_sold_time_sk,
CAST(cs_ship_date_sk AS INTEGER) AS cs_ship_date_sk,
CAST(cs_bill_customer_sk AS INTEGER) AS cs_bill_customer_sk,
CAST(cs_bill_cdemo_sk AS INTEGER) AS cs_bill_cdemo_sk,
CAST(cs_bill_hdemo_sk AS INTEGER) AS cs_bill_hdemo_sk,
CAST(cs_bill_addr_sk AS INTEGER) AS cs_bill_addr_sk,
CAST(cs_ship_customer_sk AS INTEGER) AS cs_ship_customer_sk,
CAST(cs_ship_cdemo_sk AS INTEGER) AS cs_ship_cdemo_sk,
CAST(cs_ship_hdemo_sk AS INTEGER) AS cs_ship_hdemo_sk,
CAST(cs_ship_addr_sk AS INTEGER) AS cs_ship_addr_sk,
CAST(cs_call_center_sk AS INTEGER) AS cs_call_center_sk,
CAST(cs_catalog_page_sk AS INTEGER) AS cs_catalog_page_sk,
CAST(cs_ship_mode_sk AS INTEGER) AS cs_ship_mode_sk,
CAST(cs_warehouse_sk AS INTEGER) AS cs_warehouse_sk,
CAST(cs_item_sk AS INTEGER) AS cs_item_sk,
CAST(cs_promo_sk AS INTEGER) AS cs_promo_sk,
CAST(cs_order_number AS INTEGER) AS cs_order_number,
CAST(cs_quantity AS INTEGER) AS cs_quantity,
CAST(cs_wholesale_cost AS NUMERIC) AS cs_wholesale_cost,
CAST(cs_list_price AS NUMERIC) AS cs_list_price,
CAST(cs_sales_price AS NUMERIC) AS cs_sales_price,
CAST(cs_ext_discount_amt AS NUMERIC) AS cs_ext_discount_amt,
CAST(cs_ext_sales_price AS NUMERIC) AS cs_ext_sales_price,
CAST(cs_ext_wholesale_cost AS NUMERIC) AS cs_ext_wholesale_cost,
CAST(cs_ext_list_price AS NUMERIC) AS cs_ext_list_price,
CAST(cs_ext_tax AS NUMERIC) AS cs_ext_tax,
CAST(cs_coupon_amt AS NUMERIC) AS cs_coupon_amt,
CAST(cs_ext_ship_cost AS NUMERIC) AS cs_ext_ship_cost,
CAST(cs_net_paid AS NUMERIC) AS cs_net_paid,
CAST(cs_net_paid_inc_tax AS NUMERIC) AS cs_net_paid_inc_tax,
CAST(cs_net_paid_inc_ship AS NUMERIC) AS cs_net_paid_inc_ship,
CAST(cs_net_paid_inc_ship_tax AS NUMERIC) AS cs_net_paid_inc_ship_tax,
CAST(cs_net_profit AS NUMERIC) AS cs_net_profit

);

drop table if exists customer;
create table customer
(
CAST(c_customer_sk AS INTEGER) AS c_customer_sk,
CAST(c_customer_id AS STRING) AS c_customer_id,
CAST(c_current_cdemo_sk AS INTEGER) AS c_current_cdemo_sk,
CAST(c_current_hdemo_sk AS INTEGER) AS c_current_hdemo_sk,
CAST(c_current_addr_sk AS INTEGER) AS c_current_addr_sk,
CAST(c_first_shipto_date_sk AS INTEGER) AS c_first_shipto_date_sk,
CAST(c_first_sales_date_sk AS INTEGER) AS c_first_sales_date_sk,
CAST(c_salutation AS STRING) AS c_salutation,
CAST(c_first_name AS STRING) AS c_first_name,
CAST(c_last_name AS STRING) AS c_last_name,
CAST(c_preferred_cust_flag AS STRING) AS c_preferred_cust_flag,
CAST(c_birth_day AS INTEGER) AS c_birth_day,
CAST(c_birth_month AS INTEGER) AS c_birth_month,
CAST(c_birth_year AS INTEGER) AS c_birth_year,
CAST(c_birth_country AS STRING) AS c_birth_country,
CAST(c_login AS STRING) AS c_login,
CAST(c_email_address AS STRING) AS c_email_address,
CAST(c_last_review_date AS STRING) AS c_last_review_date

);


drop table if exists customer_address;
create table customer_address
(
CAST(ca_address_sk AS INTEGER) AS ca_address_sk,
CAST(ca_address_id AS STRING) AS ca_address_id,
CAST(ca_street_number AS STRING) AS ca_street_number,
CAST(ca_street_name AS STRING) AS ca_street_name,
CAST(ca_street_type AS STRING) AS ca_street_type,
CAST(ca_suite_number AS STRING) AS ca_suite_number,
CAST(ca_city AS STRING) AS ca_city,
CAST(ca_county AS STRING) AS ca_county,
CAST(ca_state AS STRING) AS ca_state,
CAST(ca_zip AS STRING) AS ca_zip,
CAST(ca_country AS STRING) AS ca_country,
CAST(ca_gmt_offset AS NUMERIC) AS ca_gmt_offset,
CAST(ca_location_type AS STRING) AS ca_location_type

);

drop table if exists customer_demographics;
create table customer_demographics
(
CAST(cd_demo_sk AS INTEGER) AS cd_demo_sk,
CAST(cd_gender AS STRING) AS cd_gender,
CAST(cd_marital_status AS STRING) AS cd_marital_status,
CAST(cd_education_status AS STRING) AS cd_education_status,
CAST(cd_purchase_estimate AS INTEGER) AS cd_purchase_estimate,
CAST(cd_credit_rating AS STRING) AS cd_credit_rating,
CAST(cd_dep_count AS INTEGER) AS cd_dep_count,
CAST(cd_dep_employed_count AS INTEGER) AS cd_dep_employed_count,
CAST(cd_dep_college_count AS INTEGER) AS cd_dep_college_count

);

drop table if exists date_dim;
create table date_dim
(
CAST(d_date_sk AS INTEGER) AS d_date_sk,
CAST(d_date_id AS STRING) AS d_date_id,
CAST(d_date AS STRING) AS d_date,
CAST(d_month_seq AS INTEGER) AS d_month_seq,
CAST(d_week_seq AS INTEGER) AS d_week_seq,
CAST(d_quarter_seq AS INTEGER) AS d_quarter_seq,
CAST(d_year AS INTEGER) AS d_year,
CAST(d_dow AS INTEGER) AS d_dow,
CAST(d_moy AS INTEGER) AS d_moy,
CAST(d_dom AS INTEGER) AS d_dom,
CAST(d_qoy AS INTEGER) AS d_qoy,
CAST(d_fy_year AS INTEGER) AS d_fy_year,
CAST(d_fy_quarter_seq AS INTEGER) AS d_fy_quarter_seq,
CAST(d_fy_week_seq AS INTEGER) AS d_fy_week_seq,
CAST(d_day_name AS STRING) AS d_day_name,
CAST(d_quarter_name AS STRING) AS d_quarter_name,
CAST(d_holiday AS STRING) AS d_holiday,
CAST(d_weekend AS STRING) AS d_weekend,
CAST(d_following_holiday AS STRING) AS d_following_holiday,
CAST(d_first_dom AS INTEGER) AS d_first_dom,
CAST(d_last_dom AS INTEGER) AS d_last_dom,
CAST(d_same_day_ly AS INTEGER) AS d_same_day_ly,
CAST(d_same_day_lq AS INTEGER) AS d_same_day_lq,
CAST(d_current_day AS STRING) AS d_current_day,
CAST(d_current_week AS STRING) AS d_current_week,
CAST(d_current_month AS STRING) AS d_current_month,
CAST(d_current_quarter AS STRING) AS d_current_quarter,
CAST(d_current_year AS STRING) AS d_current_year

);

drop table if exists household_demographics;
create table household_demographics
(
CAST(hd_demo_sk AS INTEGER) AS hd_demo_sk,
CAST(hd_income_band_sk AS INTEGER) AS hd_income_band_sk,
CAST(hd_buy_potential AS STRING) AS hd_buy_potential,
CAST(hd_dep_count AS INTEGER) AS hd_dep_count,
CAST(hd_vehicle_count AS INTEGER) AS hd_vehicle_count

);

drop table if exists income_band;
create table income_band
(
CAST(ib_income_band_sk AS INTEGER) AS ib_income_band_sk,
CAST(ib_lower_bound AS INTEGER) AS ib_lower_bound,
CAST(ib_upper_bound AS INTEGER) AS ib_upper_bound

);

drop table if exists inventory;
create table inventory
(
CAST(inv_date_sk AS INTEGER) AS inv_date_sk,
CAST(inv_item_sk AS INTEGER) AS inv_item_sk,
CAST(inv_warehouse_sk AS INTEGER) AS inv_warehouse_sk,
CAST(inv_quantity_on_hand AS INTEGER) AS inv_quantity_on_hand

);

drop table if exists item;
create table item
(
CAST(i_item_sk AS INTEGER) AS i_item_sk,
CAST(i_item_id AS STRING) AS i_item_id,
CAST(i_rec_start_date AS STRING) AS i_rec_start_date,
CAST(i_rec_end_date AS STRING) AS i_rec_end_date,
CAST(i_item_desc AS STRING) AS i_item_desc,
CAST(i_current_price AS NUMERIC) AS i_current_price,
CAST(i_wholesale_cost AS NUMERIC) AS i_wholesale_cost,
CAST(i_brand_id AS INTEGER) AS i_brand_id,
CAST(i_brand AS STRING) AS i_brand,
CAST(i_class_id AS INTEGER) AS i_class_id,
CAST(i_class AS STRING) AS i_class,
CAST(i_category_id AS INTEGER) AS i_category_id,
CAST(i_category AS STRING) AS i_category,
CAST(i_manufact_id AS INTEGER) AS i_manufact_id,
CAST(i_manufact AS STRING) AS i_manufact,
CAST(i_size AS STRING) AS i_size,
CAST(i_formulation AS STRING) AS i_formulation,
CAST(i_color AS STRING) AS i_color,
CAST(i_units AS STRING) AS i_units,
CAST(i_container AS STRING) AS i_container,
CAST(i_manager_id AS INTEGER) AS i_manager_id,
CAST(i_product_name AS STRING) AS i_product_name

);

drop table if exists promotion;
create table promotion
(
CAST(p_promo_sk AS INTEGER) AS p_promo_sk,
CAST(p_promo_id AS STRING) AS p_promo_id,
CAST(p_start_date_sk AS INTEGER) AS p_start_date_sk,
CAST(p_end_date_sk AS INTEGER) AS p_end_date_sk,
CAST(p_item_sk AS INTEGER) AS p_item_sk,
CAST(p_cost AS NUMERIC) AS p_cost,
CAST(p_response_target AS INTEGER) AS p_response_target,
CAST(p_promo_name AS STRING) AS p_promo_name,
CAST(p_channel_dmail AS STRING) AS p_channel_dmail,
CAST(p_channel_email AS STRING) AS p_channel_email,
CAST(p_channel_catalog AS STRING) AS p_channel_catalog,
CAST(p_channel_tv AS STRING) AS p_channel_tv,
CAST(p_channel_radio AS STRING) AS p_channel_radio,
CAST(p_channel_press AS STRING) AS p_channel_press,
CAST(p_channel_event AS STRING) AS p_channel_event,
CAST(p_channel_demo AS STRING) AS p_channel_demo,
CAST(p_channel_details AS STRING) AS p_channel_details,
CAST(p_purpose AS STRING) AS p_purpose,
CAST(p_discount_active AS STRING) AS p_discount_active

);

drop table if exists reason;
create table reason
(
CAST(r_reason_sk AS INTEGER) AS r_reason_sk,
CAST(r_reason_id AS STRING) AS r_reason_id,
CAST(r_reason_desc AS STRING) AS r_reason_desc

);

drop table if exists ship_mode;
create table ship_mode
(
CAST(sm_ship_mode_sk AS INTEGER) AS sm_ship_mode_sk,
CAST(sm_ship_mode_id AS STRING) AS sm_ship_mode_id,
CAST(sm_type AS STRING) AS sm_type,
CAST(sm_code AS STRING) AS sm_code,
CAST(sm_carrier AS STRING) AS sm_carrier,
CAST(sm_contract AS STRING) AS sm_contract

);

drop table if exists store;
create table store
(
CAST(s_store_sk AS INTEGER) AS s_store_sk,
CAST(s_store_id AS STRING) AS s_store_id,
CAST(s_rec_start_date AS STRING) AS s_rec_start_date,
CAST(s_rec_end_date AS STRING) AS s_rec_end_date,
CAST(s_closed_date_sk AS INTEGER) AS s_closed_date_sk,
CAST(s_store_name AS STRING) AS s_store_name,
CAST(s_number_employees AS INTEGER) AS s_number_employees,
CAST(s_floor_space AS INTEGER) AS s_floor_space,
CAST(s_hours AS STRING) AS s_hours,
CAST(s_manager AS STRING) AS s_manager,
CAST(s_market_id AS INTEGER) AS s_market_id,
CAST(s_geography_class AS STRING) AS s_geography_class,
CAST(s_market_desc AS STRING) AS s_market_desc,
CAST(s_market_manager AS STRING) AS s_market_manager,
CAST(s_division_id AS INTEGER) AS s_division_id,
CAST(s_division_name AS STRING) AS s_division_name,
CAST(s_company_id AS INTEGER) AS s_company_id,
CAST(s_company_name AS STRING) AS s_company_name,
CAST(s_street_number AS STRING) AS s_street_number,
CAST(s_street_name AS STRING) AS s_street_name,
CAST(s_street_type AS STRING) AS s_street_type,
CAST(s_suite_number AS STRING) AS s_suite_number,
CAST(s_city AS STRING) AS s_city,
CAST(s_county AS STRING) AS s_county,
CAST(s_state AS STRING) AS s_state,
CAST(s_zip AS STRING) AS s_zip,
CAST(s_country AS STRING) AS s_country,
CAST(s_gmt_offset AS NUMERIC) AS s_gmt_offset,
CAST(s_tax_precentage AS NUMERIC) AS s_tax_precentage

);

drop table if exists store_returns;
create table store_returns
(
CAST(sr_returned_date_sk AS INTEGER) AS sr_returned_date_sk,
CAST(sr_return_time_sk AS INTEGER) AS sr_return_time_sk,
CAST(sr_item_sk AS INTEGER) AS sr_item_sk,
CAST(sr_customer_sk AS INTEGER) AS sr_customer_sk,
CAST(sr_cdemo_sk AS INTEGER) AS sr_cdemo_sk,
CAST(sr_hdemo_sk AS INTEGER) AS sr_hdemo_sk,
CAST(sr_addr_sk AS INTEGER) AS sr_addr_sk,
CAST(sr_store_sk AS INTEGER) AS sr_store_sk,
CAST(sr_reason_sk AS INTEGER) AS sr_reason_sk,
CAST(sr_ticket_number AS INTEGER) AS sr_ticket_number,
CAST(sr_return_quantity AS INTEGER) AS sr_return_quantity,
CAST(sr_return_amt AS NUMERIC) AS sr_return_amt,
CAST(sr_return_tax AS NUMERIC) AS sr_return_tax,
CAST(sr_return_amt_inc_tax AS NUMERIC) AS sr_return_amt_inc_tax,
CAST(sr_fee AS NUMERIC) AS sr_fee,
CAST(sr_return_ship_cost AS NUMERIC) AS sr_return_ship_cost,
CAST(sr_refunded_cash AS NUMERIC) AS sr_refunded_cash,
CAST(sr_reversed_charge AS NUMERIC) AS sr_reversed_charge,
CAST(sr_store_credit AS NUMERIC) AS sr_store_credit,
CAST(sr_net_loss AS NUMERIC) AS sr_net_loss

);

drop table if exists store_sales;
create table store_sales
(
CAST(ss_sold_date_sk AS INTEGER) AS ss_sold_date_sk,
CAST(ss_sold_time_sk AS INTEGER) AS ss_sold_time_sk,
CAST(ss_item_sk AS INTEGER) AS ss_item_sk,
CAST(ss_customer_sk AS INTEGER) AS ss_customer_sk,
CAST(ss_cdemo_sk AS INTEGER) AS ss_cdemo_sk,
CAST(ss_hdemo_sk AS INTEGER) AS ss_hdemo_sk,
CAST(ss_addr_sk AS INTEGER) AS ss_addr_sk,
CAST(ss_store_sk AS INTEGER) AS ss_store_sk,
CAST(ss_promo_sk AS INTEGER) AS ss_promo_sk,
CAST(ss_ticket_number AS INTEGER) AS ss_ticket_number,
CAST(ss_quantity AS INTEGER) AS ss_quantity,
CAST(ss_wholesale_cost AS NUMERIC) AS ss_wholesale_cost,
CAST(ss_list_price AS NUMERIC) AS ss_list_price,
CAST(ss_sales_price AS NUMERIC) AS ss_sales_price,
CAST(ss_ext_discount_amt AS NUMERIC) AS ss_ext_discount_amt,
CAST(ss_ext_sales_price AS NUMERIC) AS ss_ext_sales_price,
CAST(ss_ext_wholesale_cost AS NUMERIC) AS ss_ext_wholesale_cost,
CAST(ss_ext_list_price AS NUMERIC) AS ss_ext_list_price,
CAST(ss_ext_tax AS NUMERIC) AS ss_ext_tax,
CAST(ss_coupon_amt AS NUMERIC) AS ss_coupon_amt,
CAST(ss_net_paid AS NUMERIC) AS ss_net_paid,
CAST(ss_net_paid_inc_tax AS NUMERIC) AS ss_net_paid_inc_tax,
CAST(ss_net_profit AS NUMERIC) AS ss_net_profit

);

drop table if exists time_dim;
create table time_dim
(
CAST(t_time_sk AS INTEGER) AS t_time_sk,
CAST(t_time_id AS STRING) AS t_time_id,
CAST(t_time AS INTEGER) AS t_time,
CAST(t_hour AS INTEGER) AS t_hour,
CAST(t_minute AS INTEGER) AS t_minute,
CAST(t_second AS INTEGER) AS t_second,
CAST(t_am_pm AS STRING) AS t_am_pm,
CAST(t_shift AS STRING) AS t_shift,
CAST(t_sub_shift AS STRING) AS t_sub_shift,
CAST(t_meal_time AS STRING) AS t_meal_time



drop table if exists warehouse;
create table warehouse
(
CAST(w_warehouse_sk AS INTEGER) AS w_warehouse_sk,
CAST(w_warehouse_id AS STRING) AS w_warehouse_id,
CAST(w_warehouse_name AS STRING) AS w_warehouse_name,
CAST(w_warehouse_sq_ft AS INTEGER) AS w_warehouse_sq_ft,
CAST(w_street_number AS STRING) AS w_street_number,
CAST(w_street_name AS STRING) AS w_street_name,
CAST(w_street_type AS STRING) AS w_street_type,
CAST(w_suite_number AS STRING) AS w_suite_number,
CAST(w_city AS STRING) AS w_city,
CAST(w_county AS STRING) AS w_county,
CAST(w_state AS STRING) AS w_state,
CAST(w_zip AS STRING) AS w_zip,
CAST(w_country AS STRING) AS w_country,
CAST(w_gmt_offset AS NUMERIC) AS w_gmt_offset

);

drop table if exists web_page;
create table web_page
(
CAST(wp_web_page_sk AS INTEGER) AS wp_web_page_sk,
CAST(wp_web_page_id AS STRING) AS wp_web_page_id,
CAST(wp_rec_start_date AS STRING) AS wp_rec_start_date,
CAST(wp_rec_end_date AS STRING) AS wp_rec_end_date,
CAST(wp_creation_date_sk AS INTEGER) AS wp_creation_date_sk,
CAST(wp_access_date_sk AS INTEGER) AS wp_access_date_sk,
CAST(wp_autogen_flag AS STRING) AS wp_autogen_flag,
CAST(wp_customer_sk AS INTEGER) AS wp_customer_sk,
CAST(wp_url AS STRING) AS wp_url,
CAST(wp_type AS STRING) AS wp_type,
CAST(wp_char_count AS INTEGER) AS wp_char_count,
CAST(wp_link_count AS INTEGER) AS wp_link_count,
CAST(wp_image_count AS INTEGER) AS wp_image_count,
CAST(wp_max_ad_count AS INTEGER) AS wp_max_ad_count

);

drop table if exists web_returns;
create table web_returns
(
CAST(wr_returned_date_sk AS INTEGER) AS wr_returned_date_sk,
CAST(wr_returned_time_sk AS INTEGER) AS wr_returned_time_sk,
CAST(wr_item_sk AS INTEGER) AS wr_item_sk,
CAST(wr_refunded_customer_sk AS INTEGER) AS wr_refunded_customer_sk,
CAST(wr_refunded_cdemo_sk AS INTEGER) AS wr_refunded_cdemo_sk,
CAST(wr_refunded_hdemo_sk AS INTEGER) AS wr_refunded_hdemo_sk,
CAST(wr_refunded_addr_sk AS INTEGER) AS wr_refunded_addr_sk,
CAST(wr_returning_customer_sk AS INTEGER) AS wr_returning_customer_sk,
CAST(wr_returning_cdemo_sk AS INTEGER) AS wr_returning_cdemo_sk,
CAST(wr_returning_hdemo_sk AS INTEGER) AS wr_returning_hdemo_sk,
CAST(wr_returning_addr_sk AS INTEGER) AS wr_returning_addr_sk,
CAST(wr_web_page_sk AS INTEGER) AS wr_web_page_sk,
CAST(wr_reason_sk AS INTEGER) AS wr_reason_sk,
CAST(wr_order_number AS INTEGER) AS wr_order_number,
CAST(wr_return_quantity AS INTEGER) AS wr_return_quantity,
CAST(wr_return_amt AS NUMERIC) AS wr_return_amt,
CAST(wr_return_tax AS NUMERIC) AS wr_return_tax,
CAST(wr_return_amt_inc_tax AS NUMERIC) AS wr_return_amt_inc_tax,
CAST(wr_fee AS NUMERIC) AS wr_fee,
CAST(wr_return_ship_cost AS NUMERIC) AS wr_return_ship_cost,
CAST(wr_refunded_cash AS NUMERIC) AS wr_refunded_cash,
CAST(wr_reversed_charge AS NUMERIC) AS wr_reversed_charge,
CAST(wr_account_credit AS NUMERIC) AS wr_account_credit,
CAST(wr_net_loss AS NUMERIC) AS wr_net_loss

);

drop table if exists web_sales;
create table web_sales
(
CAST(ws_sold_date_sk AS INTEGER) AS ws_sold_date_sk,
CAST(ws_sold_time_sk AS INTEGER) AS ws_sold_time_sk,
CAST(ws_ship_date_sk AS INTEGER) AS ws_ship_date_sk,
CAST(ws_item_sk AS INTEGER) AS ws_item_sk,
CAST(ws_bill_customer_sk AS INTEGER) AS ws_bill_customer_sk,
CAST(ws_bill_cdemo_sk AS INTEGER) AS ws_bill_cdemo_sk,
CAST(ws_bill_hdemo_sk AS INTEGER) AS ws_bill_hdemo_sk,
CAST(ws_bill_addr_sk AS INTEGER) AS ws_bill_addr_sk,
CAST(ws_ship_customer_sk AS INTEGER) AS ws_ship_customer_sk,
CAST(ws_ship_cdemo_sk AS INTEGER) AS ws_ship_cdemo_sk,
CAST(ws_ship_hdemo_sk AS INTEGER) AS ws_ship_hdemo_sk,
CAST(ws_ship_addr_sk AS INTEGER) AS ws_ship_addr_sk,
CAST(ws_web_page_sk AS INTEGER) AS ws_web_page_sk,
CAST(ws_web_site_sk AS INTEGER) AS ws_web_site_sk,
CAST(ws_ship_mode_sk AS INTEGER) AS ws_ship_mode_sk,
CAST(ws_warehouse_sk AS INTEGER) AS ws_warehouse_sk,
CAST(ws_promo_sk AS INTEGER) AS ws_promo_sk,
CAST(ws_order_number AS INTEGER) AS ws_order_number,
CAST(ws_quantity AS INTEGER) AS ws_quantity,
CAST(ws_wholesale_cost AS NUMERIC) AS ws_wholesale_cost,
CAST(ws_list_price AS NUMERIC) AS ws_list_price,
CAST(ws_sales_price AS NUMERIC) AS ws_sales_price,
CAST(ws_ext_discount_amt AS NUMERIC) AS ws_ext_discount_amt,
CAST(ws_ext_sales_price AS NUMERIC) AS ws_ext_sales_price,
CAST(ws_ext_wholesale_cost AS NUMERIC) AS ws_ext_wholesale_cost,
CAST(ws_ext_list_price AS NUMERIC) AS ws_ext_list_price,
CAST(ws_ext_tax AS NUMERIC) AS ws_ext_tax,
CAST(ws_coupon_amt AS NUMERIC) AS ws_coupon_amt,
CAST(ws_ext_ship_cost AS NUMERIC) AS ws_ext_ship_cost,
CAST(ws_net_paid AS NUMERIC) AS ws_net_paid,
CAST(ws_net_paid_inc_tax AS NUMERIC) AS ws_net_paid_inc_tax,
CAST(ws_net_paid_inc_ship AS NUMERIC) AS ws_net_paid_inc_ship,
CAST(ws_net_paid_inc_ship_tax AS NUMERIC) AS ws_net_paid_inc_ship_tax,
CAST(ws_net_profit AS NUMERIC) AS ws_net_profit

);

drop table if exists web_site;
create table web_site
(
CAST(web_site_sk AS INTEGER) AS web_site_sk,
CAST(web_site_id AS STRING) AS web_site_id,
CAST(web_rec_start_date AS STRING) AS web_rec_start_date,
CAST(web_rec_end_date AS STRING) AS web_rec_end_date,
CAST(web_name AS STRING) AS web_name,
CAST(web_open_date_sk AS INTEGER) AS web_open_date_sk,
CAST(web_close_date_sk AS INTEGER) AS web_close_date_sk,
CAST(web_class AS STRING) AS web_class,
CAST(web_manager AS STRING) AS web_manager,
CAST(web_mkt_id AS INTEGER) AS web_mkt_id,
CAST(web_mkt_class AS STRING) AS web_mkt_class,
CAST(web_mkt_desc AS STRING) AS web_mkt_desc,
CAST(web_market_manager AS STRING) AS web_market_manager,
CAST(web_company_id AS INTEGER) AS web_company_id,
CAST(web_company_name AS STRING) AS web_company_name,
CAST(web_street_number AS STRING) AS web_street_number,
CAST(web_street_name AS STRING) AS web_street_name,
CAST(web_street_type AS STRING) AS web_street_type,
CAST(web_suite_number AS STRING) AS web_suite_number,
CAST(web_city AS STRING) AS web_city,
CAST(web_county AS STRING) AS web_county,
CAST(web_state AS STRING) AS web_state,
CAST(web_zip AS STRING) AS web_zip,
CAST(web_country AS STRING) AS web_country,
CAST(web_gmt_offset AS NUMERIC) AS web_gmt_offset,
CAST(web_tax_percentage AS NUMERIC) AS web_tax_percentage

);