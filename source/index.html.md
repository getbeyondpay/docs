---
title: Beyond Pay Developer Portal

language_tabs:
  - php
  - csharp: c#
  - java

toc_footers:
  - <a href="https://forms.office.com/Pages/ResponsePage.aspx?id=Q9V6UxGq3USJSkGsz2Jk78Ytw0d6hJlNsDOCAUz-XBhURUJXWFhEMDlDTUs3OVlROEMxOExJQzZGNS4u" class="beyond-button" target="_blank">Get API Keys</a>
  - ______________
  - <a href='https://www.getbeyond.com/' target="_blank">www.getbeyond.com</a>
  - ©2021 Beyond
  - ______________
  - <a href='https://www.getbeyond.com/privacy-policy/' target="_blank">Privacy Policy</a>
  - <a href='https://www.getbeyond.com/ccpa/' target="_blank">CCPA Consumer Privacy</a>

search: true

meta:
  - name: description
    content: Beyond Pay Gateway API Documentation
  - name: keywords
    content: GetBeyond,Beyond,BeyondPay,Gateway,API,Payments,Credit,Debit,Plugin,SDK
---
<a href="#"></a>

Welcome to Beyond Pay: an omnichannel payment suite that enables a secure and embedded payment experience within your solution.

> <a href="https://forms.office.com/Pages/ResponsePage.aspx?id=Q9V6UxGq3USJSkGsz2Jk78Ytw0d6hJlNsDOCAUz-XBhURUJXWFhEMDlDTUs3OVlROEMxOExJQzZGNS4u" target="_blank" class="beyond-button">Get Your Sandbox API Keys</a> and get coding now!

# Integration Options

> Contact us if you have questions or need help: <a href='mailto:BeyondPayIntegrations@getbeyond.com'>BeyondPayIntegrations@getbeyond.com</a>

Whether you have an existing shopping cart or are building a custom integration, we've got you covered!

## Payment Plugins

Why reinvent the wheel? We've done the heavy lifting to build robust integrations to these popular solutions for you: sit back, relax, and plug in!

### WooCommerce

> <a href="https://wordpress.org/plugins/beyond-pay-for-woocommerce" target="_blank" style=>
```
https://wordpress.org/plugins/beyond-pay-for-woocommerce
```
</a>

> <a href="https://github.com/getbeyond/beyondpay_woocommerce" target="_blank">
```
https://github.com/getbeyond/beyondpay_woocommerce
```
</a>

<a href="https://wordpress.org/plugins/beyond-pay-for-woocommerce/"  target="_blank"><img src="/images/256x256_woo_icon.png" width="100" />

Get Beyond Pay for WooCommerce</a>

```html
=== Beyond Pay for WooCommerce ===
Contributors: beyondpay
Tags: credit card, payment, woocommerce, payment gateway, subscriptions, subscription payments, recurring billing
Requires at least: 4.7
Tested up to: 5.7.2
Stable tag: trunk
Requires PHP: 7.0
License: MIT
License URI: https://opensource.org/licenses/MIT
```

Beyond Pay for <a href="woocommerce.com" target="_blank">WooCommerce</a> enables secure payment card acceptance right from within your WooCommerce store. 

- Pre-auth and later capture or instant sale modes
- Secure saving of cards on file
- Refund transactions directly from the Woo Order Details screen
- Integration with <a href="https://woocommerce.com/products/woocommerce-subscriptions/" target="_blank">WooCommerce Subscriptions</a> for recurring billing
- Interchange optimization by defaulting "Level III" data
- Custom CSS styling of the hosted payment fields
- Sandbox mode for development and staging


### Gravity Forms

> <a href="https://wordpress.org/plugins/beyond-pay-for-gravity-forms" target="_blank">
```
https://wordpress.org/plugins/beyond-pay-for-gravity-forms
```
</a>

> <a href="https://github.com/getbeyond/beyondpay_gravityforms" target="_blank">
```
https://github.com/getbeyond/beyondpay_gravityforms
```
</a>

<a href="https://wordpress.org/plugins/beyond-pay-for-gravity-forms/" target="_blank"><img src="/images/256x256_gravity_icon.png" width="100" />

Get Beyond Pay for Gravity Forms</a>

```html
=== Beyond Pay for Gravity Forms ===
Contributors: beyondpay
Tags: credit card, payment, gravity forms, payment gateway, donation
Requires at least: 4.7
Tested up to: 5.8
Stable tag: 1.1.1
Requires PHP: 7.0
License: MIT
License URI: https://opensource.org/licenses/MIT
```

Beyond Pay for <a href="gravityforms.com">Gravity Forms</a> allows you to create customized payment workflows for order checkout, donations, event registrations, and more!

- Define a Gravity Forms "feed" for each payment form
- Accept payment instantly in Sale mode or capture an authorization later from the Gravity Forms "Entries" page
- Interchange optimization by defaulting "Level III" data
- Sandbox mode for development and staging

## Payment SDKs

We offer several client libraries (or software development kits) which consume the Beyond Pay APIs, making it even easier for you to integrate with your project.

Click the respective language tab to see SDK usage examples. SDKs coming soon to Github; contact <a href="mailto:BeyondPayIntegrations@getbeyond.com">BeyondPayIntegrations@getbeyond.com</a> to request access until then.

- PHP
- .NET
- Java
- Android for mCommerce
- Android for mPOS
- iOS for mCommerce
- iOS for mPOS

<aside class="success">
Note that "mCommerce" SDKs are for use in cardholder-initiated payments such as a consumer-facing app, while "mPOS" SDKs are for use in a merchant-facing app environment such as a mobile-based Point of Sale system.
</aside>

<aside class="warning">
If your payment application stores, processes, or transmits sensitive cardholder data, then it may be in scope for the Payment Card Industry Payment Application Data Security Standard ("PCI PA-DSS"). You are responsible for adhering to all applicable industry standards, including PA-DSS and PCI DSS.
</aside>

## Payment APIs

The primary APIs for integrating to the Beyond Pay platform are:

* **TokenPay.js** – an extension of Beyond Pay that combines client-side and server-side technologies for PCI-compliant online payment capture
* **Beyond Pay API** - a set of robust web service APIs offering support for credit cards, ACH/checks, tokenization, and more
* **PayGuardian** – a cloud-based terminal integration option for Point of Sale developers

# Online Payments

## Getting Started

> To get started, include this script on your checkout page:

TokenPay maximizes the user experience by allowing for the capture of sensitive card data within the payment form of the merchant’s website or mobile application. The consumer remains on the merchant’s payment page at all times during the checkout process.

```html
<script
  src="https://api-test.getbeyondpay.com/WebSecurity/TokenPay/plain-js/tokenPay.js">
</script>
```

TokenPay is an integration interface for Beyond Pay Gateway which facilitates online card payments in a manner that ensures that no sensitive card data ever touches your servers so your integration can operate with minimized scope of PCI.

> Next, create an instance of TokenPay:

To ensure that merchants are eligible for the simplest PCI validation method, Self-Assessment Questionnaire A (SAQ-A), TokenPay utilizes

```javascript
var tokenpay = TokenPay('your-public-key');
```

> Replace `your-public-key` with your publishable public key</a>.

* **Isolation** – Beyond Pay Gateway hosts the sensitive cardholder data input fields. The fields are injected into your form as an HTML iframe thus isolating your page and your server from card sensitive data.
* **Tokenization** – in order to execute transactions against the user’s card, TokenPay replaces the sensitive cardholder data with a non-sensitive surrogate value (token). The token is generated via the use of the TokenPay JavaScript library and your payment form.
* **Segregation** – Requests for charges against the user’s card are made server-to-server – not in the browser or mobile app where it is publicly visible. The tokenized card data is submitted to your server where a secure server-to-server request is made to execute the transaction.
* **Authentication** – The injection of the TokenPay hosted input fields and card tokenization is authenticated via a public key assigned to the merchant. API requests to execute charges against the tokenized card are made by the backend server and are authenticated with a private key assigned to the merchant.

### TokenPay.js

TokenPay.js is the hosted JavaScript library for building online or mobile checkout flows with Beyond Pay Gateway. With it, you can collect sensitive data from the cardholder and create tokens for securely sending the data to your server.

TokenPay.js provides a ready-made UI component for collecting the sensitive card data from the user. TokenPay.js then tokenizes the information without it ever having to touch your server.

The TokenPay.js UI component includes:

* Automatic formatting of card information as it is entered
* Validation of card information as it is entered
* Responsive design that works on user’s screen or mobile device
* Customizable styling to match your website's look and feel

### HTTPS Requirements

All submission of payment information using TokenPay.js is made via a secure HTTPS connection. However, to protect yourself from man-in-the-middle attacks and to prevent your users from experiencing mixed content warnings in their browser, you <b>MUST</b> serve the page with your payment form over HTTPS.

## Environments

Only <a href="#test-cards-and-triggers">test cards</a> should be used in sandbox environments.

> TokenPay.js Hosted Scripts

> <b>Sandbox:</b>

```html
https://api-test.getbeyondpay.com/Bridgepay.WebSecurity/TokenPay/js/tokenPay.js
```

> <b>Production:</b>

```html
https://api.getbeyondpay.com/WebSecurity/TokenPay/js/tokenPay.js
```

The hosted TokenPay script has different versions for test and production.

> Beyond Pay SOAP API Endpoints

> <b>Sandbox:</b>

```html
https://api-test.getbeyondpay.com/PaymentService/RequestHandler.svc
```

> <b>Production:</b>

```html
https://api.getbeyondpay.com/PaymentService/RequestHandler.svc
```

A WSDL is available for Beyond Pay SOAP API by appending "?wsdl" to these endpoints.

## Create a Payment Form

> To determine where to insert the UI components, create empty DOM elements with unique IDs within your payment form.

To securely collect sensitive card details from your users, TokenPay.js creates UI components for you that are hosted by Beyond Pay Gateway. These are then inserted into your payment form.

```html
<form id="paymentForm" action="/charge" method="post"> 
  <select class="form-control" name="amount" id="amount">
    <option value="25">$25</option>
    <option value="50">$50</option> 
  </select>
  <div id="card"></div>
  <div id="errorMessage"></div>
  <button type="submit">Submit</button>
</form>
```

The TokenPay element simplifies the form and minimizes the fields required by inserting a single input field that securely collects all needed card data.

> If you want to customize the style of the card entry area, create a hidden `<div>` element to contain your styling. The `id` of this element MUST be `customStyles`.


<aside class="warning">
When implementing payment forms, it is imperative that you utilize <b>reCAPTCHA</b> or similar mechanisms. reCAPTCHA protects your web forms from spam and bot abuse. Using reCAPTCHA on your payment forms reduces the risk of fraudulent transactions on the merchant's eCommerce sites by performing a Completely Automated Public Turing Test to Tell Computers and Humans Apart (CAPTCHA). For more information on reducing form spam and bot abuse see <a href="https://developers.google.com/recaptcha/intro" target="_blank">https://developers.google.com/recaptcha/intro</a>
</aside>

```html
<div style="display: none" id="customStyles"> 
  body {
    margin: 8px 0;
    }
 #payment-form {
  border: 2px solid #003b5c; 
  padding: 5px 10px; 
  border-radius: 5px; 
  background: white;
  color: #333;
}
</div>
```

> When the form is loaded, initialize the Pay element:

```javascript
tokenpay.initialize({
  dataElement: '#card', 
  errorElement: '#errorMessage', 
  useStyles: false,
  disableZip: false
});
```

> If you have created the `customStyles` element to style the card entry area, change the value of `useStyles` to `true`.

