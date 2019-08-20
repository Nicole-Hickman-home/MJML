# Introduction

## What

## Why

# Checking Requirements

There are many different platforms that emails can be sent out from and many different ways they can be created. Use the following points to make sure that your email template can go as smoothly as possible.

Types of deliveries:

- Mailchimp
- Raw HTML files
- Outlook template (OFT)
- Marketo

# Review Requirements

Specifications and hours will have been confirmed prior to the design phase. It is essential that the effort needed matches the original brief therefore confirm hours with the producer / project manager.

Here are some points to review over when creating your templates:

**Responsive**

- Confirm if the template will need to be responsive, it’s definitely nice to have!
- When it comes to non responsive emails, this will be more of designer job that us coding, they can do a simple export from Photoshop

**Font family**

- Font families chosen need to be web-safe, which restricts the fonts that we can use to a selected few. This ensures that the font will be installed and readable on any device used to view the email. These fonts should be specified separately in the brand guidelines to the client’s primary fonts.

**Font sizes**

- Check to make sure we know the different font sizes for headings & paragraphs, as with web standards, there should be consistent use of sizes and weights to set a good content flow

**Spacing**

- Spacing between each element should be consistent

**Images**

- Make sure images aren’t too large, may need to be compressed. Average emails shouldn’t surpass 100kb.
- When you see rounded corners, this is best created as an image.

**Colours**

- Make sure all colour hexes are saved down somewhere for easy reference

**Footer links**

- Depending on the delivery platform, you’ll need to change the footer links for their subscription preference. For MailChimp this gets automatically injected, for others you’ll need to find out what the URLs are.

**Tracking**

- Confirm if extra tracking is required for the email delivery, when the delivery is through MailChimp this is all done.

# Export Assets

We can create most layouts from code however due to different email clients we are restricted in most ways, where ever possible we would use code to cut down on the email size. Saying that, anything that has special properties we will need to use image assets (i.e. rounded corners isn’t supported on Windows outlook).

Export assets as JPEG for best compression and file size, if you need transparency then PNG. Your designer should be able to give you some help on this if you cannot do it.

**Our amazing way to get the best images**

The best way to create images that are a)Smaller in size and b)Retina compatible is to x4 the size you'd like of the image and then save it out as the lowest quality jpeg.

Here's an example we tested

The idea is you'll create the artwork as needed

**It is best to keep the whole email under 150kb**, this isn’t a hard limit as such and serves more as a guidance.

# Create Template

There are multiple methods that you can use to create templates, they are listed below however certain deliveries will require you to use certain methods.

- Create via coding it yourself from scratch and HTML standards
- Use something like MJML that will create responsive emails for you
- Use MailChimp / Litmus builders to drag & drop elements

**Responsive Design**

Since people view emails on their mobile phones more often, creating a responsive email is now quite essential.

Max width: 600px Breakpoint: 320px Max columns: 3

When columns hit the breakpoint, it will stack on top of each other, below are some images that illustrates this from our past deliveries:

## Torpedo!

Torpedo is our repo for creating emails! Under the hood it uses MJML to process the files and create a bulletproof responsive email.

Run:
```npm run setup```

Then you can run:
```npm start```

Your MJML file will now generate the html file on save!

### Quirks

When developing emails, you'll **ALWAYS** have different quirks to work against, here are a list of them that you need to be aware of:

#### Backgroun images
For these to work you'll need to make sure you change "tile" to "frame" in the generated html

#### Hiding elements on Outlook
You'll need to make sure all tables that need to be hidden has:

```css
mso-hide:all;
```

This includes **all nested tables as well**.


#### Mailchimp

When sending or importing html email templates, you have to be careful about 2 column layouts because Mailchimp strips adds media queries to your template that will make sure the columns stack even on desktop. There is no way aronud this problem currently if you're trying to make a layout that changes content 
# Saving & Versioning

Going forward we should keep all our source files & compressed templates in Egynte. As of writing the folders haven’t been setup but we should follow this schema:

Shared > Email Templates > [ Name of email project ]

Under this directory will have the following sub directories:

- Design (Any PDF’s / Design files)
- Source (Source files of HTML uncompressed or MJML files)
    - Files should end with a version number i.e. Bioverativ-v1.0.html
- Output (compressed / file that is being sent for review)
    - Files should end with a version number i.e. Bioverativ-v1.0.html

# Testing

Make sure that once you have finished up all your template you test it via Litmus, sometimes it may be wise to save all the screenshots down. You’ll need to export your HTML code if you’re using MailChimp builder to create the template.

The main tests that would break a template are Outlook (Windows), Android / Mobile devices.

Depending on the problem; you’ll need to find a fix however the below table (Taken from MailChimp’s website) should outline most of the issues that you need to be aware of.

**Email HTML v. Web HTML**

The viewing technology of a typical email client isn't as up-to-date as a web browser. Web browsers display interactive, dynamic content, and they update often. But interactive elements like Flash, JavaScript, or HTML forms <a href="https://litmus.com/blog/the-tyranny-of-tables-why-web-and-email-design-are-so-different">won't work in most email inboxes.</a> 

View the table below to learn more.

<table><thead><tr><th>
        <strong>Safe to use</strong>
      </th>

      <th>
        <strong>Use with caution</strong>
      </th>

      <th>
        <strong>Do not use</strong>
      </th>
    </tr></thead><tbody><tr><td>
        static, table-based layouts<br><br>HTML tables and nested tables<br><br>template width of 600px-800px<br><br>simple, inline <a href="/help/css-in-html-email/">CSS</a><br><br><a href="/email-design-guide/#fonts">web safe fonts</a>
      </td>

      <td>
        background images<br><br>custom web fonts<br><br>wide layouts<br><br><a href="/help/add-an-image-map-to-a-campaign/">image maps</a><br><br>embedded CSS
      </td>

      <td>
        JavaScript<br><br><iframe><br><br>Flash<br><br>embedded audio<br><br>embedded video<br><br>forms<br><br><div> layering
      </div></iframe>
</td>
    </tr></tbody></table>

<a href="https://mailchimp.com/help/limitations-of-html-email/#use+with+caution">For the full explanation and please click here:</a>

# Delivery

There are many ways in which email templates can be delivered, some of the deliveries include:

- OFT format
- Marketo
- Pure HTML
- Mailchimp

**Delivering OFT**

This is format used for sending emails from a Windows Laptop through Outlook, to do so you’ll need first create your HTML file and then import it via the attach command. Please follow these instructions:

**Delivering Marketo**

Since we have no access to Marketo, we only have their email templates to go off, each section within the template is a module and it has its own ID which matches up with their system. You have to be very careful not to introduce new ID’s because the system will flag this, if you don’t have enough elements to work with you’ll need to ask them to create it and send you a new template. Usually you should be able to nest more tables within the section.

**Delivering HTML**

# Distribution

**Client Distributes**

Clients have numerous reasons why they distribute the emails themselves, in these cases they’ll probably either want a HTML file or OFT template. We would normally distribute this via Egnyte with a password.

**We distribute**

MailChimp is the preferred distribution method, 90% of the time clients will want us to delivery through MailChimp. Following the steps from before we should have our email tested through Litmus and test emails sent to the relevant personnel’s (project managers, producers, editorial services & client). When everything has been confirmed then our producer will be able to do the final checks and send the email out.

Showing Toma how this works!
