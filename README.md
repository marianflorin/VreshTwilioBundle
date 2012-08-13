Symfony2 Twilio Bundle - by Vresh.net
=====================================


About
-----

A Symfony2 bundle for interacting with Twilio.


Installation
------------

Add this to your debs file

	[VreshTwilioBundle]
		git=http://github.com/Vreshware/VreshTwilioBundle.git
		target=/bundles/Vresh/TwilioBundle
		version=origin/master

Register the namespace in your *app/autoload.php*

	$loader->registerNamespaces(array(
		//Other namespaces
		'Vresh'            => __DIR__.'/../vendor/bundles',
	));


Add the bundle to *app/AppKernel.php*

	$bundles = array(
		// ... other bundles
		new Vresh\TwilioBundle\VreshTwilioBundle(),
	);


Configuration
-------------

Place the following values in the *app/config/config.yml*

	vresh_twilio:
    	sid: replace-with-sid-from-twilio-cp
    	authToken: replace-with-auth-token-from-twilio-cp


Usage
-----

To send SMS messages:

	$twilio = $this->get('twilio.api');
    $twilio->account->sms_messages->create(
    	'+123456789', // from
    	'+987654321', // to
    	'Hello Mr. Bond' // message
    );

Generating TwiML:

	use Vresh\TwilioBundle\Twilio\Lib\Twiml;
    ...
    // within controller method
    $twiml = new Twiml();
    $twiml->sms('Welcome to the outer limits!'); // send SMS
    $response = new Response($twiml);
    $response->headers->set('Content-Type', 'application/xml');
	return $response;


Copyright
---------

TBD
