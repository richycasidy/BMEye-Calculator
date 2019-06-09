# BMEye-Calculator

The idea is to create a bmi cal with the follpwing instruction. This assesment if from andela.

Challenge  1


Build & Style The UI
Your app needs some UI elements. Follow the steps below to build it, then click the play button to run your code and see the outcome in the preview emulator.

Step 1
Within the STYLE tag, give the BODY element a white background
Create a BUTTON element with ID of filter-query, and give it a CSS class of mdc-icon-button and material-icons. Set its text to filter_list.

Create a DIV element and give it a CSS class of select. Within the DIV, create a SELECT element with a CSS class of select-text
The SELECT element should have an option that is disabled and selected by defualt. Give this option any text you like, e.g "Select User"
Next, create a new DIV with a CSS class of user-photo. Inside it, create an IMAGE and set its src to a placeholder from https://placeholder.com/ Make sure to give your IMAGE an alternate text

Next, create a DIV with CSS class of details and mdc-elevation--z3. This DIV should have 5 PARAGRAPH elements, each containing a SPAN with CSS class prop and another SPAN with CSS class of value


Step 2
Using the SPAN elements so far created, your app will display the Age, Height, Weight, Gender, and Country of any given user. Let's call these the user properties!

For a given user property, e.g Age, locate a PARAGRAPH element and give the child SPAN with class prop an HTML attribute of data-age, then set its text value to Age :. The SPAN with class value should have an HTML attribute of data-age-value. The HTML attributes do not need to have a vlaue.

Just like for Age, do same for all the user properties listed above, such that all pairs of SPAN elements are mapped to excatly one user property. Feel free to order them anyhow you like.

Step 3

Create a BUTTON with an ID of oracle and CSS class of mdc-button. Give the button an call-to-action text of your choice, e.g "Calculate BMI"

Create a DIV an ID of outcome. Within it, create a HEADING element with CSS class of mdc-typography--headline5. Set the text of the HEADING to BMI.

Next to the HEADING and still within the DIV with ID of outcome, create an empty PARAGRAPH.
Time to make your app look good. To get a better preview as you go along, feel free to set some dummy data values in the SPAN elements for each user property

Step 4

The .select DIV should have a bottom margin of 2.5em

The .user-photo DIV wrapping the user's IMAGE should have 150px of width and height, and styled to display as a circle. You might need to explore the overflow CSS property to make the IMAGE comply with the circular shape of the DIV

Step 5
The .details DIV should have white foreground color and #6200ee background color, font size of 1.3em, top margin of 4em, padding top/bottom of 0.5em and padding left/right of 1em, and optional curved edges of 10px

The PARAGRAPH elements within the .details DIV should have margins of 0.3em

The DIV with ID of outcome should use absolute positioning, with 2.2em from the right edge and 6.5em from the bottom edge of the viewport. It should be 100px wide, and have centered text.

The HEADING within the DIV with ID of outcome should have 1em padding, white background, 10% curved edges, and no margins.

The PARAGRAPH within the DIV with ID of outcome should be 40px high, have a white foreground color, solid white 5px bottom border, 2em font size, no margins, 0.5em top/bottom padding and no left/right padding

Step 6

The BUTTON with ID of oracle should have 2.5em top margin, solid 1px border, and occupy the available horizontal space.


Challenge 2

Make The UI Functional
Your app looks good, its time to power up the UI and make it respond to user interaction.

Write all JavaScript code in ES6. For DOM traversal, use the HTML5 Selector API only (i.e no use of getElementById or getelementsByTagName e.t.c).

Do not update DOM elements by setting their inner HTML, set their text content instead.

Step 1
Create a users variable and assign it an empty array literal.
Create a displaySelectedUser arrow function
Create a letsCalculateBMI arrow function
Create a powerupTheUI arrow function
Within the startApp function, invoke the powerupTheUI function, followed by the fetchAndDisplayUsers function.

Step 2

In the powerupTheUI function, and using only the DOM Selector API :

Set displaySelectedUser as a change event listener for the SELECT UI element.
Set letsCalculateBMI as the click event listener for the #oracle BUTTON

Step 3

The fetchAndDisplayUsers tries to call a displayUsers function that does not exist. Lets fix that!

