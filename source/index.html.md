---
title: Beyond Pay Gateway API Reference

toc_footers:
  - <a href='mailto:BeyondPay@getBeyond.com'>Get an API Key</a>
  - ______________
  - <a href='https://www.getbeyond.com/'>www.getbeyond.com</a>
  - ©2019 Above & Beyond - Business Tools and Services for Entrepreneurs, Inc. All Rights Reserved.
  - <a href='https://www.getbeyond.com/privacy-policy/'>Privacy Policy</a>
  - <a href='https://www.getbeyond.com/ccpa/'>CCPA Consumer Privacy</a>

search: true
---

# Introduction to Beyond Pay

> <a href="mailto:BeyondPay@getBeyond.com">Get your API keys</a> and get moving!

Welcome to the Beyond Pay Gateway API! Beyond Pay is a powerful gateway that enables you to securely accept many different payment types. Plus, by processing through Beyond Pay, you are supporting Beyond's commitment to our philanthropic cause.

The primary integration options offered by the Beyond Pay Gateway include:

* **TokenPay** – is an extension of Beyond Pay that combines client-side and server-side technologies for PCI-compliant online or mobile payment capture.
* **PayGuardian** – a lightweight middleware application that integrates seamlessly into Point of Sale (POS) software and facilitates the secure collection of cardholder data insulating the integrator from the scope of PA-DSS and the requirements of EMV certification
* **BridgeComm** – a set of robust web service APIs for payment processing


# Online Payments

## Getting Started

> To get started, include this script on your checkout page:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script> 
<script
  src="https://api-test.getbeyondpay.com/Bridgepay.WebSecurity/TokenPay/js/tokenPay.js">
</script>
```

> Next, create an instance of TokenPay:

```javascript
var tokenpay = TokenPay('your-public-key');
```

> Replace `your-public-key` with your publishable public key.

TokenPay maximizes the user experience by allowing for the capture of sensitive card data within the payment form of the merchant’s website or mobile application. The consumer remains on the merchant’s payment page at all times during the checkout process.

TokenPay is an integration interface for Beyond Pay Gateway which facilitates online card payments in a manner that ensures that no sensitive card data ever touches your servers so your integration can operate with minimized scope of PCI.

To ensure that merchants are eligible for the simplest PCI validation method, Self-Assessment Questionnaire A (SAQ-A), TokenPay utilizes

* **Isolation** – Beyond Pay Gateway hosts the sensitive cardholder data input fields. The fields are injected into your form as an HTML iframe thus isolating your page and your server from card sensitive data.
* **Tokenization** – in order to execute transactions against the user’s card, TokenPay replaces the sensitive cardholder data with a non-sensitive surrogate value (token). The token is generated via the use of the TokenPay JavaScript library and your payment form.
* **Segregation** – Requests for charges against the user’s card are made server-to-server – not in the browser or mobile app where it is publicly visible. The tokenized card data is submitted to your server where a secure server-to-server request is made to execute the transaction.
* **Public/Private Keys** – The injection of the TokenPay hosted input fields and card tokenization is authenticated via a public key assigned to the merchant. API requests to execute charges against the tokenized card are made by the backend server and are authenticated with a private key assigned to the merchant.

### TokenPay.js

> <b>Sandbox (Testing):</b>

```html
https://api-test.getbeyondpay.com/Bridgepay.WebSecurity/TokenPay/js/tokenPay.js
```

> <b>Live (Production):</b>

```html
https://api.getbeyondpay.com/WebSecurity/TokenPay/js/tokenPay.js
```


TokenPay.js is the JavaScript library for building online or mobile checkout flows with Beyond Pay Gateway. With it, you can collect sensitive data from the cardholder and create tokens for securely sending the data to your server.

TokenPay.js provides a ready-made UI component for collecting the sensitive card data from the user. TokenPay.js then tokenizes the information without ever having to touch your server.

The TokenPay.js UI component includes:

* Automatic formatting of card information as it is entered
* Validation of card information as it is entered
* Responsive design that works on user’s screen or mobile device
* Customizable styling to match your website's look and feel

### HTTPS Requirements

All submission of payment information using TokenPay.js is made via a secure HTTPS connection. However, to protect yourself from man-in-the-middle attacks and to prevent your users from experiencing mixed content warnings in their browser, you <b>MUST</b> serve the page with your payment form over HTTPS.

<aside class="notice">
You must replace <code>your-public-key</code> with your publishable public API key.
</aside>

## Create a Payment Form

> To determine where to insert the UI components, create empty DOM elements with unique IDs within your payment form.

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

> If you want to customize the style of the card entry area, create a hidden `<div>` element to contain your styling. The `id` of this element MUST be `customStyles`.

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
  useStyles: false
});
```

