Epayco
=====

Epayco android

## Description


Epayco-android facilitates the collection of credit card information without having sensitive data on your server.

These epayco methods can be used to generate data in your android application. If you have an application that charges by credit card, you must use the ePayco-android library to prevent sensitive information from remaining on your server.

## Installation

compile 'co.epayco:epayco-android:1.1.0'

## Usage

```java
Authentication auth = new Authentication();

auth.setApiKey("491d6a0b6e992cf924edd8d3d088aff1");
auth.setPrivateKey("268c8e0162990cf2ce97fa7ade2eff5a");
auth.setLang("ES");
auth.setTest(true);

Epayco epayco = new Epayco(auth);
```

### Create Token

```java
Card card = new Card();

card.setNumber("4575623182290326");
card.setMonth("12");
card.setYear("2018");
card.setCvc("123");

epayco.createToken(card, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject object) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### Customers

#### Create

```java
Client client = new Client();

client.setTokenId("Az9wdX4Wj3JRmr9NC");
client.setName("Cliente epayco");
client.setEmail("cliente@epayco.co");
client.setPhone("305274321");
client.setDefaultCard(true);

epayco.createCustomer(client, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Retrieve

```java
epayco.getCustomer("id_customer", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### List

```java
epayco.getCustomerList(new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### Plans

#### Create

```java
Plan plan = new Plan();

plan.setIdPlan("reactcourse");
plan.setName("Course React");
plan.setDescription("Course react advanced");
plan.setAmount("30000");
plan.setCurrency("COP");
plan.setInterval("month");
plan.setIntervalCount("1");
plan.setTrialDays("0");

epayco.createPlan(plan, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Retrieve

```java
epayco.getPlan("reactcourse", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### List

```java
epayco.getCustomerList(new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### Subscriptions

#### Create

```java
Subscription subscription = new Subscription();

subscription.setTokenCard("id_token");
subscription.setCustomer("id_customer");
subscription.setIdPlan("reactcourse");

epayco.createSubscription(subscription, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Retrieve

```java
epayco.getSubscription("id_subscription", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### List

```java
epayco.getSubscriptionList(new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Pay Subscription

```java
ChargeSub sub = new ChargeSub();

sub.setIdPlan("reactcourse");
sub.setCustomer("id_customer");
sub.setTokenCard("id_token");
sub.setDocType("CC");
sub.setDocNumber("5234567");

epayco.chargeSubscription(sub, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### PSE

#### Create

```java
Pse pse = new Pse();

//Schema
pse.setBank("1022");
pse.setTypePerson("0");

//Required
pse.setDocType("CC");
pse.setDocNumber("1035851980");
pse.setName("John");
pse.setLastName("Doe");
pse.setEmail("example@email.com");
pse.setInvoice("OR-1234");
pse.setDescription("Test Payment");
pse.setValue("116000");
pse.setTax("16000");
pse.setTaxBase("100000");
pse.setPhone("3010000001");
pse.setCurrency("COP");
pse.setCountry("CO");
pse.setUrlResponse("https:/secure.payco.co/restpagos/testRest/endpagopse.php");
pse.setUrlConfirmation("https:/secure.payco.co/restpagos/testRest/endpagopse.php");

//Optional
pse.setExtra1("");
pse.setExtra2("");
pse.setExtra3("");
pse.setCity("");
pse.setDepto("");
pse.setAddress("");

epayco.createPseTransaction(pse, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Retrieve

```java
epayco.getPseTransaction("transaction_id", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### Cash

#### Create

```java
Cash cash = new Cash();

//Schema
cash.setType("efecty");
cash.setEndDate("2017-12-05");

//Required
cash.setDocType("CC");
cash.setDocNumber("1035851980");
cash.setName("John");
cash.setLastName("Doe");
cash.setEmail("example@email.com");
cash.setInvoice("OR-1234");
cash.setDescription("Test Payment");
cash.setValue("116000");
cash.setTax("16000");
cash.setTaxBase("100000");
cash.setPhone("3010000001");
cash.setCurrency("COP");

//Optional
cash.setUrlResponse("");
cash.setUrlConfirmation("");
cash.setExtra1("");
cash.setExtra2("");
cash.setExtra3("");
cash.setCountry("");
cash.setCity("");
cash.setDepto("");
cash.setAddress("");

epayco.createCashTransaction(cash, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});

```

#### Retrieve

```java
epayco.getReferencePayment("epayco_reference", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

### Payment

#### Create

```java
Charge charge = new Charge();

//Schema
charge.setTokenCard("2L9R3ey5paBTN8gzr");
charge.setCustomerId("oDFmhNLasGwAhSDWw");

//Required
charge.setDocType("CC");
charge.setDocNumber("1035851980");
charge.setName("John");
charge.setLastName("Doe");
charge.setEmail("example@email.com");
charge.setInvoice("OR-1234");
charge.setDescription("Test Payment");
charge.setValue("116000");
charge.setTax("16000");
charge.setTaxBase("100000");
charge.setCurrency("COP");
charge.setDues("12");

//Optional
charge.setUrlResponse("");
charge.setUrlConfirmation("");
charge.setExtra1("");
charge.setExtra2("");
charge.setExtra3("");
charge.setCity("");
charge.setDepartament("");
charge.setCountry("");
charge.setAddress("");

epayco.createCharge(charge, new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```

#### Retrieve

```java
epayco.getReferencePayment("epayco_reference", new EpaycoCallback() {
    @Override
    public void onSuccess(JSONObject data) throws JSONException {}

    @Override
    public void onError(Exception error) {}
});
```
