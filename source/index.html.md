---
title: Beyond Pay Gateway API Reference

toc_footers:
  - <a href='https://forms.gle/AMxdRZTsS6skq2DEA'>Get an API Key</a>
  - ______________
  - <a href='https://www.getbeyond.com/'>www.getbeyond.com</a>
  - ©2019 Above & Beyond - Business Tools and Services for Entrepreneurs, Inc. All Rights Reserved.
  - <a href='https://www.getbeyond.com/privacy-policy/'>Privacy Policy</a>
  - <a href='https://www.getbeyond.com/ccpa/'>CCPA Consumer Privacy</a>

search: true
---

# Introduction to Beyond Pay

> <a href='https://forms.gle/AMxdRZTsS6skq2DEA'>Get your API keys</a> and get moving!

> Contact us if you have questions or need any help! <a href='mailto:BeyondPayIntegrations@getbeyond.com'>BeyondPayIntegrations@getbeyond.com</a>

Welcome to the Beyond Pay Gateway API! Beyond Pay is a powerful gateway that enables you to securely accept many different payment types. Plus, by processing through Beyond Pay, you help put disadvantaged kids through college just by getting paid!

The primary integration options offered by the Beyond Pay platform include:

* **TokenPay.js** – is an extension of Beyond Pay that combines client-side and server-side technologies for PCI-compliant online payment capture
* **Beyond Pay API** - a set of robust web service APIs offering support for credit cards, ACH/checks, tokenization, and more
* **PayGuardian** – a lightweight middleware application that integrates seamlessly into Point of Sale (POS) software and facilitates the secure collection of cardholder data insulating the integrator from the scope of PA-DSS and the requirements of EMV certification


# Online Payments

## Getting Started

> To get started, include these scripts on your checkout page:

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

> Replace `your-public-key` with your publishable <a href='https://forms.gle/AMxdRZTsS6skq2DEA'>public key</a>.

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

TokenPay.js provides a ready-made UI component for collecting the sensitive card data from the user. TokenPay.js then tokenizes the information without it ever having to touch your server.

The TokenPay.js UI component includes:

* Automatic formatting of card information as it is entered
* Validation of card information as it is entered
* Responsive design that works on user’s screen or mobile device
* Customizable styling to match your website's look and feel

### HTTPS Requirements

All submission of payment information using TokenPay.js is made via a secure HTTPS connection. However, to protect yourself from man-in-the-middle attacks and to prevent your users from experiencing mixed content warnings in their browser, you <b>MUST</b> serve the page with your payment form over HTTPS.

<aside class="notice">
You must replace <code>your-public-key</code> with your publishable <a href='https://forms.gle/AMxdRZTsS6skq2DEA'>public API key</a>.
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

The card data collected by the TokenPay element is posted from the client browser to Beyond Pay Gateway where it is converted into a token. If there are any errors in the collection of the card data or creation of the token, information is automatically displayed in the `errorElement` of your payment form.

The token is stored as a hidden input value and passed to your server on form submission.

## Perform a Sale Transaction

> With the token and other form fields obtained, now construct the XML payload:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>{transactionId}</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>{requestDateTime}</RequestDateTime>
    <PrivateKey>{yourPrivateKey}</PrivateKey>
    <AuthenticationTokenId>{token}</AuthenticationTokenId>
    <requestMessage>										
        <SoftwareVendor>{yourSoftwareName}</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>P</HolderType>
        <Amount>{amountInCents}</Amount>
        <CurrencyCode>USD</CurrencyCode>
    </requestMessage>
</requestHeader>';

```
> Encode the XML payload in Base-64 and package it within a SOAP envelope:

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

> POST the SOAP envelope to the appropriate endpoint:

> <b>Sandbox (Testing):</b>

```html
https://api-test.getbeyondpay.com/PaymentService/RequestHandler.svc
```

> <b>Live (Production):</b>

```html
https://api.getbeyondpay.com/PaymentService/RequestHandler.svc
```

Once you have securely collected and tokenized your user’s card data using TokenPay.js, you can charge the card or save the token for future use. Charges against cards that are tokenized in the browser using TokenPay.js must *ONLY* made from your server.

On your server, collect the token information and the form POST parameters submitted by your form.

Now submit the token and parameters according to the <a href='https://drive.google.com/file/d/1wH6xioSc2x2itloTQfoYcD3CQ1TtvUmi/view?usp=sharing'>Beyond Pay Gateway API Guide</a>, with the following substitutions:

* `{transactionId}` - unique transaction ID generated by your application for tracking purposes
* `{requestDateTime}` - date and time of the transaction in `yyyMMddHHmmss` format
* `{yourPrivateKey}` - your private API key, obtainable <a href='https://forms.gle/AMxdRZTsS6skq2DEA'>here.</a>
* `{token}` - token delivered in the submission of your payment form
* `{amountInCents}` - transaction amount in cents ($1.25 would be 125)
* `{yourSoftwareName}` - the name and version number of your software application

After your transaction has been successfully submitted to the gateway, make sure you inspect the response message. Specifically, look at:
 
* `ResponseCode` - a 5 digit response code indicating the status of the transaction request
* `ResponseDescription`- a verbose description of the ResponseCode
* `GatewayResult` - an additional response code that may provide additional information on the status of the transaction
* `GatewayMessage` - a verbose description of the GatewayResult
* `AVSResult` - a code indicating the status of the Address Verification System request, if any
* `AVSMessage` - a verbose description of the AVSResult code meaning
* `CVResult` - a code indicating the status of the Card Security Code (aka CVV2, CID) sent in the request message
* `CVMessage` - a verbose description of the CVResult code meaning
* `Token` - a non-sensitive representation of the card number used in the transaction. The last four digits are the same as the last four digits of the card number. This value can be persisted and used for future recurring transactions from the same cardholder. 

<aside class="warning">
You should always inspect the AVSResult and CVResult fields as these can be good indicators of potential fraud. If you see a AVSResult or CVResult code that you do not want to accept because it may be too risky (such as "No Match" on the submitted Zip code), then you should submit a void transaction to cancel the authorization and advise the cardholder that their transaction has been declined.
</aside>

## Perform an Authorization Only

> To change from a "sale" transaction to an "authorize" transaction, simply set `TransactionType` to `sale-auth`:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>{transactionId}</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>{requestDateTime}</RequestDateTime>
    <PrivateKey>{yourPrivateKey}</PrivateKey>
    <AuthenticationTokenId>{token}</AuthenticationTokenId>
    <requestMessage>                    
        <SoftwareVendor>{yourSoftwareName}</SoftwareVendor>
        <TransIndustryType>EC</TransIndustryType>
        <TransactionType>sale-auth</TransactionType>
        <AcctType>R</AcctType>
        <HolderType>P</HolderType>
        <Amount>{amountInCents}</Amount>
        <CurrencyCode>USD</CurrencyCode>
        <SettlementDelay>{daysToDelay}</SettlementDelay>
    </requestMessage>
</requestHeader>';

```