> If you have created the `customStyles` element to style the card entry area, change the value of `useStyles` to `true`.


To securely collect sensitive card details from your users, TokenPay.js creates UI components for you that are hosted by Beyond Pay Gateway. These are then inserted into your payment form.

The TokenPay element simplifies the form and minimizes the fields required by inserting a single input field that securely collects all needed card data.

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

The card data collected by the TokenPay element is converted into a token. If there are any errors in the collection of the card data or creation of the token, information is automatically displayed in the `errorElement` of your payment form.

## Create a Sale Transaction

> <b>Sandbox (Testing):</b>

```html
https://api-test.getbeyondpay.com/PaymentService/RequestHandler.svc
```

> <b>Live (Production):</b>

```html
https://api.getbeyondpay.com/PaymentService/RequestHandler.svc
```

> The following XML sample message is to be posted to the `RequestHandler.postRequest` method, according to the <a href='https://www.dropbox.com/s/1tg479a9n8e3dvt/BridgeComm%20Communication%20Interface%20API%20Guide.pdf?dl=0'>BridgeComm Interface API Guide</a>:

```xml
<requestHeader><ClientIdentifier>SOAP</ClientIdentifier>
<TransactionId>{transactionId}</TransactionId>
<RequestDateTime>{requestDateTime}</RequestDateTime>
<PrivateKey>{yourPrivateKey}</PrivateKey>
<AuthenticationTokenId>{token}</AuthenticationTokenId>
<RequestType>004</RequestType>
<requestMessage> 
<TransIndustryType>EC</TransIndustryType>
<TransactionType>sale</TransactionType> 
<Amount>{amountInPennies}</Amount> 
<HolderType>P</HolderType> 
<AcctType>R</AcctType> 
<CurrencyCode>USD</CurrencyCode> 
</requestMessage>
</requestHeader>
```

Once you have securely collected and tokenized your user’s card data using TokenPay.js, you can charge the card or save the token for future use. Charges against the cards that are tokenized in the browser or mobile app, are *ONLY* made from your server.

On your server, collect the token information and the form POST parameters submitted by your form.

Now submit the token and parameters according to the <a href='https://www.dropbox.com/s/1tg479a9n8e3dvt/BridgeComm%20Communication%20Interface%20API%20Guide.pdf?dl=0'>BridgeComm Interface API Guide</a>, with the following substitutions:

* `{transactionId}` - unique transaction ID generated by your backend for tracking purposes
* `{requestDateTime}` - date and time of the transaction in `yyyMMddHHmmss` format
* `{yourPrivateKey}` - your private API key
* `{token}` - token delivered in the submission of your payment form
* `{amountInPennies}` - transaction amount in pennies ($1.25 would be 125)


# In-Person Payments

## PayGuardian

> <a href='https://www.dropbox.com/s/31515dk9s1hptpu/BridgePay%20Gateway%20Certified%20Device%20Matrix.pdf?dl=0'>CERTIFIED DEVICES</a>

Point‐of‐Sale (POS) systems that process sensitive payment information are required to certify their payment applications to the Payment Application Data Security Standard (PA‐DSS). The addition of EMV certification and continued need for both encryption and tokenization has become a concern for both merchants and integrators. Instituting and maintaining these standards requires significant financial and employee resources in order to adhere to the Payments Card Industry Data Security Standards (PCI DSS) compliance requirements. Subsequently, any changes made in the POS system, may require a partial or full recertification, which increases the cost and time to market. Beyond has engaged these issues through our product line, the PayGuardian suite, to better serve the needs of our integrators and merchants.

PayGuardian is a lightweight, highly secure client application that integrates seamlessly into POS applications. PayGuardian facilitates the transaction process by handling the collection and transmission of sensitive payment information as an out of scope PA-DSS solution, thereby offloading the certification responsibility from merchants and integrators. PayGuardian is EMV enabled, handles point to point encryption, and tokenizes all transactions to ensure transaction processing is seamless and secure.

## PayGuardian Desktop

> <a href='https://www.dropbox.com/s/9mhfffnqknd2q7y/PayGuardian-2.4.4.zip?dl=0'>Download PayGuardian Desktop v 2.4.4</a>

