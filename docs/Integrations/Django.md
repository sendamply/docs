# Django

Integrating Amply with Django is easy and can be done in just a few minutes.

### Update config

Add the following to settings.py:

```python
AMPLY_API_KEY = os.getenv('AMPLY_PASSWORD')

EMAIL_HOST = 'smtp.sendamply.com'
EMAIL_HOST_USER = 'AMPLY_USERNAME'
EMAIL_HOST_PASSWORD = AMPLY_LIVE_ACCESS_KEY
EMAIL_PORT = 587
EMAIL_USE_TLS = True
```

****

### Send email

Send mail using the send_mail function:

```python
from django.core.mail import send_mail
send_mail('Subject here', 'Here is the message.', 'from@example.com', ['to@example.com'], fail_silently=False)
```

