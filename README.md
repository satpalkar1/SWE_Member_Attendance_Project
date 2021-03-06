# SWE App Data Analyzer

## Background ##

<p align="center">
  <img width="260" height="320" src="img/swe-app.png">
</p>
This customized mobile application tracks member involvement, sends out notifications generated from a consolidated event calendar and creates a centralized location for tools and resources specific to the organization. Members sign into the app to record their attendance for each event. Individual and group attendance is stored and tracked, improving the speed and simplicity of event check-in logistics. All event details can be found by clicking on events that are filtered within the calendar. Events will automatically send push notifications to each user’s phone 24 hours prior, reminding them to attend. A centralized database for SWE contacts and links allows members to easily find the information they need to stay connected. This application is currently available for Android and IOS.
  
* [iOS](https://itunes.apple.com/us/app/osu-swe/id1182610673?mt=8)
* [Android](https://play.google.com/store/apps/details?id=com.ionicframework.swe2702149&hl=en)
  
In this project, I use the CMS data maintained by OSU SWE to perform SQL queries such as:

* Calculating all members' attendance points
* Calculating how many members attend each event
* Calculating the number of members in each graduation year
* Calculating the number of members in each engineering major
* Finding all active members

## Instructions for Loading Data ##
*Ensure SQLite3 is installed first*

1. Using the command line, change directory to SWE_Member_Attendance_Project/src
2. Enter `sqlite3`
3. Enter `.read create_member_attendance.sql`
4. Enter `.mode csv`
5. Enter `.import ../csv/users.csv USERS`
6. Enter `.import ../csv/events.csv EVENTS`
7. Enter `.import ../csv/attendances.csv ATTENDANCE`
8. Enter `.save swe_app.db`
9. Enter `.exit`
10. To open database again, enter `sqlite3` followed by `.open swe_app.db`

## Instructions for Running Queries ##
Change directory to SWE_Member_Attendance_Project/src

1. To run calculate_event_points.sql, enter `.read calculate_event_points.sql`
2. To run another query, repeat step 1 with another query from the List of Queries.

List of Queries:
* calculate_event_points.sql
* calculate_member_graduationYears.sql
* calculate_member_majors.sql
* calculate_member_points.sql
* find_active_members.sql

## Entity Relationship Model ##
<p align="center">
  <img src="img/er-diagram.png">
</p>
  
## Schema ##
USERS(__user_id__, username, officer, major, firstName, lastName, graduationYear)  
EVENTS(__event_id__, title, event_date, location, description, time_range)  
ATTENDANCE(__u_id__<sup>FK</sup>, __e_id__<sup>FK</sup>)  