> <a href='https://www.dropbox.com/s/2oczvikko1olz1a/PayGuardian%20Developer%20Guide.pdf?dl=0'>PayGuardian Desktop Developer Guide</a>

> <a href='https://www.dropbox.com/s/o7itaspp454c5al/PayGuardian%20Installation%20Guide%20v2.4.3.pdf?dl=0'>PayGuardian Desktop Installation Guide</a>

> <a href='https://www.dropbox.com/s/lq6l4lpmj05f29p/PayGuardian%20User%20Guide%20v2.4.1.pdf?dl=0'>PayGuardian Desktop User Guide</a>

> Sample C# DLL integration:

```c#
private void ProcessCreditCard_Click(object sender, EventArgs e)
  {
    // 1. First create a Payment Page
    hostName=hostname.Text;
    PaymentPage pg=newPaymentPage();
    PaymentRequest paymentRequest=pg.PaymentRequest;
    paymentRequest.TenderType=PaymentRequest.ParseTenderType(TenderType.Text);
    paymentRequest.TransType=PaymentRequest.ParseTransType(TransType.Text);

    // 2. Next, set the PayLink Properties
    #regionSetPayLinkProperties

    // Set the only required field (Amount)
    paymentRequest.Amount = this.Amount.Text.ToString();

    // 3. Display the payment processing page
    ShowPageResult result = null;
    try
    {
      Result = pg.ShowPage();
    }
    catch (Exception)
    {
      // Error while processing payment
      MessageBox.Show("Error Processing Payment");
    }
    PaymentResponse paymentResponse = pg.PaymentResponse;

    // 4. Display the result of the transaction
    #region Show the PayLink Result

    If (result != null && result.code == ShowPageResultCode.OK)

   //TO DO - finish

```

PayGuardian Desktop (for Windows) comes with an executable installer file that integrators may incorporate into their Point-of-Sale system installation. A Windows object library has also been included to facilitate easy integrations with POS applications. The object library is accessible using Component Object Model (COM) or .NET technology.When invoked, PayGuardian displays a basic frame that encapsulates the browser, fetching and rendering the Virtual Terminal (VT)page. The object window is configurable, and integrators can brand the user interface using cascading style sheets. The VT object window holds focus, floating on top of all other running applications.

<aside class="success">
For development and testing, use this sandbox registration key: <b><code>H75RCGRV</code></b>. A new registration key will be required for live/production transaction processing.
</aside>

## PayGuardian iOS SDK

> <a href='https://www.dropbox.com/s/g340i0bsp4tjo01/PayGuardian-iOS-2.5.zip?dl=0'>iOS Framework</a>

> <a href='https://www.dropbox.com/s/ffdc90z7thgnxw0/PayGuardian%20iOS%20Framework%20Developer%20Guide%20v2.5.0.pdf?dl=0'>iOS Developer Guide</a>

> <a href='https://www.dropbox.com/s/0wt5jp013fszfnd/PayGuardian-iOS-Test.zip?dl=0'>Test iOS App</a>

> Create a BPNPaymentRequest object:

```objective_c
-(instancetype) initInvoiceNumber:(NSString *_Nonnull) invoiceNumber
pnRefNum:(NSString *_Nullable) pnRefNum 
amount:(NSDecimalNumber *_Nullable) amount 
tipAmount:(NSDecimalNumber *_Nullable) tipAmount 
cashBackAmount:(NSDecimalNumber *_Nullable) cashBackAmount 
tenderType:(NSString *_Nonnull) tenderType 
transactionType:(NSString *_Nonnull) transactionType 
username:(NSString *_Nonnull) username 
password:(NSString *_Nonnull) password 
merchantCode:(NSString *_Nonnull) merchantCode 
merchantAccountCode:(NSString *_Nonnull) merchantAccountCode 
paymentAccountNumber:(NSString *_Nullable) paymentAccountNumber 
token:(NSString *_Nullable) token 
expirationDate:(NSString *_Nullable) expirationDate 
terminalCommConfig:(TerminalCommConfig *_Nonnull) terminalCommConfig
industryType:(NSString *_Nonnull) industryType 
healthCareData:(BPNHealthCare *_Nullable) healthCareData 
bankAccountNumber:(NSString *_Nullable) bankAccountNumber
routingNumber:(NSString *_Nullable) routingNumber
partialApproval:(BOOL) partialApproval
enableTpi:(BOOL) enableTpi
signatureData:(NSString *_Nullable) signatureData
disableAmountConfirmation:(BOOL) disableAmountConfirmation
testMode:(BOOL) testMode;
```

