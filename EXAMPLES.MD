<?php
//
// oauth2 code here to get a token etc., then proceed with a returned token
//
$client = $this->initializeClient($known_token, ['https://www.googleapis.com/auth/plus.business.manage']);
$service = new \Google_Service_MyBusiness($client);
// get GMB accounts
$accounts = $service->accounts->listAccounts()->getAccounts();
// get GMB account locations (for the first account)
$locations = $service->accounts_locations->listAccountsLocations($accounts[0]['name']);
// get posts for the selected location
$service->accounts_locations_localPosts->listAccountsLocationsLocalPosts($locations[0]['name'])
?>
