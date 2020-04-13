# ActiveCampaign

A PHP package for working w/ the ActiveCampaign API.

## Install

Normal install via Composer.

## Usage

```php
use Travis\ActiveCampaign;

$endpoint = 'your_account_endpoint';
$key = 'your_api_key';

// create or update contact
$response = ActiveCampaign::run($endpoint, $key, 'POST', 'contacts', [
	'contact' => [
		'email' => 'foo@bar.net',
		'firstName' => 'Foo',
		'lastName' => 'Bar',
	],
]);

// get contact ID number
$response = ActiveCampaign::run($endpoint, $key, 'GET', 'contacts', [
	'email' => 'foo@bar.net',
]);
$contact_id = ex($response, 'contacts.0.id');

// subscribe
$response = ActiveCampaign::run($endpoint, $key, 'POST', 'contactLists', [
	'contactList' => [
        'list' => $your_list_id,
        'contact' => $contact_id,
        'status' => 1 // 1 = subscribe, 2 = unsubscribe
    ],
]);

// unsubscribe
$response = ActiveCampaign::run($endpoint, $key, 'POST', 'contactLists', [
	'contactList' => [
        'list' => $your_list_id,
        'contact' => $contact_id,
        'status' => 2 // 1 = subscribe, 2 = unsubscribe
    ],
]);
```

See the [API Guide](https://developers.activecampaign.com/reference) for additional methods.