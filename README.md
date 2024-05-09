## Onboard

URL: [test1internal.yosicare.com/onboard](test1internal.yosicare.com/onboard)

### Enable

- Enhance scheduling
- Old Scheduling

#### To Show Enhanced Scheduling in Page CMS

**Page CMS**

- Registration Settings
  - Work Flow
    - It will show all
      - Appointment types for practice (Click to enable/disable)
      - Provider for practice (Click to enable/disable)

**Sandbox URL**: [sso](sso)

#### Create Appointment Type

- Settings
  - Calendar & Booking
  - Add Appointment Type

#### Create Provider - Send Invite via Email after accept new provider will add

Every One hour cron to show Slot in Provider Page

- Settings
  - Calendar & Booking
  - Availability
  - Provider Locations
  - Edit
    - Add Elation Test - we can setup availability with Provider & location (NOTE: In appointment type popup if eye icon appear as hidden we can't use) Once Setup availability need to run CRON test1cronapi.yosicare.elationmetatotyosi.getPhysicianAvailabilities practice_id [sandbox.elationemr.com/patients](sandbox.elationemr.com/patients)
    - We can track Booked slots details
    - Slot will not be available for 4 conditions
      - On click the slot it should be freeze for 10 mins
      - Once slot is booked it should be hide
      - If Provider has any Event
      - Recurring Event

#### To Create Event / Recurring Event

- Event title
- Date / Start time /End time
- Recurrence (daily /weekly )
- Separate days option
- Ends / End Date

### EMR Settings

How long should we allow self-scheduling

- No of days
- Disallow scheduling
- Select multiple appointment type
- We can show by merge multiple appointment type slots
- Slot Recurrences (weekly ) we can separate particular days to show slots
- Allow Book appointment count
- Display Message to be shown after end date completed (it is pending not worked yet)

### Database

- Yosi seldfschedule

### Tables

- elationappointmentfreeze
- elation booked slots
- provider availabilities
- appointment_type_override

#### CronApi

- Module/Elationmetatoyosi/ElationMetttoyosiTable.php
  - Practice based Elation access with elation Configuration
  - We will get emr_practice_id from emr_practice
  - getPhysicianAvailabilities
    - We will call this API to update any changes in available slots for a provider for a particular practice ID
  - elationPhysicianAvailabilities
    - We will do bulk practice / provider update to update changes

**EMR ID 13 - elation**

application-api

- Scheduling/Module/v2/Model/ScheduleTable
  - openSlots function
    - This function will call for all the slot-related changes
  - ElationTable
    - AppointmentTypeOverride function
      - This function will call for all the appointment type override related changes
 - Bookelationappoinment 
  -  This function will call for all the booked slots related changes
