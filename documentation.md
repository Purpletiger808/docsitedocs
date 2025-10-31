---
mdx.format: md
---

# CARTS Highway Class Segments

**Highway Class Segments Roadway Data**  
**Version:** August 2023

---

<!-- BEGINNING OF TRAFFIC VOLUME AND CLASSIFICATION SEGMENT 


	AADT
	AADT_Motorcycle
	AADT_Truck
	AADT_Year


-->

# **Traffic Volume and Classification**

## **AADT (Annual Average Daily Traffic)**

Annual Average Daily Traffic (AADT) is a key traffic metric that represents the average number of vehicles passing a specific point on a road or highway each day over the course of a year. It is calculated by dividing the total yearly traffic volume by 365 days. AADT is crucial in traffic safety analysis as it helps transportation planners and engineers understand traffic patterns, identify high-traffic areas, and assess the potential risk of accidents. By analyzing AADT data, authorities can make informed decisions on infrastructure improvements, traffic control measures, and safety interventions to reduce accidents and enhance road safety. For roads without a direct measurement, Average Annual Daily Traffic (AADT) may be calculated by statistical methods, such as using historical traffic data, growth factors, regression analysis and traffic modeling techniques to estimate the average daily traffic counts over a year.

### Other References 
[DOTD Traffic Count App](https://ladotd.public.ms2soft.com/tcds/tsearch.asp?loc=ladotd)   |   [DOTD Traffic Viewer App](https://ladotd.public.ms2soft.com/TDMS.UI_Core/trafficviewer)

<details>
	    <summary>View Field</summary>

| Field Name | Data Type | Allow Nulls | Default Value | Domain | Precision | Scale | Length | DataSourceLayer | DataSourceField | DerivedField_Classification | Comment/Question? | Response | Disposition | Definition Query | Added | Formula |
| ---------- | --------- | ----------- | ------------- | ------ | --------- | ----- | ------ | --------------- | --------------- | --------------------------- | ----------------- | -------- | ----------- | ---------------- | ----- | ------- |
| AADT       | Long      | Yes         | Null          |        |           |       |        | AADT (ALRS)     | AADT            |

</details>

---

## **AADT_Motorcycle**

Annual Average Daily Traffic for motorcycles (AADT motorcycle) is a specific metric that quantifies the average number of motorcycles passing a particular point on a road or highway each day over a year. This is calculated by summing the total annual motorcycle traffic volume and dividing it by 365. The Federal Highway Administration (FHWA) mandates the inclusion of [vehicle classifications](https://www.fhwa.dot.gov/policyinformation/tmguide/2022_TMG_Final_Report.pdf) (1.3.3), including motorcycles, in traffic counts for certain projects to ensure a comprehensive understanding of traffic composition. This detailed classification helps transportation planners and engineers evaluate motorcycle traffic patterns, enhance infrastructure design, and implement targeted safety measures to reduce motorcycle-related accidents and improve overall traffic safety.

 <details>
 	    <summary>View Field</summary>

| Field Name      | Data Type | Allow Nulls | Default Value | Domain | Precision | Scale | Length | DataSourceLayer       | DataSourceField | DerivedField_Classification | Comment/Question?                                                                   | Response | Disposition                                                                                                 | Definition Query | Added |
| --------------- | --------- | ----------- | ------------- | ------ | --------- | ----- | ------ | --------------------- | --------------- | --------------------------- | ----------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------- | ---------------- | ----- |
| AADT_Motorcycle | Long      | Yes         | Null          |        |           |       |        | AADTMotorcycle (ALRS) |                 |                             | Can be loaded from prior year's HPMS data from MS2 - Requires schema change in R&H. |          |  |

</details>

---

## **AADT_Truck**

Annual Average Daily Traffic for trucks (AADT Truck) is a specific metric that quantifies the average number of three or more axles trucks passing a particular point on a road or highway each day over a year. This is calculated by summing the total annual motorcycle traffic volume and dividing it by 365. The Federal Highway Administration (FHWA) mandates the inclusion of [vehicle classifications](https://www.fhwa.dot.gov/policyinformation/tmguide/2022_TMG_Final_Report.pdf) (2022 Traffic Monitoring Guide, 1.3.3), including trucks, in traffic counts for certain projects to ensure a comprehensive understanding of traffic composition. This detailed classification helps transportation planners and engineers evaluate motorcycle traffic patterns, enhance infrastructure design, and implement targeted safety measures to reduce truck-related accidents and improve overall traffic safety.

<details>
	    <summary>View Field</summary>

| Field Name | Data Type | Allow Nulls | Default Value | Domain | Precision | Scale | Length | DataSourceLayer                                  | DataSourceField                | DerivedField_Classification | Comment/Question?                                                                   | Response | Disposition                                                                                                 | Definition Query | Added |
| ---------- | --------- | ----------- | ------------- | ------ | --------- | ----- | ------ | ------------------------------------------------ | ------------------------------ | --------------------------- | ----------------------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------- | ---------------- | ----- |
| AADT_Truck | Long      | Yes         | Null          |        |           |       |        | Sum of AADTSingleUnit and AADTCombination (ALRS) | AADTSingleUnit+AADTCombination |                             | Can be loaded from prior year's HPMS data from MS2 - Requires schema change in R&H. |          | Leave blank for now as it will impact the TrafficSegment schema. Will revisit after HPMS submittal June 15. |

</details>

---

## **AADT_Year**

The year in which the traffic count was performed.

<details>
    <summary>View Field</summary>

 Field Name                     | Data Type | Allow Nulls | Default Value | Domain              | Precision | Scale | Length | DataSourceLayer                                                     | DataSourceField                                     | DerivedField_Classification                                                                                                                                                                      | Definition Query                                             | Added | Formula                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
--------------------------------|-----------|-------------|---------------|---------------------|-----------|-------|--------|---------------------------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AADT_Year                      | Long      | Yes         | Null          |                     |           |       |        | AADT (ALRS)                                                         | DataYear                                            |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             

</details>

<!-- What is this table??
 Field Name                     | Data Type | Allow Nulls | Default Value | Domain              | Precision | Scale | Length | DataSourceLayer                                                     | DataSourceField                                     | DerivedField_Classification                                                                                                                                                                      | Definition Query                                             | Added | Formula                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
--------------------------------|-----------|-------------|---------------|---------------------|-----------|-------|--------|---------------------------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 AADT                           | Long      | Yes         | Null          |                     |           |       |        | AADT (ALRS)                                                         | AADT                                                |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 AADT_Motorcycle                | Long      | Yes         | Null          |                     |           |       |        | AADTMotorcycle (ALRS)                                               |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 AADT_Truck                     | Long      | Yes         | Null          |                     |           |       |        | Sum of AADTSingleUnit and AADTCombination (ALRS)                    | AADTSingleUnit+AADTCombination                      |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 AADT_Year                      | Long      | Yes         | Null          |                     |           |       |        | AADT (ALRS)                                                         | DataYear                                            |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 AccessControl                  | String    | Yes         | Null          | AccessControl       |           |       | 1      | AccessControl                                                       | AccessControl                                       |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 BeginLogMile                   | Double    | Yes         | Null          |                     |           |       |        | LRSID_Route                                                         |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 BeginLogMileCenterLine         | Double    | Yes         | Null          |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 City                           | String    | Yes         | Null          |                     |           |       | 100    | Derived from City Code Sheet - Lookup Table, BNDY_IncorporatedAreas |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 CityFIPS                       | String    | Yes         | Null          |                     |           |       | 5      | BNDY_IncorporatedAreas                                              | PlaceFIPS                                           |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 CityParish                     | String    | Yes         | Null          | CityParish          |           |       | 4      | City Code Sheet - Lookup Table                                      | Combine CityCode and ParishCode                     | CityParish                                                                                                                                                                                       |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ControlSection                 | String    | Yes         | Null          |                     |           |       | 6      | LRSID_Event                                                         | ControlSection                                      |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 Curve                          | String    | Yes         | Null          | CurveType           |           |       | 3      | Curve                                                               | HorizontalCurveType                                 | 100 Straight (HorizontalCurveType = 'A'), 101 Curve (HorizontalCurveType \<\> 'A')                                                                                                                 |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 DOTDDistrict                   | String    | Yes         | Null          |                     |           |       | 2      | BNDY_DOTD_Districts                                                 | DOTD_DistrictNumber                                 |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 EndLogMile                     | Double    | Yes         | Null          |                     |           |       |        | LRSID_Route                                                         |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 EndLogMileCenterLine           | Double    | Yes         | Null          |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 EventID                        | String    | No          |               |                     |           |       | 38     | Determined via DynSeg                                               |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 FeatureTypeCode                | String    | Yes         | Null          | FeatureTypeCode     |           |       | 2      | StatewideRoutes                                                     | FeatureTypeCode                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 FromDate                       | Date      | Yes         |               |                     |           |       |        | LoadDate                                                            |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 FromMeasure                    | Double    | Yes         |               |                     |           |       |        | Determined via DynSeg                                               |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 FromMeasureCenterLine          | Double    | Yes         | Null          |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 FunctionalClass                | String    | Yes         | Null          | FSystem             |           |       | 1      | FunctionalSystem                                                    | FunctionalSystem                                    |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 HighwayClass                   | String    | Yes         | Null          | HighwayClass        |           |       | 2      | HighwayClass (new event)                                            | HighwayClass                                        |                                                                                                                                                                                                  |                                                              |       | See HighwayClassDomain_Logic tab                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
 HighwayNum                     | String    | Yes         | Null          |                     |           |       | 12     | GP_RouteIdentification                                              | RouteNumber                                         |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 HOVLanes                       | Short     | Yes         | Null          | Number              |           |       | 1      | ManagedLanes                                                        | HOVLanes                                            |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 HOVLanesType                   | String    | Yes         | Null          | ManagedLanesType    |           |       |        | ManagedLanes                                                        | ManagedLanesType                                    | ManagedLanesType - 1 = Fulltime HOV (lane used); 2= Parttime HOV (lane used); 3= Parttime HOV (shoulder used)                                                                                    |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LaneWidth                      | Short     | Yes         | Null          | Number              |           |       |        | LaneWidth                                                           | LaneWidth                                           |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LeftShoulderWidth              | Short     | Yes         | Null          | Number              |           |       |        | ShoulderInside, ShoulderOutside, RoadUse                            | ShoulderWidthPrimary, Divided, RoadUse              |                                                                                                                                                                                                  | Left Shoulder - SWI on divided and SWO on opposite direction |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID                     | String    | No          | Null          |                     |           |       | 32     | HighwayClass                                                        | LocationID                                          |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID_Legecy_1(HPMS 2022) | String    | Yes         |               |                     |           |       | 32     | HighwayClass                                                        |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID_Legecy_2(HPMS 2021) | String    | Yes         |               |                     |           |       | 32     | HighwayClass                                                        |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID_Legecy_3(HPMS_2020) | String    | Yes         |               |                     |           |       | 32     | HighwayClass                                                        |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID_Legecy_4(NULL)      | String    | Yes         |               |                     |           |       | 32     | Future Schema                                                       |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LocationID_Legecy_5(NULL)      | String    | Yes         |               |                     |           |       | 32     | Future Schema                                                       |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LRSID                          | String    | Yes         | Null          |                     |           |       | 18     | LRSID_Event                                                         |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 LRSIDCenterLine                | String    | Yes         | Null          |                     |           |       | 225    |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 NHS                            | String    | Yes         | Null          | NHS                 |           |       | 1      | NHS                                                                 | NHS                                                 |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 NumberofLanes                  | Short     | Yes         | Null          | Number              |           |       |        | ThroughLanes                                                        | ThroughLanes                                        |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 OBJECTID                       |           |             |               |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 Parish                         | String    | Yes         | Null          |                     |           |       | 21     | BNDY_ParishBoundaries                                               | ParishName                                          |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ParishCode                     | String    | Yes         | Null          | ParishCode          |           |       | 2      | BNDY_ParishBoundaries                                               | ParishNumber                                        |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ParishFIPS                     | String    | Yes         | Null          |                     |           |       | 3      | BNDY_ParishBoundaries                                               | ParishFIPS                                          |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ReverseControl                 | String    | Yes         |               | YesNo               |           |       | 1      | LRSID_Event                                                         |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RightShoulderWidth             | Short     | Yes         | Null          | Number              |           |       |        | ShoulderInside, ShoulderOutside, RoadUse                            | ShoulderWidthPrimary, Divided, RoadUse              |                                                                                                                                                                                                  | Right Shoulder - SWO all Roads                               |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadClassification             | String    | Yes         | Null          | RoadClassification  |           |       | 3      | GP_RouteIdentification, FunctionalSystem, PublicPrivate             | RouteSigning, FSystem, Private                      | 100 Interstate, 101 US Highway, 102 State Highway, 103 Parish Road, 104 City Street, 200 Off Road/Private                                                                                        |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadName                       | String    | Yes         | Null          |                     |           |       | 60     | LouisianaRoadway                                                    | St_Name (Alias: Street Name)                        |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadNameDir                    | String    | Yes         | Null          | RoadDirection       |           |       | 9      | LouisianaRoadway                                                    | St_PreDir (Alias: Street Name Pre Directional)      |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadNameType                   | String    | Yes         | Null          | RoadType            |           |       | 50     | LouisianaRoadway                                                    | St_PosTyp (Alias: Street Name Post Type)            |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadUse                        | String    | Yes         | Null          | RoadUse             |           |       | 3      | RoadUse                                                             | RoadUse                                             |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RoadwaySubType                 | String    | Yes         | Null          | RoadwaySubType      |           |       | 3      |                                                                     |                                                     | 100 Mainline, 200 On-Ramp, 201 Off-Ramp, 300 Frontage/Service, 970 - Not Applicable                                                                                                              |                                                              |       | RoadUse IN (‘1’, ‘2’, ‘3a’, ‘3b’, ‘4a’, ‘4b’, ‘5’) Then RoadwaySubType = ‘100’ (Mainline)<br>RoadUse IN (‘6a’, ‘6b’, ‘6c’, ‘6e’, ‘6f’) Then RoadwaySubType = ‘300’ (Frontage/ServiceRoads)<br>FeatureTypeCode IN (‘A_’, ‘B_‘, ‘G_’, ‘H_’) Then RoadwaySubType = ‘200’ (On-Ramp)<br>FeatureTypeCode IN (‘C_’, ‘D_’, ‘E_’, ‘F_’) Then RoadwaySubType = ‘201’ (Off-Ramp)<br>RoadUse IS NULL Then RoadwaySubType = ‘970’ (Not Applicable)<br>                                                                                                                                                                                   
 RouteID                        | String    | No          |               |                     |           |       | 60     | Determined via DynSeg                                               |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RouteIDCenterLine              | String    | Yes         | Null          |                     |           |       | 255    |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 RouteNameFull                  | String    | Yes         | Null          |                     |           |       | 254    | LouisianaRoadway                                                    | FullName (Alias: Full Street Name)                  |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SecondaryName                  | String    | Yes         | Null          |                     |           |       | 254    | LouisianaRoadway                                                    | FullName1 (Alias: Full Street Name Alternate 1)     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SecondaryNameDir               | String    | Yes         | Null          | RoadDirection       |           |       | 9      | LouisianaRoadway                                                    | St_PreDir1 (Alias: Street Name Pre Directional Alt) |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SecondaryNameType              | String    | Yes         | Null          | RoadType            |           |       | 50     | LouisianaRoadway                                                    | St_PosTyp1 (Alias: Street Name Post Type Alt)       |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SecondaryRoadName              | String    | Yes         | Null          |                     |           |       | 60     | LouisianaRoadway                                                    | St_Name1 (Alias: Street Name Alt)                   |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SegmentLength                  | Double    | No          |               |                     |           |       |        | Calculated                                                          |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SpeedLimit                     | Short     | Yes         | Null          | Speed               |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 StateName                      | String    | Yes         | LA            |                     |           |       | 2      | LouisianaRoadway                                                    | State_L (Alias: State Left)                         |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 StateNameType                  | String    | Yes         | Null          | RouteQualifier      |           |       | 2      | GP_RouteIdentification                                              | RouteQualifier                                      |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 Station_ID                     | String    | Yes         | Null          |                     |           |       | 32     | TrafficSegment                                                      | STATION_ID                                          |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 StructureIdentificationNumber  | String    | Yes         | Null          |                     |           |       |        | Bridge                                                              | BRKEY (NBI Number)                                  |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 SystemCode                     | String    | Yes         | Null          | SystemCode          |           |       | 5      |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ToDate                         | Date      | Yes         | Null          |                     |           |       |        | Generated on Data Load                                              |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ToMeasure                      | Double    | Yes         | Null          |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 ToMeasureCenterLine            | Double    | Yes         | Null          |                     |           |       |        |                                                                     |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 TrafficDirection               | String    | Yes         | Null          | InventoryDirection  |           |       | 2      | StatewideRoutes                                                     | InventoryDirection                                  |                                                                                                                                                                                                  |                                                              |       | RouteID LIKE '%1______' TrafficDirection = ‘1’<br>RouteID LIKE '%2______' TrafficDirection = ‘2’<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        
 TrafficWayDivision             | String    | Yes         | Null          | TrafficWayDivision  |           |       | 3      | Medians, RoadUse                                                    | MedianWidthFeet, MedianType, Divided                | 000 Not Divided, 001 Not Divided with a Continuous Left-Turn Lane, 100 Divided Flush Median (greater than 4 feet, 101 Divided Raised Median (curbed), 102 Divided, Depressed Median, 999 Unknown |                                                              |       | If MedianType = ‘1’ AND TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘000’.<br>If MedianType = ‘2’ TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘100’.<br>If MedianType In {‘3’, ‘4’, ‘5’, ‘6’, ‘7’} TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘101’.<br>If RoadUse = 5 TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘001’.<br>If RoadUse IN (‘3a’, ‘3b’, ‘8’) TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘000’.<br>If Divided = ‘N’ TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘000’.<br>If TrafficWayDivision IS NULL Then TrafficWayDivision = ‘999’. 
 TrafficwayTravelDirection      | String    |             | Null          | TrafficWayDirection |           |       | 3      | RoadUse                                                             | RoadUse                                             | 100 One-Way, 200 Two-Way                                                                                                                                                                         |                                                              |       | Highway Safety.RoadUse = ‘1’ Then TrafficwayTravelDirection = ‘100’<br>Highway Safety.RoadUse = ‘2’ Then TrafficwayTravelDirection = ‘200’<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
 Troop                          | String    | Yes         | Null          |                     |           |       | 1      | TBD                                                                 |                                                     |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 UrbanRural                     | String    | Yes         | Null          | UrbanRural          |           |       | 1      | FunctionalSystem                                                    | UrbanRural                                          |                                                                                                                                                                                                  |                                                              |       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
 -->


---

<!-- BEGINNING OF LOCATION AND GEOGRAPHIC IDENTIFIERS SEGMENT 


	BeginLogMile
	BeginLogMileCenterLine
	City
	CityFIPS
	City Parish
	Parish Codes


-->

# **Location and Geographic Identifiers**



## **BeginLogMile**

**Definition:**  
The beginning measure of each roadway segment along the LRS. Measure representative of direction of segment (Primary/Inventory Direction or Secondary/Non-Inventory Direction.

<details>
	<summary>Click to Expand Begin Log Mile Table</summary> 


| Description | Data Type | Source |
|------------|----------|--------|
| Log Mile Start | Double | LRSID_Route |

</details>

---

## **BeginLogMileCenterLine**

**Definition:**  
The beginning measure of each roadway segment along the Control Direction LRS. Measure represents the control direction (Primary/Inventory Direction) only.

<details>
	<summary>Click to Expand Begin Log Mile Center Table</summary> 

| Description | Data Type | Source |
|------------|----------|--------|
| Control Direction Start | Double | DOTD |

</details>

---

## **City**

**Definition:**  
City location and code assigned by LA eCrash.

<details>
    <summary>Click to Expand City Use Table</summary> 


| Description | Data Type | Source |
|------------|----------|--------|
| City Location Code | Text | Lookup Table (City Code Sheet) |

</details>

---

## **CityFIPS**

**Definition:**  
City location FIPS code assigned by the US Census Bureau.

<details>
    <summary>Click to Expand CityFIPS Use Table</summary> 


| Description | Data Type | Source |
|------------|----------|--------|
| City FIPS Code | Text | BDNY_IncorporatedAreas |

</details>

---

## **CityParish**

**Definition:**  
City and Parish Code. City and Parish Codes Assigned by LA eCrash.

<details>
    <summary>Click to Expand City Parish Table</summary>


| Code  | Description                 |
|-------|-----------------------------|
| 1     | Rural Acadia                |
| 2     | Rural Allen                 |
| 3     | Rural Ascension             |
| 4     | Rural Assumption            |
| 5     | Rural Avoyelles             |
| 6     | Rural Beauregard            |
| 7     | Rural Bienville             |
| 8     | Rural Bossier               |
| 9     | Rural Caddo                 |
| 10    | Rural Calcasieu             |
| 11    | Rural Caldwell              |
| 12    | Rural Cameron               |
| 13    | Rural Catahoula             |
| 14    | Rural Claiborne             |
| 15    | Rural Concordia             |
| 16    | Rural DeSoto                |
| 17    | Rural East Baton Rouge      |
| 18    | Rural East Carroll          |
| 19    | Rural East Feliciana        |
| 20    | Rural Evangeline            |
| 21    | Rural Franklin              |
| 22    | Rural Grant                 |
| 23    | Rural Iberia                |
| 24    | Rural Iberville             |
| 25    | Rural Jackson               |
| 26    | Rural Jefferson             |
| 27    | Rural Jefferson Davis       |
| 28    | Rural Lafayette             |
| 29    | Rural Lafourche             |
| 30    | Rural LaSalle               |
| 31    | Rural Lincoln               |
| 32    | Rural Livingston            |
| 33    | Rural Madison               |
| 34    | Rural Morehouse             |
| 35    | Rural Natchitoches          |
| 36    | Rural Orleans               |
| 37    | Rural Ouachita              |
| 38    | Rural Plaquemines           |
| 39    | Rural Pointe Coupee         |
| 40    | Rural Rapides               |
| 41    | Rural Red River             |
| 42    | Rural Richland              |
| 43    | Rural Sabine                |
| 44    | Rural St. Bernard           |
| 45    | Rural St. Charles           |
| 46    | Rural St. Helena            |
| 47    | Rural St. James             |
| 48    | Rural St. John The Baptist  |
| 49    | Rural St. Landry            |
| 50    | Rural St. Martin            |
| 51    | Rural St. Mary              |
| 52    | Rural St. Tammany           |
| 53    | Rural Tangipahoa            |
| 54    | Rural Tensas                |
| 55    | Rural Terrebonne            |
| 56    | Rural Union                 |
| 57    | Rural Vermilion             |
| 58    | Rural Vernon                |
| 59    | Rural Washington            |
| 60    | Rural Webster               |
| 61    | Rural West Baton Rouge      |
| 62    | Rural West Carroll          |
| 63    | Rural West Feliciana        |
| 64    | Rural Winn                  |
| 101    | Church Point               |
| 102    | Elizabeth                  |
| 103    | Donaldsonville             |
| 104    | Napoleonville              |
| 105    | Bunkie                     |
| 106    | Merryville                 |
| 107    | Arcadia                    |
| 108    | Benton                     |
| 109    | Belcher                    |
| 110    | DeQuincy                   |
| 111    | Clarks                     |
| 113    | Harrisonburg               |
| 114    | Athens                     |
| 115    | Clayton                    |
| 116    | Grand Cane                 |
| 117    | Baker                      |
| 118    | Lake Providence            |
| 119    | Clinton                    |
| 120    | Basile                     |
| 121    | Baskin                     |
| 122    | Colfax                     |
| 123    | Jeanerette                 |
| 124    | Grosse Tete                |
| 125    | Chatham                    |
| 126    | Grand Isle                 |
| 127    | Elton                      |
| 128    | Broussard                  |
| 129    | Golden Meadow              |
| 130    | Jena                       |
| 131    | Choudrant                  |
| 132    | Albany                     |
| 133    | Delta                      |
| 134    | Bastrop                    |
| 135    | Ashland                    |
| 136    | New Orleans                |
| 137    | Monroe                     |
| 139    | Fordoche                   |
| 140    | Alexandria                 |
| 141    | Coushatta                  |
| 142    | Delhi                      |
| 143    | Converse                   |
| 146    | Greensburg                 |
| 147    | Gramercy                   |
| 149    | Cankton                    |
| 150    | Breaux Bridge              |
| 151    | Baldwin                    |
| 152    | Abita Springs              |
| 153    | Amite                      |
| 154    | Newellton                  |
| 155    | Houma                      |
| 156    | Bernice                    |
| 157    | Abbeville                  |
| 158    | Anacoco                    |
| 159    | Angie                      |
| 160    | Cotton Valley              |
| 161    | Addis                      |
| 162    | Epps                       |
| 163    | St. Francisville           |
| 164    | Atlanta                    |
| 201    | Crowley                    |
| 202    | Kinder                     |
| 203    | Gonzales                   |
| 205    | Cottonport                 |
| 207    | Bienville                  |
| 208    | Bossier City               |
| 209    | Blanchard                  |
| 210    | Iowa                       |
| 211    | Columbia                   |
| 213    | Jonesville                 |
| 214    | Haynesville                |
| 215    | Ferriday                   |
| 216    | Keatchie                   |
| 217    | Baton Rouge                |
| 218    | Jackson                    |
| 220    | Chataignier                |
| 221    | Gilbert                    |
| 222    | Dry Prong                  |
| 223    | Loreauville                |
| 224    | Maringouin                 |
| 225    | East Hodge                 |
| 226    | Gretna                     |
| 227    | Fenton                     |
| 228    | Carencro                   |
| 229    | Lockport                   |
| 230    | Olla                       |
| 231    | Dubach                     |
| 232    | Denham Springs             |
| 233    | Mound                      |
| 234    | Bonita                     |
| 235    | Campti                     |
| 237    | Richwood                   |
| 239    | Livonia                    |
| 240    | Ball                       |
| 241    | Edgefield                  |
| 242    | Mangham                    |
| 243    | Fisher                     |

</details>

---

## **ParishCodes**


<details>
    <summary>Click to Expand Parish Codes Table</summary>

| Code | Description          |
|------|----------------------|
| 1    | Acadia              |
| 2    | Allen               |
| 3    | Ascension           |
| 4    | Assumption          |
| 5    | Avoyelles           |
| 6    | Beauregard          |
| 7    | Bienville           |
| 8    | Bossier             |
| 9    | Caddo               |
| 10   | Calcasieu           |
| 11   | Caldwell            |
| 12   | Cameron             |
| 13   | Catahoula           |
| 14   | Claiborne           |
| 15   | Concordia           |
| 16   | DeSoto              |
| 17   | East Baton Rouge    |
| 18   | East Carroll        |
| 19   | East Feliciana      |
| 20   | Evangeline          |
| 21   | Franklin            |
| 22   | Grant               |
| 23   | Iberia              |
| 24   | Iberville           |
| 25   | Jackson             |
| 26   | Jefferson           |
| 27   | Jefferson Davis     |
| 28   | Lafayette           |
| 29   | Lafourche           |
| 30   | LaSalle             |
| 31   | Lincoln             |
| 32   | Livingston          |
| 33   | Madison             |
| 34   | Morehouse           |
| 35   | Natchitoches        |
| 36   | Orleans             |
| 37   | Ouachita            |
| 38   | Plaquemines         |
| 39   | Pointe Coupee       |
| 40   | Rapides             |
| 41   | Red River           |
| 42   | Richland            |
| 43   | Sabine              |
| 44   | St. Bernard         |
| 45   | St. Charles         |
| 46   | St. Helena          |
| 47   | St. James           |
| 48   | St. John            |
| 49   | St. Landry          |
| 50   | St. Martin          |
| 51   | St. Mary            |
| 52   | St. Tammany         |
| 53   | Tangipahoa          |
| 54   | Tensas              |
| 55   | Terrebonne          |
| 56   | Union               |
| 57   | Vermilion           |
| 58   | Vernon              |
| 59   | Washington          |
| 60   | Webster             |
| 61   | West Baton Rouge    |
| 62   | West Carroll        |
| 63   | West Feliciana      |
| 64   | Winn                |

</details>

---

<!-- BEGINNING OF ROAD CLASSIFICATION SEGMENT 


	Road Classification Codes
	Functional Classifications
	Urban vs. Rural Classification
	Highway Class
	Highway Class Schema - Questionable at Best
	F System


-->

# Road Classifications 

## **Road Classification Codes**

<details>
    <summary>Click to Expand Road Classification Code Table</summary>

| Code | Description |
|------|------------|
| 100  | Interstate |
| 101  | US Highway |
| 102  | State Highway |
| 103  | Parish Road |
| 104  | City Street |
| 200  | Off Road/Private Road|

</details>

---

## **Functional_Classifications**


<details>
    <summary>Click to Expand Functional Classification Table</summary>


| Code | Description |
|------|------------|
| 1    | Interstate |
| 2    | Principal Arterial |
| 3    | Minor Arterial |
| 4    | Collector |
| 5    | Local |

</details>

---

## **Urban vs Rural**

<details>
    <summary>Click to Expand Urban vs. Rural Classification Table</summary>

| Code | Description |
|------|------------|
| R    | Rural |
| U    | Urban |

</details>

---

## **Highway Class**

<details>
    <summary>Click to Expand Highway Class Table</summary>


| Code | Description                            | Division                         |
|------|----------------------------------------|----------------------------------|
| 1    | 1 - Rural 1-way 1-lane                | Rural 1-way 1-lane               |
| 2    | 2 - Urban 1-way 1-lane                | Urban 1-way 1-lane               |
| 3    | 3 - Rural 1-way 2-lane                | Rural 1-way 2-lane               |
| 4    | 4 - Urban 1-way 2-lane                | Urban 1-way 2-lane               |
| 5    | 5 - Rural 1-way 3-lane                | Rural 1-way 3-lane               |
| 6    | 6 - Urban 1-way 3-lane                | Urban 1-way 3-lane               |
| 7    | 7 - Rural 1-way 4-lane                | Rural 1-way 4-lane               |
| 8    | 8 - Urban 1-way 4-lane                | Urban 1-way 4-lane               |
| 9    | 9 - Urban 2-lane Interstate           | Urban 2-lane Interstate          |
| 10   | 10 - Rural 3-lane Interstate          | Rural 3-lane Interstate          |
| 11   | 11 - Urban 3-lane Interstate          | Urban 3-lane Interstate          |
| 12   | 12 - Rural 4-lane Interstate          | Rural 4-lane Interstate          |
| 13   | 13 - Urban 4-lane Interstate          | Urban 4-lane Interstate          |
| 14   | 14 - Urban 5-lane Interstate          | Urban 5-lane Interstate          |
| 15   | 15 - Rural 6-lane Interstate          | Rural 6-lane Interstate          |
| 16   | 16 - Urban 6-lane Interstate          | Urban 6-lane Interstate          |
| 17   | 17 - Rural 8-lane Interstate          | Rural 8-lane Interstate          |
| 18   | 18 - Urban 8-lane Interstate          | Urban 8-lane Interstate          |
| 19   | 19 - Rural 2-lane                     | Rural 2-lane                     |
| 20   | 20 - Urban 2-lane                     | Urban 2-lane                     |
| 21   | 21 - Rural 4-lane                     | Rural 4-lane                     |
| 22   | 22 - Urban 4-lane                     | Urban 4-lane                     |
| 23   | 23 - Rural 4-lane Divided             | Rural 4-lane Divided             |
| 24   | 24 - Urban 4-lane Divided             | Urban 4-lane Divided             |
| 25   | 25 - Urban 4-lane Freeway             | Urban 4-lane Freeway             |
| 26   | 26 - Rural 2-lane Divided             | Rural 2-lane Divided             |
| 27   | 27 - Urban 2-lane Divided             | Urban 2-lane Divided             |
| 28   | 28 - Rural 3-lane                     | Rural 3-lane                     |
| 29   | 29 - Urban 3-lane                     | Urban 3-lane                     |
| 30   | 30 - Rural 3-lane Divided             | Rural 3-lane Divided             |
| 31   | 31 - Urban 3-lane Divided             | Urban 3-lane Divided             |
| 32   | 32 - Rural 6-lane                     | Rural 6-lane                     |
| 33   | 33 - Urban 6-lane                     | Urban 6-lane                     |
| 34   | 34 - Rural >=6-lane Divided           | Rural >=6-lane Divided           |
| 35   | 35 - Urban >=6-lane Divided           | Urban >=6-lane Divided           |
| 36   | 36 - Rural 2-lane Cont Turn           | Rural 2-lane Cont Turn           |
| 37   | 37 - Urban 2-lane Cont Turn           | Urban 2-lane Cont Turn           |
| 38   | 38 - Rural 4-lane Cont Turn           | Rural 4-lane Cont Turn           |
| 39   | 39 - Urban 4-lane Cont Turn           | Urban 4-lane Cont Turn           |
| 40   | 40 - Rural >=6-lane Cont Turn         | Rural >=6-lane Cont Turn         |
| 41   | 41 - Urban >=6-lane Cont Turn         | Urban >=6-lane Cont Turn         |
| 42   | 42 - Other Rural Roads                | Other Rural Roads                |
| 43   | 43 - Other Urban Roads                | Other Urban Roads                |

</details>

---

## Highway Class Schema 

<details>
    <summary>Click to Expand Highway Class Schema Table</summary>

| Field Name                 | Data Type | Allow Nulls | Default Value | Domain                 | Precision | Scale | Length | DataSourceLayer                   | DataSourceField         | DerivedField_Classification | Comment/Question? | Response | Disposition | Definition Query | Added | Formula |
|----------------------------|----------|-------------|---------------|------------------------|-----------|-------|--------|-----------------------------------|-------------------------|----------------------------|--------------------|----------|-------------|------------------|-------|---------|
| OBJECTID                   |          |             |               |                        |           |       |        |                                   |                         |                            |                    |          |             |                  |       |         |
| FromDate                   | Date     | Yes         |               |                        |           |       |        | LoadDate                          |                         |                            |                    |          |             |                  |       |         |
| ToDate                     | Date     | Yes         | Null          |                        |           |       |        | Generated on Data Load            |                         |                            |                    |          |             |                  |       |         |
| EventID                    | String   | No          |               |                        |           |       | 38     | Determined via DynSeg             |                         |                            |                    |          |             |                  |       |         |
| RouteID                    | String   | No          |               |                        |           |       | 60     | Determined via DynSeg             |                         |                            |                    |          |             |                  |       |         |
| FromMeasure                | Double   | Yes         |               |                        |           |       |        | Determined via DynSeg             |                         |                            |                    |          |             |                  |       |         |
| ToMeasure                  | Double   | Yes         | Null          |                        |           |       |        |                                   |                         |                            |                    |          |             |                  |       |         |
| RoadUse                    | String   | Yes         | Null          | RoadUse                |           |       | 3      | RoadUse                           | RoadUse                 |                            | Is RoadUse being maintained by Inventory or Mapping? | Maintained by Mapping and is current and correct. |             |                  |       |         |
| TrafficWayDivision         | String   | Yes         | Null          | TrafficWayDivision     |           |       | 3      | Medians, RoadUse                  | MedianWidthFeet, MedianType, Divided | 000 Not Divided, 001 Not Divided with a Continuous Left-Turn Lane, 100 Divided Flush Median (greater than 4 feet, 101 Divided Raised Median (curbed), 102 Divided, Depressed Median, 999 Unknown | Is the Medians layer accurate and up to date? | Medians should be in pretty good condition for the on-system routes. However, there are only records in the one direction and we do not have records where there are no medians. | Combine median width and median type to derive TrafficWayDivision. | | If MedianType = ‘1’ AND TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘000’. If MedianType = ‘2’ TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘100’. If MedianType In \{‘3’, ‘4’, ‘5’, ‘6’, ‘7’\} TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘101’. If RoadUse = 5 TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘001’. If RoadUse IN (‘3a’, ‘3b’, ‘8’) TrafficWayDivision IS NULL ; Then TrafficWayDivision = ‘000’. If TrafficWayDivision IS NULL Then TrafficWayDivision = ‘999’." |
| TrafficwayTravelDirection  | String   |            | Null          | TrafficWayDirection    |           |       | 3      | RoadUse                            | RoadUse                 | 100 One-Way, 200 Two-Way  |                    |          |             | Map RoadUse value to one-way/two-way values in TrafficWayDirection domain. | | "Highway Safety.RoadUse = ‘1’ Then TrafficwayTravelDirection = ‘100’. Highway Safety.RoadUse = ‘2’ Then TrafficwayTravelDirection = ‘200’" |
| TrafficDirection           | String   | Yes        | Null          | InventoryDirection     |           |       | 2      | StatewideRoutes                   | InventoryDirection       |                            |                    |          |             | "RouteID LIKE '%1______' TrafficDirection = ‘1’. RouteID LIKE '%2______' TrafficDirection = ‘2’" |
| LocationID                 | String   | No         | Null          |                        |           |       | 32     | HighwayClass                      | LocationID               |                            |                    |          |             |                  |       |         |
| Parish                     | String   | Yes        | Null          |                        |           |       | 21     | BNDY_ParishBoundaries             | ParishName               |                            | Who is maintaining the Parish Boundaries? Are they accurate and up to date? | Mapping manages Parish Boundaries. There are relatively very few changes from year to year. Most changes have been caught up in ongoing legal litigations. They are accurate as we speak. |             |                  |       |         |
| ParishCode                 | String   | Yes        | Null          | ParishCode            |           |       | 2      | BNDY_ParishBoundaries             | ParishNumber             |                            |                    |          |             |                  |       |         |
| ParishFIPS                 | String   | Yes        | Null          |                        |           |       | 3      | BNDY_ParishBoundaries             | ParishFIPS               |                            |                    |          |             |                  |       |         |
| City                       | String   | Yes        | Null          |                        |           |       | 100    | Derived from City Code Sheet - Lookup Table, BNDY_IncorporatedAreas | | Who is maintaining the Incorporated Areas layer? Is it accurate and up to date? | Mapping manages Incorporated Areas. I am not sure on the frequency of these updates into the layer. I know Jason and Darryl were looking into possibly consuming this data from Sec. of State or another Federal entity since we don’t always get the changes. Most disputes are at water bodies and swamp areas where the boundary is “indefinite”, not near roadways. |             |                  |       |         |
| DOTDDistrict               | String   | Yes        | Null          |                        |           |       | 2      | BNDY_DOTD_Districts               | DOTD_DistrictNumber      |                            | Who is maintaining the District Boundaries layer? Is it accurate and up to date? | District Boundary is managed by mapping. This is up to date and will not change unless a Parish boundary is altered. |             |                  |       |         |
| Troop                     | String   | Yes         | Null          |                    | 1         |       |        | TBD                              |                                        |                            | Where can I find a connection file to the SoE Topo Geospatial Warehouse? | [Link](https://maps.dotd.la.gov/topo/rest/services/OpenData/Boundaries/MapServer/11) | Darryl provided some SDE connection info but we need to know the SQL Server instance and DB authentication password. | |
| ControlSection            | String   | Yes         | Null          |                    | 6         |       |        | LRSID_Event                     | ControlSection                         |                            |                    |          |             |                  |       |         |
| LRSID                     | String   | Yes         | Null          |                    | 18        |       |        | LRSID_Event                     |                                        |                            |                    |          |             |                  |       |         |
| BeginLogMile              | Double   | Yes         | Null          |                    |           |       |        | LRSID_Route                     |                                        |                            |                    |          |             |                  |       |         |
| EndLogMile                | Double   | Yes         | Null          |                    |           |       |        | LRSID_Route                     |                                        |                            |                    |          |             |                  |       |         |
| RoadClassification        | String   | Yes         | Null          | RoadClassification | 3         |       |        | GP_RouteIdentification, FunctionalSystem, PublicPrivate | RouteSigning, FSystem, Private | 100 Interstate, 101 US Highway, 102 State Highway, 103 Parish Road, 104 City Street, 200 Off Road/Private | Is PublicPrivate accurate and up to date? | Public/Private is in a fair to good condition. I have Nathan working on this layer. There is good confidence on records where there is a Public Record. I imagine there are still a lot of Privates that are indeed Public. | If listed as a private road, do not populate RoadClass since it is known that some roads flagged in RH as private are actually public. Patrol officers will populate road class in incident reports if not populated automatically from layer. | |
| RoadwaySubType            | String   | Yes         | Null          | RoadwaySubType     | 3         |       |        |                                  |                                        | 100 Mainline, 200 On-Ramp, 201 Off-Ramp, 300 Frontage/Service, 970 - Not Applicable | Who is maintaining RoadUse? Is it accurate and up to date? | Mapping is maintaining RoadUse and it is accurate and current for most roads. | Map fields from RoadUse to derive RoadwaySubType domain. | | "RoadUse IN (‘1’, ‘2’, ‘3a’, ‘3b’, ‘4a’, ‘4b’, ‘5’) Then RoadwaySubType = ‘100’ (Mainline). RoadUse IN (‘6a’, ‘6b’, ‘6c’, ‘6e’, ‘6f’) Then RoadwaySubType = ‘300’ (Frontage/ServiceRoads). FeatureTypeCode IN (‘A_’, ‘B_‘, ‘G_’, ‘H_’) Then RoadwaySubType = ‘200’ (On-Ramp). FeatureTypeCode IN (‘A_’, ‘B_‘, ‘G_’, ‘H_’) Then RoadwaySubType = ‘200’ (On-Ramp). FeatureTypeCode IN (‘C_’, ‘D_’, ‘E_’, ‘F_’) Then RoadwaySubType = ‘201’ (Off-Ramp). |
| RouteNameFull            | String   | Yes         | Null          |                    | 254       |       |        | LouisianaRoadway                 | FullName (Alias: Full Street Name)     | Full Street Name           |                    |          |             | Do not populate if road name contains "Unnamed". | | |
| RoadNameDir              | String   | Yes         | Null          | RoadDirection      | 9         |       |        | LouisianaRoadway                 | St_PreDir (Alias: Street Name Pre Directional) | Street Name Pre Directional | | | | | |
| RoadName                 | String   | Yes         | Null          |                    | 60        |       |        | LouisianaRoadway                 | St_Name (Alias: Street Name)           | Street Name                 |                    |          |             | Do not populate if road name contains "Unnamed". | | |
| RoadNameType             | String   | Yes         | Null          | RoadType           | 50        |       |        | LouisianaRoadway                 | St_PosTyp (Alias: Street Name Post Type) | Street Name Post Type | | | | | |
| StateName               | String   | Yes         | LA            |                    | 2         |       |        | LouisianaRoadway                 | State_L (Alias: State Left)            |                            |                    |          |             |                  |       |         |
| HighwayNum              | String   | Yes         | Null          |                    | 12        |       |        | GP_RouteIdentification          | RouteNumber                            |                            |                    |          |             |                  |       |         |
| StateNameType           | String   | Yes         | Null          | RouteQualifier     | 2         |       |        | GP_RouteIdentification          | RouteQualifier                          |                            |                    |          |             |                  |       |         |
| SecondaryName           | String   | Yes         | Null          |                    | 254       |       |        | LouisianaRoadway                 | FullName1 (Alias: Full Street Name Alternate 1) | | | | | |
| SecondaryNameDir        | String   | Yes         | Null          | RoadDirection      | 9         |       |        | LouisianaRoadway                 | St_PreDir1 (Alias: Street Name Pre Directional Alt) | | | | | |
| SecondaryRoadName       | String   | Yes         | Null          |                    | 60        |       |        | LouisianaRoadway                 | St_Name1 (Alias: Street Name Alt) | | | | | |
| SecondaryNameType       | String   | Yes         | Null          | RoadType           | 50        |       |        | LouisianaRoadway                 | St_PosTyp1 (Alias: Street Name Post Type Alt) | | | | | |
| UrbanRural             | String   | Yes         | Null          | UrbanRural        | 1         |       |        | FunctionalSystem                 | UrbanRural                              |                            |                    |          |             |                  |       |         |
| SegmentLength          | Double   | No          |               |                    |           |       |        | Calculated                        |                                        |                            |                    |          |             |                  |       |         |
| SpeedLimit                           | Short    | Yes         | Null          | Speed              |           |       |        |                                  |                                        |                            | Is SpeedLimitZone accurate and up to date? | Speed Zones are not being maintained by Inventory. We do try and keep up the Speed Limit signs event and I feel pretty good about those. The linear speed zone layer I do not have confidence in. All spot checks were wrong. If there becomes an auto-process to use signs to create zones, it will probably be good. | Leave blank for now; ETL will be modified to include speed limit information once a tool has been developed to derive good speed limit zone data from speed limit signs. | |
| Curve                                 | String   | Yes         | Null          | CurveType          |           |       | 3      | Curve                            | HorizontalCurveType                     | 100 Straight (HorizontalCurveType = 'A'), 101 Curve (HorizontalCurveType \<\> 'A') | | A curves are straight and all other curves (B,C,D,E,&F) are curved. | |
| NHS                                   | String   | Yes         | Null          | NHS                |           |       | 1      | NHS                              | NHS                                    |                            |                    |          |             |                  |       |         |
| AADT_Year                             | Long     | Yes         | Null          |                    |           |       |        | AADT (ALRS)                     | DataYear                               |                            | Waiting to get data from Adrien. | | | | |
| AADT                                  | Long     | Yes         | Null          |                    |           |       |        | AADT (ALRS)                     | AADT                                   |                            | | | | | |
| AADT_Truck                            | Long     | Yes         | Null          |                    |           |       |        | Sum of AADTSingleUnit and AADTCombination (ALRS) | AADTSingleUnit+AADTCombination | | Can be loaded from prior year's HPMS data from MS2 - Requires schema change in R&H. | Leave blank for now as it will impact the TrafficSegment schema. Will revisit after HPMS submittal June 15. | |
| AADT_Motorcycle                       | Long     | Yes         | Null          |                    |           |       |        | AADTMotorcycle (ALRS)           |                                        |                            | Can be loaded from prior year's HPMS data from MS2 - Requires schema change in R&H. | Leave blank for now as it will impact the TrafficSegment schema. Will revisit after HPMS submittal June 15. | |
| LaneWidth                             | Short    | Yes         | Null          | Number             |           |       |        | LaneWidth                        | LaneWidth                              |                            | Is LaneWidth accurate and up to date? | Lane width is a good layer (usually rounded to the nearest foot) for on-system routes. Off-system lane widths were not loaded into R&H’s. | |
| NumberofLanes                         | Short    | Yes         | Null          | Number             |           |       |        | ThroughLanes                     | ThroughLanes                           |                            | ThroughLanes - Currently being updated/fixed by Monica. What is the plan for their continued maintenance in the future? | Through lanes is currently being looked at as a “buildable” layer created in HPMS manager. If PMG cannot come up with logic to create it, we will likely have to create a stand-alone layer or add field into the current No. of Lanes event. My guess is a new layer will likely have to be created but we will see. | |
| HOVLanes                              | Short    | Yes         | Null          | Number             |           |       | 1      | ManagedLanes                     | HOVLanes                               |                            |                    |          |             |                  |       |         |
| HOVLanesType                          | String   | Yes         | Null          | ManagedLanesType   |           |       |        | ManagedLanes                     | ManagedLanesType                        | ManagedLanesType - 1 = Fulltime HOV (lane used); 2 = Part-time HOV (lane used); 3 = Part-time HOV (shoulder used) | | | | |
| LeftShoulderWidth                     | Short    | Yes         | Null          | Number             |           |       |        | ShoulderInside, ShoulderOutside, RoadUse | ShoulderWidthPrimary, Divided, RoadUse | | Are Inside and Outside shoulder layers accurate and up to date? | Shoulder data is good for on-system and should be generally up-to-date. 6/20/24 - Processing of the layer is not needed. Use the layer directly from Roads & Highways (do not use the layer from HPMS as segmentation from these events isn’t needed). Spatially join the layer to the routes (the output that has been iterated over) and assign the value based on dominant length. | Left shoulder is ShoulderWidthInside on divided roads and ShoulderWidthOutside on opposite direction routes on undivided roads. | Left Shoulder - SWI on divided and SWO on opposite direction |
| RightShoulderWidth                    | Short    | Yes         | Null          | Number             |           |       |        | ShoulderInside, ShoulderOutside, RoadUse | ShoulderWidthPrimary, Divided, RoadUse | | Per Adrien 3/13/2024: ShoulderOutside for the primary direction and ShoulderInside for secondary direction on undivided roads and ShoulderOutside on divided roads. | Shoulder data is good for on-system and should be generally up-to-date. 6/20/24 - Processing of the layer is not needed. Use the layer directly from Roads & Highways (do not use the layer from HPMS as segmentation from these events isn’t needed). Spatially join the layer to the routes (the output that has been iterated over) and assign the value based on dominant length. | Right shoulder is ShoulderWidthOutside on all roads. | Right Shoulder - SWO all Roads |
| AccessControl                         | String   | Yes         | Null          | AccessControl      |           |       | 1      | AccessControl                     | AccessControl                           |                            | Is Access Control accurate and up to date? | There is high confidence on this layer and is generally complete and up-to-date for primary and secondary directions. There may need to be some additional clean-up for off and on ramp locations. I’ll need clarification from Misty on how to handle some of the non-mainline areas. Ex. What to call an Interstate off and on ramp? | | |
| HighwayClass                          | String   | Yes         | Null          | HighwayClass       |           |       | 2      | HighwayClass (new event)         | HighwayClass                            |                            |                    |          |             | See HighwayClassDomain_Logic tab |       |         |
| FunctionalClass                        | String   | Yes         | Null          | FSystem           |           |       | 1      | FunctionalSystem                 | FunctionalSystem                        |                            |                    |          |             |                  |       |         |
| StructureIdentificationNumber         | String   | Yes         | Null          |                    |           |       |        | Bridge                            | BRKEY (NBI Number)                     |                            |                    |          |             |                  |       |         |
| Station_ID                             | String   | Yes         | Null          |                    | 32        |       |        | TrafficSegment                   | STATION_ID                              |                            |                    |          |             |                  |       |         |
| FeatureTypeCode                        | String   | Yes         | Null          | FeatureTypeCode   |           |       | 2      | StatewideRoutes                   | FeatureTypeCode                         |                            |                    |          |             |                  |       |         |
| SystemCode                             | String   | Yes         | Null          | SystemCode        |           |       | 5      |                                  |                                        |                            |                    |          |             |                  |       |         |
| RouteIDCenterLine                      | String   | Yes         | Null          |                |           |       | 255    |                  |                |                            | For Secondary Direction only. RouteID of Primary Direction route corresponding to this segment | | | | | |
| FromMeasureCenterLine                   | Double   | Yes         | Null          |                |           |       |        |                  |                |                            | For Secondary Direction only. From Measure of Primary Direction route corresponding to this segment | | | | | |
| ToMeasureCenterLine                     | Double   | Yes         | Null          |                |           |       |        |                  |                |                            | For Secondary Direction only. To Measure of Primary Direction route corresponding to this segment | | | | | |
| LRSIDCenterLine                         | String   | Yes         | Null          |                |           |       | 225    |                  |                |                            | For Secondary Direction only. LRSID of Primary Direction route corresponding to this segment | | | | | |
| BeginLogMileCenterLine                  | Double   | Yes         | Null          |                |           |       |        |                  |                |                            | For Secondary Direction only. LRSID From Measure of Primary Direction route corresponding to this segment | | | | | |
| EndLogMileCenterLine                    | Double   | Yes         | Null          |                |           |       |        |                  |                |                            | For Secondary Direction only. LRSID To Measure of Primary Direction route corresponding to this segment | | | | | |
| LocationID_Legacy_1 (HPMS 2022)         | String   | Yes         |               |                |           |       | 32     | HighwayClass     |                |                            | Location ID from previous year | | | | | |
| LocationID_Legacy_2 (HPMS 2021)         | String   | Yes         |               |                |           |       | 32     | HighwayClass     |                |                            | Location ID from two years ago | | | | | |
| LocationID_Legacy_3 (HPMS 2020)         | String   | Yes         |               |                |           |       | 32     | HighwayClass     |                |                            | Location ID from three years ago | | | | | |
| LocationID_Legacy_4 (NULL)              | String   | Yes         |               |                |           |       | 32     | Future Schema    |                |                            | Location ID from four years ago | | | | | |
| LocationID_Legacy_5 (NULL)              | String   | Yes         |               |                |           |       | 32     | Future Schema    |                |                            | Location ID from five years ago | | | | | |
| ReverseControl                          | String   | Yes         |               | YesNo          |           |       | 1      | LRSID_Event      |                |                            | | | | | |

</details>

---


## Highway Class Descriptions

<details>
    <summary>Click to Expand Highway Class Domain Logic Table</summary>

| New Code | COLUMN_ID | COLUMN_NAME | CODE_DESCRIPTION | FULL_CODE_DESC | NEW QUERY DETAIL | QueryUsed_AlisonM |
|----------|------------|--------------|-------------------|------------------|--------------------|----------------------|
| 1 | HC | HIGHWAY_CLASS | Rural 1-way 1-lane | 1 - Rural 1-way 1-lane | UrbanRural = 'R' AND ThroughLanes = 1 AND RoadUse In ('1','7','8') | UrbanRural = 'R' AND NumberofLanes = 1 AND RoadUse In ('1','7','8') AND HighwayClass Is Null |
| 2 | HC | HIGHWAY_CLASS | Urban 1-way 1-lane | 2 - Urban 1-way 1-lane | UrbanRural = 'U' AND ThroughLanes = 1 AND RoadUse Not In ('4a','4b','2','6c','0') | UrbanRural = 'U' AND NumberofLanes = 1 AND RoadUse Not In ('4a','4b','2','6c','0') AND HighwayClass Is Null |
| 3 | HC | HIGHWAY_CLASS | Rural 1-way 2-lane | 3 - Rural 1-way 2-lane | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse In ('1','7','8') | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse In ('1','7','8') AND HighwayClass Is Null |
| 4 | HC | HIGHWAY_CLASS | Urban 1-way 2-lane | 4 - Urban 1-way 2-lane | UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse IN ('1' ,'6a','6b','7','8') | UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse IN ('1' ,'6a','6b','7','8') AND HighwayClass Is Null |
| 5 | HC | HIGHWAY_CLASS | Rural 1-way 3-lane | 5 - Rural 1-way 3-lane | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalClass \<\> '1' AND RoadUse = '1' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass \<\> '1' AND RoadUse = '1' AND HighwayClass Is Null |
| 6 | HC | HIGHWAY_CLASS | Urban 1-way 3-lane | 6 - Urban 1-way 3-lane | UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalClass \<\> '1' AND RoadUse = '1' | UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass \<\> '1' AND RoadUse = '1' AND HighwayClass Is Null |
| 7 | HC | HIGHWAY_CLASS | Rural 1-way 4-lane | 7 - Rural 1-way 4-lane | UrbanRural = 'R' AND ThroughLanes = 4 AND FunctionalClass \<\> '1' AND RoadUse = '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND FunctionalClass \<\> '1' AND RoadUse = '1' AND HighwayClass Is Null |
| 8 | HC | HIGHWAY_CLASS | Urban 1-way 4-lane | 8 - Urban 1-way 4-lane | UrbanRural = 'U' AND ThroughLanes = 4 AND FunctionalClass \<\> '1' AND RoadUse = '1' | UrbanRural = 'U' AND NumberofLanes = 4 AND FunctionalClass \<\> '1' AND RoadUse = '1' AND HighwayClass Is Null |
| 9 | HC | HIGHWAY_CLASS | Urban 2-lane Interstate | 9 - Urban 2-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 2 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 2 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 10 | HC | HIGHWAY_CLASS | Rural 3-lane Interstate | 10 - Rural 3-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 11 | HC | HIGHWAY_CLASS | Urban 3-lane Interstate | 11 - Urban 3-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 12 | HC | HIGHWAY_CLASS | Rural 4-lane Interstate | 12 - Rural 4-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 4 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 13 | HC | HIGHWAY_CLASS | Urban 4-lane Interstate | 13 - Urban 4-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 4 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 4 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 14 | HC | HIGHWAY_CLASS | Urban 5-lane Interstate | 14 - Urban 5-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 5 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 5 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 15 | HC | HIGHWAY_CLASS | Rural 6-lane Interstate | 15 - Rural 6-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 6 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 6 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 16 | HC | HIGHWAY_CLASS | Urban 6-lane Interstate | 16 - Urban 6-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 6 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 6 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 17 | HC | HIGHWAY_CLASS | Rural 8-lane Interstate | 17 - Rural 8-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 8 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 8 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 18 | HC | HIGHWAY_CLASS | Urban 8-lane Interstate | 18 - Urban 8-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 8 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 8 AND FunctionalClass = '1' AND HighwayClass Is Null |
| 19 | HC | HIGHWAY_CLASS | Rural 2-lane | 19 - Rural 2-lane | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND Divided = 'N' | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND (RoadUse \<\> '4a' AND RoadUse \<\> '4b')) AND HighwayClass Is Null |
| 20 | HC | HIGHWAY_CLASS | Urban 2-lane | 20 - Urban 2-lane | UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND Divided = 'N' | UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND (RoadUse \<\> '4a' AND RoadUse \<\> '4b')) AND HighwayClass Is Null |
| 21 | HC | HIGHWAY_CLASS | Rural 4-lane | 21 - Rural 4-lane | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse \<\> '5' AND FunctionalSystem \<\> '1' AND Divided = 'N' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse \<\> '5' AND FunctionalClass \<\> '1' AND (RoadUse \<\> '4a' AND RoadUse \<\> '4b')) AND HighwayClass Is Null |
| 22 | HC | HIGHWAY_CLASS | Urban 4-lane | 22 - Urban 4-lane | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem NOT IN ('1', '2') AND Divided = 'N' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass NOT IN ('1', '2') AND (RoadUse \<\> '4a' AND RoadUse \<\> '4b')) AND HighwayClass Is Null |
| 23 | HC | HIGHWAY_CLASS | Rural 4-lane Divided | 23 - Rural 4-lane Divided | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse \<\> '5' AND FunctionalSystem \<\> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse \<\> '5' AND FunctionalClass \<\> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
| 24 | HC | HIGHWAY_CLASS | Urban 4-lane Divided | 24 - Urban 4-lane Divided | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem NOT IN ('1', '2') AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass NOT IN ('1', '2') AND (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 25 | HC | HIGHWAY_CLASS | Urban 4-lane Freeway | 25 - Urban 4-lane Freeway | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem = '2' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass = '2' AND HighwayClass Is Null |
| 26 | HC | HIGHWAY_CLASS | Rural 2-lane Divided | 26 - Rural 2-lane Divided | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse \<\> '5' AND FunctionalSystem \<\> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse \<\> '5' AND FunctionalClass \<\> '1' AND (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 27 | HC | HIGHWAY_CLASS | Urban 2-lane Divided | 27 - Urban 2-lane Divided | UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem \<\> '1' AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND FunctionalClass \<\> '1' AND (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 28 | HC | HIGHWAY_CLASS | Rural 3-lane | 28 - Rural 3-lane | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalSystem \<\> '1' AND NOT Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass \<\> '1' AND NOT (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 29 | HC | HIGHWAY_CLASS | Urban 3-lane | 29 - Urban 3-lane | UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalSystem \<\> '1' AND NOT Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass \<\> '1' AND NOT (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 30 | HC | HIGHWAY_CLASS | Rural 3-lane Divided | 30 - Rural 3-lane Divided | UrbanRural = 'R' AND ThroughLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem \<\> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalClass \<\> '1' AND (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 31 | HC | HIGHWAY_CLASS | Urban 3-lane Divided | 31 - Urban 3-lane Divided | UrbanRural = 'U' AND ThroughLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem \<\> '1' AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalClass \<\> '1' AND (RoadUse = '4a' OR RoadUse = '4b')) AND HighwayClass Is Null |
| 32 | HC | HIGHWAY_CLASS | Rural 6-lane | 32 - Rural 6-lane | UrbanRural = 'R' AND ThroughLanes = 6 AND RoadUse = '2' AND FunctionalSystem \<\> '1' | UrbanRural = 'R' AND NumberofLanes = 6 AND RoadUse = '2' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 33 | HC | HIGHWAY_CLASS | Urban 6-lane | 33 - Urban 6-lane | UrbanRural = 'U' AND ThroughLanes = 6 AND RoadUse = '2' AND FunctionalSystem \<\> '1' | UrbanRural = 'U' AND NumberofLanes = 6 AND RoadUse = '2' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 34 | HC | HIGHWAY_CLASS | Rural >=6-lane Divided | 34 - Rural >=6-lane Divided | UrbanRural = 'R' AND ThroughLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalSystem \<\> '1' | UrbanRural = 'R' AND NumberofLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 35 | HC | HIGHWAY_CLASS | Urban >=6-lane Divided | 35 - Urban >=6-lane Divided | UrbanRural = 'U' AND ThroughLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalSystem \<\> '1' | UrbanRural = 'U' AND NumberofLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 36 | HC | HIGHWAY_CLASS | Rural 2-lane Cont Turn | 36 - Rural 2-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 37 | HC | HIGHWAY_CLASS | Urban 2-lane Cont Turn | 37 - Urban 2-lane Cont Turn | UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 38 | HC | HIGHWAY_CLASS | Rural 4-lane Cont Turn | 38 - Rural 4-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 39 | HC | HIGHWAY_CLASS | Urban 4-lane Cont Turn | 39 - Urban 4-lane Cont Turn | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 40 | HC | HIGHWAY_CLASS | Rural >=6-lane Cont Turn | 40 - Rural >=6-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes >= 6 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'R' AND NumberofLanes >= 6 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 41 | HC | HIGHWAY_CLASS | Urban >=6-lane Cont Turn | 41 - Urban >=6-lane Cont Turn | UrbanRural = 'U' AND ThroughLanes >= 6 AND RoadUse = '5' AND FunctionalSystem \<\> '1' | UrbanRural = 'U' AND NumberofLanes >= 6 AND RoadUse = '5' AND FunctionalClass \<\> '1' AND HighwayClass Is Null |
| 42 | HC | HIGHWAY_CLASS | Other Rural Roads | 42 - Other Rural Roads | UrbanRural = 'R' AND HighwayClass NOT IN ('U', 'X', 'D', 'E', 'F', 'G', 'H', 'R', 'S', 'A', 'B', 'C', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18') | UrbanRural = 'R' AND HighwayClass Is Null |
| 43 | HC | HIGHWAY_CLASS | Other Urban Roads | 43 - Other Urban Roads | UrbanRural = 'U' AND HighwayClass NOT IN ('U', 'X', 'D', 'E', 'F', 'G', 'H', 'R', 'S', 'A', 'B', 'C', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18') | UrbanRural = 'U' AND HighwayClass Is Null |

</details>

---

## **F System**

<details>
    <summary>Click to Expand F System Table</summary>


| Code | Description                                        | Division                                        |
|------|----------------------------------------------------|------------------------------------------------|
| 1    | 1-Interstate                                      | Interstate                                    |
| 2    | 2-Principal Arterial – Other Freeways/Expressways | Principal Arterial – Other Freeways/Expressways |
| 3    | 3-Principal Arterial – Other                      | Principal Arterial – Other                     |
| 4    | 4-Minor Arterial                                  | Minor Arterial                                |
| 5    | 5-Major Collector                                | Major Collector                              |
| 6    | 6-Minor Collector                                | Minor Collector                              |
| 7    | 7-Local                                         | Local                                        |


</details>

---

<!-- BEGINNING OF ROAD FEATURES AND ATTRIBUTES SEGMENT


Access Control
Curve Type
Feature Type Code
Roadway Type
Roadway Sub Type
Route Qualifier
Speed Limit


-->

# **Road Features and Attributes**

## **Access Control**

<details>
    <summary>Click to Expand Access Control Table</summary>


| Code | Description                        | Division               |
|------|------------------------------------|------------------------|
| 1    | 1-Full Access Control              | Full Access Control    |
| 2    | 2-Partial Access Control           | Partial Access Control |
| 3    | 3-No Access Control                | No Access Control      |

</details>

---

## **Curve Type**

<details>
    <summary>Click to Expand Curve Type Table</summary>

| Code | Description        | Division  |
|------|--------------------|-----------|
| 100  | 100 - Straight    | Straight  |
| 101  | 101 - Curved      | Curved    |

</details>

---
## **Feature Type Code**


<details>
    <summary>Click to Expand Feature Type Code Table</summary>

| Code | Description                               | Division                          |
|------|-------------------------------------------|-----------------------------------|
| 0    | 0-Non-State Bridge/Approach              | Non-State Bridge/Approach        |
| 1    | 1-Primary Dir of LRS                     | Primary Dir of LRS               |
| 2    | 2-Secondary Dir of LRS                   | Secondary Dir of LRS             |
| 3    | 3-Frntg on Right of Primary Dir          | Frntg on Right of Primary Dir    |
| 4    | 4-Frntg on Right of Secndry Dir          | Frntg on Right of Secndry Dir    |
| 5    | 5-Opp Dir of Frntg Coded 3               | Opp Dir of Frntg Coded 3         |
| 6    | 6-Opp Dir of Frntg Coded 4               | Opp Dir of Frntg Coded 4         |
| 7    | 7-Removed from State System              | Removed from State System        |
| A    | A-On Ramp from Right                     | On Ramp from Right               |
| B    | B-On Ramp from Left                      | On Ramp from Left                |
| C    | C-Off Ramp to Right                      | Off Ramp to Right                |
| D    | D-Off Ramp to Left                       | Off Ramp to Left                 |
| E    | E-Ramp Off Ramp to Right                 | Ramp Off Ramp to Right           |
| F    | F-Ramp Off Ramp to Left                  | Ramp Off Ramp to Left            |
| G    | G-Ramp Onto Ramp from Right              | Ramp Onto Ramp from Right        |
| H    | H-Ramp Onto Ramp from Left               | Ramp Onto Ramp from Left         |
| R    | R-Roundabout                             | Roundabout                       |
| T    | T-Climbing Lanes                         | Climbing Lanes                   |
| U    | U-U-Turn Crossover                       | U-Turn Crossover                 |
| V    | V-HOV Separate from ThruLane             | HOV Separate from ThruLane       |
| W    | W-Turn Lane                              | Turn Lane                        |
| X    | X-Crossover of Divided Rdwy              | Crossover of Divided Rdwy        |
| Y    | Y-Bypass Lane                            | Bypass Lane                      |
| Z    | Z-Contra-Flow Crossover                  | Contra-Flow Crossover            |

</details>

---

## **Roadway Type**

<details>
    <summary>Click to Expand Roadway Type Table</summary>

| Code   | Description                              | with division                     |
| ------ | ---------------------------------------- | --------------------------------- |
| ACC    | Access Road - ACC                        | Access Road                       |
| ACRS   | Acres - ACRS                             | Acres                             |
| ALCV   | Alcove - ALCV                            | Alcove                            |
| ALT    | Alternate Route - ALT                    | Alternate Route                   |
| ALY    | Alley - ALY                              | Alley                             |
| ANX    | Annex - ANX                              | Annex                             |
| APPR   | Approach - APPR                          | Approach                          |
| ARC    | Arcade - ARC                             | Arcade                            |
| ARCH   | Arch - ARCH                              | Arch                              |
| AVCT   | Avenue Court - AVCT                      | Avenue Court                      |
| AVE    | Avenue - AVE                             | Avenue                            |
| AVN    | Avenida - AVN                            | Avenida                           |
| BAY    | Bay - BAY                                | Bay                               |
| BCH    | Beach - BCH                              | Beach                             |
| BG     | Burg - BG                                | Burg                              |
| BGS    | Burgs - BGS                              | Burgs                             |
| BIAR   | Bureau of Indian Affairs Route - BIAR    | Bureau of Indian Affairs Route    |
| BLF    | Bluff - BLF                              | Bluff                             |
| BLFS   | Bluffs - BLFS                            | Bluffs                            |
| BLVD   | Boulevard - BLVD                         | Boulevard                         |
| BND    | Bend - BND                               | Bend                              |
| BNK    | Bank - BNK                               | Bank                              |
| BR     | Branch -BR                               | Branch                            |
| BRG    | Bridge - BRG                             | Bridge                            |
| BRK    | Brook - BRK                              | Brook                             |
| BRKS   | Brooks - BRKS                            | Brooks                            |
| BRWK   | Boardwalk - BRWK                         | Boardwalk                         |
| BTM    | Bottom - BTM                             | Bottom                            |
| BUS    | Business Route - BUS                     | Business Route                    |
| BYP    | Bypass Route - BYP                       | Bypass Route                      |
| BYPS   | Bypass - BYPS                            | Bypass                            |
| BYU    | Bayou - BYU                              | Bayou                             |
| BYWY   | Bayway - BYWY                            | Bayway                            |
| CAL    | Calle - CAL                              | Calle                             |
| CAM    | Camino - CAM                             | Camino                            |
| CAR    | Carril - CAR                             | Carril                            |
| CHM    | Chemin - CHM                             | Chemin                            |
| CHS    | Chase - CHS                              | Chase                             |
| CIR    | Circle - CIR                             | Circle                            |
| CIRS   | Circles - CIRS                           | Circles                           |
| CLB    | Club - CLB                               | Club                              |
| CLF    | Cliff - CLF                              | Cliff                             |
| CLFS   | Cliffs - CLFS                            | Cliffs                            |
| CLR    | Cluster - CLR                            | Cluster                           |
| CLS    | Close - CLS                              | Close                             |
| CMN    | Common - CMN                             | Common                            |
| CMNS   | Commons - CMNS                           | Commons                           |
| CMP    | Camp - CMP                               | Camp                              |
| CNCR   | Concourse - CNCR                         | Concourse                         |
| CONN   | Connector - CONN                         | Connector                         |
| COR    | Corner - COR                             | Corner                            |
| CORS   | Corners - CORS                           | Corners                           |
| CPE    | Cape - CPE                               | Cape                              |
| CRC    | Circus - CRC                             | Circus                            |
| CRDR   | Corridor - CRDR                          | Corridor                          |
| CRES   | Crescent - CRES                          | Crescent                          |
| CRK    | Creek - CRK                              | Creek                             |
| CRS    | Cross - CRS                              | Cross                             |
| CRSE   | Course - CRSE                            | Course                            |
| CRST   | Crest - CRST                             | Crest                             |
| CRT    | Cartway - CRT                            | Cartway                           |
| CRTE   | Corte - CRTE                             | Corte                             |
| CRWY   | Crossway - CRWY                          | Crossway                          |
| CSWY   | Causeway - CSWY                          | Causeway                          |
| CT     | Court - CT                               | Court                             |
| CTNG   | Cutting - CTNG                           | Cutting                           |
| CTR    | Center - CTR                             | Center                            |
| CTRS   | Centers - CTRS                           | Centers                           |
| CTS    | Courts - CTS                             | Courts                            |
| CURV   | Curve - CURV                             | Curve                             |
| CUTOF  | Cutoff - CUTOF                           | Cutoff                            |
| CV     | Cove - CV                                | Cove                              |
| CVS    | Coves - CVS                              | Coves                             |
| CYN    | Canyon - CYN                             | Canyon                            |
| DEL    | Dell - DEL                               | Dell                              |
| DL     | Dale - DL                                | Dale                              |
| DM     | Dam - DM                                 | Dam                               |
| DR     | Drive - DR                               | Drive                             |
| DRFT   | Drift - DRFT                             | Drift                             |
| DRS    | Drives - DRS                             | Drives                            |
| DV     | Divide - DV                              | Divide                            |
| DVWY   | Driveway - DVWY                          | Driveway                          |
| DWN    | Down - DWN                               | Down                              |
| DWNS   | Downs - DWNS                             | Downs                             |
| END    | End - END                                | End                               |
| ESPL   | Esplanade - ESPL                         | Esplanade                         |
| EST    | Estate - EST                             | Estate                            |
| ESTS   | Estates - ESTS                           | Estates                           |
| EXCH   | Exchange - EXCH                          | Exchange                          |
| EXIT   | Exit - EXIT                              | Exit                              |
| EXPY   | Expressway - EXPY                        | Expressway                        |
| EXT    | Extension - EXT                          | Extension                         |
| EXTS   | Extensions - EXTS                        | Extensions                        |
| FALL   | Fall - FALL                              | Fall                              |
| FLD    | Field - FLD                              | Field                             |
| FLDS   | Fields - FLDS                            | Fields                            |
| FLS    | Falls - FLS                              | Falls                             |
| FLT    | Flat - FLT                               | Flat                              |
| FLTS   | Flats - FLTS                             | Flats                             |
| FLWY   | Flyway - FLWY                            | Flyway                            |
| FMRD   | Farm Road - FMRD                         | Farm Road                         |
| FR     | Fare - FR                                | Fare                              |
| FRD    | Ford - FRD                               | Ford                              |
| FRDS   | Fords - FRDS                             | Fords                             |
| FRG    | Forge - FRG                              | Forge                             |
| FRGS   | Forges - FRGS                            | Forges                            |
| FRK    | Fork - FRK                               | Fork                              |
| FRKS   | Forks - FRKS                             | Forks                             |
| FRM    | Farm - FRM                               | Farm                              |
| FRNT   | Front - FRNT                             | Front                             |
| FRNTRD | Frontage Road - FRNTRD                   | Frontage Road                     |
| FRST   | Forest - FRST                            | Forest                            |
| FRY    | Ferry - FRY                              | Ferry                             |
| FT     | Fort - FT                                | Fort                              |
| FTS    | Forts - FTS                              | Forts                             |
| FWY    | Freeway - FWY                            | Freeway                           |
| GDN    | Garden - GDN                             | Garden                            |
| GDNS   | Gardens - GDNS                           | Gardens                           |
| GLD    | Glade - GLD                              | Glade                             |
| GLN    | Glen - GLN                               | Glen                              |
| GLNS   | Glens - GLNS                             | Glens                             |
| GRDE   | Grade - GRDE                             | Grade                             |
| GRG    | Gorge - GRG                              | Gorge                             |
| GRN    | Green - GRN                              | Green                             |
| GRNS   | Greens - GRNS                            | Greens                            |
| GRTH   | Garth - GRTH                             | Garth                             |
| GRV    | Grove - GRV                              | Grove                             |
| GRVS   | Groves - GRVS                            | Groves                            |
| GT     | Gate - GT                                | Gate                              |
| GTS    | Gates - GTS                              | Gates                             |
| GTWY   | Gateway - GTWY                           | Gateway                           |
| HBR    | Harbor - HBR                             | Harbor                            |
| HBRS   | Harbors - HBRS                           | Harbors                           |
| HILS   | Hills - HLS                              | Hills                             |
| HL     | Hill - HL                                | Hill                              |
| HOLW   | Hollow - HOLW                            | Hollow                            |
| HRB    | Harbour - HRB                            | Harbour                           |
| HRS    | Horseshoe - HRS                          | Horseshoe                         |
| HTS    | Heights - HTS                            | Heights                           |
| HVN    | Haven - HVN                              | Haven                             |
| HWY    | Highway - HWY                            | Highway                           |
| INLT   | Inlet - INLT                             | Inlet                             |
| INT    | Interstate - INT                         | Interstate                        |
| INTV   | Interval - INTV                          | Interval                          |
| IS     | Island - IS                              | Island                            |
| ISLE   | Isle - ISLE                              | Isle                              |
| ISS    | Islands - ISS                            | Islands                           |
| JCT    | Junction - JCT                           | Junction                          |
| JCTS   | Junctions - JCTS                         | Junctions                         |
| KNL    | Knoll - KNL                              | Knoll                             |
| KNLS   | Knolls - KNLS                            | Knolls                            |
| KP     | Keep - KP                                | Keep                              |
| KY     | Key - KY                                 | Key                               |
| KYS    | Keys - KYS                               | Keys                              |
| LAND   | Land - LAND                              | Land                              |
| LCK    | Lock - LCK                               | Lock                              |
| LCKS   | Locks - LCKS                             | Locks                             |
| LDG    | Lodge - LDG                              | Lodge                             |
| LF     | Loaf - LF                                | Loaf                              |
| LG     | Ledge - LG                               | Ledge                             |
| LGT    | Light - LGT                              | Light                             |
| LGTS   | Lights - LGTS                            | Lights                            |
| LK     | Lake - LK                                | Lake                              |
| LKS    | Lakes - LKS                              | Lakes                             |
| LKT    | Lookout - LKT                            | Lookout                           |
| LN     | Lane - LN                                | Lane                              |
| LNDG   | Landing - LNDG                           | Landing                           |
| LOGRD  | Log Road - LOGRD                         | Log Road                          |
| LOOP   | Loop - LOOP                              | Loop                              |
| LR     | Lair - LR                                | Lair                              |
| LTR    | Lateral - LTR                            | Lateral                           |
| MALL   | Mall - MALL                              | Mall                              |
| MDW    | Meadow - MDW                             | Meadow                            |
| MDWS   | Meadows - MDWS                           | Meadows                           |
| MEWS   | Mews - MEWS                              | Mews                              |
| MHP    | Mobile Home Park - MHP                   | Mobile Home Park                  |
| ML     | Mill - ML                                | Mill                              |
| MLS    | Mills - MLS                              | Mills                             |
| MNR    | Manor - MNR                              | Manor                             |
| MNRS   | Manors - MNRS                            | Manors                            |
| MRKT   | Market - MRKT                            | Market                            |
| MSN    | Mission - MSN                            | Mission                           |
| MT     | Mount - MT                               | Mount                             |
| MTN    | Mountain - MTN                           | Mountain                          |
| MTNS   | Mountains - MTNS                         | Mountains                         |
| MTWY   | Motorway - MTWY                          | Motorway                          |
| NCK    | Neck - NCK                               | Neck                              |
| NK     | Nook - NK                                | Nook                              |
| NRW    | Narrows - NRW                            | Narrows                           |
| OKS    | Oaks - OKS                               | Oaks                              |
| OPAS   | Overpass - OPAS                          | Overpass                          |
| ORCH   | Orchard - ORCH                           | Orchard                           |
| OVAL   | Oval - OVAL                              | Oval                              |
| OVLK   | Overlook - OVLK                          | Overlook                          |
| PASS   | Pass - PASS                              | Pass                              |
| PATH   | Path - PATH                              | Path                              |
| PIKE   | Pike - PIKE                              | Pike                              |
| PINE   | Pine - PINE                              | Pine                              |
| PINES  | Pines - PINES                            | Pines                             |
| PKWY   | Parkway - PKWY                           | Parkway                           |
| PKWYS  | Parkways - PKWYS                         | Parkways                          |
| PL     | Place - PL                               | Place                             |
| PLN    | Plain - PLN                              | Plain                             |
| PLNS   | Plains - PLNS                            | Plains                            |
| PLZ    | Plaza - PLZ                              | Plaza                             |
| PNTE   | Pointe - PNTE                            | Pointe                            |
| PR     | Prairie - PR                             | Prairie                           |
| PRK    | Park - PRK                               | Park                              |
| PRKE   | Parke - PRKE                             | Parke                             |
| PRKS   | Parks - PRKS                             | Parks                             |
| PRMND  | Promenade - PRMND                        | Promenade                         |
| PRT    | Port - PRT                               | Port                              |
| PRTS   | Ports - PRTS                             | Ports                             |
| PSGE   | Passage - PSGE                           | Passage                           |
| PSO    | Paseo - PSO                              | Paseo                             |
| PT     | Point - PT                               | Point                             |
| PTS    | Points - PTS                             | Points                            |
| PTWY   | Pathway - PTWY                           | Pathway                           |
| PVT    | Private Road - PVT                       | Private Road                      |
| QTR    | Quarter - QTR                            | Quarter                           |
| QY     | Quay - QY                                | Quay                              |
| RADL   | Radial - RADL                            | Radial                            |
| RAMP   | Ramp - RAMP                              | Ramp                              |
| RCH    | Reach - RCH                              | Reach                             |
| RD     | Road - RD                                | Road                              |
| RDG    | Ridge - RDG                              | Ridge                             |
| RDGS   | Ridges - RDGS                            | Ridges                            |
| RDS    | Roads - RDS                              | Roads                             |
| RDWY   | Roadway - RDWY                           | Roadway                           |
| RIV    | River - RIV                              | River                             |
| RNCH   | Ranch - RNCH                             | Ranch                             |
| RND    | Round - RND                              | Round                             |
| RNWY   | Runway - RNWY                            | Runway                            |
| ROW    | Row - ROW                                | Row                               |
| RPD    | Rapid - RPD                              | Rapid                             |
| RPDS   | Rapids - RPDS                            | Rapids                            |
| RS     | Rise - RS                                | Rise                              |
| RST    | Rest - RST                               | Rest                              |
| RTE    | Route - RTE                              | Route                             |
| RTR    | Retreat - RTR                            | Retreat                           |
| RUE    | Rue - RUE                                | Rue                               |
| RUN    | Run - RUN                                | Run                               |
| RVRD   | River Road - RVRD                        | River Road                        |
| SHL    | Shoal - SHL                              | Shoal                             |
| SHLS   | Shoals - SHLS                            | Shoals                            |
| SHR    | Shore - SHR                              | Shore                             |
| SHRS   | Shores - SHRS                            | Shores                            |
| SKWY   | Skyway - SKWY                            | Skyway                            |
| SLP    | Slip - SLP                               | Slip                              |
| SMT    | Summit - SMT                             | Summit                            |
| SPDWY  | Speedway - SPDWY                         | Speedway                          |
| SPG    | Spring - SPG                             | Spring                            |
| SPGS   | Springs - SPGS                           | Springs                           |
| SPR    | Spur - SPR                               | Spur                              |
| SPRS   | Spurs - SPRS                             | Spurs                             |
| SPUR   | Spur Route - SPUR                        | Spur Route                        |
| SQ     | Square - SQ                              | Square                            |
| SQS    | Squares - SQS                            | Squares                           |
| SRVRD  | Service Road - SRVRD                     | Service Road                      |
| ST     | Street - ST                              | Street                            |
| STA    | Station - STA                            | Station                           |
| STCR   | Street Circle - STCR                     | Street Circle                     |
| STCT   | Street Court - STCT                      | Street Court                      |
| STHY   | State Highway - STHY                     | State Highway                     |
| STLP   | Street Loop - STLP                       | Street Loop                       |
| STPK   | State Parkway - STPK                     | State Parkway                     |
| STPL   | Street Place - STPL                      | Street Place                      |
| STRA   | Stravenue - STRA                         | Stravenue                         |
| STRD   | State Road - STRD                        | State Road                        |
| STRM   | Stream - STRM                            | Stream                            |
| STRND  | Strand - STRND                           | Strand                            |
| STRP   | Strip - STRP                             | Strip                             |
| STRS   | Strasse - STRS                           | Strasse                           |
| STRT   | State Route - STRT                       | State Route                       |
| STS    | Streets - STS                            | Streets                           |
| STSC   | State Secondary - STSC                   | State Secondary                   |
| TER    | Terrace - TER                            | Terrace                           |
| TERN   | Tern - TERN                              | Tern                              |
| THWY   | Throughway - THWY                        | Throughway                        |
| TPKE   | Turnpike - TPKE                          | Turnpike                          |
| TRAK   | Track - TRAK                             | Track                             |
| TRCE   | Trace - TRCE                             | Trace                             |
| TRFWY  | Trafficway - TRFWY                       | Trafficway                        |
| TRKWY  | Truckway - TRKWY                         | Truckway                          |
| TRL    | Trail - TRL                              | Trail                             |
| TRLR   | Trailer - TRLR                           | Trailer                           |
| TRN    | Turn - TRN                               | Turn                              |
| TRNG   | Triangle - TRNG                          | Triangle                          |
| TRWY   | Thruway - TRWY                           | Thruway                           |
| TUNL   | Tunnel - TUNL                            | Tunnel                            |
| TURN   | Turnaround - TURN                        | Turnaround                        |
| TWNRD  | Township Road - TWNRD                    | Township Road                     |
| TXWY   | Taxiway - TXWY                           | Taxiway                           |
| UN     | Union - UN                               | Union                             |
| UNS    | Unions - UNS                             | Unions                            |
| UPAS   | Underpass - UPAS                         | Underpass                         |
| US     | United States Highway - US               | United States Highway             |
| USFR   | United States Forest Service Road - USFR | United States Forest Service Road |
| VI     | Via - VI                                 | Via                               |
| VIA    | Viaduct - VIA                            | Viaduct                           |
| VILA   | Villa - VILA                             | Villa                             |
| VIS    | Vista - VIS                              | Vista                             |
| VL     | Ville - VL                               | Ville                             |
| VLG    | Village - VLG                            | Village                           |
| VLGS   | Villages - VLGS                          | Villages                          |
| VLY    | Valley - VLY                             | Valley                            |
| VLYS   | Valleys - VLYS                           | Valleys                           |
| VOI    | Voie - VOI                               | Voie                              |
| VW     | View - VW                                | View                              |
| VWS    | Views - VWS                              | Views                             |
| WALL   | Wall - WALL                              | Wall                              |
| WDS    | Woods - WDS                              | Woods                             |
| WEEG   | Weeg - WEEG                              | Weeg                              |
| WHRF   | Wharf - WHRF                             | Wharf                             |
| WL     | Well - WL                                | Well                              |
| WLK    | Walk - WLK                               | Walk                              |
| WLKS   | Walks - WLKS                             | Walks                             |
| WLS    | Wells - WLS                              | Wells                             |
| WND    | Wynd - WND                               | Wynd                              |
| WY     | Way - WY                                 | Way                               |
| WYE    | Wye - WYE                                | Wye                               |
| WYS    | Ways - WYS                               | Ways                              |
| XING   | Crossing - XING                          | Crossing                          |
| XOVR   | Crossover - XOVR                         | Crossover                         |
| XRD    | Crossroad - XRD                          | Crossroad                         |
| XRDS   | Crossroads - XRDS                        | Crossroads                        |

</details>

---

## **Roadway Sub Type**

<details>
    <summary>Click to Expand Roadway Sub Type Table</summary>

| Code | Description                | Division             |
|------|----------------------------|----------------------|
| 100  | 100 - Mainline             | Mainline            |
| 200  | 200 - On-Ramp              | On-Ramp             |
| 201  | 201 - Off-Ramp             | Off-Ramp            |
| 300  | 300 - Frontage / Service   | Frontage / Service  |
| 970  | 970 - Not Applicable       | Not Applicable      |

</details>

---

## **Route Qualifier**

<details>
    <summary>Click to Expand Route Qualifier Table</summary>

| Code | Description                          | Division                     |
|------|--------------------------------------|------------------------------|
| 1    | 1-No Qualifier or Not Signed        | No Qualifier or Not Signed  |
| 2    | 2-Alternate Route                   | Alternate Route             |
| 3    | 3-Business Route                    | Business Route              |
| 4    | 4-Bypass Business Route             | Bypass Business Route       |
| 5    | 5-Spur Route                        | Spur Route                  |
| 6    | 6-Loop                              | Loop                        |
| 7    | 7-Proposed Route                    | Proposed Route              |
| 8    | 8-Temporary Route                   | Temporary Route             |
| 9    | 9-Truck Route                       | Truck Route                 |
| 10   | 10-None of the Above                | None of the Above           |

</details>

---

## **Speed Limit**

<details>
    <summary>Click to Expand Speed Limit Table</summary>

| Code | Description  |
|------|------------|
| 5    | 5 mph     |
| 10   | 10 mph    |
| 15   | 15 mph    |
| 20   | 20 mph    |
| 25   | 25 mph    |
| 30   | 30 mph    |
| 35   | 35 mph    |
| 40   | 40 mph    |
| 45   | 45 mph    |
| 50   | 50 mph    |
| 55   | 55 mph    |
| 60   | 60 mph    |
| 65   | 65 mph    |
| 70   | 70 mph    |
| 75   | 75 mph    |
| 80   | 80 mph    |
| 85   | 85 mph    |
| 90   | 90 mph    |
| 95   | 95 mph    |
| 100  | 100 mph   |
| 105  | 105 mph   |
| 110  | 110 mph   |

</details>

---

<!-- BEGINNING OF TRAFFIC MANAGEMENT SEGMENT 


	Inventory Direction
	Managed Lanes Type
	NHS
	Number
	Road Direction
	Road Use
	Traffic Flow Direction
	Traffic Way Division


-->

# Traffic Management

## **Inventory Direction**

<details>
    <summary>Click to Expand Inventory Direction Table</summary>



| Code | Description                                     | Division                                      |
|------|-----------------------------------------------|----------------------------------------------|
| 1    | 1 - Primary / inventory direction of travel  | Primary / inventory direction of travel     |
| 2    | 2 - Secondary / non-inventory direction of travel | Secondary / non-inventory direction of travel |

</details>

---
## **Managed Lanes Type**


<details>
    <summary>Click to Expand Managed Lanes Type Table</summary>

| Code | Description                                | Division                           |
|------|--------------------------------------------|-----------------------------------|
| 1    | 1-Full-time HOV (Lane Used)               | Full-time HOV (Lane Used)        |
| 2    | 2-Part-time HOV (Lane Used)               | Part-time HOV (Lane Used)        |
| 3    | 3-Part-time HOV (Shoulder Used)           | Part-time HOV (Shoulder Used)    |

</details>

---

## **NHS**

<details>
    <summary>Click to Expand NHS Table</summary>



| Code | Description                                                                        | Division                                                   |
|------|------------------------------------------------------------------------------------|------------------------------------------------------------|
| 0    | 0-Not Designated as NHS Route                                                     | Not Designated as NHS Route                                |
| 1    | 1-Designated NHS Route                                                            | Designated NHS Route                                       |
| 2    | 2-Major Airport (Intermodal Connector)                                            | Major Airport (Intermodal Connector)                      |
| 3    | 3-Major Port Facility (Intermodal Connector)                                      | Major Port Facility (Intermodal Connector)                |
| 4    | 4-Major Amtrak Station (Intermodal Connector)                                     | Major Amtrak Station (Intermodal Connector)               |
| 5    | 5-Major Rail/Truck Terminal (Intermodal Connector)                               | Major Rail/Truck Terminal (Intermodal Connector)          |
| 6    | 6-Major Inter City Bus Terminal (Intermodal Connector)                           | Major Inter City Bus Terminal (Intermodal Connector)      |
| 7    | 7-Major Public Transportation or Multi-Modal Passenger Terminal (Intermodal Connector) | Major Public Transportation or Multi-Modal Passenger Terminal (Intermodal Connector) |
| 8    | 8-Major Pipeline Terminal (Intermodal Connector)                                 | Major Pipeline Terminal (Intermodal Connector)            |
| 9    | 9-Major Ferry Terminal (Intermodal Connector)                                   | Major Ferry Terminal (Intermodal Connector)               |

</details>

---

## **Number**
**Use:**\
Defines the range of values possible for numeric attributes

<details>
    <summary>Click to Expand Number Table</summary>

| Mininum | Maximum |
|---------|---------|
| 0       | 300		|

</details>

---

## **Road Classification**


<details>
    <summary>Click to Expand Road Classification Table</summary>

| Code | Description                          | Division                     |
|------|--------------------------------------|------------------------------|
| 100  | 100 - Interstate                    | Interstate                   |
| 101  | 101 - US Highway                     | US Highway                   |
| 102  | 102 - State Highway                  | State Highway                |
| 103  | 103 - Parish Road                    | Parish Road                  |
| 104  | 104 - City Street                    | City Street                  |
| 200  | 200 - Off Road / Private Road        | Off Road / Private Road      |

</details>

---

## **Road Direction**

<details>
    <summary>Click to Expand Road Direction Table</summary>


| Code | Description              | Division   |
|------|--------------------------|------------|
| E    | E - East                 | East       |
| N    | N - North                | North      |
| NE   | NE - Northeast           | Northeast  |
| NW   | NW - Northwest           | Northwest  |
| S    | S - South                | South      |
| SE   | SE - Southeast           | Southeast  |
| SW   | SW - Southwest           | Southwest  |
| W    | W - West                 | West       |

</details>

---
## **Road Use**

<details>
    <summary>Click to Expand Road Use Table</summary>

| Code | Description                                                   | Division                                       |
|------|---------------------------------------------------------------|-----------------------------------------------|
| 1    | 1-One-Way Roadway                                            | One-Way Roadway                              |
| 2    | 2-Two-Way Roadway                                            | Two-Way Roadway                              |
| 3a   | 3a-One-Way Couplet – Primary Direction                       | One-Way Couplet – Primary Direction          |
| 3b   | 3b-One-Way Couplet – Secondary Direction                     | One-Way Couplet – Secondary Direction        |
| 4a   | 4a-Divided Roadway – Primary Direction                       | Divided Roadway – Primary Direction          |
| 4b   | 4b-Divided Roadway – Secondary Direction                     | Divided Roadway – Secondary Direction        |
| 5    | 5-Undivided with Continuous Turn-Lane                        | Undivided with Continuous Turn-Lane          |
| 6a   | 6a-Frontage Roadway – One-Way in Primary Direction           | Frontage Roadway – One-Way in Primary Direction |
| 6b   | 6b-Frontage Roadway – One-Way in Secondary Direction         | Frontage Roadway – One-Way in Secondary Direction |
| 6c   | 6c-Frontage Roadway – Two-Way                                | Frontage Roadway – Two-Way                   |
| 6e   | 6e-Frontage Roadway – Divided in Primary Direction           | Frontage Roadway – Divided in Primary Direction |
| 6f   | 6f-Frontage Roadway – Divided in Secondary Direction         | Frontage Roadway – Divided in Secondary Direction |
| 7    | 7-Non-Mainline Ramps in GRADE SEPARATED Interchanges         | Non-Mainline Ramps in GRADE SEPARATED Interchanges |
| 8    | 8-Non-Mainline Ramps in AT-GRADE Interchanges                | Non-Mainline Ramps in AT-GRADE Interchanges  |
| 9    | 9-Connectors – Crossover or Wide Flange Intersection         | Connectors – Crossover or Wide Flange Intersection |
| 10   | 10-ACTIVE Proposed Road                                      | ACTIVE Proposed Road                         |
| 11   | 11-INACTIVE Proposed Road                                    | INACTIVE Proposed Road                       |
| 15   | 15-Roundabout                                               | Roundabout                                   |
| 20   | 20-State Facility / DOTD Facility                           | State Facility / DOTD Facility               |
| 21   | 21-Ferry                                                   | Ferry                                        |
| 22   | 22-Welcome Center                                          | Welcome Center                               |
| 23   | 23-Rest Area                                               | Rest Area                                    |
| 24   | 24-Weigh Station                                           | Weigh Station                                |
| 25   | 25-State Park                                              | State Park                                   |
| 26   | 26-State Historic Site                                     | State Historic Site                          |
| 27   | 27-Port Facility                                           | Port Facility                                |
| 28   | 28-Rail Facility                                           | Rail Facility                                |
| 29   | 29-Airport Facility                                        | Airport Facility                             |
| 30   | 30-Dam                                                    | Dam                                         |
| 31   | 31-Levee                                                  | Levee                                       |
| 32   | 32-Boat Launch                                            | Boat Launch                                 |

</details>

---

## **Traffic Flow Direction**

<details>
    <summary>Click to Expand Traffic Flow Direction Table</summary>

| Code | Description     | Division  |
|------|---------------|-----------|
| 100  | 100 - One-Way  | One-Way   |
| 200  | 200 - Two-Way  | Two-Way   |

</details>

---

## **Traffic Way Division**

<details>
    <summary>Click to Expand Traffic Way Division Table</summary>

| Code | Description                                              | Division                                      |
|------|----------------------------------------------------------|-----------------------------------------------|
| 0    | 000 - Not Divided                                        | Not Divided                                  |
| 1    | 001 - Not Divided with a Continuous Left-Turn Lane      | Not Divided with a Continuous Left-Turn Lane |
| 100  | 100 - Divided Flush Median (greater than 4 feet)        | Divided Flush Median (greater than 4 feet)   |
| 101  | 101 - Divided Raised Median (curbed)                    | Divided Raised Median (curbed)               |
| 102  | 102 - Divided Depressed Median                          | Divided Depressed Median                     |
| 999  | 999 - Unknown                                           | Unknown                                      |

</details>

---

<!-- BEGINNING OF SYSTEM IDENTIFIERS SEGMENT 


	System Code
	Field Mapping


-->

# **System Identifiers**

## **System Code**

<details>
    <summary>Click to Expand System Code Table</summary>

| Code  | Description                            | Division                  |
|-------|----------------------------------------|---------------------------|
| 001_  | 001-Acadia Parish                     | Acadia Parish            |
| 003_  | 003-Allen Parish                      | Allen Parish             |
| 005_  | 005-Ascension Parish                  | Ascension Parish         |
| 007_  | 007-Assumption Parish                 | Assumption Parish        |
| 009_  | 009-Avoyelles Parish                  | Avoyelles Parish         |
| 011_  | 011-Beauregard Parish                 | Beauregard Parish        |
| 013_  | 013-Bienville Parish                  | Bienville Parish         |
| 015_  | 015-Bossier Parish                    | Bossier Parish           |
| 017_  | 017-Caddo Parish                      | Caddo Parish             |
| 019_  | 019-Calcasieu Parish                  | Calcasieu Parish         |
| 021_  | 021-Caldwell Parish                   | Caldwell Parish          |
| 023_  | 023-Cameron Parish                    | Cameron Parish           |
| 025_  | 025-Catahoula Parish                  | Catahoula Parish         |
| 027_  | 027-Claiborne Parish                  | Claiborne Parish         |
| 029_  | 029-Concordia Parish                  | Concordia Parish         |
| 031_  | 031-De Soto Parish                    | De Soto Parish           |
| 033_  | 033-East Baton Rouge Parish           | East Baton Rouge Parish  |
| 035_  | 035-East Carroll Parish               | East Carroll Parish      |
| 037_  | 037-East Feliciana Parish             | East Feliciana Parish    |
| 039_  | 039-Evangeline Parish                 | Evangeline Parish        |
| 041_  | 041-Franklin Parish                   | Franklin Parish          |
| 043_  | 043-Grant Parish                      | Grant Parish             |
| 045_  | 045-Iberia Parish                     | Iberia Parish            |
| 047_  | 047-Iberville Parish                  | Iberville Parish         |
| 049_  | 049-Jackson Parish                    | Jackson Parish           |
| 051_  | 051-Jefferson Parish                  | Jefferson Parish         |
| 053_  | 053-Jefferson Davis Parish            | Jefferson Davis Parish   |
| 055_  | 055-Lafayette Parish                  | Lafayette Parish         |
| 057_  | 057-Lafourche Parish                  | Lafourche Parish         |
| 059_  | 059-La Salle Parish                   | La Salle Parish          |
| 061_  | 061-Lincoln Parish                    | Lincoln Parish           |
| 063_  | 063-Livingston Parish                 | Livingston Parish        |
| 065_  | 065-Madison Parish                    | Madison Parish           |
| 067_  | 067-Morehouse Parish                  | Morehouse Parish        |
| 069_  | 069-Natchitoches Parish               | Natchitoches Parish      |
| 071_  | 071-Orleans Parish                    | Orleans Parish           |
| 073_  | 073-Ouachita Parish                   | Ouachita Parish         |
| 075_  | 075-Plaquemines Parish                | Plaquemines Parish      |
| 077_  | 077-Pointe Coupee Parish              | Pointe Coupee Parish    |
| 079_  | 079-Rapides Parish                    | Rapides Parish          |
| 081_  | 081-Red River Parish                  | Red River Parish        |
| 083_  | 083-Richland Parish                   | Richland Parish        |
| 085_  | 085-Sabine Parish                     | Sabine Parish          |
| 087_  | 087-St. Bernard Parish                | St. Bernard Parish     |
| 089_  | 089-St. Charles Parish                | St. Charles Parish     |
| 091_  | 091-St. Helena Parish                 | St. Helena Parish      |
| 093_  | 093-St. James Parish                  | St. James Parish       |
| 095_  | 095-St. John the Baptist Parish       | St. John the Baptist Parish |
| 097_  | 097-St. Landry Parish                 | St. Landry Parish      |
| 099_  | 099-St. Martin Parish                 | St. Martin Parish      |
| 101_  | 101-St. Mary Parish                   | St. Mary Parish        |
| 103_  | 103-St. Tammany Parish                | St. Tammany Parish     |
| 105_  | 105-Tangipahoa Parish                 | Tangipahoa Parish      |
| 107_  | 107-Tensas Parish                     | Tensas Parish          |
| 109_  | 109-Terrebonne Parish                 | Terrebonne Parish      |
| 111_  | 111-Union Parish                      | Union Parish           |
| 113_  | 113-Vermilion Parish                  | Vermilion Parish       |
| 115_  | 115-Vernon Parish                     | Vernon Parish          |
| 117_  | 117-Washington Parish                 | Washington Parish      |
| 119_  | 119-Webster Parish                    | Webster Parish         |
| 121_  | 121-West Baton Rouge Parish           | West Baton Rouge Parish |
| 123_  | 123-West Carroll Parish               | West Carroll Parish   |
| 125_  | 125-West Feliciana Parish             | West Feliciana Parish  |
| 127_  | 127-Winn Parish                       | Winn Parish            |
| 888_  | 888-All Facilities                    | All Facilities         |
| 999_  | 999-State Highway System              | State Highway System   |

</details>

---

## **Field Mapping**

<details>
    <summary>Click to Expand Fields Mapping Table</summary>	

| Field Name                         | Data Type | Domain               | Precision | Scale | Length | Data Source Layer        | Data Source Field                  | Allow Nulls | Default Value |
|-------------------------------------|----------|----------------------|-----------|-------|--------|--------------------------|-------------------------------------|-------------|--------------|
| OBJECTID                            |          |                      |           |       |        |                          |                                     |             |              |
| FromDate                            | Date     |                      |           |       |        | LoadDate                 |                                     | Yes         |              |
| ToDate                              | Date     |                      |           |       |        | Generated on Data Load   |                                     | Yes         | Null         |
| EventID                             | String   |                      |           |       | 38     | Determined via DynSeg    |                                     | No          |              |
| RouteID                             | String   |                      |           |       | 60     | Determined via DynSeg    |                                     | No          |              |
| FromMeasure                         | Double   |                      |           |       |        | Determined via DynSeg    |                                     | Yes         |              |
| ToMeasure                           | Double   |                      |           |       |        |                          |                                     | Yes         | Null         |
| RoadUse                             | String   | RoadUse              |           |       | 3      | RoadUse                  | RoadUse                             | Yes         | Null         |
| TrafficWayDivision                  | String   | TrafficWayDivision   |           |       | 3      | Medians, RoadUse         | MedianWidthFeet, MedianType, Divided | Yes         | Null         |
| TrafficwayTravelDirection           | String   | TrafficWayDirection  |           |       | 3      | RoadUse                  | RoadUse                             |             |              |
| TrafficDirection                    | String   | InventoryDirection   |           |       | 2      | StatewideRoutes          | InventoryDirection                  | Yes         | Null         |
| LocationID                          | String   |                      |           |       | 32     | HighwayClass             | LocationID                          | No          | Null         |
| Parish                              | String   |                      |           |       | 21     | BNDY_ParishBoundaries    | ParishName                          | Yes         | Null         |
| ParishCode                          | String   | ParishCode           |           |       | 2      | BNDY_ParishBoundaries    | ParishNumber                        | Yes         | Null         |
| ParishFIPS                          | String   |                      |           |       | 3      | BNDY_ParishBoundaries    | ParishFIPS                          | Yes         | Null         |
| City                                | String   |                      |           |       | 100    | Derived from City Code Sheet - Lookup Table, BNDY_IncorporatedAreas |  | Yes         | Null         |
| CityFIPS                            | String   |                      |           |       | 5      | BNDY_IncorporatedAreas   | PlaceFIPS                           | Yes         | Null         |
| CityParish                          | String   | CityParish           |           |       | 4      | City Code Sheet - Lookup Table | Combine CityCode and ParishCode    | Yes         | Null         |
| DOTDDistrict                        | String   |                      |           |       | 2      | BNDY_DOTD_Districts      | DOTD_DistrictNumber                 | Yes         | Null         |
| Troop                               | String   |                      |           |       | 1      | TBD                      |                                     | Yes         | Null         |
| ControlSection                      | String   |                      |           |       | 6      | LRSID_Event              | ControlSection                      | Yes         | Null         |
| LRSID                               | String   |                      |           |       | 18     | LRSID_Event              |                                     | Yes         | Null         |
| BeginLogMile                        | Double   |                      |           |       |        | LRSID_Route              |                                     | Yes         | Null         |
| EndLogMile                          | Double   |                      |           |       |        | LRSID_Route              |                                     | Yes         | Null         |
| HighwayClass                        | String   | HighwayClass         |           |       | 2      | HighwayClass (new event) | HighwayClass                         | Yes         | Null         |
| FunctionalClass                     | String   | FSystem              |           |       | 1      | FunctionalSystem         | FunctionalSystem                     | Yes         | Null         |
| ReverseControl                      | String   | YesNo                |           |       | 1      | LRSID_Event              |                                     | Yes         |              |

</details>

---

# **4. References and External Links**

- [DOTD Traffic Count App](https://ladotd.public.ms2soft.com/tcds/tsearch.asp?loc=ladotd)
- [DOTD Traffic Viewer App](https://ladotd.public.ms2soft.com/TDMS.UI_Core/trafficviewer)

---