<aside class="success">
You should always submit the ZIP or Postal code in order to ensure the best chances for fraud reduction as well as the lowest interchange rates. "disableZip" is only intended for when you will collect the ZIP code with the rest of your form data rather than in the TokenPay iframe.
</aside>

> To disable the ZIP code field from appearing in the iframe so that it can be captured elsewhere in your form, set `disableZip` to `true`.

## Obtain a Token

```javascript
var form = document.getElementById('paymentForm'); 
$('#paymentForm').on('submit', function (event) {
  event.preventDefault(); 
  tokenpay.createToken(function (result) {
    var hiddenInput = document.createElement('input'); 
    hiddenInput.setAttribute('type', 'hidden'); 
    hiddenInput.setAttribute('name', 'token'); 
    hiddenInput.setAttribute('value', result.token); 
    form.appendChild(hiddenInput);
    form.submit();
  }, function (result) {
    console.log("error: " + result);
  });
});
```

The card data collected by the TokenPay element is posted from the client browser to Beyond Pay Gateway where it is converted into a token. If there are any errors in the collection of the card data or creation of the token, information is automatically displayed in the `errorElement` of your payment form.

The token is stored as a hidden input value and passed to your server on form submission.

## Token Sale

> With the token and other form fields obtained by your server, now construct the payload:

