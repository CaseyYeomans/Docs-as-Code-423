# Using the Melissa Data Personator Service Provider

The **Melissa Data Personator** service provider is available by default within all instances of Profisee 2024.R1 and beyond. Unlike custom service providers, Melissa Data Personator can be selected from the [Service Provider](https://support.profisee.com/wikis/profiseeplatform/service_providers) list as soon as your instance is upgraded to 2024.R1 or later. For additional information about using the Melissa Data Personator Consumer API, click [here](https://devconsole.melissadata.com/personator/).

As of 2024.R1, the only available service for this provider is the **Verify Contact** service, which includes two operations:

* **Realtime Contact Verify**: This option sends a HTTP GET request. The get operation is used to perform real time (single record) requests for contact verification.
* **Batch Contact Verify**: This option sends a HTTP Post request. The post operation is used to perform batch-based requests where Personator can verify up to 100 records per request.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3124659c8008ff8b.png)

Once the service provider is configured, the Settings tab for this service provider includes the following options:

* **License Key:** This option raises a Credential dialog, allowing the user to provide their API key to Personator. This is a required field.
* **Actions:**This option determines which action the service will perform on the input data. While all actions are presented, the user should only select the actions that are allowed with their license. This is a required field.
* **Columns to Return:**This option specifies which columns are returned. Personator Consumer allows the user to select what data the service will output. The Columns input field allows the user to select either individual columns or groups, which are  returned in the output. These selected columns are returned in addition to the default columns, which are always returned. More information, including column definitions, can be found [here](http://wiki.melissadata.com/index.php?title=Personator:Output_Columns).

You must select the columns you wish to map in your strategy.

* **Request Options**: the Options section allows you to configure a number of options that change the way the service behaves. See Personator docs for more information on the available settings.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id2645b754cfd62df.png)

---

### Available fields for Personator ContactVerify

