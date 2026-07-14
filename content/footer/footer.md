+++
title =  "Footer"
type = "footer"
draft = false
+++


{{< newsletter-section 
    newsletter_title="Stay updated"
    newsletter_placeholder="Enter your email"
    newsletter_button="Subscribe"
    newsletter_success_message="Thank you for subscribing!"
    newsletter_error_message="Something went wrong, please try again."
    newsletter_note="We respect your privacy and won't share your data."
    form_action="/"
    form_method="POST"
>}}


{{< text-section
title="Extra footer content"
centered="true"
>}}
Additional content added after the `section` blocks. 

Here you could freestyle, add other shortcodes, ...  Or just let the content empty, and rely on the shortcode sections alone.

To make the text nicely wrapped in the footer, the shortcode `text-section` is used.
{{< /text-section >}}