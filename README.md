AWS SES is a very simple UI-less plugin for sending `wp_mail()`s email via AWS SES.

Getting Set Up
==========

Download and run "composer update".

Once you have `git clone`d the repo, or added it as a Git Submodule, add the following constants to your `wp-config.php`:

```PHP
define( 'AWS_SES_WP_MAIL_REGION', 'us-east-1' );
define( 'AWS_SES_WP_MAIL_KEY', '' );
define( 'AWS_SES_WP_MAIL_SECRET', '' );
```

If you plan to use IAM instance profiles to protect your AWS credentials on disk you'll need the following configuration instead:

```PHP
define('AWS_SES_WP_MAIL_REGION', 'us-east-1');
define('AWS_SES_WP_MAIL_USE_INSTANCE_PROFILE', true);
```


The next thing that you should do is to verify your sending domain for SES. You can do this via the AWS Console, which will allow you to automatically set headers if your DNS is hosted on Route 53. Alternatively, you can get the required DNS records by running:

```
wp aws-ses verify-sending-domain
```

Once you have verified your sending domain, you are all good to go!

**Note:** If you have not used SES in production previously, you need to apply to [move out of the Amazon SES sandbox](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/request-production-access.html).

Other Commands
=======

`wp aws-ses send <to> <subject> <message> [--from-email=<email>]`

Send a test email via the command line. Good for testing!
