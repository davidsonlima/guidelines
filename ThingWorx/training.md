Day 01

https://support.ptc.com/appserver/cs/view/solution.jsp?n=CS192961&lang=en&source=snippet
r@d1Xc0rp16_02
https://precisionlms.ptc.com
classnumber = 00245506
vm-password - stand1
tomcat - admin/admin
twx: Administrator/admin
twx: ThingWorkStudent/ptc

ferrario.adam@gmail.com

http://marketplace.thingworx.com/

Widgets
http://support.ptc.com/cs/help/thingworx_hc/thingworx_6.0_hc/index.jspx?id=thingworx09&action=show
 
Rss
http://apps.shareholder.com/rss/rss.aspx?channels=8626&companyid=PMTC&sh_auth=1327966735%2E0%2E0%2E42543%2Ee821bd4beb119dcffdb56e31a34f3e64

https://precisionlms.ptc.com/viewer/guide/en/23464865/page/23593454#23593457


https://support.ptc.com/appserver/cs/portal/

http://support.ptc.com/appserver/ptcu/class_eval_list.jsp?


Day 02

Aula 02 - Link Data in Marshup +Truck Challenge

GetThinkWorxFeed  Code

var params = {
	proxyScheme: undefined /* STRING */,
	headers: undefined /* JSON */,
	ignoreSSLErrors: undefined /* BOOLEAN */,
	useNTLM: undefined /* BOOLEAN */,
	workstation: undefined /* STRING */,
	useProxy: undefined /* BOOLEAN */,
	withCookies: undefined /* BOOLEAN */,
	proxyHost: undefined /* STRING */,
	url: 'http://apps.shareholder.com/rss/rss.aspx?channels=8626&companyid=PMTC&sh_auth=1327966735%2E0%2E0%2E42543%2Ee821bd4beb119dcffdb56e31a34f3e64' /* STRING */,
	timeout: undefined /* NUMBER */,
	proxyPort: undefined /* INTEGER */,
	password: undefined /* STRING */,
	domain: undefined /* STRING */,
	username: undefined /* STRING */
};

// result: XML
var xmlPage = Resources["ContentLoaderFunctions"].GetXML(params);

var params = {
	infoTableName : "InfoTable",
	dataShapeName : "ThingWorkFeedData"
};

// CreateInfoTableFromDataShape(infoTableName:STRING("InfoTable"), dataShapeName:STRING):INFOTABLE(ThingWorkFeedData)
var result = Resources["InfoTableFunctions"].CreateInfoTableFromDataShape(params);

for each(var item in xmlPage.channel.item){
    // ThingWorkFeedData entry object
    var newEntry = new Object();
    newEntry.link = item.link; // HYPERLINK
    newEntry.title = item.title; // STRING
    result.AddRow(newEntry);
}


jdbc:mysql://127.0.0.1:3306/thingworxtrainingsample?allowMultiQueries=true
SELECT * FROM SampleTable


Aula 03 - Alertas

Mail Configuration
server: smtp.gmail.com
port: 465
pop3: pop.gmail.com/995
useSSL: yes
email: aftwtraining@gmail.com/ thingworx

http://www.google.com/accounts/DisplayUnlockCaptcha


Users[me.FieldServiceTech].smsAddress

####################################################
               
//Set booleans and tags for high/low temperature/humidity
var tag = {}; 
if (me.CurrentHumidity < me.VMHumidityLowLimit) {
    tag.vocabulary = "VendingMachineEventTags";
    tag.vocabularyTerm = "Humidity Low";
    tags.push(tag);
    me.VMHumidityLow = true;
} else {
    me.VMHumidityLow = false;
}  
if (me.CurrentHumidity > me.VMHumidityHighLimit) {
    tag.vocabulary = "VendingMachineEventTags";
    tag.vocabularyTerm = "Humidity High";
    tags.push(tag);
    me.VMHumidityHigh = true; 
} else {
    me.VMHumidityHigh = false; 
}   
 
if (me.CurrentTemperature < me.VMTempLowLimit) {
    tag.vocabulary = "VendingMachineEventTags";
    tag.vocabularyTerm = "Temperature Low";
    tags.push(tag);
    me.VMTemperatureLow = true; 
} else {
    me.VMTemperatureLow = false;
}
if (me.CurrentTemperature > me.VMTempHighLimit) {
    tag.vocabulary = "VendingMachineEventTags";
    tag.vocabularyTerm = "Temperature High";
    tags.push(tag);
    me.VMTemperatureHigh = true; 
} else {
    me.VMTemperatureHigh = false; 
} 

####################################################

var newInv = me.CurrentInventory;
newInv.AddRow({
    vendPosition : VendingPosition,
    productID : ProductID,
    currentInvQty : CurrentInvQty,
    positionCapacity : PositionCapacity,
    productPrice : ProductPrice,
});
me.CurrentInventory = newInv; 

####################################################

var newInv = me.CurrentInventory; 
newInv.Delete({     
    productID: ProductID 
});
me.CurrentInventory = newInv;

####################################################

var newInv = me.CurrentInventory;
var params = {
    types : "NUMBER",
    columns : "SalesPerProduct",
    t : newInv,
    expressions : "((positionCapacity-currentInvQty)*productPrice)" 
}  
 
// DeriveFields 
var result = Resources['InfoTableFunctions'].DeriveFields(params);

####################################################


var salesPerProduct = me.SalesPerProduct();
var params = {
    columns : "SalesPerProduct",
    aggregates : "SUM",
    t : salesPerProduct };
var totalSales = Resources['InfoTableFunctions'].Aggregate(params);
var result = totalSales.SUM_SalesPerProduct;

###############################################
var query = {filters: {
    type: "GT",
    fieldName: "productPrice",
    value: Price     
}};
var result = Resources['InfoTableFunctions'].Query({
	query : query, 
	t : me.CurrentInventory
}); 

