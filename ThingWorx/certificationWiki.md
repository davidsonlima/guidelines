# ThingWorx Certification Wiki  

This wiki contains the major components identified to accomplish the certification exam. Its content is based on the [ThingWorx Documentantion](http://support.ptc.com/cs/help/thingworx_hc/thingworx_7.0_hc/) and on the material of the **Introduction to ThingWorx 6.5** course.

#### Define the following key concepts: (Exam Coverage 12%) 

* Properties
* Services
* Events
* Subscriptions
* Thing Shapes
* Thing Templates
* Things
* Data Shapes
* Mashups
* ThingWorx Organization
* Application Keys
* Resources
* Subsystems
* Remote Thing
* Virtual Thing
* Info Tables  

##### Properties

Properties are the attributes (i.e. speed, location, firmware version, temperature, etc) of an specific entity (Thing, ThingTemplate or ThingShape). It is the same as attributes of a class in Object Oriented Programming.  

* How you describe the data directly related to a Thing
  - The Thing’s current conditions  
  - Static or dynamic aspects  
  - Example: Serial No. (static), Current Temperature (dynamic)  
* Defined at Thing, ThingTemplate, or ThingShape level
  - Properties are inherited from implemented ThingTemplates and ThingShapes
* Each property has a name, description, and base type.
  - Depending on the base type, a property may contain different kinds of information
  - Example: a base type InfoTable can hold a table of values described by a DataShape

##### Services

Services can be viewed as methods of a class using the analogy with OO Programming.

* Services are functions that an Entity can perform
* Can be defined at Thing, ThingTemplate or ThingShape level
  - Such as properties are inherited from implemented ThingTemplates and ThingShapes
* Two aspects:
  - Service Definition
    - Name
    - Input and output parameters – not required, but usually there is one or both
    - Individual runtime permissions, if applicable
  - Service Implementation
    - What the Service actually does
    - Methods (Handler): JavaScript, SQL Query, SQL Command
    - Script Handler is a powerful way to use the server’s data, Things, and services for your application
    - Can perform calculations, lookups, and call/access properties or services from other Things and/or even access to external databases
* Can be invoked through URL, REST client capable application, or by another Service within ThingWorx
* Can have ONLY one output, but may have many inputs

##### Events

Events are actions or occurrences that can be recognised and might be handled by some subscriber to the specific action or occurrence.

* When triggered, sends information about a Thing
* Built-in Event:
  - Attached to an Entity’s specific property
  - Can be triggered when property value changes (DataChange) or hits a certain value (Alert).
  - An alert is just a particular kind of event
* User-defined Event
  - Attached to an Entity
  - User must define a name and the DataShape that describes the data being sent upon Event trigger
  - Does not have pre-defined trigger
  - Event must be fired, usually from within a Service
* To use an Event, it must have a Subscriber
  - An Event can have multiple Subscriptions

##### Subscriptions

* Links an Entity to an Event. `Subscriptions` are `Services` triggerd by `Events` 
* Receives data from the Event
  - When the Event is fired, the source of the Event sends the Event data to the subscriber
* Performs a Subscription code when the Event triggers
  - Can use the Event’s data as an input
  - Uses the same technique as the creation of a Service with Script Handler
* Subscribe to built-in or User-defined Event
Subscription to a built-in Property (DataChange or Alert)
  - When a Property value changes, perform the Subscription’s script implementation
    - Subscription to a User-defined Event of an Entity
  - When the Event is triggered, perform the Subscription’s script implementation with the data sent from the Event
    - An Entity can subscribe to its own Event, or to that of another Entity

##### Thing Shape 

Base definition component. Top of inheritance structure. Should have unique behaviours. From the perspective of OO programming, a Thing Shape can be seen as an `Abstract Class`. Example: `Vehicule` and `Refigerated Machine`

##### Thing Template

Used to model a set of similar objects. Can implement multiple Thing Shapes and one Thing Template. From the perspective of OO programming, a Thing Shape can be seen as a `Class`. Example: `Car`, `Truck`, `Normal Truck`, `Refrigerated Truck` and `Refigerated Machine`

##### Thing

A specific instance of an object or system. Can implement one Thing Template and multiple Thing Shapes. From the perspective OO of programming, a Thing Shape can be seen as an `Object` (instance of a Class). `Car1`, `Car2`, `NT1`, `NT2`, `RT1`, `VM1`, `VM2` 

##### Data Shapes

* Data Shapes are useful with **streams**, **data & info tables**, and **events** 
* When a custom event is triggered, and fires an event it also provides the ability to pass along a data packet containing information about to the event. 
  - Because of this, a custom event must be tied to a Data Shape that defines the data packet that is passed along. 
* Built-in events (e.g. DataChange and Alert) also have an associated Data Shape, assigned automatically by the system 
* Field definitions must also be defined 
* A field definition may be a Primary Key that is only used and enforced in data tables… 
  - In **data tables**, must set at least one field definition to be Primary or cannot use that Data Shape for the data table 
  - Primary key also serves as an index 
  - Events, streams, and info tables do not enforce uniqueness 
* Also, Permissions (section) can be set to define visibility, and other properties 

#### Infotables




#### Identify the following: (Exam Coverage 5%)
* ThingWorx connectivity technologies
* ThingWorx extensions

The ThingWorx platform offers a variety of tools and ways to access and consume external information sources 
ThingWorx Edge MicroServer 
Extensibility 
Relational Databases



##### ThingWorx connectivity technologies

##### ThingWorx extensions
 
  Located on the Market Place (http://marketplace.thingworx.com/).
  Thingworx developpers can download existing ones and create and publish their owns as well.
  Extensions might contain custom widgets (JavaScript, HTML, CSS) for the mashup builder and/or Java classes for develop server-side capabilities.  

#### Navigate the ThingWorx Composer User Interface (Exam Coverage 5%)

#### Create Thing Templates (Exam Coverage 2%)	
* Use predefined Things such as Timer Thing*
*se Thing Templates to create Things (Exam Coverage: 3%)

Work with ThingWorx entities and data by doing the following: (Exam Coverage 7%)
* Applying model tags to ThingWorx Entities
* Exporting ThingWorx Entities and Data
* Importing ThingWorx Entities

Create Mashups by doing the following: (Exam Coverage 18%)
* Configure Widgets
* Determine when to use a Responsive versus Static mashup
* Read the Connections panel of the mashup builder
* Add Services to a mashup
* Use dynamic entities in a mashup
* Use entities to populate widget properties
* Use widgets to populate entitity input parameters
* Use the Layout widget
* Use the Workspace tab
* Use Data Entry widgets
* Use List and Grid widgets
* Use the visibility parameter in widgets
* Test a mashup as the administrator
* Test a mashup as the administrator

Secure a ThingWorx application by doing the following: (Exam Coverage 13%)
* Create a ThingWorx group.
* Define a ThingWorx organization and sub-units.
* Apply security to an organization.
* Create an application key.
* Set security for Entities
* Set security for Services.

Bind Edge devices to the platform by doing the following: (Exam Coverage 2%)
* Identify when the platform has access to an unbound thing.
* Bind a virtual thing to a remote thing.

Add the following to things: (Exam Coverage 9%)
* Properties
* Services
* Events
* Subscriptions

Do the following with Services: (Exam Coverage 2%)
* Create InfoTables in Services
* Manipulate InfoTables in Services

Work with repositories by doing the following: (Exam Coverage 4%)
* Define Platform File Repositories
* Define Remote File Repositories
* Transfer files from the client to a platform repository
* Download files from repository
* Transfer files between remote and platform repositories
* Integrate file transfers into a mashup

Work with ThingWorx extensions by doing the following: (Exam Coverage 4%)
* Import ThingWorx extensions
* Locate extensions on the ThingWorx marketplace
* Use Templates from ThingWorx Model Extensions
* Use Widgets from ThingWorx Extensions

Use ThingWorx data structures, including the following: (Exam Coverage 14%)
* Log values to value streams
* Display value streams in a mashup
* Create ThingWorx Streams
* Create ThingWorx Data Tables
* Tag data in streams and data tables
* Identify persistence provider options
