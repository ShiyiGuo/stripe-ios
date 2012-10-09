stripe-ios
==========

Charge credit card for ios 5.0 by Stripe API
This is a updated version from Brian Collins's SDK

This library charges credit card in the amount of cent. It takes parameters of user's secrete key, card information (card number, expire year & month, security code), amount and currency.
*****************************************
Usage:

1. Add the files to your project.

2. Import the header file
   
   #import "Stripe.h"

3. Initialize StripeConnection with your Stripe secrete key and token.

   StripeConnection *stripe = [StripeConnection connectionWithPublishableKeyAndToken:@"sk_zAWnpWaVWqzhuXy0BNfoVB1CJLQ8G" token:@"charges"];

4. Create card object and add card information.

   StripeCard *card = [[StripeCard alloc] init];
    NSNumberFormatter *formatter = [[NSNumberFormatter alloc] init];
    [formatter setNumberStyle:NSNumberFormatterNoStyle];

    card.number = self.cardnum;
    card.securityCode = self.cvvnum;
    card.expiryMonth = [formatter numberFromString:self.expiremonth];
    card.expiryYear = [formatter numberFromString:self.expireyear];

5. Send asynchronous call by performRequestWithCard function.

   [stripe performRequestWithCard:card amountInCents:chargeAmount currency:currency success:^(StripeResponse *response) {
	//any actions to take for success
    } error:^(NSError *error) {
	//any actions to take for errors
    }];


