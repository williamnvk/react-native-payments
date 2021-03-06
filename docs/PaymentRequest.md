# PaymentRequest
### constructor(methodData, details, ?options)
Initializes the payment request.

__Arguments__
- methodData - `Array<PaymentMethodData>`
- details - `PaymentDetailsInit`
- ?options - `PaymentOptions`

<details>
<summary><strong>Example</strong></summary>

```es6
const METHOD_DATA = [
  {
    supportedMethods: ['apple-pay'],
    data: {
      merchantIdentifier: 'merchant.com.your-app.namespace',
      supportedNetworks: ['visa', 'mastercard', 'amex'],
      countryCode: 'US',
      currencyCode: 'USD'
    }
  }
];

const DETAILS = {
  id: 'demo',
  displayItems: [
    {
      label: 'Movie Ticket',
      amount: { currency: 'USD', value: '15.00' }
    },
    {
      label: 'Shipping',
      amount: { currency: 'USD', value: '0.00' }
    }
  ],
  total: {
    label: 'Merchant Name',
    amount: { currency: 'USD', value: '15.00' }
  },
  shippingOptions: [
    {
      id: 'economy',
      label: 'Economy Shipping',
      amount: { currency: 'USD', value: '0.00' },
      detail: 'Arrives in 3-5 days',
      selected: true
    },
    {
      id: 'express',
      label: 'Express Shipping',
      amount: { currency: 'USD', value: '5.00' },
      detail: 'Arrives tomorrow'
    }
  ]
};

const OPTIONS = {
  requestPayerName: true,
  requestPayerPhone: true,
  requestPayerEmail: true,
  requestShipping: true
};

const paymentRequest = new PaymentRequest(METHOD_DATA, DETAILS, OPTIONS);
```

</details>

---

### show()
Displays the payment request to the user.

<details>
<summary><strong>Example</strong></summary>

```es6
paymentRequest
  .show()
  .then(paymentResponse => chargePaymentResponse(paymentResponse));
```

</details>

---

### abort()
Dismisses the payment request.

<details>
<summary><strong>Example</strong></summary>

```es6
paymentRequest.abort();
```

</details>

---

### id
Returns the payment requests's `details.id`

<details>
<summary><strong>Example</strong></summary>

```es6
console.log(paymentRequest.id); // demo
```

</details>

---

### shippingAddress
A payment request's `shippingAddress` is populated when the user provides a shipping address. It is `null` by default.

<details>
<summary><strong>Example</strong></summary>

```es6
console.log(paymentRequest.shippingAddress); // null
```

</details>

---

### shippingOption
A payment request's `shippingOption` is populated when the user chooses a shipping option. It is `null` by default.

<details>
<summary><strong>Example</strong></summary>

```es6
console.log(paymentRequest.shippingOption); // economy
```

</details>

---
