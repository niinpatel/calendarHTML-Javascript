# Calendar with Pure JavaScript and HTML

The program uses Date() function to build a simple calendar with Pure JavaScript and HTML. 
Here's the final implementation of it - http://iamnitinpatel.com/projects/calendar

![alt html javascript calendar](https://cdn-images-1.medium.com/max/800/1*7nkXuZNIB7UUdSFKdIZHVQ.png)

**Explanation-** When the program is started, the function *showCalendar()* is with arguments *currentMonth* and *currentYear*. 
This function populates the table with dates at the correct places. 

The buttons "previous", "next" and dropdown "jump" control the functions, *previous()*, *next()* and *jump()*. 
These function update the *currentMonth* and *currentYear* variable. 

**How showCalendar Works-** 

showCalendar(month, year) function which takes in two parameters, month and year. Once, the function is called, it dynamically generates a calendar in HTML and appends it into our table. Here’s my approach.

Get the starting day of the month, we’ll use -

    let firstDay = (new Date(year, month)).getDay();
2. Next, get the number of days in that month. We can achieve this too using date function.


    let daysInMonth = 32 - new Date(year, month, 32).getDate();

Explanation, the function new Date(year, month, 32) returns the 32nd day after the month started. If we subtract that date from 32, we get the final day of that month. Example, If we pass feb 2018 as an argument, its ‘32nd’ day will be 4th of march, subtract 32 from 4 and we get 28, final day of the month of feb 2018.

Once we have the two things ready, we populate the table with numbers 1 to [last day of month] on appropriate places. For example, if the starting of that month is Thursday and Ending date is 28, we’ll put the number 1 below thursday, 2 below, friday, 3 below saturday and so on. When we reach 28, we break out of the loop.

Here, we use a nested for loop because we have upto 6 rows and 7 columns.

In the outer loop, we create a new “tr” element, ie, table row, up to 6 times. (maximum number of rows we need to create the calendar), then run the inner loop to create elements in each rows, then append those rows into our table.

In the inner loop, we populate each row with “td” elements in it. We keep track of the date using variable “date” in it.There are three if conditions at each iteration:

If we’re at first row and we have not yet reached first yet, create td element and leave it blank.

If “date” is higher than max days in that month, we break out of the loop because we have finished creating the table.

Else, we create the “td” element and print the “date” in it. 