Create a displayUsers arrow function just above the fetchAndDisplayUsers function. It should take a users parameter
It should use the array .forEach function to iterate over users and populate the SELECT UI element with OPTION elements. Each OPTION should have its value set to the id of a given user, while its display text should be set to the user's name
We can see a sample user in our app; a certain Charles Odili from Nigeria! Add a new user object (e.g representing yourself) to the users array in fetchAndDisplayUsers. Feel free to not use real data values, but ensure the id is different from that of the existing user.

Step 4

When we select the sample user from the list, nothing happens. Let's fix that!

Create a getSelectedUser arrow function above displaySelectedUser. It should take a userId parameter and use the Array .find function on the users collection to find and return the selected user object. Your .find call should take an inline arrow function and de-structure its single parameter to obtain the id property.

Step 5

Recall that the displaySelectedUser function is called as an event handler. This means it will receive an event object when the DOM event is triggered.

Update the displaySelectedUser function and de-structure the expected event parameter to just the target property.

Next, displaySelectedUser should call getSelectedUser with a certain property of target that represents the selected value of the SELECT element from the change event. Feel free to do some Googling if you dont know the property in question. Finally, assign the result of your .getSelectedUser call to a user variable.

Next, use Object.keys(..) to get the collection of properties of user. Assign it to a properties variable.

Iterate over properties with the array .forEach function, and display the properties in the UI. Hint: * a given property like *Age has a corresponding SPAN element with a data-age-value attribute. You can use ES6 template strings to build the query selector targeting the SPAN for that property, and then query the DOM with it. You also want to make sure you only update the UI if the DOM query was successful. Good luck!


Challenge 3

Calculate BMI
You've got sample user data that gets displayed when a selection is made. Lets give BMEye the power to see through people by calculating their BMI (Body Mass Index).

Step 1
Just abouve getSelectedUser, create a computeBMI arrow function that expects a user parameter, but immediately de-strctures it to the weight, height, and country properties.

Step 2
Go back to letsCalculateBMI and get it to obtain the selected value from the SELECT element, pass that value to a getSelectedUser function call, which should return the user object for the selected value. This user object should be assigned to a user variable.

At this point, letsCalculateBMI is ready to claculate the user's BMI. It should do this by calling computeBMI and passing it user. It then sets the return value from invoking computeBMI to a bmi variable, which is finally set as the text content of the PARAGRAPH within the #outcome DIV

Compute BMI as (weight/height^2) : Each user's height is expressed in feet, so the calculation needs to first convert it to meters. *HINT: * multiple height by 0.3048.

BMEye calculates BMI with an advanced algorithm! BMEye has the notion of countries with the healthiest diet and they are Chad, Sierra Leone, Mali, Gambia, Uganda, Ghana, Senegal, Somalia, Ivory Coast, and Isreal If the user is from any of these countries, then the calculated BMI figure is multipled by 0.82, bringing it down a little.

Step 3

Following the guide and hints above, get computeBMI to use the user's weight, height, and country to calculate and return the BMI value for the user.

Run your code (click on the play button), select the sample user and see if/how the UI displays the properties and computed BMI for the user.

Double check that your BMI computation is correct. Well, you can bet Gradr will make sure of that!


Challenge 4

Use Remote API Data
To have gotten here, you are definitely a rockstar.



Install the JSONViewer extension for Chrome and open https://randomapi.com/api/y1lfp11q?key=LEIX-GF3O-AG7I-6J84 in a new tap. Take a look at the structure of the returned JSON data.

Step 1
Within fetchAndDisplayUsers, after the call to displayUsers, declare an api varialble and set it value to https://randomapi.com/api/y1lfp11q?key=LEIX-GF3O-AG7I-6J84

Use the Browser's fetch API to make a HTTP call to the API endpoint represneted by api

The fetch call returns a Promise that contains the response. Use an arrow function in a .then call to convert the response to JSON.

Use an arrow function in another .then call to receive the converted JSON data. The arrow function should de-structure its parameter to get the results property. The function body should then de-structure results (an array) to get the first item (the user object from the API), which should be assigned to a user variable. Finally, it should add the user object to our users array and then call displayUsers with an inline array containing the new user object.

Add error handling to the fetch call.