> Construct the PayGuardianTransaction object:

```objective_c
initWithPaymentRequest:(BPNPaymentRequest *)request;
```

> The run method with completion is:

```objective_c
-(void)runOnCompletion:(void (^)(BPNPayment *payment, NSError *error)) onCompletion onStateChanged:(void (^)(PayGuardianTransactionState state)) onStateChanged;
```

> Implement a handler for the returned BPNPayment response:

```objective_c
BPNPayment.BridgeCommResponse:
transactionID: 8888
requestType: 004
responseCode: 0
responseDescription: Successful Request
token: 11110000000068530608
expirationDate: 1225
authorizationCode: 290144
originalReferenceNumber: MCC7754741020
authorizedAmount: $5.50
originalAmount: $5.50
gatewayTransactionID: 214973401
gatewayMessage: A01 -Approved
internalMessage: Approved: 290144 (approval code)
gatewayResult: 00000
AVSMessage:
AVSResponse:
CVMessage:
CVResult:
transactionCode: (null)
transactionDate: 20161020
remainingAmount: $0.00
ISOCountryCode: (null)
ISOCurrencyCode: USD
ISOTransactionDate: 2016-10-20 14:32:47.86
ISORequestDate: 2016-10-20 14:32:47.86
networkReferenceNumber: MCC7754741020
merchantCategoryCode:
networkMerchantID: 518564010126944
networkTerminalID: PPB01.
cardType: Mastercard
maskedPAN: 5***********0608
responseTypeDescription: sale
isCommercialCard: False
streetMatchMessage:
secondsRemaining: (null)
merchantCode: (null)
merchantAccountCode: (null)
merchantName: (null)
receiptTagData: (null)
issuerTagData: (null)
applicationIdentifier: (null)
terminalVerificationResults: (null)
issuerApplicationData: (null)
transactionStatusInformation: (null)
```

PayGuardian iOS is a lightweight, highly secure iOS framework library that integrates seamlessly into mPOS applications. PayGuardian iOS facilitates the transaction process by handling the collection and transmission of sensitive payment information as an out of scope PA-DSS solution, thereby offloading the certification responsibility from merchants and integrators. PayGuardian iOS is EMV enabled, handles point to point encryption, and tokenizes all transactions to ensure transaction processing is seamless and secure.

Programmatically, a PayGuardian iOS transaction is comprised of a four step process:

* Create a BPNPaymentRequest object.
* Pass the BPNPaymentRequest object to the constructor of a PayGuardianTransaction object.
* Call the runOnCompletion method and provide an implementation for the completion.
* Implement a handler for the returned BPNPayment and/or NSError.

<aside class="success">
For development and testing, use this sandbox registration key: <b><code>H75RCGRV</code></b>. A new registration key will be required for live/production transaction processing.
</aside>

## PayGuardian Android SDK

> <a href='https://www.dropbox.com/s/zoa1s4n9s8cleob/PGAndroid-2.5.zip?dl=0'>PayGuardian for Android</a>

> <a href='https://www.dropbox.com/s/wem8vf780lffxfx/PayGuardian%20Android%20Developer%20Guide%20%20v2.5.0.pdf?dl=0'>Android Developer Guide</a>

> <a href='https://www.dropbox.com/s/35d2k95ltrrw7nm/App2AppSampleProject.zip?dl=0'>Android app-to-app sample project</a>

> Java sample (App-to-App method):

```java
public void processTransaction(String paymentRequestXml)
  {
    final int PAYGUARDIAN_REQUEST_CODE = 102;
    Intent sendIntent = new Intent(android.content.Intent.ACTION_SEND);
    sendIntent.setType("text/plain");
    sendIntent.putExtra(Intent.EXTRA_TEXT, paymentInputXml);

    PackageManager pm = getApplicationContext().getPackageManager();
    List<ResolveInfo> activityList = pm.queryIntentActivities(sendIntent, 0);

    for (final ResolveInfo app : activityList)
    {
      if ((app.activityInfo.name).contains("ProcessSecurelyActivity"))
      {
        final ActivityInfo activity = app.activityInfo;
        final ComponentName name = new ComponentName(activity.applicationInfo.packageName, activity.name);

        sendIntent.setComponent(name);

        startActivityForResult(sendIntent, PAYGUARDIAN_REQUEST_CODE);

        break;
      }
    }
```

