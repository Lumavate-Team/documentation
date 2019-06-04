.. _Getting Started:

================
Getting Started
================

The following tutorials will have you designing & publishing a Lumavate Experience using Tools available within the Platform, as well as prepare your
environment to develop containers to run within Lumavate.

Example: Quick Survey Tool
--------------------------

Learning Objectives
^^^^^^^^^^^^^^^^^^^
After completing this tutorial, you will be able to:

* Build an Experience using Lumavate Tools
* Publish an Experience
* Describe the communication from Component to Widget to Microservice
* Be able to use Lumavate Components including:
     * Markdown
     * Radio Buttons
     * Button
     * Data Repeater
* Be able to configure & use the Lumavate Data Store Microservice

**Time Estimate**: 35 minutes

Creating a Collection & an Experience
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Login to the Lumavate Studio to begin by creating a Collection to house your Experience.

1. Add a new "Examples" Collection

  a. In the lower left corner of the Experiences screen, Click Add Collection
  b. Enter Name: ``Examples``
  c. Click Save

.. note::
  The Examples Collection may already exist, if so, feel free to create a different named collection to be used in this example, or simply go to Step 2.

2. Add A New Experience, updating the following fields:

  a. Name: ``My Quick Survey``
  b. Text Activation Code: <your initials>

.. note::
  This code will serve as the code that will be texted in to receive the Experience via SMS, along with becoming the domain used for your Experience.

c. Experience Collection: ``Examples``
d. Default Device: ``Mobile``
e. Redirect URL: Leave Blank

3. Click Save
4. Click Design
5. Hover the Add Button
6. Select Add Widget
7. Click Page Builder - Grid Container
8. Click the Start Designing button

9. Update the following fields

  a. Name: ``Home Page``
  b. Page Type: ``Home``

10. Click on the Header tab & update the following fields:

  a. Display Header: ``On``
  b. Show Back Button: ``Off``
  c. Text: ``My Quick Survey``

11. Click on the Body tab & scroll down to the Body Items section
12. Click on the Add button
13. Click Markdown (icon)
14. Back on the designer page, click the Edit icon for the Markdown item just added & update the following fields:

  a. Content:
      ``<div style="text-align:center">Today's question<hr/>
      What is your favorite programming language?</div>``
  b. Number of Rows to Span: ``2``

15. Click Apply

Here's what it should look like at this point:


Adding Radio Buttons for Question Choices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Radio Buttons can be found in Lumavate Components, which is added to a new Experience by default.  Follow these steps to add Radio Buttons to your Experience.

1.  On the Experience Designer page for the Home Page, click on the Body tab & scroll down to the Body Items section
2.  Click on the Add Button
3.  Click on the Radio Buttons icon
4.  Back on the designer page, click the Edit icon for the Radio Button item just added & modify the following fields:

    a. Component Id: ``rdo1``
    b. Label: <leave blank>
    c. Select Options: ``Python|Python,NodeJS|NodeJS,Java|Java,Go|Go``
    d. Display Vertically: ``On``
    e. Body Row start: ``3``
    f. Number of Rows to Span: ``2``

5. Click Apply

By now, your Quick Survey should be starting to take shape:
<image here>

Creating a Submit Button to store data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Click Add button
2. Click Button (image)
3. Back on the designer page, click the Edit icon for the Button just added & modify the following fields:

  a. Component Id: ``btnSubmit``
  b. Button text: ``Submit``
  c. Body Row Start: ``5``
  d. Number of Rows to Span: ``1``

4. Click Apply
5. Click Save

Data Store service configuration to store answers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to add and configure the Data Store service on the Experience.

1. On the Experience Designer page, hover the Add button
2. This time, click Add Microservice
3. Click Data Store
4. Click Start Designing
5. Click the Launch button that appears under Admin
6. After user is redirected to Admin GUI window, click the Add table button
7. Enter 'survey-answers' as the table name and click the Add button that appears in middle of screen
8. After new row appears, enter question for Column Name and set it to type Text
9. Click Add button again
10. After new row appears, enter answer for Column Name and set it to type Text
11. You'll notice we default the Dev Name field to match the Column Name value, but users can edit these if necessary
12. Click the Create button that appears at bottom right of screen
13. Close the Admin GUI to return to the Experience Designer

Now that we have added schema to the Data Store, we will ensure the Experience is set up to view & modify data accordingly.

14. On the Experience Designer page, click the Edit icon next to the Data Store service
15. On the Data Store tab, click the Add button
16. Click the Edit icon on the newly added type, labeled: Type - None
17. Update the following fields:

   a. Type Name: ``survey-answers``
   b. View Access: ``Click "All Users"``
   c. Modify Access: ``Click "All Users"``

18. Click Apply
19. Click Save

Hooking up the Submit Button
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. On the Experience Designer page, click the Edit icon on the Home Page widget
2. On the Script tab, paste the following code **immediately above** the ``/* Please place your code above this comment */``:

.. code-block:: javascript

	//Add an onPress Event Listener for the submit button
	c_btnSubmit.addEventListener('lumaClick', async function(evt) {

		//Disable the button to ensure it is not clicked multiple times
		c_btnSubmit.disabled = true;

		//Get the radio button group value -- getValue returns a promise
		var selection = await c_rdo1.getValue();

		//Create the data object to POST to the Data Store
		var data = {
				'question': 'What is Your favorite programming language', 
				'answer': selection
		};
		//Post data to the Service
		m_Data_Store.post('/survey-answers', data=JSON.stringify(data)).then( (response) =>
		{
			//Upon completion go to the Results page
			p_Results_Page.go();
		});
  });

3. Click Save

