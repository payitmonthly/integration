---
layout: "v1"
toc: toc.html
---

# PayItMonthly Simple Integration

***We recommend that you use either [PayByLink](https://payitmonthly.uk/blog/news/introudcing-paybylink/) or [our API Integration](https://developer.payitmonthly.uk/) as they have more features and are more secure.***

PayItMonthly enables your business to offer your customers finance.

This guide shows you how to embed our simple integration within your website.

## Support

If you need to contact us for any reason, you can email us at [support@payitmonthly.uk](mailto:support@payitmonthly.uk) or call us on 0333 212 3914.

## Document History

***23/09/2026***

1. Updated the form submission URL and method.

***v1.1*** (26/06/2020)

1. Redirect URLs added.

***v1.0.0*** (30/05/2017)

1. First integration launched.

## Getting Started

You need to have opened an account with [PayItMonthly](https://payitmonthly.uk). Once you have opened your account, you can create a Simple Integration API key [here](https://app.payitmonthly.uk/partner/admin/developers). If you have any problems creating your API key, you can email us at [support@payitmonthly.uk](mailto:support@payitmonthly.uk).

## Updating an Existing Integration

If your form uses the old integration URL, you only need to make these two changes:

- Change `action="https://payitmonthly.uk/simple-integration/"` to `action="https://app.payitmonthly.uk/simple-integration"`.
- Change `method="post"` to `method="get"`.

Keep your existing API key and all other form values unchanged.

## HTML Form Based Application

Replace the example `identification_key` below with your own Simple Integration API key, and update the goods description, price and deposit to match the purchase.

Prices and deposits must be supplied in pence. In this example, the goods cost £600 and the deposit is £60.

```html
<form action="https://app.payitmonthly.uk/simple-integration" method="get">
    <input type="hidden" name="identification_key" value="YOUR_SIMPLE_INTEGRATION_API_KEY"/>
    <input type="hidden" name="goods_description" value="Photos - CD - Gold Package"/>
    <input type="hidden" name="goods_price" value="60000"/>
    <input type="hidden" name="finance_deposit_total" value="6000"/>
    <input type="hidden" name="test_or_live" value="test"/>
    <input type="submit" value="PayItMonthly"/>
</form>
```

Use `test_or_live="test"` while testing. When you are ready to accept live applications, change the value to `live`.

## Parameters

Name | Description | Required | Type | Validation
-----|-------------|----------|------|-----------
identification_key | Public API key | Yes | string |
test_or_live | This specifies which mode to operate the system in | Yes | string | 'test' or 'live'
goods_description | Description of the goods/service that the customer is purchasing. This will be shown on the customer's agreement | Yes | string |
goods_price | Price of the goods/service that the customer is purchasing in pence before the deposit is taken. The value of finance required is calculated automatically (goods_price - finance_deposit_total) | Yes | int | Positive integer between 1200 and 1000000
finance_deposit_total | Total deposit paid/to be paid by the customer in pence. This is not collected by PayItMonthly | Yes | int | Integer between 0 and 1000000
finance_number_of_instalments | Number of instalments that the customer will pay — do not include the deposit as an instalment | No | int | Between 2 and 12
finance_max_duration | Maximum number of instalments/months that the customer can choose if you want it to be less than 12. This value is not used if the number of instalments is set | No | int | Between 2 and 12
customer_title | Customer's title | No | string | Either 'Mr.', 'Mrs.', 'Miss.', 'Ms.' or 'Dr.'
customer_firstname | Customer's first name | No | string |
customer_middle_name | Customer's middle name | No | string |
customer_surname | Customer's surname | No | string |
customer_mobile | Customer's mobile number | No | string |
customer_landline | Customer's landline | No | string |
customer_email | Customer's email address | No | string |
customer_address_line_1 | House number/name | No | string |
customer_address_line_2 | Street address | No | string |
customer_address_line_3 | Town | No | string |
customer_address_line_4 | County | No | string |
customer_address_postcode | Postcode | No | string |
redirecturl_pass | URL the customer returns to if they are accepted for credit | No | string |
redirecturl_fail | URL the customer returns to if they are declined credit | No | string |
redirecturl_refer | URL the customer returns to if they are referred for a manual check | No | string |

Please note that if the address or contact details are not valid, we will not pre-populate the form with that information. The customer will need to enter those details into our form.

### Test Bank Details

Please use the following bank details when completing an agreement in test mode.

Sort Code | Account Number
----------|--------------------
***20-00-00*** | ***55779911***

## Notifications

Once the customer has entered into the agreement, you will receive an email at the address associated with your account, with a link to view the details provided.
