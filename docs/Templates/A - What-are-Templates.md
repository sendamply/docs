# What are Templates?

Templates wrap email contents in a structured manner.

A template defines the surroundings of an HTML email. It's the place to define a common look and feel of your final output. You can define common headers, footers, etc to your email.

By using templates, you define a shared resource, like a header, and all emails using your template will use your shared resource. Sharing resources across your email means your branding is more recognizable to your customers, and your email layout is maintainable and can be easily updated in one place.


### Creating Templates

Templates are created in your dashboard.

Amply has built in substitution tags you can use to modify the final contents of your email. You can yield the email body contents, etc.


### Yielding

The  icon inserts a DIV element that has the class "amply-body" into your template. This provides a way to use a template with dynamic content. When you send your message, this DIV will be replaced by the original email body, surrounded by the HTML code you've defined in your template.



