.. _Getting Started:

================
Getting Started
================

This tutorial will have you designing & publishing a Lumavate Experience using Tools available within the Platform.

Example: Quick Survey Tool
--------------------------

Learning Objectives
^^^^^^^^^^^^^^^^^^^
After completing this tutorial, you will be able to:

* Build an Experience using Lumavate Tools
* Publish an Experience
* Describe the communication from Component to Widget to Microservice'
* Be able to use Lumavate Components including:
  * Markdown
  * Radio Buttons
  * Button
  * Data Repeater
* Be able to configure & use the Lumavate Data Store Microservice

## Time Estimate
35 minutes

Creating a Collection & an Experience
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Login to the Lumavate Studio to begin by creating a Collection to house your Experience.

1. Add a new "Examples" Collection
NOTE: The Examples Collection may already exist, if so, feel free to create a different named collection to be used in this example, or simply go to Step 2.
a. In the lower left corner of the Experiences screen, Click Add New Collection
b. Name: Examples
c. Click Save

2. Add A New Experience
· Name: My Quick Survey
· Text Activation Code: <your initials>

.. note::
        This code will serve as the code that will be texted in to receive the Experience via SMS, along with becoming the domain used for your Experience.


· Experience Collection: Examples
· Default Device: Mobile
· Redirect URL: Leave Blank

3. Click Save
4. Click Design
5. Hover the Add Button
6. Select Add Widget
7. Click Page Builder - Grid Container
8. Click the Start Designing button

9. Update the following fields

  a. Name: Home Page
  b. Page Type: Home

10. Click on the Header tab & update the following fields:

  a. Display Header: On
  b. Show Back Button: Off
  c. Text: My Quick Survey

11. Click on the Body tab & scroll down to the Body Items section
12. Click on the Add button
13. Click Markdown (icon)
14. Back on the designer page, click the Edit icon for the Markdown item just added & modify the following fields:

  a. Content:
      <div style="text-align:center">Today's question<hr/>What is your favorite programming language?</div>
  b. Number of Rows to Span: 2
  c. Number of Columns to Span: 5

15. Click Apply

Here's what it should look like at this point:


Adding Radio Buttons for Question Choices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Radio Buttons can be found in Lumavate Components, which is added to a new Experience by default.  Follow these steps to add Radio Buttons to your Experience.

1.  On the Experience Designer page for the Home Page, click on the Body tab & scroll down to the Body Items section
2.  Click on the Add Button
3.  Click on the Radio Buttons icon
4.  Back on the designer page, click the Edit icon for the Radio Button item just added & modify the following fields:
    a. Component Id: rdo1
    b. Label: <leave blank>
    c. Select Options: Python|Python,NodeJS|NodeJS,Java|Java,Go|Go
    d. Display Vertically: On
    e. Body Row start: 3
    f. Number of Rows to Span: 2
    g. Body Column Start: 3
    h. Number of Columns to Span: 2
5. Click Apply

By now, your Quick Survey should be starting to take shape:
<image here>

Creating a Submit Button to store data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Click Add button
2. Click Button (image)
3. Back on the designer page, click the Edit icon for the Button just added & modify the following fields:

  a. Component Id: btnSubmit
  b. Button text: Submit
  c. Body Row Start: 5
  d. Number of Rows to Span: 1
  e. Body Column Start: 3
  f. Number of Columns to Span: 1

4. Click Apply
5. Click Save

Adding the Data Store service to store answers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Anytime a Microservice is added to an Experience, a page level object is created which enables the Page Builder Widget to easily communicate with the
Microservice. At this time, we will just be adding the Data Store service to the Experience for use later.

1. On the Experience Designer page, hover the Add button
2. This time, click Add Microservice
3. Click Data Store
4. Click Start Designing
5. Since we are just adding the service to the Experience for use later, click Save in the upper right-hand corner of the screen