Once you have securely collected and tokenized your user’s card data using TokenPay.js you can now use the single-use token to submit a transaction. Authorization or sale requests using single-use tokens must *ONLY* made from your server and not from the client.

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->RequestType = "004";
$bpRequest->PrivateKey = "YourPrivateKey";
$bpRequest->AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "SALE";
$bpRequest->$requestMessage->ExpirationDate = "1224";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->IsoCurrencyCode = "USD";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.PrivateKey = "YourPrivateKey";
bcRequest.AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.IsoCurrencyCode = "USD";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setRequestType("004");
bcRequest.setAuthenticationTokenId("00000000-0000-0000-0000-000000000000");
bcRequest.setTransactionID(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setAmount("1200");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("SALE");
rqMessage.setHolderType("O");
rqMessage.setExpirationDate("1234");
rqMessage.setIsoCurrencyCode("USD");
rqMessage.setAcctType("R");
rqMessage.setSoftwareVendor("Your Software Name 1.0");
```

> Beyond Pay SDKs wrap the core XML API message

You can construct the SOAP/XML message to Beyond Pay gateway or let our SDKs do it for you. Instructions are provided for those who want to send the raw SOAP message.

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <PrivateKey>YourPrivateKey</PrivateKey>
    <AuthenticationTokenId>00000000-0000-0000-0000-000000000000</AuthenticationTokenId>
    <requestMessage>										
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>O</HolderType>
        <Amount>1200</Amount>
        <CurrencyCode>USD</CurrencyCode>
    </requestMessage>
</requestHeader>
```

You will have a 15 minute window in which to complete the transaction request once you have obtained the client-side token. The token expires after the window or once used.

> The XML payload is then Base64-encoded and packaged within a SOAP envelope

On your server, collect the token information and the form POST parameters submitted by your form.

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:req="http://bridgepaynetsecuretx.com/requesthandler">
                    <soapenv:Header/>
                        <soapenv:Body>
                            <req:ProcessRequest>
                                <req:requestMsg>{Base-64 encoded XML payload}</req:requestMsg>
                            </req:ProcessRequest>
                        </soapenv:Body>
                    </soapenv:Envelope>
```

Now submit the token and parameters according to the example XML request, with the following substitutions:

* `{transactionId}` - unique transaction ID generated by your application for tracking purposes
* `{requestDateTime}` - date and time of the transaction in `yyyyMMddHHmmss` format
* `{yourPrivateKey}` - your private API key
* `{token}` - token delivered in the submission of your payment form
* `{amountInCents}` - transaction amount in cents ($1.25 would be 125)
* `{yourSoftwareName}` - the name and version number of your software application

> Beyond Pay Sample Approved Sale Response

```php
$bcResponse->TransactionID = "635693706433821501<";
$bcResponse->RequestType = "004";
$bcResponse->ResponseCode = "00000";
$bcResponse->ResponseDescription = "Successful Request";
$rsMessage = $bcResponse->responseMessage;
$rsMessage->AuthenticationTokenId = "735333";
$rsMessage->Token = "100000007470001";
$rsMessage->PublicKey = "";
$rsMessage->ExpirationDate = "1022";
$rsMessage->AuthorizationCode = "735333";
```

```csharp
BridgeCommConnection connection = new BridgeCommConnection();
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
ResponseMessage rsMessage = bcResponse.responseMessage;

bcResponse.BridgeCommResponseType = "Auth";
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "20190709092529";

rsMessage.GatewayMessage = "A01 - Approved";
rsMessage.GatewayResult = "00000";
rsMessage.GatewayTransID = "3710636504";
rsMessage.TransactionCode = "20190709092529";
rsMessage.TransactionDate = "20190709";
rsMessage.AuthorizationCode = "537977";
rsMessage.AuthorizedAmount = "1200";
rsMessage.InternalMessage = "Approved: 537977 (approval code)";
rsMessage.isCommercialCard = "False";
rsMessage.IsoCountryCode = "840";
rsMessage.IsoCurrencyCode = "USD";
rsMessage.IsoRequestDate = "2019-07-09 09:25:30.663";
rsMessage.IsoTransactionDate = "2019-07-09 09:25:30.663";
rsMessage.MaskedPan = "1***********1234";
rsMessage.ExpirationDate = "1234";
rsMessage.CardClass = "Credit";
rsMessage.CardType = "Visa";
rsMessage.OriginalAmount = "1200";
rsMessage.ProviderResponseMessage = "Approved";
rsMessage.Token = "11110000000375160150";
```

```java
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "635693706433821501";

ResponseMessage rsMessage = bcResponse.responseMessage;
rsMessage.Token = "1000000074700016";
rsMessage.ExpirationDate = "1022";
rsMessage.AuthrorizationCode = "735333";
```

> Raw XML response

```xml
<?xml version="1.0" encoding="utf-16"?>
<Auth>
  <TransactionID>123456789</TransactionID>
  <RequestType>004</RequestType>
  <ResponseCode>00000</ResponseCode>
  <ResponseDescription>Successful Request</ResponseDescription>
  <responseMessage>
    <Token>1000000010261111</Token>
    <AuthorizationCode>642973</AuthorizationCode>
    <ReferenceNumber></ReferenceNumber>
    <GatwayResult>00000</GatewayResult>
    <AuthorizedAmount>700</AuthorizedAmount>
    <OriginalAmount>700</OriginalAmount>
    <ExpirationDate>1224</ExpirationDate>
    <AVSMessage>Street address and ZIP match</AVSMessage>
    <AVSResult>4F</AVSResult>
    <StreetMatchMessage></StreetMatchMessage>
    <ZipMatchMessage></ZipMatchMessage>
    <CVMessage>Matches</CVMessage>
    <CVResult>M</CVResult>
    <IsCommercialCard>False</IsCommercialCard>
    <GatewayTransID>1235539604</GatewayTransID>
    <GatewayMessage>A01 - Approved</GatewayMessage>
    <InternalMessage>Approved: 642973 (approval Code)</InternalMessage>
    <Balance></Balance>
    <CashBackAmount></CashBackAmount>
    <TransactionCode>123456789</TransactionCode>
    <TransactionDate>20200528</TransactionDate>
    <RemainingAmount>0</RemainingAmount>
    <IsoCountryCode>840</IsoCountryCode>
    <IsoCurrencyCode>USD</IsoCurrencyCode>
    <IsoTransactionDate>2020-05-28 12:41:33.587</IsoTransactionDate>
    <IsoRequestDate>2020-05-28 12:41:33.587</IsoRequestDate>
    <NetworkReferenceNumber></NetworkReferenceNumber>
    <NetworkMerchantId></NetworkMerchantId>
    <NetworkTerminalId></NetworkTerminalId>
    <CardClass>Credit</CardClass>
    <CardType>Visa</CardType>
    <CardHolderName>Test card</CardHolderName>
    <CardModifier>None</CardModifier>
    <ProviderResponseCode></ProviderResponseCode>
    <ProviderResponseMessage>Approved</ProviderResponseMessage>
    <MaskedPan></MaskedPan>
    <WalletID></WalletID>
    <WalletPaymentMethodID></WalletPaymentID>
    <WalletResponseMessage></WalletResponseMessage>
    <WalletResponseCode></WalletResponseCode>
    <MerchantCategoryCode></MerchantCategoryCode>
    <ResponseTypeDescription>sale</ResponseTypeDescription>
    <ReceiptTagData></ReceiptTagData>
    <IssuerTagData></IssuerTagData>
  </responseMessage>
</Auth>
```

After your transaction has been successfully submitted to the gateway, make sure you inspect the response message. Specifically, look at:
 
* `ResponseCode` - a 5 digit response code indicating the status of the transaction request
* `ResponseDescription`- a verbose description of the ResponseCode
* `GatewayResult` - an additional response code that may provide additional information on the status of the transaction
* `GatewayMessage` - a verbose description of the GatewayResult
* `AVSResult` - a code indicating the status of the Address Verification System request, if any
* `AVSMessage` - a verbose description of the AVSResult code meaning
* `CVResult` - a code indicating the status of the Card Security Code (aka CVV2, CID) sent in the request message
* `CVMessage` - a verbose description of the CVResult code meaning
* `Token` - a non-sensitive representation of the card number used in the transaction. The last four digits are the same as the last four digits of the card number. This value can be persisted and used for <a href="#repeat-sales-and-cards-on-file">future recurring transactions from the same cardholder</a>. 

> Beyond Pay Sample Declined Sale Response

```php
$bcResponse->TransactionID = "635693706433821501<";
$bcResponse->RequestType = "004";
$bcResponse->ResponseCode = "30032";
$bcResponse->ResponseDescription = "Denied by customer's bank";
```

```csharp
BridgeCommConnection connection = new BridgeCommConnection();
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
ResponseMessage rsMessage = bcResponse.responseMessage;

bcResponse.BridgeCommResponseType = "Auth";
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "30032";
bcResponse.ResponseDescription = "Denied by customer's bank";
bcResponse.TransactionID = "20190709092529";

rsMessage.GatewayMessage = "D01 - Denied by customer's bank (Issuer Unavailable)";
rsMessage.GatewayResult = "30032";
rsMessage.GatewayTransID = "3710636804";
rsMessage.TransactionCode = "20190709094426";
rsMessage.TransactionDate = "20190709";
rsMessage.AuthorizationCode = "537977";
rsMessage.AuthorizedAmount = "1200";
rsMessage.InternalMessage = "Denied by customer's bank";
rsMessage.ResponseTypeDescription = "denied";
rsMessage.isCommercialCard = "False";
rsMessage.IsoCountryCode = "840";
rsMessage.IsoCurrencyCode = "USD";
rsMessage.IsoRequestDate = "2019-07-09 09:25:30.663";
rsMessage.IsoTransactionDate = "2019-07-09 09:25:30.663";
rsMessage.MaskedPan = "1***********1234";
rsMessage.ExpirationDate = "1234";
rsMessage.CardClass = "Credit";
rsMessage.CardType = "Visa";
rsMessage.OriginalAmount = "1200";
rsMessage.ProviderResponseMessage = "Declined";
```

```java
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "30032";
bcResponse.ResponseDescription = "Denied by customer's bank";
bcResponse.TransactionID = "635693706433821501";

ResponseMessage rsMessage = bcResponse.responseMessage;
rsMessage.CardType = "Visa";
rsMessage.CardClass = "Credit";
rsMessage.ProviderResponseMessage = "735333";
```

> Raw XML response

```xml
<Auth>
	<TransactionID>123</TransactionID>
	<RequestType>004</RequestType>
	<ResponseCode>30032</ResponseCode>
	<ResponseDescription>Denied by customer's bank</ResponseDescription>
	<responseMessage>
		<Token>1000000010532376</Token>
		<ExpirationDate>1224</ExpirationDate>
		<OrganizationId>1706</OrganizationId>
		<AuthorizationCode />
		<ReferenceNumber>960406639</ReferenceNumber>
		<AuthorizedAmount>0</AuthorizedAmount>
		<OriginalAmount>20</OriginalAmount>
		<GatewayTransID>4011311504</GatewayTransID>
		<GatewayMessage>D01 - Denied by customer's bank (Issuer Unavailable)</GatewayMessage>
		<InternalMessage>Denied by customer's bank</InternalMessage>
		<GatewayResult>30032</GatewayResult>
		<AVSMessage />
		<AVSResult />
		<CVMessage />
		<CVResult />
		<TransactionCode>123</TransactionCode>
		<TransactionDate>20210831</TransactionDate>
		<RemainingAmount>0</RemainingAmount>
		<IsoCountryCode>840</IsoCountryCode>
		<IsoCurrencyCode>USD</IsoCurrencyCode>
		<IsoTransactionDate>2021-08-31 21:33:09.537</IsoTransactionDate>
		<IsoRequestDate>2021-08-31 21:33:09.537</IsoRequestDate>
		<NetworkReferenceNumber />
		<MerchantCategoryCode />
		<NetworkMerchantId />
		<NetworkTerminalId />
		<CardClass>Credit</CardClass>
		<CardType>Amex</CardType>
		<CardHolderName />
		<CardModifier>None</CardModifier>
		<ProviderResponseCode />
		<ProviderResponseMessage>Denied by customer's bank (Issuer Unavailable)</ProviderResponseMessage>
		<MaskedPan>3**********2376</MaskedPan>
		<ResponseTypeDescription>decline</ResponseTypeDescription>
		<IsCommercialCard>False</IsCommercialCard>
		<StreetMatchMessage />
		<WalletID />
		<WalletPaymentMethodID />
		<WalletResponseCode />
		<WalletResponseMessage />
	</responseMessage>
</Auth>
```

<aside class="warning">
You should always inspect the AVSResult and CVResult fields as these can be good indicators of potential fraud. If you see a AVSResult or CVResult code that you do not want to accept because it may be too risky (such as "No Match" on the submitted Zip code), then you should submit a void transaction to cancel the authorization and advise the cardholder that their transaction has been declined.
</aside>

## Token Authorize

> To change from a "sale" transaction to an "authorize" transaction, simply set `TransactionType` to `sale-auth` in the Beyond Pay SDK:

Sometimes you may not want to accept payment right away for a transaction, such as when shipping physical goods. The normal practice in this scenario is to first authorize a card which will place a hold on the funds, and then to later "capture" that authorization when the order is fulfilled.

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->RequestType = "004";
$bpRequest->PrivateKey = "YourPrivateKey";
$bpRequest->AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "SALE-AUTH";
$bpRequest->$requestMessage->ExpirationDate = "1224";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->IsoCurrencyCode = "USD";
$bpRequest->$requestMessage->SettlementDelay = "30";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.PrivateKey = "YourPrivateKey";
bcRequest.AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE-AUTH";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.IsoCurrencyCode = "USD";
rqMessage.SettlementDelay = "30";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setRequestType("004");
bcRequest.setAuthenticationTokenId("00000000-0000-0000-0000-000000000000");
bcRequest.setTransactionID(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setAmount("1200");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("SALE-AUTH");
rqMessage.setHolderType("O");
rqMessage.setExpirationDate("1234");
rqMessage.setAcctType("R");
rqMessage.setSettlementDelay("30");
rqMessage.setSoftwareVendor("YourSoftwareName 1.0");
```

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <PrivateKey>YourPrivateKey</PrivateKey>
    <AuthenticationTokenId>00000000-0000-0000-0000-000000000000</AuthenticationTokenId>
    <requestMessage>                    
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale-auth</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>O</HolderType>
        <Amount>1200</Amount>
        <CurrencyCode>USD</CurrencyCode>
        <SettlementDelay>30</SettlementDelay>
    </requestMessage>
</requestHeader>

```

> Beyond Pay Sample Authorization Response

```php
$bcResponse->TransactionID = "635693706433821501";
$bcResponse->RequestType = "004";
$bcResponse->ResponseCode = "00000";
$bcResponse->ResponseDescription = "Successful Request";
$rsMessage = $bcResponse->responseMessage;
$rsMessage->AuthenticationTokenId = "735333";
$rsMessage->Token = "100000007470001";
$rsMessage->PublicKey = "";
$rsMessage->ExpirationDate = "1022";
$rsMessage->AuthorizationCode = "735333";
```

```csharp
BridgeCommConnection connection = new BridgeCommConnection();
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
ResponseMessage rsMessage = bcResponse.responseMessage;

bcResponse.BridgeCommResponseType = "Auth";
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "20190709092529";

rsMessage.GatewayMessage = "A01 - Approved";
rsMessage.GatewayResult = "00000";
rsMessage.GatewayTransID = "3710636504";
rsMessage.TransactionCode = "20190709092529";
rsMessage.TransactionDate = "20190709";
rsMessage.AuthorizationCode = "537977";
rsMessage.AuthorizedAmount = "1200";
rsMessage.InternalMessage = "Approved: 537977 (approval code)";
rsMessage.isCommercialCard = "False";
rsMessage.IsoCountryCode = "840";
rsMessage.IsoCurrencyCode = "USD";
rsMessage.IsoRequestDate = "2019-07-09 09:25:30.663";
rsMessage.IsoTransactionDate = "2019-07-09 09:25:30.663";
rsMessage.MaskedPan = "1***********1234";
rsMessage.ExpirationDate = "1234";
rsMessage.CardClass = "Credit";
rsMessage.CardType = "Visa";
rsMessage.OriginalAmount = "1200";
rsMessage.ProviderResponseMessage = "Approved";
rsMessage.Token = "11110000000375160150";
```

```java
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
bcResponse.RequestType = "004";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "635693706433821501";

ResponseMessage rsMessage = bcResponse.responseMessage;
rsMessage.Token = "1000000074700016";
rsMessage.ExpirationDate = "1022";
rsMessage.AuthrorizationCode = "735333";
```

> Raw XML response

```xml
<Auth>
 <TransactionID>635693706433821501</TransactionID>
    <RequestType>004</RequestType>
    <ResponseCode>00000</ResponseCode>
    <ResponseDescription>Successful Request</ResponseDescription>
        <responseMessage>
            <Token>1000000074700016</Token>
            <ExpirationDate>1022</ExpirationDate>
            <OrganizationId>3538</OrganizationId>
            <AuthorizationCode>735333</AuthorizationCode>
        </responseMessage>
</Auth>
```

The `SettlementDelay` tag can be added for sale-auth transactions, and designates the number of batch cycles that the authorization remains "open" (or uncaptured). If the sale-auth transaction is not captured before completion of the designated number of batches, then the original authorization will be automatically voided and not captured. This value cannot exceed "30" (batch cycles).

> In order to capture that authorization and charge the card, you must submit 019 capture `RequestType`, passing the original sale-auth `ReferenceNumber`, and using the `User` and `Password` credentials instead of `AuthenticationTokenId` and `PrivateKey` to authenticate:

To capture an authorization, simply submit a `RequestType` of `019` for capture, along with passing the reference number of the original authorization as shown here.

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->User = "xxxxxx";
$bpRequest->Password = "xxxxxx";
$bpRequest->RequestType = "019";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "CAPTURE";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->ReferenceNumber = "12345678";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.User = "xxxxxx";
bcRequest.Password = "xxxxxx";
bcRequest.RequestType = "019";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "CAPTURE";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.ReferenceNumber = "12345678";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setUser("xxxxxx");
bcRequest.setPassword("xxxxxx");
bcRequest.setRequestType("019");
bcRequest.setTransactionID("00000000-0000-0000-0000-000000000000");
bcRequest.setRequestDateTime(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("CAPTURE");
rqMessage.setReferenceNumber("12345678");
rqMessage.setSoftwareVendor("YourSoftwareName 1.0");
```

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>019</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <User>xxxxxx</User>
    <Password>xxxxxx</Password>
    <requestMessage>                    
        <SoftwareVendor>YourSoftwareNam 1.0</SoftwareVendor>
        <TransactionType>capture</TransactionType>
        <ReferenceNumber>12345678</ReferenceNumber>
        <Amount>1200</Amount>
    </requestMessage>
</requestHeader>
```

<aside class="notice">
This capture request and several other API requests described here may take differing credentials in order to authenticate the client. All such credentials will be provided by Beyond for testing and production.
</aside>

> Beyond Pay Sample Capture Response

```php
$bcResponse->TransactionID = "635693706433821501";
$bcResponse->RequestType = "019";
$bcResponse->ResponseCode = "00000";
$bcResponse->ResponseDescription = "Successful Request";
$rsMessage = $bcResponse->responseMessage;
$rsMessage->ReferenceNumber = "735333";
$rsMessage->GatewayResult = "00000";
$rsMessage->GatewayTransID = "3710636504";
$rsMessage->GatewayMessage = "A01 - Approved";
$rsMessage->TransactionCode = "";
```

```csharp
BridgeCommConnection connection = new BridgeCommConnection();
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
ResponseMessage rsMessage = bcResponse.responseMessage;

bcResponse.BridgeCommResponseType = "Auth";
bcResponse.RequestType = "019";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "20190709092529";

rsMessage.GatewayMessage = "A01 - Approved";
rsMessage.GatewayResult = "00000";
rsMessage.GatewayTransID = "3710636504";
rsMessage.TransactionCode = "20190709092529";
```

```java
BridgeCommConnection connection = new BridgeCommConnection();
BridgeCommResponse bcResponse = connection.processRequest(URL, bcRequest);
ResponseMessage rsMessage = bcResponse.responseMessage;

bcResponse.BridgeCommResponseType = "Auth";
bcResponse.RequestType = "019";
bcResponse.ResponseCode = "00000";
bcResponse.ResponseDescription = "Successful Request";
bcResponse.TransactionID = "20190709092529";

rsMessage.GatewayMessage = "A01 - Approved";
rsMessage.GatewayResult = "00000";
rsMessage.GatewayTransID = "3710636504";
rsMessage.TransactionCode = "20190709092529";
```

> Raw XML response

```xml
<?xml version="1.0" encoding="utf-16"?>
<Capture>
  <TransactionID>20190709092529</TransactionID>
  <RequestType>019</RequestType>
  <ResponseCode>00000</ResponseCode>
  <responseMessage>
    <ReferenceNumber></ReferenceNumber>
    <GatewayResult>00000</GatewayResult>
    <GatewayTransID>3710636504</GatewayTransID>
    <GatewayMessage>A01 - Approved</GatewayMessage>
    <TransactionCode></TransactionCode>
  </responseMessage>
</Capture>
```

## Repeat Sales and Cards-on-File

> The `Token` element represents a card number, can be used multiple times, and does not expire. It may be used as input in a transaction in lieu of the `PaymentAccountNumber` or the `AuthenticationTokenId`, and also requires the `ExpirationDate` field to be submitted with it.

Every sale or authorization response from Beyond Pay contains a `Token` element. This Token represents the card number used in the original transaction, but is not considered a sensitive data element per the PCI DSS. To ease in identifying the original card, however, the last four digits of the `Token` are the same as the last four digits of the card number.

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->User = "xxxxxx";
$bpRequest->Password = "xxxxxx";
$bpRequest->RequestType = "004";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "SALE";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
$bpRequest->$requestMessage->Token = "1000000010532376";
$bpRequest->$requestMessage->ExpirationDate = "12/23";
$bpRequest->requestMessage->StoredCredential = "recurring";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.User = "xxxxxx";
bcRequest.Password = "xxxxxx";
bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
rqMessage.Token = "1000000010532376";
rqMessage.ExpirationDate = "12/23";
rqMessage.StoredCredential = "recurring";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setUser("xxxxxx");
bcRequest.setPassword("xxxxxx");
bcRequest.setRequestType("004");
bcRequest.setTransactionID("00000000-0000-0000-0000-000000000000");
bcRequest.setRequestDateTime(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("SALE");
rqMessage.setReferenceNumber("12345678");
rqMessage.setSoftwareVendor("YourSoftwareName 1.0");
rqMessage.setToken("1000000010532376");
rqMessage.setExpirationDate("12/23");
rqMessage.StoredCredential("recurring");
```

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <User>xxxxxx</User>
    <Password>xxxxxx</Password>
    <requestMessage>
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>                    
        <Token>1000000010532376</Token>
        <ExpirationDate>1223</ExpirationDate>
        <TransactionType>sale</TransactionType>
        <TransIndustryType>EC</TransIndustryType>
        <AcctType>R</AcctType>
        <HolderType>O</HolderType>
        <Amount>1200</Amount>
        <CurrencyCode>USD</CurrencyCode>
        <StoredCredential>recurring</StoredCredential>
    </requestMessage>
</requestHeader>
```

This Token value may be persisted and, with the cardholder's permission, associated with their user account in your application in order to make future purchases with the same card ("card-on-file").

Submitting a sale or sale-auth transaction with the Token as input requires use of the `User` and `Password` credentials in the request message, and also requires that the card `ExpirationDate` value be persisted and stored with the `Token` (the `ExpirationDate` value is returned in the original response message along with the `Token`).

## Refunds and Voids

In order to refund or void a previous sale or sale-auth transaction, simply construct an XML message with `RequestType` of `012` and `TransactionType` of `refund`. Note that if the original transaction is still in an unsettled batch, the gateway will perform a void/reversal transaction. If the original transaction has already settled, then the gateway will perform a refund to the original card.

> The `GatewayTransId` is returned in the response to a previous sale or sale-auth request and may be used as input to refund or void that original transaction.

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->User = "xxxxxx";
$bpRequest->Password = "xxxxxx";
$bpRequest->RequestType = "012";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransactionType = "REFUND";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
$bpRequest->$requestMessage->ReferenceNumber = "12345678";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.User = "xxxxxx";
bcRequest.Password = "xxxxxx";
bcRequest.RequestType = "012";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "REFUND";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
rqMessage.ReferenceNumber = "12345678";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setUser("xxxxxx");
bcRequest.setPassword("xxxxxx");
bcRequest.setRequestType("012");
bcRequest.setTransactionID("00000000-0000-0000-0000-000000000000");
bcRequest.setRequestDateTime(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setTransactionType("REFUND");
rqMessage.setReferenceNumber("12345678");
rqMessage.setSoftwareVendor("YourSoftwareName 1.0");
rqMessage.setReferenceNumber("12345678");
```

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>{transactionId}</TransactionID>
    <RequestType>012</RequestType>
    <RequestDateTime>{requestDateTime}</RequestDateTime>
    <User>{Beyond-assigned username}</User>
    <Password>{Beyond-assigned password}</Password>
    <requestMessage>                    
        <SoftwareVendor>{yourSoftwareName}</SoftwareVendor>
        <TransactionType>refund</TransactionType>
        <ReferenceNumber>{original sale or sale-auth GatewayTransId}</ReferenceNumber>
        <Amount>{amountInCents}</Amount>
    </requestMessage>
</requestHeader>
```

<aside class="notice">
You may refund/void the full amount of an original transaction or only part of the amount (a "partial refund" or "partial reversal"). If the transaction is in the current open (unsettled) batch, then only a single void (for the full amount or partial amount) may be performed. If the transaction has settled, the refund request transaction may be repeated for multiple partial refunds up to the amount of the original transaction.
</aside>

> Raw XML response

```xml
<?xml version="1.0" encoding="utf-16"?>
<VoidRefund>
  <TransactionID>12345</TransactionID>
  <RequestType>012</RequestType>
  <ResponseCode>00000</ResponseCode>
  <ResponseDescription>Successful Request</ResponseDescription>
  <responseMessage>
    <ReferenceNumber />
    <GatewayTransID>3807822104</GatewayTransID>
    <GatewayMessage>A08 - Partial Refund Posted</GatewayMessage>
    <InternalMessage>Approved: 945466 (approval code)</InternalMessage>
    <GatewayResult>00000</GatewayResult>
    <TransactionCode>12345</TransactionCode>
    <RemainingAmount>3000</RemainingAmount>
    <OrganizationId>2380</OrganizationId>
    <MerchantAccountCode />
    <ResponseType>refund</ResponseType>
    <ResponseTypeDescription>refund</ResponseTypeDescription>
    <CardClass />
    <CardType />
    <CardHolderName />
    <ProviderResponseCode />
    <ProviderResponseMessage />
  </responseMessage>
</VoidRefund>

```

## Level II and Level III Data

Some business cards may be eligible for lower interchange rates if you send additional data with the transaction. Beyond Pay supports these additional data fields and can help you or your clients secure <a href="https://www.getbeyond.com/b2b-payment-solutions/" target="_blank">these significantly reduced rates and other B2B benefits</a>.

### Level II Data

> Sample transaction with Level II data:

```php
$bpRequest = new BeyondPayRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->RequestType = "004";
$bpRequest->PrivateKey = "YourPrivateKey";
$bpRequest->AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "SALE";
$bpRequest->$requestMessage->ExpirationDate = "1224";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->IsoCurrencyCode = "USD";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
$bpRequest->$requestMessage->PONum = "PO-4321";
$bpRequest->$requestMessage->TaxAmount = "110";
$bpRequest->$requestMessage->TaxIndicator = "P";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.PrivateKey = "YourPrivateKey";
bcRequest.AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.IsoCurrencyCode = "USD";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
rqMessage.PONum = "PO-4321";
rqMessage.TaxAmount = "110";
rqMessage.TaxIndicator = "P";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setRequestType("004");
bcRequest.setAuthenticationTokenId("00000000-0000-0000-0000-000000000000");
bcRequest.setTransactionID(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setAmount("1200");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("SALE");
rqMessage.setHolderType("O");
rqMessage.setExpirationDate("1234");
rqMessage.setIsoCurrencyCode("USD");
rqMessage.setAcctType("R");
rqMessage.setSoftwareVendor("Your Software Name 1.0");
rqMessage.setPONum("PO-4321");
rqMessage.setTaxAmount("110");
rqMessage.setTaxIndicator("P");
```

In order for a transaction to qualify at reduced "Level II" interchange rates, assuming the card is eligible for such, the following fields should be provided in the XML message to the gateway in addition to the basic required fields given in the <a href="#token-sale">instructions for processing a basic sale transaction</a>:

- `PONum` - the customer's Purchase Order number; may be up to 24 alphanumeric characters and hyphens
- `TaxAmount` - applicable tax amount in cents (implied decimal); must be less than the total transaction `Amount`
- `TaxIndicator` - may be `P` (Provided), `N` (Not Provided), or `E` (Exempt). Use P if you are sending a value in `LocalTaxAmount`, or E if you are tax-exempt

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <PrivateKey>YourPrivateKey</PrivateKey>
    <AuthenticationTokenId>00000000-0000-0000-0000-000000000000</AuthenticationTokenId>
    <requestMessage>                    
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>O</HolderType>
        <Amount>1200</Amount>
        <CurrencyCode>USD</CurrencyCode>
        <PONum>PO-4321</PONum>
        <TaxAmount>110</TaxAmount>
        <TaxIndicator>P</TaxIndicator>
    </requestMessage>
</requestHeader>
```

### Level III Data

Cards that are eligible for Level III interchange rates are typically corporate purchasing or some travel cards. If a card is eligible for such, you can achieve a reduced interchange rate by providing the following fields in your gateway request message (in addition to those required for Level II and basic sale or "Level I" transactions).

> Sample sale transaction via <a href="/getting-started">TokenPay.js</a> with Level III line-item details:

```php
$bpRequest = new BeyondPayRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->RequestType = "004";
$bpRequest->PrivateKey = "YourPrivateKey";
$bpRequest->AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransIndustryType = "EC";
$bpRequest->$requestMessage->TransactionType = "SALE";
$bpRequest->$requestMessage->ExpirationDate = "1224";
$bpRequest->$requestMessage->AcctType = "R";
$bpRequest->$requestMessage->HolderType = "O";
$bpRequest->$requestMessage->IsoCurrencyCode = "USD";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
$bpRequest->$requestMessage->InvoiceNum = "INV-1234";
$bpRequest->$requestMessage->PONum = "PO-4321";
$bpRequest->$requestMessage->CustomerAccountCode = "CID-9876";
$bpRequest->$requestMessage->TaxAmount = "110";
$bpRequest->$requestMessage->TaxIndicator = "P";
$bpRequest->$requestMessage->ItemCount = "1";

$requestMessage->$rqItem = new Item();
$requestMessage->$rqItem->ItemCode = "123456";
$requestMessage->$rqItem->ItemCommodityCode = "5999";
$requestMessage->$rqItem->ItemDescription = "Widget";
$requestMessage->$rqItem->ItemQuantity = "1";
$requestMessage->$rqItem->ItemUnitCostAmt = "1000";
$requestMessage->$rqItem->ItemUnitMeasure = "EA";
$requestMessage->$rqItem->ItemTotalAmount = "1110";
```

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.PrivateKey = "YourPrivateKey";
bcRequest.AuthenticationTokenId = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE";
rqMessage.TransIndustryType = "EC";
rqMessage.Amount = "1200";
rqMessage.HolderType = "O";
rqMessage.AcctType = "R";
rqMessage.IsoCurrencyCode = "USD";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
rqMessage.PONum = "PO-4321";
rqMessage.InvoiceNum = "INV-1234";
rqMessage.CustomerAccountCode = "CID-9876";
rqMessage.TaxAmount = "110";
rqMessage.TaxIndicator = "P";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setRequestType("004");
bcRequest.setAuthenticationTokenId("00000000-0000-0000-0000-000000000000");
bcRequest.setTransactionID(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setAmount("1200");
rqMessage.setTransIndustryType("EC");
rqMessage.setTransactionType("SALE");
rqMessage.setHolderType("O");
rqMessage.setExpirationDate("1234");
rqMessage.setIsoCurrencyCode("USD");
rqMessage.setAcctType("R");
rqMessage.setSoftwareVendor("Your Software Name 1.0");
rqMessage.setInvoiceNum("INV-1234");
rqMessage.setPONum("PO-4321");
rqMessage.setCustomerAccountCode("CID-9876");
rqMessage.setTaxAmount("110");
rqMessage.setTaxIndicator("P");
rqMessage.setItemCount("1");
rqMessage.setItem(new rqItem);

rqItem.setItemCode("123456");
rqItem.setItemCommodityCode("5999");
rqItem.setItemDescription("Widget");
rqItem.setItemQuantity("1");
rqItem.setItemUnitCostAmt("1000");
rqItem.setItemUnitMeasure("EA");
rqItem.setItemTotalAmount("1110");
```

> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <PrivateKey>YourPrivateKey</PrivateKey>
    <AuthenticationTokenId>00000000-0000-0000-0000-000000000000</AuthenticationTokenId>
    <requestMessage>                    
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>O</HolderType>
        <Amount>1110</Amount>
        <CurrencyCode>USD</CurrencyCode>
        <InvoiceNum>INV-1234</InvoiceNum>
        <PONum>PO-4321</PONum>
        <CustomerAccountCode>CID-9876</CustomerAccountCode>
        <TaxAmount>110</TaxAmount>
        <TaxIndicator>P</TaxIndicator>
        <ItemCount>1</ItemCount>
        <Item>
          <ItemCode>123456</ItemCode>
          <ItemCommodityCode>5999</ItemCommodityCode>
          <ItemDescription>Widget</ItemDescription>
          <ItemQuantity>1</ItemQuantity>
          <ItemUnitCostAmt>1000</ItemUnitCostAmt>
          <ItemUnitMeasure>EA</ItemUnitMeasure>
          <ItemTotalAmount>1110</ItemTotalAmount>
        </Item>
    </requestMessage>
</requestHeader>
```

Note that Level III transactions require line-item details from the purchase. You should send one Item array for each line item on a given invoice; many integrators will dynamically map these required fields into their existing inventory, order management, or ERP systems. Alternatively, if you only sell one type of item, you may consider creating a static mapping of these fields, or "hard-coding" the values specific to your business.

- `ItemCount` - the total number of line items being submitted in this request
- `Item` - an array representing each line item in the request, consisting of:
- `ItemCode` - a unique identifier assigned to this item in the merchant's inventory system (typically a SKU, SKID, or UPC) - 12 character maximum
- `ItemCommodityCode` - a standardized code that classifies the item, such as the <a href="https://www.unspsc.org/" target="_blank">UN Standard Products and Services Code (UNSPSC)</a>; many integrators and merchants use the Merchant Category Code in this field
- `ItemDescription` - A short textual description of the item, limited to 35 characters
- `ItemQuantity` - quantity of item units purchased as part of this transaction; supports up to 4 decimal places
- `ItemUnitCostAmt` - cost of a single unit of the item in cents (implied decimal)
- `ItemUnitMeasure` - unit of measure used to quantify the items purchased (e.g.: kg, lb, in, etc.); "EA" for "each" is most commonly used and recommended for single-item merchants
- `ItemTotalAmount` - total amount paid for the item (including tax and any discount)

<aside class="success">
In general, for most card brands and card issuers, the presence of a value in the appropriate Level III field is enough to qualify for the reduced interchange rate. The accuracy of these values is not validated by the card brands in most cases, but may impact the reporting received by the administrator of a given corporate purchasing card program.
</aside>

## ACH and eChecks

```php
$bpRequest = new BridgeCommRequest();
$bpRequest->$requestMessage = new RequestMessage();

$bpRequest->RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");
$bpRequest->User = "xxxxxx";
$bpRequest->Password = "xxxxxx";
$bpRequest->RequestType = "004";
$bpRequest->TransactionID = "00000000-0000-0000-0000-000000000000";
$bpRequest->$requestMessage->MerchantCode = "123456";
$bpRequest->$requestMessage->MerchantAccountCode = "789123";
$bpRequest->$requestMessage->Amount = "1200";
$bpRequest->$requestMessage->TransactionType = "SALE";
$bpRequest->$requestMessage->TransIndustryType = "WEB";
$bpRequest->$requestMessage->AcctType = "C";
$bpRequest->$requestMessage->SoftwareVendor = "YourSoftwareName 1.0";
$bpRequest->$requestMessage->RoutingNum = "021000021";
$bpRequest->$requestMessage->BankAccountNum = "4099999992";
```

Processing an eCheck/ACH transaction is very similar to processing a credit card transaction. Instead of passing a token to the webservice, you can directly pass the bank's routing/transit number and the bank account number. These data elements are not considered sensitive to the same degree as card data, and are not covered by the scope of PCI DSS. You should still encrypt said data elements whether at rest or in motion, but they will not impact your scope of PCI compliance.

```csharp
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.User = "xxxxxx";
bcRequest.Password = "xxxxxx";
bcRequest.RequestType = "004";
bcRequest.TransactionID = "00000000-0000-0000-0000-000000000000";
bcRequest.RequestDateTime = DateTime.Now.ToString("yyyyMMddHHmmss");

rqMessage.MerchantCode = "123456";
rqMessage.MerchantAccountCode = "789123";
rqMessage.TransactionType = "SALE";
rqMessage.Amount = "1200";
rqMessage.TransIndustryType = "WEB";
rqMessage.AcctType = "C";
rqMessage.SoftwareVendor = "YourSoftwareName 1.0";
rqMessage.RoutingNum = "021000021";
rqMessage.BankAccountNum = "4099999992";
```

```java
BridgeCommRequest bcRequest = new BridgeCommRequest();
RequestMessage rqMessage = new RequestMessage();

bcRequest.setUser("xxxxxx");
bcRequest.setPassword("xxxxxx");
bcRequest.setRequestType("012");
bcRequest.setTransactionID("00000000-0000-0000-0000-000000000000");
bcRequest.setRequestDateTime(DateTime.Now.ToString("yyyyMMddHHmmss"));
bcRequest.setRequestMessage(new rqMessage);

rqMessage.setMerchantCode("123456");
rqMessage.setMerchantAccountCode("789123");
rqMessage.setTransactionType("SALE");
rqMessage.setAcctType("C");
rqMessage.setTransIndustryType("WEB");
rqMessage.setSoftwareVendor("YourSoftwareName 1.0");
rqMessage.setRoutingNumber("021000021");
rqMessage.setBankAccountNumber("4099999992");
```
> Or, in the raw XML:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>00000000-0000-0000-0000-000000000000</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>yyyyMMddHHmmss</RequestDateTime>
    <User>xxxxxx</User>
    <Password>xxxxxx</Password>
    <requestMessage>
        <SoftwareVendor>YourSoftwareName 1.0</SoftwareVendor>
        <TransactionType>sale</TransactionType>
        <TransIndustryType>WEB</TransIndustryType>
        <RoutingNum>021000021</RoutingNum>
        <BankAccountNum>4099999992</BankAccountNum>
        <AcctType>C</AcctType>
        <Amount>1200</Amount>
    </requestMessage>
</requestHeader>
```

In addition to passing the routing and account number, you also need to specify whether the bank account is a checking or savings account, as well as the "Standard Entry Class" code as defined by NACHA.

<br>`WEB` - Internet-Initiated Entry
<br>`PPD` - Prearranged Payment and Deposit - for consumer checks (requires written authorization from customer)
<br>`CCD` - Corporate Credit or Debit - for business checks (requires written authorization from customer)
<br>`TEL` - Telephone-Initiated Entry

<aside class="notice">
Different NACHA SEC codes require different types of authorizations from or disclosure to your customer:
<br><b>WEB</b> - <a href="https://www.nacha.org/system/files/resources/Authorization_0.pdf" target="_blank">best practices for authorization and sample language</a>
<br><b>CCD</b> and <b>PPD</b> - <a href="http://www.checktraining.com/docs/general/Programs/ACH%20Debit/ACH_Debit_auth_form.pdf" target="_blank">sample consumer authorization form</a>
<br><b>TEL</b> - <a href="http://www.checktraining.com/docs/general/Programs/Check%20By%20Phone/Checks-By-Phone_sample_script.pdf" target="_blank">sample script for IVR</a> or <a href="http://www.checktraining.com/docs/general/Programs/Check%20By%20Phone/Checks-By-Phone_written_auth.pdf" target="_blank">sample written authorization form</a>
</aside>

# In-Person Payments

## Overview

If you are developing a payment application or point of sale (POS) system for use by only your business, then that application falls in your scope of PCI DSS compliance as a merchant. 

If you are developing a POS to sell or license to other businesses, that application is in scope for PCI Payment Application Data Security Standard (PA-DSS) if it interacts with card data. 

If that application is hosted/SaaS-based then you may also be in-scope PCI Service Provider (similar to a gateway provider).

The costs involved in validating PCI compliance for such software can be prohibitive for Indepdendent Software Vendors (ISVs). Increasingly, ISVs are also expected to offer support for EMV or chip cards: direct integration of which can also be very costly and time-consuming.

The solution to both of these challenges is a semi-integrated or "out-of-scope" architectural model, whereby a POS or application can integrate (or "semi-integrate") to a pre-certified payment application and device. This removes the burden of complicated EMV/chip card certification and insulates the application from interacting with sensitive data.

Beyond PayGuardian is a cloud-based semi-integrated solution that makes it possible to easily support in-person card payments from any platform or environment.

## Supported Devices

Beyond's preferred card present devices are the Android-based "A-series" from PAX Technology:

- <a href="https://www.paxtechnology.com/a920" target="_blank">PAX A920</a>
- <a href="https://www.paxtechnology.com/a80" target="_blank">PAX A80</a>

Development devices are available to purchase by request. Please contact <a href="mailto:BeyondPayIntegrations@getbeyond.com">BeyondPayIntegrations@getbeyond.com</a>.

Beyond will provide development and production devices pre-configured with the necessary account information and settings. The only credential you will need to communicate with the device is its UUID or "locationID", which will be provided by Beyond and can also be confirmed in the PayGuardian Cloud app on the the terminal device.

## Getting Started

> <b>Endpoint (Test and Production):</b>

```html
https://pgc.bridgepaynetsecuretx.com/req/payment
```

Initiating a card present transaction is as simple as POSTing just a few lines of JSON to the web service, passing the following arguments:

> Credit Sale Request


> `POST`

```json
{
"locationID": "91552FCB-01A7-4BA2-B00A-EA33FC660307",
"mode": "UAT",
"amount": "17.00",
"softwareVendor": "My POS 1.0",
"tenderType": "CREDIT",
"transType": "SALE"
}
```

- `locationID` - the UUID from the PayGuardian Cloud app installed on the device
- `mode` - indicates what environment to use; options are: UAT for testing and development and PROD for production/live usage
- `amount` - the amount of the transaction
`softwareVendor` - the name and version of your POS or application
`tenderType` - the type of payment to expect; common values are: `UNKNOWN`, `CREDIT`, `DEBIT`, `CHECK`, `GIFT`
`transType` - the type of transaction to perform; common values are: `SALE`, `SALE_AUTH`, `REFUND`, `VOID`, `TOKENADD`, `CAPTURE`

>Credit Sale Response

```json
{
"requestID": "2aaf2fe8663c561fe7edf5c663b4e7262dd47274bdba13f3daafb207",
"locationID": "91552FCB-01A7-4BA2-B00A-EA33FC660307",
"terminalID": "3EADDF76-27E6-4883-A49C-0AA876E64734",
"approvedAmount": "17.00",
"authCode": "830705",
"avsMessage": "",
"avsResponse": "",
"cardType": "Visa",
"cashBackAmt": "",
"cvMessage": "",
"cvResponse": "",
"expirationDate": "0323",
"extData": {
    "lodgingItem": [],
    "receiptTagData": {
        "maskedCard": "4***********2645",
        "chipCardAID": "A0000000031010",
        "invoice": "12345678",
        "seq": "23dbde68c492a6c2c6b5cbe726d40741",
        "authCode": "830705",
        "entryMethod": "Chip_Read",
        "totalAmount": "17.00",
        "pinVerified": "NO"
    },
    "signatureEncoded": "iVBORw0KGgoAAAANSUhEUgAAAe8AAACWCAIAAAB4sZcnAAADOklEQVR42u..."
},
"gatewayMessage": "A01 - Approved",
"gatewayResult": "0",
"internalMessage": "Approved: 830705 (approval code)",
"isCommercialCard": "False",
"isoCountryCode": "840",
"isoCurrencyCode": "USD",
"isoRequestDate": "2018-06-28 14:25:04.963",
"isoTransactionDate": "2018-06-28 14:25:04.963",
"maskedAccountNumber": "4***********2645",
"merchantCategoryCode": "",
"networkMerchantId": "",
"networkReferenceNumber": "",
"networkTerminalId": "",
"pnRefNum": "253271004",
"remainingAmount": "0.00",
"requestedAmount": "",
"responseTypeDescription": "sale",
"resultCode": "0",
"resultTxt": "Successful Request",
"streetMatchMessage": "",
"submittedAmount": "17.00",
"timestamp": "20180628",
"tipAmount": "",
"token": "11110000000400142645",
"transactionCode": "23dbde68c492a6c2c6b5cbe726d40741"
}
```




If the card is an EMV/chip card, then the user will be presented with an option to select whichever Applications reside on the chip (that is, they can select an Application ID associated with either Credit or Debit, depending on their card) regardless of what tender type is sent in the request. If the `UNKNOWN` tender type is used, the cardholder will similarly be prompted to select either the credit or debit application on the chip.

If the card is magnetic stripe only and capable of being processed as either a debit or a credit transaction, then it will be processed as whatever tender type is sent in the request. If `UNKNOWN` is selected, the cardholder will likewise be prompted to make the selection.

Transaction types may be defined as follows:

`SALE` - authorizes a card and captures it, placing it in the batch for settlement
`SALE_AUTH` - authorizes a card but does not capture it, holding the cardholder's funds until the capture transaction is performed (or until 7 days at which time the authorization is voided)
`REFUND` - this is the preferred transaction for both refunding and voiding; if the original transaction is still in an unsettled batch, the gateway will perform a void/reversal transaction; if the original transaction has already settled, then the gateway will perform a refund to the original card. See below notice.
`TOKENADD` - this transaction only tokenizes a given card number and does not perform any financial adjustments to the account
`CAPTURE` - used to capture a previous `SALE_AUTH` transaction and add it to the batch for settlement

<aside class="notice">
Additional data elements are presented in the following sections that cover industry-specific use cases and provide more detailed workflows.
</aside>

## Basic Sale Options

```json
{
"locationID": "91552FCB-01A7-4BA2-B00A-EA33FC660307",
"mode": "UAT",
"amount": "#####.##",
"softwareVendor": "My POS 1.0",
"tenderType": "CREDIT",
"transType": "SALE",
"invNum": "Invoice number",
"pnRefNum": "Reference number from a previous transaction",
"poNum": "Purchase order number",
"taxAmt": "#####.##",
"allowPartialApproval": "true|false",
"clerkID": "Employee/Clerk ID",
}
```

You may also want to send these additional fields on some transactions:

- `invNum` - an invoice number you would like to associate with the transaction (may be up to 24 alphanumeric characters and hyphens)
- `pnRefNum` - the reference number from a prior transaction response, primarily used to perform refunds, voids, or adjustments
- `poNum` - a Purchase Order number associated with the transaction; required to receive a lower interchange rate on eligible B2B cards (may be up to 24 alphanumeric characters and hyphens)
- `taxAmt` - the amount of the tax on the transaction; required to receive a lower interchange rate on eligible B2B cards (may be up to 24 alphanumeric characters and hyphens)
- `allowPartialApproval` - whether or not to allow partial approvals; see below notice
- `clerkID` - an employee or clerk identifier for reporting purposes

<aside class="notice">
Partial authorization support is required for some merchant types and strongly encouraged for all others in order to reduce declines on prepaid open-loop (branded) cards when there are insufficient funds to cover the total amount of the transaction. See the <a href="https://usa.visa.com/dam/VCOM/global/support-legal/documents/visa-partial-authorization-service.pdf" target="_blank">Visa Partial Authorization Service Guide</a> for more details.
</aside>

## Tips & Gratuities

`tenderType`=`CREDIT` and `transType`=`ADJUSTMENT` will adjust a previous `SALE` or `SALE_AUTH` adding a tip amount based on a `pnRefNum` (previous transaction reference number). This action can only be performed on unsettled transactions in an open batch. 

> `CREDIT` + `ADJUSTMENT` request:

```json
{
"locationID": "C832D913-982C-4256-9895-2DD13BDA5947",
"pnRefNum": "Reference number from a previous transaction",
"mode":"UAT",
"tipAmt": "5.00",
"tenderType": "CREDIT",
"transType": "ADJUSTMENT"
}
```

> `CREDIT` + `ADJUSTMENT` response:

```json
{
"requestID": "388c37acbd88d7f00fce90ffee8b83c156efedb57828c1e8439e6284",
"locationID": "C832D913-982C-4256-9895-2DD13BDA5947",
"terminalID": "9102C064-F990-41AB-BAD4-C98F33E4C684",
"approvedAmount": "20.00",
"authCode": "802431",
"avsMessage": "",
"avsResponse": "",
"cardType": "",
"cashBackAmt": "",
"cvMessage": "",
"cvResponse": "",
"expirationDate": "",
"extData": {
    "lodgingItem": [],
    "receiptTagData": {}
            }   , "gatewayMessage": "A12 - Tip Adjustment Posted",
"gatewayResult": "0",
"internalMessage": "Tip Adjustment Posted",
"isCommercialCard": "False",
"isoCountryCode": "0",
"isoCurrencyCode": "",
"isoRequestDate": "",
"isoTransactionDate": "",
"maskedAccountNumber": "",
"merchantCategoryCode": "",
"networkMerchantId": "",
"networkReferenceNumber": "",
"networkTerminalId": "",
"pnRefNum": "253276004",
"remainingAmount": "0.00",
"requestedAmount": "",
"resultCode": "0",
"resultTxt": "Successful Request",
"streetMatchMessage": "",
"submittedAmount": "15.00",
"timestamp": "",
"tipAmount": "",
"token": "",
"transactionCode": ""
}
```

If successful, the response will contain the new total approved amount: (initial amount) + (tip amount).

## Lodging & Hotels

```json
{
"locationID": "your-locationID",
"mode": "UAT",
"amount": "10.00",
"softwareVendor": "your_POS_name",
"tenderType": "CREDIT",
"transType": "SALE",
"extData": {
/* Lodging fields */
"checkInDate": "Actual or anticipated check in date.",
"checkOutDate": "Actual or anticipated check out date.",
"departureAdjAmount": "Additional amount charged after cardholder left the hotel.",
"folioNumber": "Hotel folio number",
"lodgingChargeType": "H (Hotel)|R (Restaurant)|G (Gift Shop)|S (Health Spa)|B (Beauty Shop)|F (Convention Fee)|T (Tennis)|O (Golf)",
/*Collection of lodging item records.*/
"lodgingItem": [{
"lodgingItemAmount": "Amount (in cents) for lodging extra charge item. Implied (no) decimal.",
"lodgingItemCode": "",
"lodgingItemType": "G (Gift Shop)|L (Laundry)|B (Mini Bar)|R (Restaurant)|T (Telephone)"
}],
"lodgingItemCount": "Indicates number of lodging industry items purchased as part of this transaction.",
"roomNumber": "Hotel room number",
"roomRateAmt": "Amount (in cents) of the daily room rate.",
"roomTaxAmt": "Amount (in cents) of the tax applied to daily room rate.",
"specialProgramType": "AD (Advance deposit)|AR (Assured reservation)|DC (Delayed charge)|ES (Express service)|NC (Normal charge)|NS (No show charge)",
"stayDuration": "Anticipated, actual or incremental stay in days."
}
```

The extended data fields required for lodging transactions can easily be passed through the semi-integrated device to Beyond Pay Gateway.

## Pharmacy & Healthcare

```json
{
"locationID": "your-locationID",
"mode": "UAT",
"amount": "10.00",
"softwareVendor": "your_POS_name",
"tenderType": "CREDIT",
"transType": "SALE",
/* Healthcare related fields */
"isQualifiedIIAS": "Indicates whether purchase items are verified against IIAS. Can be t|f",
"healthCareAmt": "Amount (in cents) of the total Healthcare Amount.",
"clinicAmt": "Amount (in cents) of the portion of the Healthcare Amount spent on hospitalization.",
"dentalAmt": "Amount (in cents) of the portion of the Healthcare Amount spent on dental related medical services.",
"prescriptionAmt": "Amount (in cents) of the portion of the Healthcare Amount spent on prescription drugs or products.",
"transitAmt": "Amount (in cents) of the portion of the Healthcare Amount spent on transportaion.",
"visionAmt": "Amount (in cents) of the portion of the Healthcare Amount spent on vision related medical services."
}
```

Payment systems and Points of Sale for pharmacy merchants are required to pass some of these additional data fields in conjunction with their implementation of "auto-substantiation" using an "inventory information approval system" (IIAS). See <a href="https://sig-is.org/">sig-is.org</a> for more information.

# Transaction Reporting

> <a href='https://www.dropbox.com/s/h7ih2g47w8b8v39/BridgePay%20Public%20Reporting%20API%20v1%200%201.pdf?dl=0'>Reporting Developer Guide</a>

> <a href='https://www.dropbox.com/s/epf9jhj5swi5q68/BridgePay_Reporting%20_API.zip?dl=0'>Reporting API (Visual Studio)</a>

> Service: <a href='https://www.bridgepaynetsecuretest.com/Bridgepay.Reporting.API/ReportingAPI.svc'>https://www.bridgepaynetsecuretest.com/Bridgepay.Reporting.API/ReportingAPI.svc</a>

> C# sample implementation:

```c#
class Program
{
  static void Main(string[] args)
  {
    ReportingAPI.Credentials credentials = new ReportingAPI.Credentials();

    credentials.UserName = "username";
    credentials.Password = "password";

    ReportingAPI.ReportingAPIV1Client client = new ReportingAPI.ReportingAPIV1Client();
    ReportingAPI.TransactionRowFilter filter = new ReportingAPI.TransactionRowFilter();

    filter.MerchantID = 2000;
    filter.MerchantAccountID = 2001;

    filter.DateRangeFrom = DateTime.Now.AddMonths(-2);
    filter.DateRangeTo = DateTime.Now;

    filter.Skip = 0;
    filter.Take = 20;

    ReportingAPI.TransactionSet ts = new ReportingAPI.TransactionSet();

    Ts = client.PublicGetTransactionsByFilter(credentials, filter);

    foreach (ReportingAPI.TransactionRow tr in ts.TransactionList)
    {
      Console.WriteLine("Transaction ID: " + tr.TransactionId); 
      Console.WriteLine("Sale Date / Time: " + tr.SaleDateTime); 
      Console.WriteLine("Merchant Name: " + tr.MerchantName); 
      Console.WriteLine("Card Holder Name: " + tr.FirstName + " " + tr.LastName); 
      Console.WriteLine("Invoice Number: " + tr.InvoiceNumber); 
      Console.WriteLine("Auth Code: " + tr.AuthCode); 
      Console.WriteLine("Requested Amount: " + tr.RequestedAmount); 
      Console.WriteLine("Authorized Amount: " + tr.AuthorizedAmount); 
      Console.WriteLine("Remaining Amount: " + tr.RemainingAmount); 
      Console.WriteLine("Settle Anmount: " + tr.SettleAmnount); 
      Console.WriteLine("--------------------------------------------");
    }
  }
}
```

The Beyond Pay Reporting API provides integrators with the ability to request transaction data via a SOAP request made to the service.  The user must provide data they wish to use as a filter in the parameter to the SOAP method and will receive a response containing the data they requested.

The Reporting API provides three data contracts.  One for the incoming request and two for the response to the request.  When making a request, the consumer must provide a TransctionRowFilter object. When receiving the response, the consumer will get a TransactionSet object which will contain a collection of TransactionRow objects.  The data contracts are described in more detail below.

### TransactionRowFilter

Parameter Name | Data Type | Validations | Comparison Type
-------------- | --------- | ----------- | ---------------
AmountRangeFrom | Implied Integer | Optional | GTE
AmountRangeTo | Implied Integer | Optional | | LTE
AuthorizationCode | String | Optional, Exact Match | EQUIV
BatchID | Integer | Optional | EQUIV
CardBrand | String | Optional, Must match known card brands | EQUIV
CardholderFirstName | String | Optional, Exact Match | EQUIV
CardholderLastName | String | Optional, Partial Match | CONTAINS
ClerkId | String | Optional, Exact Match | EQUIV
CustomerNumber | String | Optional, Exact Match | EQUIV
DateRangeFrom | DateTime | Optional | GTE
DateRangeTo | DateTime | Optional | LTE
EndPartialAccountNumber | String | Optional | EQUIV
ExcludeTransResults* | Boolean | Optional (1 or 0) | N/A
ExcludeVoid | Boolean | Optional (1 or 0) | N/A
ID | Integer | Optional, Exact Match | EQUIV
InvoiceNumber | String | Optional, Exact Match | EQUIV
MerchantAccountId | Integer | Optional | EQUIV
MerchantId | Integer | Optional | EQUIV
PaymentMethodID | String | Optional, Exact Match | EQUIV
PurchaseOrderNumber | String | Optional, Exact Match | EQUIV
ResellerID | Integer | Optional | EQUIV
ResponseCode | String | Optional, Partial Match | CONTAINS
SettlementStatus | String | Optional, Exact Match | EQUIV
Skip | Integer | Required | N/A
Take | Integer | Required | N/A
TransactionSourceIP | String | Optional, Exact Match | EQUIV
TransactionStatus | String | Optional, Exact Match | EQUIV
TransResults* | String | Optional, Multi-Match (comma separated list) | INLIST

The TransResults field works by mapping the BridgeComm 5-digit response code back to the gateway response code (the ResponseCode field in this contract).  In some cases, more than one mapping may exist for a given code.  It is recommended that you use the ResponseCode field for more granular filtering. The ExcludeTransResults field can modify the behavior of the TransResults field by establishing a “not in” condition.

### TransactionSet

|Parameter Name|Data Type|Description|
|--- |--- |--- |
|RecordCount|Integer|The total number of records that match the filter, excluding the Take & Skip fields.|
|TransactionList|List|A collection of TransactionRow objects.|


### TransactionRow

|Parameter Name|Data Type|Description|
|--- |--- |--- |
|Account Type|String|1 character identifier that determines the type of account. Valid values are R (Branded Credit Card), E (Branded debit checking card), V (Branded debit savings card), D (Unbranded debit checking card), I (Unbranded debit savings card), S (Bank savings account), C (Bank checking account), F (EBT food stamp), H (EBT cash benefit), G (Gift card), L (Fleet), A (Cash), K (Check)|
|AuthCode|String|The Authorization Code provided by the card issuer|
|AuthorizedAmount|Implied Integer|The amount that was actually authorized. This may be different from the requested amount (e.g., partial approvals)|
|BatchDateTime|DateTime|The close date of the batch that contains the transaction|
|BatchId|Integer|The gateway Batch ID that contains this transaction|
|CardBrand|String|Description of the card brand used. Valid values: AMEX, DISCOVER, MASTERCARD, DINERS, and VISA|
|ClerkId|String|The client-supplied Clerk ID (or the Username used to process the transaction if no Clerk ID was provided)|
|ClerkName|String|The client-supplied name of the Clerk who processed the transaction|
|CustomerAddress|String|The client-provided Street Address for the transaction|
|CustomerEmail|String|The client-provided Email Address for the transaction|
|CustomerNumber|String|The client-provided Customer ID|
|CustomerZip|String|The client-provided Zip Code|
|EntryModeId|String|Identifies how the transaction was processed. Valid valus are T1 (Track 1 Data), T2 (Track 2 Data), T3 (Track 1 and 2 Data), KD (Keyed)|
|ExpirationDate|String|Month and Year of the card expiry date in MMYY format|
|FirstName|String|First name of the account holder|
|HolderType|String|A one-character code identifying if the payment method was a personal account (P) or a business/corporate account (O)|
|InvoiceNumber|String|The client-provided Invoice Number|
|LastFour|String|The last four digits of the Primary Account Number (card number)|
|LastName|String|The last name of the account holder|
|MaskedAccount|String|A masked version of the account number used to process the transaction|
|Memo|String|The client-provided "PaymentType" value|
|MerchantAccountId|Integer|The "MerchantAccountCode" for the transaction|
|MerchantAccount|Integer|The "MerchantAccount" for the transaction|
|PaymentMethodId|String|Two letter code that identifies the payment method transaction type. Valid values: AC (Amex), bp (Bank Checking), BD (Bank Card Debit), BS (Bank Savings), DC (Discover Credit), DD (Discover Debit), EC (EBT Cash Benefit), EF (Food Stamps), FL (Fleet One), GF (Fuelman Fleet Wide), GG (General Gift), MC (Master Card Credit), MD (Master Card Debit), MF (Master Card Fleet), MP (Master Card Prepaid), NC (Diner’s Club), VC (Visa Credit), VD (Visa Debit), VF (Voyager), VP (Visa Prepaid), VS (Visa Fleet), WX (Wright Express)|
|ProcessorResponse|String|Description of the response provided by the account issuer|
|PurchaseOrderNumber|String|The client-provided Purchase Order Number|
|RemainingAmount|Implied Integer|The amount of the authorization that is remaining after partial refunds or voids have been applied|
|RequestedAmount|Implied Integer|The amount that was requested to be authorized when the transaction was processed|
|ResellerId|Integer|The gateway reseller ID for the transaction|
|ResponseCode|String|The 3-character <a href="#gateway-message-codes">Gateway Message code</a>|
|SaleDateTime|DateTime|The date and time the transaction was processed|
|SettleAmount|Implied Integer|The amount of the transaction that was actually settled. This may be different than the requested or authorized amounts.|
|SettlementStatus|String|Identifies whether the transaction has been settled yet or not. Valid valuies: Settled, Unsettled|
|TerminalId|String|Reserved for Future Use|
|Token|String|The tokenized account number|
|TransactionId|Long Integer|The unique gateway ID for the transaction|
|TransactionIndustryType|String|A 2-3 character string that identifies what industry or SEC code the transaction was processed under. Valid values: RE (Retail), DM (Direct Marketing), EC (eCommerce), RS (Restaurant), LD (Lodging), PT (Petroleum), POP (Point Of Purchase), PPD (Prearranged Payment and Deposit), CCD (Corporate Credit or Debit), TEL (Telephone Initiated Entry), WEB (Internet Initiated Entry), C21 (Check 21)|
|TransactionSourceIP|String|The IP Address and Port where the transaction request originated|
|TransactionStatus|String|Identifies what state the transaction is in. Valid values: Open, Confirmed, or Voided.|
|TransactionType|String|Identifies the type of transaction that was requested. Valid values: Sale, Sale-Auth (authorization only), Credit, Void, Refund, Increment (incremental authorization).|
|VoidIndicator|Boolean|Indicates whether or not the transaction was voided before the batch was settled|

## Operation Contract

> This method returns a `TransactionSet` object as described above:

```csharp
PublicGetTransactionsByFilter(Credentials credentials, TransactionRowFilter filterObject)

```

At this time, the Reporting API provides only one operation contract for retrieving transactional data.

## Reporting Tips & Examples

There are two types of parameters in the TransactionRowFilter object: DBQuery Filters and Post-Query Filters.

Most of the parameters in the filter are DBQuery filters that are used directly against the persisted data store that contains the transactional data. However, some of the filters are Post-Query filters, meaning the filters are not applied until after the persisted data is retrieved. Post-Query filters have transformational logic that is better suited after the bulk of the query has been processed by the data store.

Filters that are processed directly against the data store also have specific comparison modes that can be utilized for easier queries. Review the comparison modes listed in the <a href"#transactionrowfilter">TransactionRowFilter</a> table for a full list.

### Comparison Types










### Post-Query Filters

The following fields are Post-Query filters. They will not process until after the initial data store query has completed.

- TransactionStatus
- CardBrand

The data used to query on these parameters must be transformed before the filter can be applied. The data store resources are too time-consuming for these filters and they are therefore added after the data store query is completed. <b>You should never use a Post-Query Filter without first limiting the data store query with some DBQuery filters such as a date range and/or the merchant account information.</b>

> Examples:

> Returns all transactions of $1.00 or more:

```xml
<AmountRangeFrom>100</AmountRangeFrom>
```

- GTE = Greater Than or Equal. The query will look for data that is greater than or equal to the data provided in the filter parameter.

> Returns all transactions of $2.00 or less:

```xml
<AmountRangeTo>100</AmountRangeTo>
```

- LTE = Less Than or Equal. The query will look for data that is less than or equal to the data provided in the filter parameter.

> Returns all transactions with Invoice Number 2001:

```xml
<InoviceNumber>2001</InvoiceNumber>
```

- EQUIV = Equals. The query will look for data that exactly matches the data provided in the filter parameter.

> Returns all declined transactions:

```xml
<ResponseCode>D</ResponseCode>
```

- CONTAINS = The query will look for data that contains the data provided in the filter parameter.

> Returns all declined transactions with <a href="#gateway-message-codes">Gateway Message</a> codes D01-D09:

```xml
<ResponseCode>D0</ResponseCode>
```

- INLIST = The query will look for data where the stored data matches one of the comma-delimited entries in the data provided in the filter parameter.

> Returns only those transactions that were declined with <a href="#gateway-message-codes">Gateway Message</a> code D01:

```xml
<ResponseCode>D01</ResponseCode>
```

- N/A = The parameter is either a Boolean parameter or does not affect the data filtering process.

> Returns only those transactions that were declined with <a href="#gateway-message-codes">Gateway Message</a> code D01:

```xml
<ResponseCode>D01</ResponseCode>
```

> Provides those transactions where the <a href="#gateway-result-codes">Gateway Result code</a> is equal to 00000, 00001, or 10012 only:

```xml
<TransResults>00000,00001,10012</TransResults>
```

NOTE: `ExcludeTransResults` must be used with `TransResults`. It modifies the behavior of the TransResults field.

> Return all transactions where <a href="#gateway-result-codes">Gateway Result code</a> code is NOT equal to 00000, 00001, or 10012:

```xml
<TransResults>00000,00001,10012</TransResults>
<ExcludeTransResults>1</ExcludeTransResults>
```

# Response Codes

## AVS Response Codes

<aside class="warning">
 You should always inspect the AVSResult and CVResult fields as these can be good indicators of potential fraud. If you see a AVSResult or CVResult code that you do not want to accept because it may be too risky (such as "No Match" on the submitted Zip code), then you should submit a void transaction to cancel the authorization and advise the cardholder that their transaction has been declined.
</aside>

Response Code | Description
------------- | -----------
00 | AVS Error - Retry, System unavailable or Timed out
40 | Address not available (Address not verified)
43 | Street address not available (not verified), ZIP matches
44 | Address failed
45 | Street address and ZIP don't match
46 | Street address doesn't match, 5-digit ZIP matches
47 | Street address doesn't match, 9-digit ZIP matches
4A | Street address or ZIP doesn't match
4D | Street address matches, ZIP does not
4E | Street address and 5-digit ZIP match
4F | Street address and ZIP match
53 | Account holder name incorrect, billing postal code matches
55 | Unrecognized response
5C | Account holder name incorrect, billing address matches
5F | Account holder name incorrect, billing address and postal code match
70 | Account holder name matches
73 | Account holder name and billing postal code match
7C | Account holder name and billing address match
7F | Account holder name, billing address and postal code match
80 | AVS service not supported by issuer - Issuer doesn't participate in AVS

## CVV Response Codes

<aside class="warning">
 You should always inspect the AVSResult and CVResult fields as these can be good indicators of potential fraud. If you see a AVSResult or CVResult code that you do not want to accept because it may be too risky (such as "No Match" on the submitted Zip code), then you should submit a void transaction to cancel the authorization and advise the cardholder that their transaction has been declined.
</aside>

Response Code | Description
------------- | -----------
M | Matches
N | No match
P | Not processed
S | Should be present
U | Issuer is not certified
X | Unrecognized reason

## Gateway Result Codes

Response Code | Description
------------- | -----------
00000 | Successful request
00001 | Partial Authorization
10001 | Missing Reference Number
10002 | Invalid Card Number - Blank/Null
10003 | Invalid Card Type - Doesn't match accepted card types
10004 | Invalid Expiration Date - Blank/Null
10005 | Invalid Security Code - Blank/Null
10007 | Invalid Card Number - Not Numeric
10008 | Invalid Length for card type 
10009 | Invalid Expiration Date - Card Expired
10010 | Invalid Security Code - Not Numeric
10011 | Invalid Transaction ID 
10012 | Invalid Card Number - Failed Mod10
10013 | Invalid Expiration Date Value
10014 | Invalid Security Code Length
10017 | Invalid Expiration Date - Invalid Month
10018 | Invalid Expiration Date - Invalid Year
10019 | Invalid Expiration Date
10020 | Invalid Client Identifier
10021 | Invalid Request Element – Missing Element
10022 | Invalid Request Type
10023 | Password Expired
10024 | Invalid Credentials
10025 | Invalid Zip – Not Numeric
10026 | Invalid Zip – Wrong Length
10027 | Invalid Amount – Blank/Null
10028 | Invalid Amount – Not Numeric
10029 | Invalid Request Date/Time
10030 | Invalid Token
10031 | Invalid Track
10032 | Invalid Track Identifier
10033 | Invalid Void Request
10034 | Invalid Encryption ID
10035 | Invalid Account Number – Blank/Null
10036 | Invalid Account Number – Not Numeric
10037 | Invalid Payment Type – Blank/Null
10038 | Invalid Payment Type – Unrecognized Payment Type
10039 | Invalid Account Number – Account Number Does Not Exist
10040 | Missing Required Pass-Thru Data Element
10041 | Missing / Invalid BIN
10042 | Already Voided
10050 | Incorrect Trace Number
10051 | Incorrect Merchant Setup
10052 | Processing Network Error
10053 | Credit Card Entry Refused by Receiver
10054 | Mandatory Field Error
20001 | Tokenization Service Connection Error
20002 | Beyond Pay Internal Server Error
20003 | Client Service Unavailable
20004 | Payment Service Sensitive Data Timeout
30004 | Invalid Request Message
30005 | Invalid Response Message
30006 | New Password Doesn't Match Confirmation Password
30007 | New Password Too Weak
30008 | Missing Payment Card Data
30009 | Internal Payment Card Data Error
30010 | Invalid Record Format
30011 | Invalid Merchant Number (from Gateway)
30012 | Bad Card Number (from Gateway)
30013 | Invalid Store Number
30020 | Invalid Transaction Industry Type
30021 | Missing Transaction Industry Type
30022 | Processing Network Unavailable
30023 | Invalid Account Number
30024 | No Account
30025 | Invalid Security Code
30026 | Invalid Amount
30027 | Refund limit is reached for the day (occurs when merchant has reached the refund limit allowed per day on the account)
30028 | Settlement Failed
30029 | Transaction Error
30030 | Transaction data integrity validation error
30032 | Denied by customer’s bank
30033 | Insufficient funds
30034 | Hold - Pick up card
30035 | Incorrect PIN
30036 | Duplicate Transaction
30037 | Card reported lost
30038 | Card reported stolen
30039 | Service not allowed
30040 | Stop Recurring
30041 | Unattempted Batch Decline
30042 | Maximum transaction limit is exceeded at the moment. Try processing your transaction tomorrow.
30043 | Re-enter Transaction
30044 | Unmapped decline
30045 | Billing profile configuration error
30046 | Pin Try Exceeded
30047 | Refund was not processed/received
30048 | Chargeback received
30049 | Processing Canceled by User
30050 | Invalid Transaction Category
30051 | Invalid Verification Status
30052 | Invalid Terminal Type
30053 | Invalid Petroleum Product Type
30060 | Invalid IApp User Id
30061 | Account insert failed
30062 | Merchant insert failed
30070 | New Password Previously Used
30071 | Missing Clerk Id
30072 | Call for Authorization
30073 | Card is Restricted
30074 | Declined due to fraud rules
30075 | Bank Account Blacklisted
30076 | Declined due to insufficient information
30077 | Rejected by the processor
30078 | Account Closed
30079 | Invalid Account
30080 | Account can not process ACH
30082 | Invalid MICR
30083 | Customer opt out check Conversion
30100 | Invalid Account Data – Blank/Null
30101 | Invalid EMV Tag Data – Blank/Null
40001 | Lodging Reauth Failed
40002 | Missing Lodging Folio Number
80000 | Gateway Services Available
80001 | Gateway Services Unavailable
80002 | Invalid Purchase Token
80003 | More than one result found for search criteria
80004 | More than one service fee block received in request message
80005 | Cascade Void. Indicates that the transaction was successfully authorized (fully or partially) and then voided due to an auto-void policy setting.  Only occurs on principal transactions and only when the accompanying service fee was either declined or voided due to an auto-void policy setting.
80006 | Partial Auto Void. Indicates that the transaction was partially authorized and then voided due to an auto-void policy setting.  Can occur on a service fee or principal transaction.
80007 | Database query processing error.  Can occur on a Find Transaction request if the data requested is unavailable.
80008 | Invalid GatewayTransID
80009 | Invalid MerchantCode
800010 | Invalid MerchantAccountCode
800011 | Transaction not found
800012 | Invalid Length for PersistData
90000 | Token Store failed to encrypt a token
90001 | Token Store failed to decrypt a token
99999 | Unknown Error

## Gateway Message Codes

|Gateway Message Code|Message|
|--- |--- |
|A01|Approved: XXXXXX (approval code)|
|A02|Credit Posted|
|A03|Void Posted (Auth Reversed)|
|A04|No Update|
|A05|Partially Approved|
|A06|Void Posted (Auth Not Reversed)|
|A07|Partial Void Posted|
|A08|Partial Refund Posted|
|A09|Incremental Auth Posted|
|A10|Request Accepted|
|A11|Approval (Reversal failed)|
|A60|Terminal Offline Approval - EMV/Chip|
|A61|Terminal Offline Approval - Swipe|
|A62|Terminal Offline Approval - Credit|
|D01|Denied by customer's bank|
|D02|Invalid Expiration Date|
|D03|Insufficient funds|
|D04|Hold - Pick up card|
|D05|Invalid card number|
|D06|No account|
|D07|Incorrect PIN|
|D08|CSC is invalid|
|D09|Duplicate Transaction|
|D10|Card reported lost/stolen|
|D11|Card reported stolen|
|D12|Service not allowed|
|D13|Stop Recurring|
|D15|Maximum transaction limit is exceeded|
|D16|Card is expired|
|D17|Re-enter Transaction|
|D18|Bad Amount|
|D19|Unmapped decline|
|D20|Billing profile configuration error|
|D21|PIN try excdeed|
|D22|Refund was not processed/received|
|D24|Chargeback received|
|D25|Refund limit is reached for the day|
|D26|Settlement Failed|
|D27|Transaction Error|
|D28|Cashback limit exceeded/Cashback unavailable|
|D29|Card is restricted|
|D30|Call for Authorization|
|D31|Declined due to fraud rules|
|D32|Declined due to fraud engine decision|
|D33|Incorrect merchant setup|
|D34|Merchant profile configuration issue|
|D35|Card chip decline|
|E02|Processing Network Unavailable|
|E03|Transaction data integrity validation error|
|E04|Refund limit is reached for the day|
|E06|Card is blacklisted|
|E07|Tokenization is not supported|
|E08|Refunds are not allowed|
|E09|Processing Network Error|
|E10|3D Secure Verification Failed|
|E31|Declined due to pre-processing rules|
|X01|Processing Cancelled by User|
|X02|Pending processing|
|X03|3D Secure Verification Required|
|X04|Processing cancelled: the request has expired|

# Test Cards and Triggers

## Cards and Checks

You can use the following card numbers for testing. CVV numbers are 1234 or 1111 for Amex; all others are 111 or 999.

Card Type | Card Brand | Card Number | Expiration Date
--------- | ---------- | ----------- | ---------------
Credit | Visa | 4111111111111111 | 10/25
Credit | MasterCard | 5499740000000057 | 10/25
Credit | Discover | 6011000991001201 | 10/25
Credit | Amex | 371449635392376 | 10/25
Debit | Visa | 4217651111111119 | 10/25
Debit | MasterCard | 5149612222222229 | 10/25

The following information may be used for ACH / eCheck testing:

Bank Account Number | Routing Number | Account Type
--------- | ---------- | -----------
4099999992 | 021000021 | Checking

## Trigger Amounts

As part of your development and testing efforts, the amount ranges specified below can be used to trigger specific response codes from the server. These test ranges may be used with any valid card number.

### Card Response Triggers

Amount | Response Code | Response Message
-------------- | --------- | ----------- 
0.01 - 0.99 | D01 | Denied by customer's bank (Do Not Honor)
1.00 | A01 | Approved
1.01 - 4.98 | D01 | Denied by customer's bank (Do Not Honor)
4.99 | 20002 | Internal ServerError
5.00 - 69.99 | A01 | Approved
70.00 - 79.99 | D05 | Invalid card number
80.00 - 89.99 | D10 | Card reported lost/stolen
90.00 - 99.99 | D30 | Call for authorization
100.00 - 109.99 | D04 | Pick up card
110.00 - 119.99 | D08 | Invalid security code
120.00 - 129.99 | D03 | Insufficient funds
130.00 - 139.99 | E02 | Processing network unavailable
140.00 - 149.99 | E09 | Internal ServerError
150.00 - 159.99 | A05 | Partially approved [approved amount will be $10 less than the requested amount]
170.00 - 181.99 | A01 | Approved
182.00 - 1999.99 | D01 | Denied by customer's bank (Do Not Honor)

### ACH/eCheck Response Triggers
Amount | Response Code | Response Message
-------------- | --------- | ----------- 
170.00 - 171.99 | C01 | Customer's account number is incorrect
172.00 - 173.99 | C02 | Customer's routing number is incorrect
174.00 - 175.99 | C03 | Customer's routing number and DFI account numbers are incorrect
176.00 - 177.99 | C04 | Customer's name is incorrect
178.00 - 179.00 | C05 | Customer's account type (Savings/Checking) is incorrect
180.00 - 181.99 | C06 | Account number is incorrect and transaction is being routed to the wrong type of account

### AVS Response Triggers
ZIP Code | AVS Response Code | AVS Response Message
-------------- | --------- | ----------- 
11111 | 00 | AVS Error - Retry, System unavailable, or Timed out
22222 | 46 | Street address doesn't match, 5-digit ZIP matches
33333 | 43 | Street address not available (not verified), ZIP matches
44444 | 40 | Address failed
55555 | 4F | Street address and ZIP match

### Refund ("Blind Credit") Response Triggers
Amount | Response Code | Response Message
-------------- | --------- | ----------- 
0.01 - 4.99 | D01 | Denied by customer's bank (Do Not Honor)
5.00 - 69.99 | A02 | Credit Posted
70.00+ | D01 | Denied by customer's bank (Do Not Honor)