PayGuardian Android is a lightweight, highly secure Android application that integrates seamlessly into mobile POS (mPOS) applications. PayGuardian Android facilitates the transaction process by handling the collection and transmission of sensitive payment information as an out of scope PA-DSS solution, thereby offloading the certification responsibility from merchants and integrators. PayGuardian Android is EMV enabled, handles point to point encryption, and tokenizes all transactions to ensure transaction processing is seamless and secure.

### Process Flow

* The mPOS application collects transaction data, such as the dollar amount, invoice number, tender type, transaction type, merchant account information, etc.
* The mPOS application constructs the transaction requesting an XML format upon the selection of the Process button.
* PayGuardian obtains the card information via the claiming of the mPOS device using the Device USB Host connection and validates the transaction request object.
* The mPOS device prompts to swipe or insert the card and transmits the card information to the PayGuardian application, which captures the card data as a swiped or EMV transaction respectively.
* PayGuardian constructs the payload request and transmits the transaction request to the Beyond Pay Gateway.
* PayGuardian transmits the transaction response returned from the Gateway back to the mPOS application.
* The mPOS application implementation responds accordingly to the transaction response.

For the App-to-App integration method, the PayGuardian Android application is accessed by starting an activity with an intent which encapsulates a request payload.

<aside class="success">
For development and testing, use this sandbox registration key: <b><code>H75RCGRV</code></b>. A new registration key will be required for live/production transaction processing.
</aside>

## PayGuardian Cloud

> <a href='https://pgc.bridgepaynetsecuretx.com/'>PayGuardian Cloud API</a>

> `POST https://pgc.bridgepaynetsecuretest.com/req/payment`

```json
{
"locationID": "your-locationID",
"terminalID": "00000000-0000-0000-0000-000000000000",
"username": "your_user_name",
"password": "your_password",
"merchantAccountCode": "your_merchantAccountCode",
"merchantCode": "your_merchantCode",
"mode": "UAT",
"amount": "10.00",
"softwareVendor": "your_POS_name",
"tenderType": "CREDIT",
"transType": "SALE"
}
```

PayGuardian Cloud is designed for cloud-based Point-of-Sale systems, and delivers the same scope removal and easy EMV acceptance as other versions of PayGuardian. PayGuardian Cloud is operating system independent, and is installed on the merchant's router as a network appliance.

<aside class="notice">
PayGuardian Cloud is currently in limited beta testing. <a href='mailto:BeyondPay@getBeyond.com'>Contact us</a> if you are interested!
</aside>

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
DateRangeFrom |
DateRangeTo |
EndPartialAccountNumber |
ExcludeTransResults |
ExcludeVoid |
ID |
InvoiceNumber |
MerchantAccountId |
MerchantId |
PaymentMethodID |
PurchaseOrderNumber |
ResellerID |
ResponseCode |
SettlementStatus |
Skip |
Take |
TransactionSourceIP |
TransactionStatus |
TransResults |

The TransResults field works by mapping the BridgeComm 5-digit response code back to the gateway response code (the ResponseCode field in this contract).  In some cases, more than one mapping may exist for a given code.  It is recommended that you use the ResponseCode field for more granular filtering. The ExcludeTransResults field can modify the behavior of the TransResults field by establishing a “not in” condition.

### TransactionSet

TODO: finish

### TransactionRow

TODO: finish

# Response Codes

## PayGuardian Response Codes

Response Code | Description
------------- | -----------
0 | Approved
1 | Declined
2 | Error
12 | EMV Chip Declined

## Gateway Response Codes

Response Code | Description
------------- | -----------
00000 | Successful request
00001 | Partial Authorization
TODO | FINISH TABLE + include A01 codes


## AVS Response Codes

Response Code | Description
------------- | -----------
A | Street addresses match, but postal/ZIP does not or was not provided
B | Street addresses match, but postal/ZIP code is not verified due to incompatible formats
TODO | FINISH TABLE

## CVV Response Codes

Response Code | Description
------------- | -----------
(blank) | CVV was not verified
1 | CVV failed verification
TODO | FINISH TABLE

# Testing & Certification

## Certification

When you are finished developing your interface to one of the Beyond Pay solutions, please <a href='mailto:BeyondPay@getBeyond.com'>contact us</a> to get certified and obtain your production keys!

## Test Cards and Checks

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