| Category | Name | Description | Direction | Data Type |
| --- | --- | --- | --- | --- |
| Address | AddressDeliveryInstallation (Canada Only) | Returns the parsed delivery installation for the address entered in the AddressLine field. | Output | string |
| Address | AddressExtras | Any extra information that does not fit in the AddressLine fields. | Output | string |
| Address | AddressHouseNumber | Returns the parsed house number for the address entered in the AddressLine field. | Output | string |
| Address | AddressKey | Returns a unique identifier for an address. This key can be used with other current and future Melissa services. | Output | string |
| Address | AddressLine1 | Street address. If including a suite, you can add it to the end of AddressLine1 field or enter it into the AddressLine2 field. | Input/Output | string |
| Address | AddressLine2 | Street address. Can be a continuation of AddressLine1 (ex: suite) or another address. | Input/Output | string |
| Address | AddressLockBox (Canada Only) | Returns the parsed lock box number for the address entered in the AddressLine field. | Output | string |
| Address | AddressPostDirection | Returns the parsed post-direction for the address entered in the AddressLine field. | Output | string |
| Address | AddressPreDirection | Returns the parsed pre-direction for the address entered in the AddressLine field. | Output | string |
| Address | AddressPrivateMailboxName | Returns the parsed private mailbox name for the address entered in the AddressLine field. | Output | string |
| Address | AddressPrivateMailboxRange | Returns the parsed private mailbox range for the address entered in the AddressLine field. | Output | string |
| Address | AddressRouteService (Canada Only) | Returns the parsed route service number for the address entered in the AddressLine field. | Output | string |
| Address | AddressStreetName | Returns the parsed street name for the address entered in the AddressLine field. | Output | string |
| Address | AddressStreetSuffix | Returns the parsed street suffix for the address entered in the AddressLine field. | Output | string |
| Address | AddressSuiteName | Returns the parsed suite name for the address entered in the AddressLine field. | Output | string |
| Address | AddressSuiteNumber | Returns the parsed suite number for the address entered in the AddressLine field. | Output | string |
| Address | AddressTypeCode | Returns a code for the address type in the AddressLine field. Please see the appendix for the list of possible codes. | Output | string |
| Address | CarrierRoute | Returns a 4-character code defining the carrier route for this record. | Output | string |
| Address | DeliveryIndicator | Returns an indicator of whether an address is a business address or residential address. | Output | string |
| Address | DeliveryPointCheckDigit | Returns a string value containing the 1-digit delivery point check digit. | Output | string |
| Address | DeliveryPointCode | Returns a string value containing the 2-digit delivery point code. | Output | string |
| Address | DistanceAddressToIP | This is the distance in miles between the latitude and longitude of the physical location of the IP Address and the latitude and longitude of the input Address. | Output | string |
| Address | EmailAddress | Email address. | Input/Output | string |
| Address | IPAddress | IP Address. | Input/Output | string |
| Address | MailboxName | Returns the parsed mailbox name for the email entered in the Email field. | Output | string |
| Address | MelissaAddressKey | Melissa Address Key - A proprietary unique key identifier for an address. | Input/Output | string |
| Address | MelissaAddressKeyBase | Returns a unique key associated with a building containing multiple suites/apartments. | Output | string |
| Address | PrivateMailBox | Returns the private mail box number for the address in the AddressLine field, if any. | Output | string |
| Address | Suite | Returns the suite for the address in the AddressLine field, if any. | Output | string |
| Address | UrbanizationName | Returns the urbanization name for the address entered in the AddressLine field. Usually only used if the address is in Puerto Rico. | Output | string |
| Demographic/Census | CBSACode | Census Bureau's Core Based Statistical Area (CBSA). Returns the 5-digit code for the CBSA associated with the requested record. | Output | string |
| Demographic/Census | CBSADivisionCode | Returns the code for a division associated with the requested record, if any. | Output | string |
| Demographic/Census | CBSADivisionLevel | Returns whether the CBSA division, if any, is metropolitan or micropolitan. | Output | string |
| Demographic/Census | CBSADivisionTitle | Returns the title for the CBSA division, if any. | Output | string |
| Demographic/Census | CBSALevel | Returns whether the CBSA is metropolitan or micropolitan. | Output | string |
| Demographic/Census | CBSATitle | Returns the title for the CBSA. | Output | string |
| Demographic/Census | CensusBlock | Returns a 4-digit string containing the census block number associated with the requested record. | Output | string |
| Demographic/Census | CensusKey | Returns a 16 digit string assigned by the US Census Bureau. | Output | string |
| Demographic/Census | CensusTract | Returns a 4-to 6-digit string containing the census tract number associated with the requested record. | Output | string |
| Demographic/Census | CongressionalDistrict | Returns the 2-digit congressional district that the requested record belongs to. | Output | string |
| Demographic/Census | CountyFIPS | Returns the FIPS code for the county in the County field. | Output | string |
| Demographic/Census | CountyName | Returns the county name. | Output | string |
| Demographic/Census | CountySubdivisionCode | Returns a 5 digit string representing the County Subdivision Code for the requested record. | Output | string |
| Demographic/Census | CountySubdivisionName | Returns the County Subdivision Name for the requested record. | Output | string |
| Demographic/Census | ElementarySchoolDistrictCode | Returns a 5 digit string representing the Elementary School District Code for the requested record. | Output | string |
| Demographic/Census | ElementarySchoolDistrictName | Returns the Elementary School District Name for the requested record. | Output | string |
| Demographic/Census | PlaceCode | When ZIP codes overlap, the City field will always return the city that covers most of the ZIP area. | Output | string |
| Demographic/Census | PlaceName | When ZIP codes overlap, the City field will always return the city that covers most of the ZIP area. | Output | string |
| Demographic/Census | SecondarySchoolDistrictCode | Returns a 5 digit string representing the Secondary School District Code for the requested record. | Output | string |
| Demographic/Census | SecondarySchoolDistrictName | Returns the Secondary School District Name for the requested record. | Output | string |
| Demographic/Census | State | State. Accepts either two-character abbreviation or full state name. | Input/Output | string |
| Demographic/Census | StateDistrictLower | Returns a 3 digit string representing the Lower State District Code for the requested record. | Output | string |
| Demographic/Census | StateDistrictUpper | Returns a 3 digit string representing the Upper State District Code for the requested record. | Output | string |
| Demographic/Census | StateName | Returns the full name of the state entered in the State field. | Output | string |
| Demographic/Census | UnifiedSchoolDistrictCode | Returns a 5 digit string representing the Unified School District Code for the requested record. | Output | string |
| Demographic/Census | UnifiedSchoolDistrictName | Returns the Secondary Unified District Name for the requested record. | Output | string |
| Email | TopLevelDomain | Returns the parsed top-level domain name for the email entered in the Email field. | Output | string |
| Geographic | City | City. | Input/Output | string |
| Geographic | CityAbbreviation | Returns an abbreviation for the city entered in the City field, if any. | Output | string |
| Geographic | Country | Country. | Input | string |
| Geographic | CountryCode | Returns the country code for the country in the Country field. | Output | string |
| Geographic | Latitude | Returns the geocoded latitude for the address entered in the AddressLine field. | Output | string |
| Geographic | Longitude | Returns the geocoded longitude for the address entered in the AddressLine field. | Output | string |
| Geographic | PostalCode | Postal Code or ZIP Code. | Input/Output | string |
| Geographic | UTC | Returns the time zone of the requested record. All Melissa products express time zones in UTC (Coordinated Universal Time). | Output | string |
| Household/Lifestyle | ChildrenAgeRange | Returns the age range of children present in the household. | Output | string |
| Household/Lifestyle | CreditCardUser | Returns whether the user has a credit card or not. | Output | string |
| Household/Lifestyle | HouseholdIncome | Returns the range of the household's income. | Output | string |
| Household/Lifestyle | HouseholdSize | Returns the number of occupants in the household. | Output | string |
| Household/Lifestyle | LengthOfResidence | Returns the range of the individual's length of residency in their current address. | Output | string |
| Household/Lifestyle | MoveDate | Returns the date associated with the move address. | Output | string |
| Household/Lifestyle | OwnRent | Returns the individual's status as owner or renter of the property. | Output | string |
| Household/Lifestyle | PresenceOfChildren | Returns the presence of children in the household. | Output | string |
| Household/Lifestyle | PresenceOfSenior | Returns the presence of senior/s in the household. | Output | string |
| IP Address | IPCity | The city where the IP address is located. | Output | string |
| IP Address | IPConnectionSpeed | The connection speed associated with this IP address. | Output | string |
| IP Address | IPConnectionType | The type of connection used by this IP address. | Output | string |
| IP Address | IPContinent | The continent where the IP address is located. | Output | string |
| IP Address | IPCountryAbbreviation | The ISO 3166-1 alpha-2 country code of the country where the IP address is located. | Output | string |
| IP Address | IPLatitude | The latitude for the IP address. This usually points to the IP Address's postal code. | Output | string |
| IP Address | IPLongitude | The longitude for the IP address. This usually points to the IP Address's postal code. | Output | string |
| IP Address | IPPostalCode | The postal code where the IP Address is located. | Output | string |
| IP Address | IPProxyDescription | Additional Details for the Proxy Type returned. | Output | string |
| IP Address | IPProxyType | The type of proxy for an IP Address. | Output | string |
| IP Address | IPRegion | The region where the IP address is located. | Output | string |
| IP Address | IPUTC | The GMT offset for the area where the IP address is located. | Output | string |
| Metadata | DemographicsResults | If any demographics are enabled, Demographics Results will return a comma delimited string containing all the results of the demographics combined. | Output | string |
| Metadata | RecordID | Provides the correlation ID associated with each record. | Input/Output | string |
| Metadata | Results | Returns a string value with comma delimited status, error codes, and change codes for the record. | Output | string |
| Options | Format | Sets the format of the response. | Input | string |
| Other | FreeForm | Single Line Input containing Address, Name, Phone, Email, and Company. | Input | string |
| Other | LastLine | City + State + ZIP. | Input | string |
| Other | Plus4 | Returns the 4-digit plus4 for the input address. | Output | string |
| Other | SocialSecurity | Social Security Number - Accepts the full Social Security Number or the Last 4 digits. | Input | string |
| Personal Information | BirthDay | The birth day of the contact record in DD format. | Input | string |
| Personal Information | BirthMonth | The birth month of the contact record in MM format. | Input | string |
| Personal Information | BirthYear | The birth year of the contact record in YYYY format. | Input | string |
| Personal Information | CompanyName | Company name. | Input/Output | string |
| Personal Information | CountryName | Returns the country name for the record. | Output | string |
| Personal Information | DateOfBirth | Returns the date of birth in the format YYYYMM. | Output | string |
| Personal Information | DateOfDeath | Returns the full date of death in the format YYYYMMDD. | Output | string |
| Personal Information | DemographicsGender | Returns gender based on demographics data. | Output | string |
| Personal Information | DomainName | Returns the parsed domain name for the email entered in the Email field. | Output | string |
| Personal Information | Education | Returns the highest level of education completed by an individual. | Output | string |
| Personal Information | EthnicCode | Returns an individual's specific ethnicity. | Output | string |
| Personal Information | EthnicGroup | Returns the grouped category for a person's ethnicity. | Output | string |
| Personal Information | FirstName | First name. | Input | string |
| Personal Information | FullName | Full name. | Input | string |
| Personal Information | Gender | Returns a gender for the name in the FullName field. | Output | string |
| Personal Information | Gender2 | Only used if 2 names are in the FullName field. Returns a gender for the second name. | Output | string |
| Personal Information | IPCountryName | The full name of the country where the IP address is located. | Output | string |
| Personal Information | IPDomainName | The domain name associated with this IP address. | Output | string |
| Personal Information | IPISPName | The name of the Internet Service Provider associated with the IP Address. | Output | string |
| Personal Information | LastName | Last name. | Input | string |
| Personal Information | MaritalStatus | Returns the individual's marital status. | Output | string |
| Personal Information | NameFirst | Returns the first name in the FullName field. | Output | string |
| Personal Information | NameFirst2 | Only used if 2 names are in the FullName field. Returns the second first name. | Output | string |
| Personal Information</ |