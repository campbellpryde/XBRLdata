
ElementUseMultipleGet REST API
----
This API allows the user to fetch XBRL facts from the XBRL US database in an XML format, by passing financial statement parameters to define the data requested.

* **URL**

  <http://csuite.xbrl.us/php/dispatch.php?Task=ElementUseMultipleGet&ElementID=OperatingLeasesFutureMinimumPaymentsDueCurrent&PeriodID=Y&YearID=2014&EntityID=0000732717&Ultimus=true&NoYearsID=1&DimReqd=false>

* **Method:**

  The API supports the following

  `GET` | `POST`

*  **URL Params**

   **Required:**

   `TASK=ElementUseMultipleGet`

   **Optional:**

   `ElementID=[alphanumeric]` - The XBRL element

   `PeriodID=[Y|1Q|2Q|3Q|3QCUM|4Q|1H|2H|Other]` - Period required, if not provided all periods are returned

   `YearID=[integer]`     - Year of the data required

   `EntityID=[integer]`   - CIK of the Company

   `Ultimus=[boolean]`    - True returns the latest value, false returns all values

   `NoYearsID=[integer]`  - Years of data to return based on value eneter for YearID

   `DimReqd=[boolean]`    - True returns all dimensions associated with fact, false only returns the default

   `AxisID=[alphanumeric]` - The XBRL axis element

   `MemberID=[alphanumeric]` - The XBRL member element

   `RestatedID=[boolean]` - A value of false will exclude amounts subsequently restated, a value of true will include amounts that were restated

   `TaxonomiesConceptID=[alphanumericNumeric]` - Enter comma separated list of namespaces. For the extension enter http://www.entity.com/extension/XX where xx is a reference number corresponding to a taxonomy.

   | Reference     | Taxonomy     |
   | :------------- | :------------- |
   | 11       | 2015      |
   | 10       | 2014      |
   | 9       | 2013      |
   



* **Data Params**

  <_If making a post request, what should the body payload look like? URL Params rules apply here too._>

* **Success Response:**

  <_What should the status code be on success and is there any returned data? This is useful when people need to to know what their callbacks should expect!_>

  * **Code:** 200 <br />
    **Content:** `{ id : 12 }`

* **Error Response:**

  <_Most endpoints will have many ways they can fail. From unauthorized access, to wrongful parameters etc. All of those should be liste d here. It might seem repetitive, but it helps prevent assumptions from being made where they should be._>

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "Log in" }`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "Email Invalid" }`

* **Sample Call:**

  <_Just a sample call to your endpoint in a runnable format ($.ajax call or a curl request) - this makes life easier and more predictable._>

* **Notes:**

  <_This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself when leaving comments here._>
