# Laravel

Laravel provides a robust API over the popular SwiftMailer library with drivers for SMTP, PHP's mail, sendmail and more. In this example, we will be sending an email withusing the SMTP Driver. For more information, check out the docs for [Laravel's Mail interface](https://laravel.com/docs/7.x/mail).

****

### Configure

Add the following to your .env file:

```
MAIL_DRIVER=smtp
MAIL_HOST=smtp.sendamply.com
MAIL_PORT=587
MAIL_USERNAME=your_amply_username
MAIL_PASSWORD=your_amply_live_access_key
MAIL_ENCRYPTION=tls
MAIL_FROM_NAME="John Smith"
MAIL_FROM_ADDRESS=from@example.com
```

****

### Create a mailable

Next, you need to create a Mailable class. Laravel's CLI tool Artisan makes it easy. From the CLI:

```
php artisan make:mail MyTestEmail
```

This creates a new file under app/Mail/MyTestEmail.php and it should look something like this:


```php
<?php

namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;
use Illuminate\Contracts\Queue\ShouldQueue;

class MyTestEmail extends Mailable
{
    use Queueable, SerializesModels;

    public $data;

    public function __construct($data)
    {
        $this->data = $data;
    }

    public function build()
    {
        $address = 'johnsmith@example.com';
        $subject = 'This is a demo!';
        $name = 'John Smith';
        
        return $this->view('emails.test')
                    ->from($address, $name)
                    ->cc($address, $name)
                    ->bcc($address, $name)
                    ->replyTo($address, $name)
                    ->subject($subject)
                    ->with([ 'message' => $this->data['message'] ]);
    }
}
```

****

### Create a view

In Laravel Views are used as 'templates' when sending an email. Create a file under app/resources/views/emails/test.blade.php and insert this code:


```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <h2>Test Email</h2>
    <p>{{ $message }}</p>
  </body>
</html>
```

****

### Send an email

To send an email, run the following code:


```php
<?php
use App\Mail\MyTestEmail;

$data = ['message' => 'This is a test!'];

Mail::to('john@example.com')->send(new MyTestEmail($data));
?>
```