###############################################
me.CurrentInventory = Inventory;
###############################################


Aula 04 -  Events & Subscription

####################################################

var values = Things["VendingMachineIssueStream"].CreateValues(); 
values.Type = "Temperature and Humidity High"; 
values.CurrentTemperature = eventData.VMCurTemperature; 
values.CurrentHumidity = eventData.VMCurHumidity;  
var params = {
    location : eventData.VMLocation,
    tags : "VendingMachineEventTags:Temperature and Humidity High",
    timestamp : eventData.VMTime,
    source : me.name,
    values : values 
}; 
Things["VendingMachineIssueStream"].AddStreamEntry(params);

####################################################

if (me.VMTemperatureHigh) { // Do nothing if temperature not high
    var timestamp = new Date();
    if (me.VMHumidityHigh) { // If temp and hum high, emit event.
        var eventData = new Object();
        eventData.VMCurTemperature = me.CurrentTemperature;
        eventData.VMCurHumidity = me.CurrentHumidity;
        eventData.VMTime = timestamp;
        eventData.VMLocation = me.Location;
        me.TemperatureHumidityHigh(eventData);
    } else { // If only temp high, log to stream
        var values = Things["VendingMachineIssueStream"].CreateValues();
        values.CurrentTemperature = me.CurrentTemperature;
        values.CurrentHumidity = me.CurrentHumidity;
        values.Type = "Temperature High";
        var params = {
            timestamp : timestamp,
            tags : "VendingMachineEventTags:Temperature High",
            source : me.name,
            location : me.Location,
            values : values
        };
        Things["VendingMachineIssueStream"].AddStreamEntry(params);    
    } 
}

####################################################

if (me.VMHumidityHigh) {
    // Do nothing if humidity not high
    var timestamp = new Date();
    if (me.VMTemperatureHigh) {
        // If temp and hum high, emit event.
        var eventData = new Object();
        eventData.VMCurTemperature = me.CurrentTemperature;
        eventData.VMCurHumidity = me.CurrentHumidity;
        eventData.VMTime = timestamp;
        eventData.VMLocation = me.Location;
        me.TemperatureHumidityHigh(eventData);
    } else {
        // If only hum high, log to stream
        var values =
            Things["VendingMachineIssueStream"].CreateValues();
        values.CurrentTemperature = me.CurrentTemperature;
        values.CurrentHumidity = me.CurrentHumidity;
        values.Type = "Humidity High";
        var params = {
            timestamp : timestamp,
            tags : "VendingMachineEventTags:Humidity High",
            source : me.name,
            location : me.Location,
            values : values
        };       
        Things["VendingMachineIssueStream"].AddStreamEntry(params);    
    } 
}


####################################################

Configuração AD:

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<Entities build="33" majorVersion="5" minorVersion="0" revision="2" schemaVersion="773">
	<DirectoryServices>
		<DirectoryService className="com.thingworx.security.directoryservices.LDAPDirectoryService" deion="Thingworx Active Directory Services Example" documentationContent="<p>&nbsp;Use this Example, Duplicate it and update the Configuration to tie into your Active Directory System.</p><p>In LDAP terms, you can define as many DC and CN as you need.<br></p>" enabled="false" homeMashup="" lastModifiedDate="2014-08-20T17:20:39.620-04:00" name="TWLDAPExample" priority="1" tags="">
			<Owner name="Administrator" type="User"/>
			<avatar/>
			<DesignTimePermissions>
				<Create/>
				<Read/>
				<Update/>
				<Delete/>
				<Metadata/>
			</DesignTimePermissions>
			<RunTimePermissions/>
			<VisibilityPermissions>
				<Visibility/>
			</VisibilityPermissions>
			<ConfigurationTables>
				<ConfigurationTable deion="LDAP Settings" isMultiRow="false" name="LDAPProxyConfiguration" ordinal="0">
					<DataShape>
						<FieldDefinitions>
							<FieldDefinition aspect.defaultValue="10389.0" baseType="NUMBER" deion="LDAP Server port" name="port" ordinal="0"/>
							<FieldDefinition aspect.defaultValue="uid=admin,ou=system" baseType="STRING" deion="LDAP Distinguished Name to use when binding" name="adminBindDN" ordinal="0"/>
							<FieldDefinition baseType="PASSWORD" deion="LDAP administrative password" name="adminPassword" ordinal="0"/>
							<FieldDefinition aspect.defaultValue="ou=people" baseType="STRING" deion="User Base DN" name="userBaseDN" ordinal="0"/>
							<FieldDefinition aspect.defaultValue="localhost" baseType="STRING" deion="LDAP Server" name="server" ordinal="0"/>
							<FieldDefinition aspect.defaultValue="uid" baseType="STRING" deion="LDAP user id attribute to match when looking up a user" name="userIdAttribute" ordinal="0"/>
						</FieldDefinitions>
					</DataShape>
					<Rows>
						<Row>
							<port>389.0</port>
							<adminBindDN>
								<![CDATA[DC=AdminDC,CN=AdminCN]]>
							</adminBindDN>
							<adminPassword>
								<![CDATA[ugd08BRQrg5gmA1yOvImaw==]]>
							</adminPassword>
							<userBaseDN>
								<![CDATA[DC=UserDC]]>
							</userBaseDN>
							<server>
								<![CDATA[<Directory Server IP>]]>
							</server>
							<userIdAttribute>
								<![CDATA[User Name]]>
							</userIdAttribute>
						</Row>
					</Rows>
				</ConfigurationTable>
			</ConfigurationTables>
			<ConfigurationChanges/>
		</DirectoryService>
	</DirectoryServices>
</Entities>



Aula 05 - Dashbord
