# Templates Overview

Templates wrap email contents in a structured manner.

A template defines the surroundings of an HTML email. It's the place to define a common look and feel of your final output. You can define common headers, footers, etc to your email.

By using templates, you define a shared resource, like a header, and all emails using your template will use your shared resource. Sharing resources across your email means your branding is more recognizable to your customers, and your email layout is maintainable and can be easily updated in one place.

****

### Special Variables

There are several special variables that you may use in your templates:

|  Name | Description |
|---|---|
| **<% subject %>** | This will be replaced with the email subject. |
| **<% body %>** | This will be replaced with the email body. |
| **<% unsubscribe_group_url %>** | This will be replaced with an unsubscribe group url (if the unsubscribe group has been set)   |
| **<% unsubscribe_group_link %>** | This will be replaced with an unsubscribe group link (if the unsubscribe group has been set) |

For example if your template looks like:

```json
"subject": "Hello <% subject %>",
"html_part": "<b><% body %></b><br/><% unsubscribe_group_link %>",
"text_part": "<% body %>\n<% unsubscribe_group_url %>"
```

And the email you send looks like:
```
Subject: John Smith
Content-Type: multipart/alternative;
Content-Transfer-Encoding: 7bit

----==_mimepart_5f07611de823a_13381c0d4956be
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 7bit

This is the text part

----==_mimepart_5f07611de823a_13381c0d4956be
Content-Type: text/html; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

<p>This is the HTML part.</p>
```

Then once the template is applied, the email will look like:

```
Subject: Hello John Smith
Content-Type: multipart/alternative;
Content-Transfer-Encoding: 7bit

----==_mimepart_5f07611de823a_13381c0d4956be
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 7bit

This is the text part
http://amply_unsubscribe_url.com

----==_mimepart_5f07611de823a_13381c0d4956be
Content-Type: text/html; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

<b><p>This is the HTML part.</p></b>

<a href="http://amply_unsubscribe_url.com">Unsubscribe From This List</a>
```