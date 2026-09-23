---
layout: "v1"
toc: toc.html
---

# PayItMonthly Simple Integration

***We recommend that you use either [PayByLink](https://payitmonthly.uk/blog/news/introudcing-paybylink/) or [our API Integration](https://developer.payitmonthly.uk/) as they have more features and are more secure.***

PayItMonthly enables your business to offer your customer finance. 

This guide shows you how to embed our simple integration within your website.

## Support

If you need to contact us for any reason you can email us at [support@payitmonthly.uk](mailto:support@payitmonthly.uk) or call us on 0333 212 3914.

## Document History

***v1.1*** (26/06/2020)

1. Redirect URLs added

***v1.0.0*** (30/05/2017)

1. First integration launched

## Getting Started

You need to have opened an account with [PayItMonthly](https://payitmonthly.uk). Once you have opened your account you can create a Simple Integration API key [here](https://app.payitmonthly.uk/partner/admin/developers). If you have any problems creating your API key you can email us [support@payitmonthly.uk](mailto:support@payitmonthly.uk).

## HTML Form Based Application

```markdown
<form action="https://app.payitmonthly.uk/simple-integration" method="get"> 
    <input type="hidden" name="identification_key" value="adfwt2894ahgBUDSFOHE8we9"/>
    <input type="hidden" name="goods_description" value="Photos - CD - Gold Package"/> 
    <input type="hidden" name="goods_price" value="60000"/> 
    <input type="hidden" name="finance_deposit_total" value="6000"/> 
    <input type="hidden" name="test_or_live" value="test"/>
    <input type="submit" value="PayItMonthly"/>
</form>
```

## Parameters

Name | Description | Required | Type | Validation
-----|-------------|----------|------|-----------
identification_key | Public API key | Yes | string | 
identification_version | Integration version number | Yes | string |
test_or_live | This specifies which mode to operate the system in | Yes | string | test' or 'live'
goods_description | Description of the goods/service that the customer is purchasing. This will be shown on the customers agreement | Yes | string | 
goods_price | Price of the goods/service that the customer is purchasing in pence before the deposit is taken. The value of finance required is calculated automatically (goods_price - finance_deposit_total) | Yes | int | Positive integer between 1200 and 1000000 
finance_deposit_total | Total deposit paid/to be paid by the customer in pence. This is not collected by PayItMonthly | Yes | int | Positive integer between 0 and 1000000
finance_number_of_instalments | Number of instalments that the customer will pay - do not include the deposit as an instalment | No | int | Between 2-12
finance_max_duration | Maximum number of instalments/months that the customer can choose if you want it to be less than 12. This value is not used if the number of instalments is set | No | int | Between 2-12
customer_title | Customers title | No | string | Either 'Mr.', 'Mrs.', 'Miss.', 'Ms.' or 'Dr.'
customer_firstname | Customers firstname | No | string | 
customer_middle_name | Customers middle name | No | string | 
customer_surname | Customers surname | No | string | 
customer_mobile | Customers mobile number | No | string | 
customer_landline | Customers landline | No | string | 
customer_email | Customers email address | No | string | 
customer_address_line_1 | House Number/Name | No | string | 
customer_address_line_2 | Street Address | No | string | 
customer_address_line_3 | Town | No | string | 
customer_address_line_4 | County | No | string | 
customer_address_postcode | Postcode | No | string | 
redirecturl_pass | URL customer returns to if they are accepted for credit | No | string | 
redirecturl_fail | URL customer returns to if they are declined credit | No | string | 
redirecturl_refer | URL customer returns to if they are refered for a manual check | No | string | 

Please note that if the address or contact details are not valid we will not pre-populate the form with the information and the customer will need to input them into our form.

### Test Bank Details

Please use the following bank details when completeing an agreement in test mode.

Sort Code | Account Number
----------|--------------------
***20-00-00*** | ***55779911***

## Notifications

Once the customer has entered into the agreement you will receive an email to the address associated with your account with a link so that you can see the details that have been provided.
