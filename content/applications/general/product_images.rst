==============
Product images
==============

The integration with **Google Custom Search API** is a feature that allows finding images
automatically for your product, based on their barcode.

Configuration
=============

This functionnality requires configuration both on Google and on Odoo.

Google includes 100 free requests per day (about 100 images if all of them are found). To enable
up to 10K requests per day, you need to configure your Google account to do so.

.. seealso::
   - `Create, modify, or close your Cloud Billing account
     <https://cloud.google.com/billing/docs/how-to/manage-billing-account>`_

Google API dashboard
--------------------

#. Go to `Google Cloud Platform <https://console.developers.google.com/>`__ API & Services page
   to generate Google Custom Search API credentials. Log in with your Google account.

#. Select or create an API project to store the credentials if not yet done
   before. Give it an explicit name (e.g. Odoo Images).

#. In the credentials section, click on Create Crendentials and select **API Keys**.

   .. image:: product_images/google-images-credentials00.png
      :align: center

#. Save it, you'll need it for the next step in Odoo !

#. Use the search bar to find for *Google Custom Search API* and select it.

   .. image:: product_images/google-images-credentials01.png
      :align: center

#. Enable the API.

   .. image:: product_images/google-images-credentials02.png
      :align: center

Google Programmable Search dashboard
------------------------------------

#. Go to `Google Programmable Search Engine <https://programmablesearchengine.google.com/>`__ and
   click on Get Started. Log in with your Google account.

   .. image:: product_images/google-images-credentials03.png
      :align: center

#. Fill the language and the name of the search engine. Give it an explicit name
   (e.g. Odoo Images).

   .. note::
      Google doesn't allow to create a search engine without having entered at least one specific
      site to search on. You can put any website (e.g. www.google.com) for this step, we will
      remove it later.

#. Validate the form by clicking on Create. Then, go to the edition mode of the search engine
   that you created (either by clicking on Control Panel button on the confirmation page or by
   clicking on the name of your Search Engine on the Home page).

#. In the basics tab, make sure to enable Image search, SafeSearch and Search the entire web.

   .. note::
      Once Search the entire web enabled, you can safely delete the site that you previously
      entered at the previous step.

#. Save your **Search Engine Id**.

   .. tip::
      You can easily save your Search Engine ID by clicking on the Copy to clipboard button next to
      it.

Odoo
----

#. Go to :menuselection:`Settings --> General Settings --> Integrations`,
   activate **Google Images** and save.

#. Go back to :menuselection:`Settings --> General Settings` and enter your **API Key** and
   **Search Engine ID** in Google Images option.

#. The setup is now ready.

Automatically get your product images in Odoo
=============================================

#. Go to :menuselection:`Inventory --> Products --> Products` or Inventory --> Products -->
   Product Variants.

#. Select the products that needs an image.

   .. important::
      Only the 10K first products or product variants selected will be processed.

   .. note::
      Only the products or product variants with a barcode and without an image will be processed.
      If you select a product that has one or more variants from the Products view, each variant
      matching the previous criteria will be processed.

#. In the action menu, select 

   ..
      TODO VCR: complete the step by step in the wizard

   .. note::
      Images are fetched as a background job, so you can continue doing your work while
      illustrating your products.

      The background job process about 100 images in a minute. If you reach the quota authorized
      by Google (either with a free or a paid plan), the background job will put itself on hold
      for 24 hours and continue right where he stopped the day before. Any other background task
      with a more important weight (e.g. payment post-processing job) will be executed in priority
      and might extend the processing time.

A walkthrough of possible errors
================================
   ..
      TODO VCR: complete a walkthrough all the possible error and the quickest way to fix them