Adding a Results Page
^^^^^^^^^^^^^^^^^^^^^

1. On the Experience Designer page, hover the Add button & click Add Widget
2. Click the Page Builder - Grid container
3. Click the Start Designing button
4. On the Widget tab, update the following fields:

   a. Name: ``Results Page``

5. Click on the Header tab
6. Update the following fields:

   a. Display Header: ``On``
   b. Text: ``Survey Results``

7. Click on the Body tab & scroll down to the Body Items section
8. Click on the Add button
9. Click on the Markdown icon
10. Back on the designer page, click the Edit icon for the Markdown component just added & update the following fields:

    a. Content: ``<div style="text-align:center">And the winner is….<hr/></div><br/>``
    b. Number of Rows to Span: ``2``

11. Click Apply

Displaying the results
^^^^^^^^^^^^^^^^^^^^^^

1. On the Body tab of the Results Page, scroll down to the Body Items & Click the Add button
2. Click the Data Repeater icon under the Lumavate Components section
3. Back on the designer page, click the Edit icon for the Data Repeater component just added & update the following fields:

   a. Component Id: ``rpt1``
   b. Row Template (set the field value to the HTML below):

    ``<div style="width:100%;text-align:center;color:var(--accent-color-family-100)">
      <div style="font-size:2em;font-weight:bold">\{answer\}</div><br/>
      <div style="font-size:1.5em;color:var(--primary-color-family-100)">\{total\}</div><br/>
    </div>``

  c. Body Row Start: ``3``

4. Click Apply
5. Click Save

Retrieving the results
^^^^^^^^^^^^^^^^^^^^^^

1. On the Results Page, click the Script tab
2. Under the ``/* Please place your code beneath this comment */``, paste the following code:

.. code-block:: javascript

	m_Data_Store.get("/survey-answers").then(async function(response) {
		var answers = [];
		for (const [key, value] of Object.entries(response.payload.data)) {
			var dataKey = value.answer;
			var answer = answers.find(obj => {
				return obj.answer === dataKey
			});
			if (answer) {
				answer.total++;
			} else {
				answers.push({'answer': dataKey, 'total': 1});
			}
		}
		//Sort DESC by total
		answers.sort(function(a,b)
		{
			return (b.total > a.total) ? 1 : ((a.total > b.total) ? -1 : 0);
		});
		c_rpt1.setData(answers);
  });

3. Click Save

Previewing the home page, you can see how the Survey will store your response & display the results

Publishing the Experience
^^^^^^^^^^^^^^^^^^^^^^^^^

1. Navigate to the Experience View Page.  If you are still on the Experience Designer Page, click Close
2. On the left hand side of the screen, click PUBLISH

After the publish confirmation message pops-up, use the QR Code, URL or Text Activation located on the bottom right part of the screen to see your Quick
Survey in action!


Local Development
-----------------

Using VS.Code, it is easy to modify running containers within Lumavate.  The following steps will walk you through getting a development enabled cotnainer
regsitered with Lumavate & then using VS.Code to edit that container real-time.

Learning Objectives
^^^^^^^^^^^^^^^^^^^

After completing this walkthrough, you will be able to:

* Use the Lumavate CLI to connect to a running container
* Use VS.Code to edit a running Microservice

Before You Start
^^^^^^^^^^^^^^^^

Before going forward, you will need to have the following available on your machine:

* `VS.Code <https://code.visualstudio.com/download>`_
* Lumavate CLI
* Git - This example requires downloading code from Github.com


Setting up your Profile
^^^^^^^^^^^^^^^^^^^^^^^

To start developing on running containers, you will need to configure your development profile via the Lumavate CLI.

Login to your current Command Center & copy the environment creation code under the Lumavate CLI menu item. This environment will enable you to create a
profile to manage tools within the Command Center.

After creating an environment, create a profile using the CLI by using the following command:

.. code-block:: javascript

  luma profile add

Set up your profile based on your "prod" environment as follows:

.. code-block:: javascript

  Profile name: ``CommandCenter``

You should then see your environments like the following:

.. code-block:: javascript

  Env Name App                                         Audience                               Token
  prod     https://app.studio.lumavate.com             https://designer.lumavate.com/app      lumavate.auth0.com

  Name of the Env you want to use with this profile:

Select your "prod" environmentby typing the Env Name (in this case prod)

You will then see a list of Studios & Command Centers associated to this environment like below:

.. code-block:: javascript

  id  Org Name           Org Type Test Org
  51  Trial              studio   True
  52  Trial CC           dev      None

  Org ID you want to associate with this profile:

Select the Command Center that will be used to manage your Tools, in the case above org ID 52, for the Trial CC.

This should result in the following:

.. code-block:: javascript

  Environment Org Name Org ID
  prod        Trial CC 52

You will now be able to use the ``CommandCenter`` profile anytime you use the Lumavate CLI to connect when managing Tools within your Command Center

Connecting VS.Code
^^^^^^^^^^^^^^^^^^

Using VS.Code & the Lumavate Extension, you can edit code directly within a Lumavate running container for easier debugging & development.

After installing `VS.Code <https://code.visualstudio.com/download>`_, view the Extensions within VS.Code.
Using the Search Extensions in the Marketplace input box, type ``Lumavate``, to search for the Lumavate Extension.

  .. figure:: ../images/extension.PNG

Click on the Lumavate Extension & proceed to install the latest version.

Using the Command Palette, you should now be able to start using the ``Luma`` commands, which will enable you to:

* Edit a running Container
* Commit Container Changes - Make a development ready container read-only for use in Production mode
* Follow Container Logs Real-Time
* Add Packages - Add reference libraries as needed to the current running container
* Download Source


MORE TO COME SOON