> In order to actually capture that authorization and charge the card, you must submit 019 capture `RequestType`, passing the original sale-auth `ReferenceNumber`, and using the `User` and `Password` credentials instead of `AuthenticationTokenId` and `PrivateKey` to authenticate:

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>{transactionId}</TransactionID>
    <RequestType>019</RequestType>
    <RequestDateTime>{requestDateTime}</RequestDateTime>
    <User>{Beyond-assigned username}</User>
    <Password>{Beyond-assigned password}</Password>
    <requestMessage>                    
        <TransactionCode>{must match header transaction ID}</TransactionCode>
        <SoftwareVendor>{yourSoftwareName}</SoftwareVendor>
        <TransactionType>capture</TransactionType>
        <ReferenceNumber>{original sale-auth ReferenceNumber from response}</ReferenceNumber>
        <Amount>{amountInCents}</Amount>
    </requestMessage>
</requestHeader>';
```


Sometimes you may not want to accept payment right away for a transaction, such as when shipping physical goods. The normal practice in this scenario is to first authorize a card which will place a hold on the funds, and then to later "capture" that authorization when the order is fulfilled.

The `SettlementDelay` tag can be added for sale-auth transactions, and designates te number of batch cycles that the authorization remains "open" (or unsettled). If the sale-auth transaction is not captured before completion of the designated number of batches, then the original authorization will be automatically voided and not captured.

To capture an authorization (sometimes called a "pre-auth"), simply submit a `RequestType` of `019` for capture, along with passing the reference number of the original authorization as shown here.

<aside class="notice">
This capture request and several other API requests described here may take differing credentials in order to authenticate the client. All such credentials will be provided by Beyond for testing and production.</a>.
</aside>

## Tokenization and repeat sales

> The `Token` element represents a card number, can be used multiple times, and does not expire. It may be used as input in a transaction in lieu of the `PaymentAccountNumber` or the `AuthenticationTokenId`, and still requires the `ExpirationDate` field as well.

```xml
<requestHeader>
    <ClientIdentifier>SOAP</ClientIdentifier>
    <TransactionID>{transactionId}</TransactionID>
    <RequestType>004</RequestType>
    <RequestDateTime>{requestDateTime}</RequestDateTime>
    <User>{Beyond-assigned username}</User>
    <Password>{Beyond-assigned password}</Password>
    <requestMessage>
        <SoftwareVendor>{yourSoftwareName}</SoftwareVendor>                    
        <Token>{token - not to be confused with AuthenticationTokenId}</Token>
        <ExpirationDate>{expirationDate}</ExpirationDate>
        <TransactionType>sale</TransactionType>
        <TransIndustryType>EC</TransIndustryType>
        <AcctType>R</AcctType>
        <HolderType>P</HolderType>
        <Amount>{amountInCents}</Amount>
        <CurrencyCode>USD</CurrencyCode>
    </requestMessage>
</requestHeader>
```

Every API response message from Beyond Pay contains a `Token` element. This Token represents the card number used in the original transaction, but is not considered a sensitive data element per the PCI DSS. To ease in identifying the original card, however, the last four digits of the `Token` are the same as the last four digits ot the card number.

This Token value may be persisted and, with the cardholder's permission, associated with their user account in your application in order to make future purchases with the same card ("card-on-file").

Submitting a sale or sale-auth transaction with the Token as input requires use of the User and Password credentials in the request message, and also requires that the card `ExpirationDate` value be persisted and stored with the `Token` (the `ExpirationDate` value is returned in the original response message along with the `Token`).


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

PayGuardian iOS is a secure iOS framework library that integrates seamlessly into iOS applications. PayGuardian iOS facilitates the transaction process by handling the collection and transmission of sensitive payment information as an out of scope PA-DSS solution, thereby offloading the certification responsibility from merchants and integrators. PayGuardian iOS is EMV enabled, handles point to point encryption, and tokenizes all transactions to ensure transaction processing is seamless and secure.

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
000 | Successful request
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


## AVS Response Codes

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

Response Code | Description
------------- | -----------
M | Matches
N | No match
P | Not processed
S | Should be present
U | Issuer is not certified
X | Unrecognized reason

# Testing & Certification

## Certification

When you are finished developing your interface to one of the Beyond Pay solutions, please <a href='mailto:BeyondPayIntegrations@getBeyond.com'>contact us</a> to get certified and obtain your production keys!

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