Initializing the Data Store using JavaScript
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. On the Experience Designer page, click the Edit icon on the Home Page widget
2. Click on the Script tab
3. Under the `/* Please place your code beneath this comment */` lines, paste the following code:

.. code-block:: javascript

    //Initialize Data Store
    //Code to initialize the datastore, not needed after first visit to the page
    m_Data_Store.get('/type?name=survey-answers').then ((r) => {
      // Check to see if the Survey-Answers type has already been created
      if (r.payload.data.length == 0) {
        // Insert a new type record for survey-answers
        data = {}
        data['name'] = 'survey-answers';
        data['scope'] = 'experience';
        m_Data_Store.post('/type', data=JSON.stringify(data)).then( (response) => {
          console.log("Data Store has been initialized for Survey Answers");
        });
      }
    });
    //End Initialization Code

4. Click Apply
5. Click Save

Now that we have added code to initialize the Data Store, we will ensure the Experience is set up to view & modify data accordingly.

6. On the Experience Designer page, click the Edit icon next to the Data Store service
7. On the Data Store tab, click the Add button
8. Click the Edit icon on the newly added type, labeled: Type - None
9. Update the following fields:
   a. Type Name: survey-answers
   b. View Access: Click "All Users"
   c. Modify Access: Click "All Users"
10. Click Apply
11. Click Save

Hooking up the Submit Button
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. On the Experience Designer page, click the Edit icon on the Home Page widget
2. On the Script tab, paste the following code **immediately above** the `/* Please place your code above this comment */`:

.. code-block:: javascript

	//Add an onPress Event Listener for the submit button
	c_btnSubmit.addEventListener('onPress', async function(evt) {

		//Disable the button to ensure it is not clicked multiple times
		c_btnSubmit.disabled = true;

		//Get the radio button group value -- getValue returns a promise
		var selection = await c_rdo1.getValue();

		//Create the data object to POST to the Data Store
		var data = {
			'data':
			{
				'question': 'What is Your favorite programming language', 
				'answer': selection
			}
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
   a. Name: Results Page
5. Click on the Header tab
6. Update the following fields:
   a. Display Header: On
   b. Text: Survey Results
7. Click on the Body tab & scroll down to the Body Items section
8. Click on the Add button
9. Click on the Markdown icon
10. Back on the designer page, click the Edit icon for the Markdown component just added & update the following fields:
    a. Content:

      `<div style="text-align:center">And the winner is….<hr/></div><br/>`

    b. Number of Rows to Span: 2
    c. Number of Columns to Span: 5
11. Click Apply

Displaying the results
^^^^^^^^^^^^^^^^^^^^^^

1. On the Body tab of the Results Page, scroll down to the Body Items & Click the Add button
2. Click the Data Repeater icon under the Lumavate Components section
3. Back on the designer page, click the Edit icon for the Data Repeater component just added & update the following fields:
   a. Component Id: rpt1
   b. Row Template (set the field value to the HTML below):

    `<div style="width:100%;text-align:center;color:var(--accent-color-family-100)">
      <div style="font-size:2em;font-weight:bold">\{answer\}</div><br/>
      <div style="font-size:1.5em;color:var(--primary-color-family-100)">\{total\}</div><br/>
    </div>`

  c. Body Row Start: 3
  d. Number of Columns to Span: 5

4. Click Apply
5. Click Save

Retrieving the results
^^^^^^^^^^^^^^^^^^^^^^

1. On the Results Page, click the Script tab
2. Under the `/* Please place your code beneath this comment */`, paste the following code:

.. code-block:: javascript

	m_Data_Store.get("/survey-answers").then(async function(response) {
		var answers = [];
		for (const [key, value] of Object.entries(response.payload.data)) {
			var dataKey = value.data.answer;
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

1. Navigate dto the Experience View Page.  If you are still on the Experience Designer Page, click Close
2. On the left hand side ofh te screen, clikc PUBLISH

After the publish confirmation message pops-up, use the QR Code, URL or Text Activation located on the bottom right part of the screen to see your Quick
Survey in action!

