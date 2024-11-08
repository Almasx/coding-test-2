# solution explanation

as i understood right now everything works with greedy algorithm and quite trivial, so based on that i did the same thing.

the task was to implement a fixed bundle price discount where customers can:

- buy 3 items for total $10
- buy 6 items for total $17
- buy 9 items for total $20

my solution:

1. added new discount type "FIXED_BUNDLE_AMOUNT" to handle fixed price bundles

2. in the discount calculation logic (lines 228-245 in bundle-builder.ts):

   - calculated original total price of items
   - subtracted the fixed bundle price from original total
   - returned the difference as the discount amount

3. the discount is distributed equally across all items in the bundle

4. added test case to verify

## Setup

```bash
npm install
```

## Running the tests

```bash
npm test
```

The current bundle builder function in `bundle-builder.ts` processes a cart object and returns discounts to be applied to the cart.

For example:

The discount logic is as follows:

- Buy 3 items in a list of products, get 10% off
- Buy 6 items in a list of products, get 17% off
- Buy 9 items in a list of products, get 20% off

The discount function will take in input objection and return "targets" along with the discount to be applied. Read more here: https://shopify.dev/docs/api/functions/reference/product-discounts/graphql

You can find the example in the test file `bundle.test.ts`.

The current discount function allow 2 types of discount application: Percentage and Fixed amount.

The above example is a percentage discount. Here's an example of a fixed amount discount:

- Buy 3 items in a list of products, get $10 off
- Buy 6 items in a list of products, get $17 off
- Buy 9 items in a list of products, get $20 off

The targets in this case will make sure the applied target has distribution of the discount equally across all the items.

For example, if the cart has 3 items and 3 of them are eligible for discount, the discount for each item will be $10 / 3 = $3.33.

# YOUR TASK

1. Update `bundle-builder.ts` to create a new discount application: Fixed bundle price.

The discount logic is as follows:

- Buy 3 items in a list of products for a total of $10
- Buy 6 items in a list of products for a total of $17
- Buy 9 items in a list of products for a total of $20

Your function need to return the targets with a fixed amount so that the total discounted price is correct.

2. Update the test file to test the new discount application.
