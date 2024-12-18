# Spotflow React Library

## Introduction

The **Spotflow React SDK** helps you or rather enables users to make payments seamlessly. It integrates smoothly into your application, providing a streamlined checkout experience.

Available Features:

- Collections: Card, Bank Transfers, USSD
- Recurring payments: Tokenization and Subscriptions.

## Table of Contents

1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Support](#supports)
5. [License](#license)
6. [Contributing Guidelines](#contribting-guidelines)
7. [Contributors](#contributors)

## Requirements

1. Spoflow Encryption keys
2. Spotflow API keys
3. Node versions >= 16.x.x npm >=7.x.x
4. React version >= 16.8.0

## Demo

![Alt text](https://github.com/user-attachments/assets/4dbb0b2e-2142-4f04-994a-5c352de7d30e "a title")

## Installation

using npm

 ```bash
  npm i @spot-flow/react-spotflow-checkout

# or

  yarn add @spot-flow/react-spotflow-checkout

# or
  pnpm add @spot-flow/react-spotflow-checkout
   ```

## Usage

Add Spotflow as a component or React Hook

This library can be implemented using the following

1. By Using the SpotflowButton component
2. By Using Hooks (preferred method)

### 1. Using the Payment CheckoutButton

```javascript

import React from "react";
import { SpotflowButton } from "@spot-flow/react-spotflow-checkout";

const PaymentComponent = () => {
  return (
    <div>
      <SpotflowButton
        amount={4000} // Not required for subscription payment
        currency="NGN" // Not required for subscription payment
        email="temi@mailinator.com"
        firstname="John"
        lastname="Doe"
        phone="09090909090"
        encryptionKey="SKKXXXXXXXXXXXXXXXXX"
        planId="9e0808304-344d-XXXXXXXXX-XXXXX834034" // Not required for a one time payment
        merchantKey="sk_test_fXXXXedhXXXXXXXXXXXXXXXX"
        text="Pay Money"
      />
    </div>
  );
};

```

SpotflowButton has the ButtonProps which can allow you to customize to your design



### 2. Using Hooks

```javascript

import React from "react";
import { useSpotflowPayment } from "@spot-flow/react-spotflow-checkout";

const PaymentComponent = () => {
  const config = {
    amount: 4000, // Not required for subscription payment
    currency: "NGN", // Not required for subscription payment
    email: "temi@mailinator.com",
    merchantKey: "sk_test_fXXXXedhXXXXXXXXXXXXXXXX",
    planId: "9e0808304-344d-XXXXXXXXX-XXXXX834034", // Not required for a one time payment
    encryptionKey:"SKKXXXXXXXXXXXXXXXXX"
  }
  const initialFn = useSpotflowPayment(config);

  return (
    <div>
      <button
        type="button"
        onClick={() => {
          initialFn({
            config: undefined,
            onClose: () => {
               // Enter your action here
            },
            onSuccess: () => {
               // Enter your action here 
            }
          });
        }}
        className=" bg-primary-main text-black"
      >
        Pay
      </button>
    </div>
  );
};


```

### Parameters

Read more about our parameters and how they can be used [here](https://docs.spotflow.one/Developer%20Tools/inline-js).

| Parameter           | Required |Description     |
| ------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| merchantKey         | True              | Your API Secret |
| reference           | False             | Your transaction reference. This MUST be unique for every transaction  |
| amount              | False              | Amount to charge the customer. NB: this most likely comes from the plan details. This is not required for subscription payments.   |
| currency            | False             | Currency to charge in. Defaults to NGN. This is not required for subscription payments.                 |
| encryptionKey       | True               | This is the encryption key for the merchant |
| planId   | True | This is the plan id being paid for however, this is not required for one time payments.  |
| firstname | False | This is the Customer's First Name |
| lastname | False | This is the Customer's Last Name |
| email | True | This is the Customer's Email Address |

## Contribution Guidelines

We welcome contributions from the community. Read more about our community contribution guidelines [here](/CONTRIBUTION.md).

## License

By contributing to this library, you agree that your contributions will be licensed under its [MIT license](/LICENSE).

Copyright (c) Spotflow Inc.

## Contributors

- [Olukayode Ogunnowo](http://github.com/dansagam)
- [Oluwatomisin Jimoh](https://github.com/ekiira)
