Introduction
------------
Originally posted on SteelmanDigital.com on May 25, 2022.

Are you looking for a comprehensive guide on how to integrate Webflow with IDX? Look no further! In this blog post, we will discuss everything you need to know about the process. We will go over the benefits of using IDX with Webflow, and show you how to set it up correctly.

So whether you're just getting started with Webflow or are looking for ways to improve your website's functionality, this blog post is for you!

### What is an IDX?

An IDX, which stands for Internet Data Exchange, is a data feed that allows real estate websites to display MLS listings. This data includes information on homes for sale, as well as recent sales data.

By using an IDX on your website, you can give your visitors access to this valuable information. So, if you're looking to add MLS to your Webflow website, you'll need to add an IDX feed.

### What's the best IDX for Webflow?

Fortunately, there are many IDX platforms to choose from. Some of the most popular ones include:

*   [IDX Broker](https://idxbroker.com/)
*   [iHomefinder](https://www.ihomefinder.com/)
*   [Showcase IDX](https://showcaseidx.com/)

All of these platforms offer different features and have different pricing, so be sure to do your research before choosing one. If you're a developer working on a project for a real estate agent or broker, be sure to consult with them on what options fit their price point and desired features.

For this guide, we'll be using [IDX Broker](https://idxbroker.com/), as we believe it provides the best value for the money and has the most versatile feature set. However, the steps in this guide are very similar to other platforms, like iHomeFinder.

Steps to Integrate Webflow and IDX
----------------------------------

There are a few steps we'll have to complete to get the site up and running.

1.  Create an IDX Broker account
2.  Register IDX feed with your local MLS
3.  Configure your IDX Broker account
4.  Create a page wrapper
5.  Configure and embed your desired widgets
6.  Add Dynamic Widgets to CMS Collection Pages
7.  Submit to local MLS for final approval

Without further ado, let's get started!

### 1\. Create an IDX Broker Account

Before we get started, you'll need to create an IDX Broker account or have your client create an account. If you're building for a brokerage, you'll need either the Office or Team plan, and if you're building for an agent, you'll need the Agent plan.

IDX Broker offers these [plans](https://idxbroker.com/idx_broker) in two tiers, Lite and Premium. Lite will work for most agents. However, if you have a higher budget and would like the [Polygon search feature](https://idxbroker.com/features/polygon-search-tool) and a few extra goodies, then we would recommend the Premium plan.

### 2\. Register IDX feed with your local MLS

Now that you've created your account, we can move on to the next step.

You'll receive a confirmation email with an order number, and a follow-up email that will have a five-digit code you can use to temporarily access the MLS while you develop your site.

Within two business days, IDX Broker should reach out to you with your account information (login/password) and some additional steps to complete the link between your IDX Broker account and your local MLS data provider.

Your local MLS will likely require you to submit your completed site to verify that you comply with their rules. For example, our local MLS requires all search results to display their logo and a disclaimer.

### 3\. Configure your IDX Broker account

Now that your account is all set up, it's time to configure it.

There are a few things you'll need to do in your IDX Broker dashboard:

*   Connect and configure your domain
*   Configure your IDX page wrapper
*   Configure design settings

#### Connect and configure your domain

First, you'll need to connect and configure your site's domain. Sign into your IDX Broker dashboard, find "Account" in the sidebar, then click on "Details" under "Account."

![a window showing IDX broker's account details page](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293aa2f394a4c33fc528358_account-details.jpg)

Under the Subdomain/Domain control section, check the box to enable the custom domain, then choose a title for your subdomain. In our client's case, we used "search" so their final URL for listings would be "search.clientdomain.com."

![more details about IDX broker's domain control panel](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293aa60e1953444948df963_idxbroker-domain-setup.jpg)

For proper Weflow configuration, your Subdomain/Domain Control section should look like this.

For your subdomain, you can choose any name you'd like, for example, search, listings, or properties.

After choosing your domain, you'll receive some DNS records. In your domain's control panel, create some DNS records with the host as your selected name (in our case, "search") and everything else as described by IDX Broker. This is the same process you go through when setting up a custom domain on your Webflow site.

Save your DNS changes, and wait up to 24-48 hours for the changes to propagate. It usually takes a lot less, but be prepared for a long wait.

**What exactly did we just do?** You now have two websites: your Webflow site and your IDXBroker site.

Your Webflow site is your front-facing website that looks pretty and sends your visitors to the IDX website. Speaking of, you now have a separate IDX Broker website whose sole purpose is to hold the IDX pages and search functionality.

Your Webflow site will point visitors to the IDX website, where they can search for listings, access certain listings, and even fill out contact forms. In the next steps, we'll customize this IDX website to look like your Webflow site.

#### Configure your IDX page wrapper

Great! Your custom domain should be set up now. Our next step is to customize your IDX website's pages to match that of your Webflow site.

In IDX Broker, use the sidebar to navigate to Design > Website > Wrappers. This is the Wrappers Management page, and it looks something like this.

![IDX Broker window showing wrappers management](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293aaacece0a913e6ffc1d3_wrappers-management.jpg)

IDX Broker pages have no navigation bar or footer by default and will extend to fill the full width of the frame. We want to match the layout and width of the other pages on your website, and a wrapper will allow us to do this.

We'll create the wrapper in the next major step, but we need to configure it while we're in IDX Broker.

##### Global Wrapper Setup

Still on the Wrappers Management page, select the "Global" tab, and under Dynamic URL enter your site's published domain followed **/idx-wrapper**.

This will be the slug of your wrapper page, so it can be anything you want, but we would recommend /idx-wrapper or /idx-header.

![a screenshot of IDX Broker's global wrapper management section](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ab02b289f26cc77f6290_global-wrapper-management.jpg)

**Note:** If you don't see the "Dynamic URL" field, make sure "Dynamic" is selected on the middle segmented control.

We'd recommend copying the full URL to your IDX wrapper page for the next few steps.

##### Categories Wrapper Setup

Click on the "Categories" tab. As an extra measure to ensure everything is set properly, click on each of the page categories (Search, Map Search, Results, ...etc) and paste the URL to your IDX wrapper page in each one's Dynamic URL field.

![a screenshot of IDX broker's category wrapper management section](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ab2e161a4151f0dc53e6_category-wrapper-management.jpg)

Don't worry about the "Pages" tab, that won't be relevant.

Finally, make sure to click Save Changes at the bottom of the Wrappers Management page. We're ready to move on to the next step.

#### Configure design settings

Let's configure some design settings!

Head over to Design > Settings > Global, which will open the Global Preferences page.

![a screenshot of IDX broker's global preferences management window](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ab61e5ab0b45eefce887_global-preferences-window.jpg)

None of these settings are critical for this guide, but it's important to look them over and make sure everything is set to your or your client's preference.

### 4\. Create a page wrapper

We're ready to start setting up IDX on your site!

#### Creating the page in Webflow

Head over to your Webflow site, and create a new page called IDX Wrapper. Make sure the slug matches the slug you entered into IDX Broker for your global wrapper. If you're following this guide down to a tee, your slug should be /idx-header.

![a graphic showing how webflow needs to be configured with idx broker to link up the page wrapper](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293abd900484ce322e24bb3_wf-idxbroker-link.jpg)

Remember, the path needs to match on both sides.

#### Building the wrapper page

Let's get started!

For our wrapper page, we want a navigation bar, a content section, and a footer, just like every other page on our site. However, our content section will be empty (for now).

If you're using [Finsweet's](https://finsweet.com/) [Client First](https://www.finsweet.com/client-first/) style system, you'll want a page-wrapper with your global styling symbol, your navigation symbol, the main-wrapper div, and a footer symbol.

Inside the main-wrapper div, add the page padding element, and create a new div called "section-idx" (this isn't in ours but you'd need it for Client First) and inside that div, add your page width container. Ours is named "container-large."

Inside your container component, you can add in a padding component or just apply padding styles to your container component if applicable.

![screenshot of webflow navigator showing idx wrapper config](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ac0800484c8c62e24c31_page-wrapper-navigator.jpg)

Example structure of how your wrapper page should be structured

Now, here's where we link up the IDX. Add two divs inside the deepest child, where you want the IDX content to appear.

For the first div, give it an ID of **idxStart** (case sensitive)

For the second div, give it an ID of **idxStop** (case sensitive).

![graphic showing the page setup of the start and stop divs](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ac39394a4c458e5291ed_idx-start-stop.jpg)

IDX Broker will insert the page content between the divs.

When IDX Broker retrieves the wrapper page, it will look for these start and stop divs by ID, and insert the content for the page inside the two divs.

We're not quite finished yet, but we're almost there.

If your symbols contain relative links, clicking them when on the IDX broker page will cause them to look for a relative path on the IDX Broker site. This is because the IDX wrapper will be displayed on a different domain than your other pages (about, services, home, etc). Click here to [learn more about absolute and relative URLs](https://www.seoclarity.net/resources/knowledgebase/difference-relative-absolute-url-15325/).

Essentially, page links on Webflow end up as relative URLs in the code.

For example, if your "About" link on Webflow is set to type Page and the About page is selected, the actual href attribute of that link in your site's code is "/about." It's a relative link.

When you're on the IDX Broker page (search.yourdomain.com), and you click on the About link, the browser sends you to _search.yourdomain.com/about_ because it's a relative link. As a result, you'll get a 404 page since your IDX Broker search site doesn't have an "/about" page.

**To fix this,** we'll need to unlink the symbols and hard-code the hrefs on each of the links. So, unlink the navigation and footer symbols, then change each link type to URL, and hard code the path to that URL.

It's quite a pain, especially if you have lots of links, but as far as we know it's the only way.

If you have a CMS collection inside your navigation or footer, and inside the collection you have links, you'll need to add a URL field in your collection settings and paste in the absolute link to that CMS item inside the URL field, then instead of the "Current \[collection name\] page" link, choose the "Get URL from \[URL field name\]" link type.

![screenshot showing how to fix the relative cms link issue](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293aca07925c5c911ff0ca3_relative-link-issue-cms-fix.jpg)

Instead of the purple page icon, use the link icon and check "Get URL from"

After you've finished that, pass through one more time and make sure you don't have any more relative links. (don't forget the logo link back to the homepage!)

Remember, now that the IDX wrapper is unlinked from your nav and footer symbols, they won't update if you make any changes to them down the road, so you'll need to repeat the above process each time you update your nav or footer.

Voila! We've successfully created your page wrapper. Publish your site, then visit the Wrappers Management page (Design > Website > Wrappers) and clear the cache to pull in the latest update to your IDX wrapper.

### 5\. Configure and embed your desired widgets

Now comes the fun part. In IDX Broker, go to Design > Widgets > Legacy.

![window showing the legacy widgets page in IDX Broker](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293acf274c4069addf66b4d_legacy-widgets.jpg)

You may already have widgets in here, and you can attempt to use those and reconfigure them if you'd like, but we're going to walk you through the process to create those from scratch.

#### 5a. Quick Search Widget

The Quick Search widget is the most essential of all, since it's how your users will actually search for properties. Users can search by minimum and maximum price, minimum square feet, number of bedrooms, number of bathrooms, property type, and location.

##### Creating the Quick Search widget

First, we'll create a quick search widget like the one shown below.

![an example of a quick search widget built in webflow and idx broker](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ad63cc12923ae42cd7b3_quicksearch-example.jpg)

With the Legacy Widgets page open, click the "Create New" button in the upper right hand corner.

![idx broker window showing first stage of creating a quck search widget](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293adb6e5ab0b7e05fcfadd_create-quicksearch-widget.jpg)

In the dropdown box, select "Quick Search." Now, you'll be able to configure the settings for this quick search widget. We recommend enabling Responsive and Open Search in New Window. Feel free to change the other settings to your or your client's preferences.

Click on "Build Widget," and you should get some widget code and a preview link. If you click on the preview link, you'll see the following:

![idx broker's default styling of the quick search widget which is extremely ugly](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293add9345465e988caf694_default-quicksearch.jpg)

Wow! It's hideous. But we're going to fix that.

Back in IDX Broker, click on "Customize Widget CSS." You'll see some default styles in there. We'll add some styles here later.

![a window showing the widget css section where you paste in your widget's custom code](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b02be5ab0b2a79fd1574_modify-widget-css.jpg)

##### Adding the Quick Search widget to Webflow

Copy the script tag provided by IDX Broker when you created your widget. On your Webflow site, add an HTML Embed element, paste the code, save, and publish.

Let's take a look at the widget's embed code.

If you look in the code, you'll see an "id" attribute on the <script> tag with the value "idxwidgetsrc-00000," where 00000 is your widget's ID. Remember this, we'll need it later.

##### Structure of the Quick Search widget:

On your published Webflow site, you can inspect the widget's structure by inspecting with Chrome DevTools (right click the embed element and click Inspect) or look at the general structure of the widget below:

There's an outer wrapper, an inner wrapper, and multiple field wrappers inside the inner wrapper. Inside each field wrapper, there's a label and an input element. Each element has a class and an ID.

If you look on the live site, you'll notice that the number at the end of each ID is the same number on your script tag.

##### Overriding the Quick Search Widget's default styles:

We can actually override the default styles by using the custom CSS field when we created the widget.

If you've already exited the widget creation window or need to get back to the CSS part, head back to the Legacy Widgets page (Design > Widgets > Legacy) and click the Edit Widget button next to widget name, then scroll down to the "Modify widget styling" section.

![a window in idx broker showing where the edit button is located](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293ae2674c4061404f67f4e_edit-widget-button-legacy-widgets-page.jpg)

To help you get started with modifying the element's CSS, I've created a starter file for you to use. The file overrides the default values and provides a bunch of empty selectors for you to style the widget how you'd like.

To get started, copy the code below and use a text editor like [Visual Studio Code](https://code.visualstudio.com/) or [Atom](https://atom.io/) to replace 00000 with your widget's ID.

If you paste the file (with modified widget ID but no custom styles) into the custom CSS field for the widget in IDX Broker, much of the widget's awful styling goes away.

From here, you can use the empty selectors on the example file to begin styling the widget to match your site.

For an easy workflow, I would recommend editing in a code editor, copying and pasting the code onto IDX Broker, updating the CSS, and using the preview link to check on the widget's styling.

#### 5b. Showcase Widget

The Showcase widget is a simple way to showcase your listings on any page of your website. This widget will display as a grid and link to more information about each listing.

##### Creating the Showcase widget:

Creating the showcase widget is similar to creating the Quick Search Widget. Head over to Design > Widgets > Legacy in the left-hand menu, click on the gray "Create Widget" button in the upper right, and select Showcase from the dropdown menu.

Now you'll be able to choose which listings you would like to display in the widget. Here are some of the most common or most selected options.

*   **Featured Properties:** these are properties that are listed by you (agent plan) or your brokerarge (Office and Team plans)
*   **Supplemental Properties:** these are properties that you can manually select to feature
*   **Featured Agent's Properties:** allows you to narrow down featured properties to a specific agent or agent(s), only on Team or Office plans.
*   **Custom search:** allows you to build a custom search, maybe for a specific city, ZIP code, price point, and more.
*   **More options** are explained over on [IDX Broker's knowledgebase](https://support.idxbroker.com/s/article/widget---property-showcase).

After selecting an option, you may be prompted to enter more information about your search. For this widget, we'll use Featured Properties.

After selecting an option for listings, you'll be able to name your widget, as well as configure some options for it.

![an idx broker window showing the first stage of creating a showcase widget](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293af10b64554e6c060d983_showcase-widget-options.jpg)

How you configure this is up to you, but we strongly encourage limiting the quantity of listings shown (about 6-10 maximum) as a high quantity may cause the page to freeze or load for too long. Make sure to leave Responsive enabled.

When you're done, click on the blue "Build Widget" button at the bottom of the page.

##### Adding the Showcase widget to Webflow:

After configuring the widget, you'll get some custom code ready to be embedded on your Webflow site.

Speaking of, head over to your Webflow site and add an HTML Embed element to the page where you would like the listings grid to be. Paste in your custom code, save, and publish your site.

Open the live site and take a look at the widget. You can also open the preview link provided by IDX Broker, if you prefer.

![a window showing the default styling of the showcase widget](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b055a87fbc09ee803bb9_showcase-widget-preview.jpg)

Are you starting to notice a pattern?

Great! Now, let's talk about the structure of this widget, and we can get to styling it.

##### Structure of the Showcase widget:

Just like the quick search widget, you can view the structure by right clicking and inspecting with Chrome DevTools, or use the below (simplified) structure of the widget.

Our showcase widget has a much cleaner structure, but that comes at a cost.

Unless you want to write some JavaScript code that runs before the page finishes loading, you can't really modify the structure of the widget items, so you're somewhat limited in design freedom.

Additionally, some of the elements have inline styles (on the .IDX-showcaseContainer and .IDX-showcaseCell elements) so if you want to adjust those properties you'll need to add the [!important exception](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity#the_!important_exception) when you declare that property in the style sheet.

Generally, the **!important** exception [isn't recommended for a multitude of reasons](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity), but there is no other way (without using JavaScript) to manually remove the styles.

##### Overriding the Showcase widget's default styles:

Head back over to the Legacy Widgets page (Design > Widgets > Legacy) and click the Edit Widget button next to your newly created Showcase widget, then scroll down to the "Modify widget styling" section.

Open up the custom CSS dropdown, then delete the default styling. Save the widget, then use the preview link to check it out (mostly) bare.

![a window showing the unstyled version of the showcase widget](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b065e5ab0b0ea7fd164d_unstyled-showcase-widget.jpg)

You can see that you have quite a bit to work with here.

Just like the previous widget, I've created a template styleguide for you to use that eliminates most (if not all) of the default styling on the Showcase widget and set you off with a cleaner, more modern design. See below:

![a window showing the custom styles built by carbon creative on the idx broker widget in webflow](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b073c73160dde6c3d4c6_customized-showcase-widget.jpg)

Everything is done completely with CSS, including the icons.

And the custom CSS code for the widget:

Feel free to modify and play around with the file. Change up the colors, fonts, and layout to make it match your site!

### 6\. Add Dynamic Widgets to CMS Collection Pages

In some cases, you or your client may want to integrate Webflow's CMS collection pages with an IDX Broker widget to dynamically widgets based on the current collection page.

If I have a brokerage based in Los Angeles, California, I may serve the surrounding areas, like Beverly Hills, Pasadena, and Long Beach. Having a page for each of these cities might give me an SEO benefit for anyone searching "houses for sale in Beverly Hills" or "homes for sale in Pasadena."

On each of these collection pages, I want to display a Showcase widget with the city filter set to the current collection page, so my Los Angeles collection page shows results from Los Angeles. How do I do this?

#### Create widgets for each of your collection items

First, you'll need to create a new widget in IDX Broker for each of your collection items. Luckily, there isn't a limit to how many widgets you can have on IDX Broker.

**How do I do this?** We created a Showcase widget (custom search type) for the first city, configured it the same way we want all widgets to be configured, and set the city to their primary service area.

Next, we duplicated the widget in the Legacy Widgets view using the duplicate button next to the widget's name. We changed the name of the widget to the next city, and changed only the city property to match the name.

We repeated that process until we had the correct set of widgets for our collection.

#### Configure your Webflow collection

We need to configure our Webflow collection in order to get the widgets to change dynamically.

Each time you create a widget, it's assigned a **unique ID**. If you were extra observant, you may have noticed this.

We're going to use each widget's unique ID to dynamically change which widget is shown on which page.

In your CMS Collection Settings, add a number field for the widget's ID. Ours is called "IDX Number," and that's what we'll call it for the rest of the steps.

![an example of the collection setup for the page so webflow cms and idx broker can be integrated](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b097354f09e480c41284_cities-cms-configuration.jpg)

In each of your collection items, change their IDX Number property to the corresponding widget's ID in IDX Broker.

![a graphic showing how IDX Broker and Webflow are integrated to display a dynamic widget on each collection page](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b283393a292082219029_idxbroker-webflow-ID-link.jpg)

Awesome, now your widgets are successfully linked up to your Webflow CMS. Now, we just have to add the widgets to the collection page.

#### Adding the dynamic widget to the collection page

Back in IDX Broker, copy the code for any of the widgets you created for the CMS collection. It does not matter which one.

In Webflow, head over to your Collection Page template and drop in an HTML Embed element. Paste in your widget's code, and you should have something that looks like this.

![a script tag showing the default implementation](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b0f707a52313d92f7f30_cms-widget-embed-step1.jpg)

In the code, you'll see the ID of the widget you copied in two spots, once in the value on the <script> tag's ID attribute, and once more at the end of the value on the <script> tag's src attribute.

Delete the four or five digit ID from the end of the <script> tag's ID attribute, then click "+ Add Field" in the upper right hand corner. Select the option for "IDX Number," or whatever you named your field.

Repeat the process for the hard-coded ID at the end of the <script> tag's src attribute. Your custom code window should look like the following.

![a script tag showing a dynamic webflow field in the code](https://uploads-ssl.webflow.com/60061f2a577b445904365d36/6293b1030e1832c82263888f_cms-widget-embed-step2.jpg)

Make sure everything looks good, save and close, and publish your site. If you followed everything correctly, when you open up your collection page on the live site, you should see the custom widget that you created.

### 7\. Submit to local MLS for final approval

Congratulations, you've successfully implemented IDX and Webflow!

Before your site can go live, ask your local MLS what specifications your site needs to have in order to get final MLS approval.

Every MLS is different, so reach out to your local MLS and ask what specifications are needed, get your site in compliance, and find out from them how to submit your site for final approval.

Conclusion
----------

Adding IDX to your Webflow site can be pretty difficult, especially for those inexperienced with Webflow and web development. We hope that our guide has helped clear up any confusion you may have and given you a solid foundation to continue building your Webflow real estate site.

If you enjoyed this guide, please consider sharing it with your friends. Sharing helps us produce more high quality content and guides like this one.

If you have any questions or comments about this guide, please feel free to [reach out Steelman Digital](/get-started). Our expert Webflow real estate developers would be happy to help you.

Happy Webflowing!
