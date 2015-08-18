
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

    The API supports the same params as the URL.

* **Success Response:**

```XML
<dataRequest>
  <fact>
    <entity>
      <![CDATA[ MICROSOFT CORPORATION ]]>
      </entity>
    <entityCode>0000789019</entityCode>
    <accessionID>135819</accessionID>
    <elementName>Assets</elementName>
    <namespace>http://fasb.org/us-gaap/2015-01-31</namespace>
    <extensionflag>N</extensionflag>
    <axis/>
    <member/>
    <Units>USD</Units>
    <amount>172384000000</amount>
    <period>Y</period>
    <year>2014</year>
    <filings>2015-07-31</filings>
    <aligned>FALSE</aligned>
    <factID>104030451</factID>
    <dimensions/>
    <dimensionCount>0</dimensionCount>
    <url>
    http://csuite.xbrl.us/php/dispatch.php?Task=htmlExport&FactID=104030451
    </url>
  </fact>
  <count>
    <elementName>Number of Rows: 1</elementName>
    </count>
</dataRequest>
```


* **Sample Call:**

```Flex
<mx:HTTPService id="ElementValue_HTTPRequest" url="{SERVERNAME}{SERVERPATH}dispatch.php"
		 useProxy="false"
		 method="POST"  
		 showBusyCursor="true"
		 result="{globalResultEventHandler(event)}{generateColsForAxis(event)}"
		 fault="Alert.show(HTTP_REQUEST_ERROR +
		 		event.fault.faultString, 'Connection Error')">
    <mx:request xmlns="">
    <Task>ElementUseMultipleGet</Task>
    <ElementID>{sendFilterSettings.elementUseID}</ElementID>
    <EntityID>{sendFilterSettings.entityUseID}</EntityID>
    <AxisID>{sendFilterSettings.axisUseID}</AxisID>
    <MemberID>{sendFilterSettings.memberUseID}</MemberID>
    <PeriodID>{sendFilterSettings.period}</PeriodID>
    <YearID>{sendFilterSettings.endYear}</YearID>
    <StartYearID>{sendFilterSettings.startYear}</StartYearID>
    <NoYearsID>{sendFilterSettings.noYears}</NoYearsID>
    <RestatedID>{sendFilterSettings.latestID}</RestatedID>
    <AccessionID>{sendFilterSettings.accessionUseID}</AccessionID>
    <IndustryID>{sendFilterSettings.industryUseID}</IndustryID>
    <DivisionID>{sendFilterSettings.divisionUseID}</DivisionID>
    <DimensionID>{sendFilterSettings.dimensionUseID}</DimensionID>
    <TaxonomiesMemberID>{sendFilterSettings.selectedTaxonomiesMemberValuePostVariable}</TaxonomiesMemberID>
    <TaxonomiesAxisID>{sendFilterSettings.selectedTaxonomiesAxisValuePostVariable}</TaxonomiesAxisID>
    <TaxonomiesConceptID>{sendFilterSettings.selectedTaxonomiesValuePostVariable}</TaxonomiesConceptID>
    <Ultimus>{sendFilterSettings.ultimus}</Ultimus>
    <DimReqd>{!sendFilterSettings.defaultValuesOnly}</DimReqd>
    ```

* **Notes:**

  For additional parameters contact campbell.pryde@xbrl.us.
