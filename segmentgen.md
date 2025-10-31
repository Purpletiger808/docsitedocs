---
mdx.format: md
---

# Segment Generation

## Overview

The purpose of this story is to document the benchmark process for generating the traffic safety segment layer. This layer will be provided to the Highway Safety Section team for analysing crash statistics and Louisiana State University (LSU) Center for Analytics & Research in Transportation Safety (CARTS) for input into the eCrash automated crash reporting system for use in Louisiana State Police vehicles. The process outlined in this document is intended to be repeatable and contain the requirements for categorizing roadways based on requirements and attributes set by the LSU CARTs group. While final datasets will be hosted in an offline geodatabase for analysis and distribution, it is anticipated that the Highway Class Segments layer will also be included in the DOTD Roads and Highways (LARH) database as an internal event.

Note: Two additional requirements for the Highway Class Segments are that generation of the layer must be automated and that Segment IDs must be static, meaning that when route or event edits in R&H necessitate a change in the extent of a segment, previous segment extents will be mapped to their current route locations and IDs so that crash analysis can be traced back to the same section of roadway over time. These two requirements are not addressed in this document.

## Schema

### Table 1: Highway Class Schema properties
For updates, please see file:///\\dotd-statewide.swe.la.gov\FS_GIS_RnH\GeodatabaseMaintenance\SchemaChanges\HighwayClassSegment_SchemaChange_20230825.xlsx.

| Field name                  | Type     | Allow NULL Values | Default Value | Domain              | Length |
|----------------------------|----------|-------------------|----------------|----------------------|--------|
| FromDate                   | Date     | Yes               |                |                      |        |
| ToDate                     | Date     | Yes               |                |                      |        |
| LoadDate                   | Date     | Yes               |                |                      |        |
| EventID                    | String   | Yes               |                |                      | 38     |
| RouteID                    | String   | Yes               |                |                      | 255    |
| FromMeasure                | Double   | Yes               |                |                      |        |
| ToMeasure                  | Double   | Yes               |                |                      |        |
| RoadUse                    | String   | Yes               |                | RoadUse              | 3      |
| TrafficWayDivision         | String   | Yes               |                | TrafficWayDivision   | 3      |
| TrafficwayTravelDirection  | String   | Yes               |                | TrafficwayDirection  | 3      |
| TrafficDirection           | String   | Yes               |                | InventoryDirection   | 3      |
| LocationID                 | String   | Yes               |                |                      | 32     |
| Parish                     | String   | Yes               |                |                      | 50     |
| ParishCode                 | String   | Yes               |                | ParishCode           | 3      |
| ParishFIPS                 | String   | Yes               |                |                      | 100    |
| City                       | String   | Yes               |                |                      | 50     |
| CityFIPS                   | String   | Yes               |                |                      | 5      |
| CityParish                 | String   | Yes               |                | CityParish           | 4      |
| DOTDDistrict               | String   | Yes               |                | DOTDDistrict         | 2      |
| Troop                      | String   | Yes               |                |                      | 2      |
| ControlSection             | String   | Yes               |                |                      | 6      |
| LRSID                      | String   | Yes               |                |                      | 18     |
| BeginLogMile               | Double   | Yes               |                |                      |        |
| EndLogMile                 | Double   | Yes               |                |                      |        |
| RoadClassification         | String   | Yes               |                | RoadClassification   | 1      |
| RoadwaySubType             | String   | Yes               |                | RoadwaySubType       | 3      |
| RouteNameFull              | String   | Yes               |                |                      | 254    |
| RoadNameDir                | String   | Yes               |                | RoadDirection        | 2      |
| RoadName                   | String   | Yes               |                |                      | 60     |
| RoadType                   | String   | Yes               |                | RoadType             | 4      |
| StateName                  | String   | Yes               |                |                      | 2      |
| HighwayNum                 | String   | Yes               |                |                      | 10     |
| StateNameType              | String   | Yes               |                | RouteQualifier       | 3      |
| SecondaryName              | String   | Yes               |                |                      | 254    |
| SecondaryNameDir           | String   | Yes               |                | RoadDirection        | 2      |
| SecondaryRoadName          | String   | Yes               |                |                      | 60     |
| SecondaryNameType          | String   | Yes               |                | RoadType             | 4      |
| UrbanRural                 | String   | Yes               |                | UrbanRural           | 1      |
| SegmentLength              | Double   | Yes               |                |                      |        |
| SpeedLimit                 | String   | Yes               |                |                      | 3      |
| Curve                      | String   | Yes               |                | CurveType            | 3      |
| NHS                        | String   | Yes               |                | NHS                  | 1      |
| AADT_Year                  | Long     | Yes               |                |                      |        |
| AADT                       | Long     | Yes               |                |                      |        |
| AADT_Truck                 | Long     | Yes               |                |                      |        |
| AADT_Motorcycle            | Long     | Yes               |                |                      |        |
| LaneWidth                  | Short    | Yes               |                | Number               |        |
| NumberofLanes              | Short    | Yes               |                |                      |        |
| HOVLanes                   | Short    | Yes               |                | Number               |        |
| HOVLanesType               | String   | Yes               |                | ManagedLaneType      | 1      |
| LeftShoulderWidth          | Short    | Yes               |                | Number               |        |
| RightShoulderWidth         | Short    | Yes               |                | Number               |        |
| AccessControl              | String   | Yes               |                | AccessControl        | 1      |
| HighwayClass               | String   | Yes               |                | HighwayClass         | 1      |
| FunctionalClass            | String   | Yes               |                | FSystem              | 1      |
| StructureIdentificationNumber | String | Yes             |                |                      | 15     |
| Station_ID                 | String   | Yes               |                |                      | 10     |
| RouteIDCenterLine          | String   | Yes               |                |                      | 255    |
| FromMeasureCenterLine      | Double   | Yes               |                |                      |        |
| ToMeasureCenterLine        | Double   | Yes               |                |                      |        |
| LRSIDCenterLine            | String   | Yes               |                |                      | 18     |
| BeginLogMileCenterLine     | Double   | Yes               |                |                      |        |
| EndLogMileCenterLine       | Double   | Yes               |                |                      |        |
| LocationID_Legacy_1        | String   | Yes               |                |                      | 32     |
| LocationID_Legacy_2        | String   | Yes               |                |                      | 32     |
| LocationID_Legacy_3        | String   | Yes               |                |                      | 32     |
| LocationID_Legacy_4        | String   | Yes               |                |                      | 32     |
| LocationID_Legacy_5        | String   | Yes               |                |                      | 32     |


### Table 2: Highway Class field definitions and calculation methods. 
Updates are retained at file:///\\dotd-statewide.swe.la.gov\FS_GIS_RnH\GeodatabaseMaintenance\SchemaChanges\HighwayClassSegment_SchemaChange_20230825.xlsx.

| **Field Name**                  | **Field Description**                                                               | **Primary/ Secondary/ Dominant Route** | **Source Data**                                                                 |
|--------------------------------|-------------------------------------------------------------------------------------|----------------------------------------|----------------------------------------------------------------------------------|
| FromDate                       | Effective date of the HighwayClass event                                            | Maintained separately                  |      Load Date                                                                            |
| ToDate                         | Retire date of HighwayClass event                                                   | Maintained separately                  |                     Generated on Data Load                                                             |
| EventID                        | Join identifier for HighwayClass event                                              | Dominant Route                         | Determined via DynSeg                                                           |
| RouteID                        | The Statewide Routes record upon which the HighwayClass event is located           | Maintained separately                  | Determined via DynSeg                                                           |
| FromMeasure                    | Starting location in miles from beginning of the route                             | Maintained separately                  | Determined via DynSeg                                                           |
| ToMeasure                      | Ending location in miles from the end of the route                                 | Maintained separately                  | Determined via DynSeg                                                           |
| RoadUse                        | Primary function of the roadway                                                     | Dominant Route                         | RoadUse [RoadUse]                                                               |
| TrafficWayDivision            | Indicates whether road is divided and type of median                                | Dominant Route                         | Medians, RoadUse [MedianWidthFeet, MedianType, Divided]                         |
| TrafficwayTravelDirection     | Direction of travel                                                                 | Dominant Route                         | RoadUse [RoadUse]                                                               |
| TrafficDirection              | Indicates if on the primary or secondary inventory direction                        | Dominant Route                         | StatewideRoutes [InventoryDirection]                                            |
| LocationID                    | Unique segment ID tied to traffic segments                                          | Maintained Separately                  | TrafficSegment [Station_ID, if <NULL> TMP OBJECTID]                             |
| Parish                        | Parish Name                                                                         | Maintained Separately                  | BNDY_ParishBoundaries [ParishName]                                              |
| ParishCode                    | DOTD Parish Code                                                                    | Maintained Separately                  | BNDY_ParishBoundaries [ParishNumber]                                            |
| ParishFIPS                    | Parish US FIPS Code                                                                 | Maintained Separately                  | BNDY_ParishBoundaries [ParishFIPS] (Unmatched parishes from RouteID prefix.)    |
| City                          | Municipality Name                                                                   | Maintained Separately                  | Derived from City Code Sheet, BNDY_IncorporatedAreas                            |
| CityFIPS                      | Municipality US FIPS Code                                                           | Maintained Separately                  | BNDY_IncorporatedAreas [PlaceFIPS]                                              |
| CityParish                    | Combined City and Parish Codes                                                      | Maintained Separately                  | City Code Sheet [Combine CityCode and ParishCode]                               |
| DOTDDistrict                  | DOTD Maintenance District                                                           | Maintained Separately                  | BNDY_DOTD_Districts [DOTD_DistrictNumber]                                       |
| Troop                         | LA State Police Troop ID                                                            | Maintained Separately                  | BNDY_LSP_StatePoliceTroops [PoliceTroopID]                                      |
| ControlSection                | DOTD Control Section ID                                                             | Dominant Route                         | LRSID_Event [ControlSection]                                                    |
| LRSID                         | DOTD LRSID_Routes Route ID                                                          | Dominant Route                         | LRSID_Event                                                                     |
| BeginLogMile                  | LRSID_Routes starting mileage                                                       | Maintained Separately                  | LRSID_Route                                                                     |
| EndLogMile                    | LRSID_Routes ending mileage                                                         | Maintained Separately                  | LRSID_Route                                                                     |
| RoadClassification           | Type of mainline roadway                                                             | Dominant Route                         | GP_RouteIdentification, FunctionalSystem, PublicPrivate                         |
| RoadwaySubType               | Type of secondary roadway if not mainline                                           | Dominant Route                         |                                                                                  |
| RouteNameFull                | Concatenated Street Name/Highway Number                                             | Dominant Route                         | LouisianaRoadway [FullName]                                                     |
| RoadNameDir                  | Street Name Prefix Direction                                                        | Dominant Route                         | LouisianaRoadway [St_PreDir]                                                    |
| RoadName                     | Street Name                                                                          | Dominant Route                         | LouisianaRoadway [St_Name]                                                      |
| RoadType                     | Street Name Post Type                                                                | Dominant Route                         | LouisianaRoadway [St_PosTyp]                                                    |
| StateName                    | State Name                                                                           | Dominant Route                         | LouisianaRoadway [State_L]                                                      |
| HighwayNum                   | Highway Shield Number                                                                | Dominant Route                         | GP_RouteIdentification [RouteNumber]                                            |
| StateNameType                | Route Qualifier/Shield Type                                                          | Dominant Route                         | GP_RouteIdentification [RouteQualifier]                                         |
| SecondaryName                | Alternate Concatenated Street Name                                                  | Dominant Route                         | LouisianaRoadway [FullName1]                                                    |
| SecondaryNameDir             | Alternate Street Prefix Direction                                                   | Dominant Route                         | LouisianaRoadway [St_PreDir1]                                                   |
| SecondaryRoadName            | Alternate Street Name                                                               | Dominant Route                         | LouisianaRoadway [St_Name1]                                                     |
| SecondaryNameType            | Alternate Street Name Type                                                          | Dominant Route                         | LouisianaRoadway [St_PosTyp1]                                                   |
| UrbanRural                   | Urban or Rural roadway                                                               | Dominant Route                         | FunctionalSystem [UrbanRural]                                                   |
| SegmentLength                | Length of Highway Class segment                                                     | Calculated                             | Calculated                                                                      |
| SpeedLimit                   | Speed Limit                                                                          | Dominant Route                         | N/A (blank for now)                                                             |
| Curve                        | Horizontal Curve Type                                                               | Dominant Route                         | Curve [HorizontalCurveType]                                                     |
| NHS                          | National Highway System Indicator                                                  | Dominant Route                         | NHS [NHS]                                                                       |
| AADT_Year                    | Year of last traffic collection                                                     | Dominant Route                         | AADT (ALRS) [DataYear]                                                           |
| AADT                         | Average Annualized Daily Traffic                                                    | Dominant Route                         | AADT (ALRS) [AADT]                                                               |
| AADT_Truck                   | AADT Trucks                                                                         | Dominant Route                         | Sum of AADTSingleUnit and AADTCombination                                       |
| AADT_Motorcycle              | AADT Motorcycle                                                                     | Dominant Route                         | AADTMotorcycle (ALRS)                                                            |
| LaneWidth                    | Lane Width                                                                           | Secondary = ??                         | LaneWidth [LaneWidth]                                                            |
| NumberofLanes                | Number of Lanes                                                                      | Secondary is calculated as of primary  | ThroughLanes [ThroughLanes]                                                     |
| HOVLanes                     | High Occupancy Vehicle Lane                                                         | Dominant Route                         | ManagedLanes [HOVLanes]                                                          |
| HOVLanesType                 | High Occupancy Vehicle Lane Type                                                    | Dominant Route                         | ManagedLanes [ManagedLanesType]                                                  |
| LeftShoulderWidth            | Left Shoulder Width (direction of travel)                                           | Maintained Separately                  | ShoulderInside, ShoulderOutside, RoadUse                                        |
| RightShoulderWidth           | Right Shoulder Width (direction of travel)                                          | Maintained Separately                  | ShoulderInside, ShoulderOutside, RoadUse                                        |
| AccessControl                | HPMS Access Control Type                                                             | Dominant Route                         | AccessControl [AccessControl]                                                    |
| HighwayClass                 | Traffic Safety Highway Classification Code                                          | Calculated                             |                                                                                  |
| FunctionalClass              | HPMS Functional System                                                               | Dominant Route                         | FunctionalSystem [FunctionalSystem]                                              |
| StructureIdentificationNumber| Bridge or Tunnel ID                                                                 | Dominant Route                         | Bridge [BRKEY (NBI Number)]                                                      |
| Station_ID                   | Traffic Station ID                                                                  | Dominant Route                         | Traffic Segment [???]                                                            |
| RouteIDCenterLine            | Statewide Routes Route ID for the primary direction of the main route              | Maintained Separately                  |                                                                                  |
| FromMeasureCenterLine        | Begin Measure along centerline in primary direction                                 | Calculated                             |                                                                                  |
| ToMeasureCenterLine          | End Measure along centerline in primary direction                                   | Calculated                             |                                                                                  |
| LRSIDCenterLine              | LRSID Routes Route ID for the primary direction                                     | Calculated                             |                                                                                  |
| BeginLogMileCenterLine       | LRSID Begin Measure along centerline in primary direction                          | Calculated                             |                                                                                  |
| EndLogMileCenterLine         | LRSID End Measure along centerline in primary direction                            | Calculated                             |                                                                                  |
| LocationID_Legecy_1          | Historical Highway Class Segment ID (1 year prior)                                  | Maintained Separately                  |                                                                                  |
| LocationID_Legecy_2          | Historical Highway Class Segment ID (2 years prior)                                 | Maintained Separately                  |                                                                                  |
| LocationID_Legecy_3          | Historical Highway Class Segment ID (3 years prior)                                 | Maintained Separately                  |                                                                                  |
| LocationID_Legecy_4          | Historical Highway Class Segment ID (4 years prior)                                 | Maintained Separately                  |                                                                                  |
| LocationID_Legecy_5          | Historical Highway Class Segment ID (5 years prior)                                 | Maintained Separately                  |                                                                                  |


## Domains
Several domains specific to HighwayClass are listed below for convenience. CityParish is maintained in file:///\\DOTD-Statewide.swe.la.gov\FS_GIS_RnH\Processes\HighwayClass\CityParishCodes_eCrash.xlsx in the CityParishCodes worksheet.

### Table 3: CurveType Domain
| **Domain Name** | **Field Type**| **Domain Type** | **Code** | **Description** |  
|-----------------|---------------|-----------------|----------|-----------------|
| CurveType | Text| Coded Values | 100 | Straight |  
| CurveType | Text| Coded Values | 101 | Curved |

### Table 4: HighwayClass Domain
| Domain Name   | Field Type | Domain Type   | Code | Description                      |
|---------------|------------|----------------|------|----------------------------------|
| HighwayClass  | Text       | Coded Values   | 1    | Rural 1-way 1-lane               |
| HighwayClass  | Text       | Coded Values   | 2    | Urban 1-way 1-lane               |
| HighwayClass  | Text       | Coded Values   | 3    | Rural 1-way 2-lane               |
| HighwayClass  | Text       | Coded Values   | 4    | Urban 1-way 2-lane               |
| HighwayClass  | Text       | Coded Values   | 5    | Rural 1-way 3-lane               |
| HighwayClass  | Text       | Coded Values   | 6    | Urban 1-way 3-lane               |
| HighwayClass  | Text       | Coded Values   | 7    | Rural 1-way 4-lane               |
| HighwayClass  | Text       | Coded Values   | 8    | Urban 1-way 4-lane               |
| HighwayClass  | Text       | Coded Values   | 9    | Urban 2-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 10   | Rural 3-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 11   | Urban 3-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 12   | Rural 4-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 13   | Urban 4-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 14   | Rural 5-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 15   | Rural 6-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 16   | Urban 6-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 17   | Rural 8-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 18   | Urban 8-lane Interstate          |
| HighwayClass  | Text       | Coded Values   | 19   | Rural 2-lane                     |
| HighwayClass  | Text       | Coded Values   | 20   | Urban 2-lane                     |
| HighwayClass  | Text       | Coded Values   | 21   | Rural 4-lane                     |
| HighwayClass  | Text       | Coded Values   | 22   | Urban 4-lane                     |
| HighwayClass  | Text       | Coded Values   | 23   | Rural 4-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 24   | Urban 4-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 25   | Urban 4-lane Freeway             |
| HighwayClass  | Text       | Coded Values   | 26   | Rural 2-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 27   | Urban 2-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 28   | Rural 3-lane                     |
| HighwayClass  | Text       | Coded Values   | 29   | Urban 3-lane                     |
| HighwayClass  | Text       | Coded Values   | 30   | Rural 3-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 31   | Urban 3-lane Divided             |
| HighwayClass  | Text       | Coded Values   | 32   | Rural 6-lane                     |
| HighwayClass  | Text       | Coded Values   | 33   | Urban 6-lane                     |
| HighwayClass  | Text       | Coded Values   | 34   | Rural >=6-lane Divided           |
| HighwayClass  | Text       | Coded Values   | 35   | Urban >=6-lane Divided           |
| HighwayClass  | Text       | Coded Values   | 36   | Rural 2-lane Cont Turn           |
| HighwayClass  | Text       | Coded Values   | 37   | Urban 2-lane Cont Turn           |
| HighwayClass  | Text       | Coded Values   | 38   | Rural 4-lane Cont Turn           |
| HighwayClass  | Text       | Coded Values   | 39   | Urban 4-lane Cont Turn           |
| HighwayClass  | Text       | Coded Values   | 40   | Rural >=6-lane Cont Turn         |
| HighwayClass  | Text       | Coded Values   | 41   | Urban >=6-lane Cont Turn         |
| HighwayClass  | Text       | Coded Values   | 42   | Other Rural Roads                |
| HighwayClass  | Text       | Coded Values   | 43   | Other Urban Roads                |

### Table 5: RoadClassification Domain
| **Domain Name** | **Field Type**| **Domain Type** | **Code** | **Description** |  
|-----------------|---------------|-----------------|----------|-----------------|
| RoadClassification | Text| Coded Values | 100 | Interstate |  
| RoadClassification | Text| Coded Values | 101 | US Highway |
| RoadClassification | Text| Coded Values | 102 | State Highway |
| RoadClassification | Text| Coded Values | 103 | Parish Road |
| RoadClassification | Text| Coded Values | 104 | City Street |
| RoadClassification | Text| Coded Values | 200 | Off road / Private Road |

### Table 6: RoadwaySubType Domain
| Domain Name     | Field Type | Domain Type   | Code | Description         |
|------------------|------------|----------------|------|---------------------|
| RoadwaySubType   | Text       | Coded Values   | 100  | Mainline            |
| RoadwaySubType   | Text       | Coded Values   | 200  | On-ramp             |
| RoadwaySubType   | Text       | Coded Values   | 201  | Off-Ramp            |
| RoadwaySubType   | Text       | Coded Values   | 300  | Frontage / Service  |
| RoadwaySubType   | Text       | Coded Values   | 970  | Not Applicable      |

### Table 7: TrafficWayDirection Domain
| Domain Name        | Field Type | Domain Type   | Code | Description |
|---------------------|------------|----------------|------|-------------|
| TrafficWayDirection | Text       | Coded Values   | 100  | One-Way     |
| TrafficWayDirection | Text       | Coded Values   | 200  | Two-Way     |

### Table 8: TrafficWayDivision Domain
| Domain Name          | Field Type | Domain Type    | Code | Description                                         |
|----------------------|------------|----------------|------|-----------------------------------------------------|
| TrafficwayDivision   | Text       | Coded Values   | 000  | Not Divided                                         |
| TrafficwayDivision   | Text       | Coded Values   | 001  | Not Divided with Continuous Left-Turn Lane          |
| TrafficwayDivision   | Text       | Coded Values   | 100  | Divided Flush Median (greater than 4 feet)          |
| TrafficwayDivision   | Text       | Coded Values   | 101  | Divided Raised Median (curbed)                      |
| TrafficwayDivision   | Text       | Coded Values   | 102  | Divided Depressed Median                            |
| TrafficwayDivision   | Text       | Coded Values   | 999  | Unknown                                             |

## Processing Highway Class Segments
The Highway Class Segments process begins annually with a file geodatabase copy of the enterprise R&H database. This file geodatabase copy should be from the same date as the one used to generate HPMS. Unless specified, the events used in this process should be from that file geodatabase to maintain consistency with the most recent HPMS submittal.

The Certified Public Mileage route network (CPM) from HPMS becomes the base for Highway Class. This will make up the majority of the Highway Class segment data. Some non-CPM routes that are necessary for Highway Class will be added later in the process, See Non-CPM Routes section below for more information.

Previously Highway Class data groups were referred to as Named routes and Unnamed routes. It is more accurate to refer to them as CPM routes and non-CPM routes. This is mentioned because the Named and Unnamed terminology may still come up in documentation or conversation. 

### CPM (Certified Public Mileage) Routes

<p class="abnormal">

   1. Begin with a copy of the CPM file from HPMS

   2. Bring in Functional System event from the R&H file geodatabase copy  
      1. Check this event for gaps and overlaps  
         1. This is a full-extent event that should not have gaps or overlaps. Any gaps should have been addressed in the R&H data as part of HPMS preparations.

   3. Use Identity to combine Functional System with Public/Private event into one file.  
      Use Erase with HPMS CPM file to make sure all records from that file are covered.

   4. Iterate through events: Process the Functional System + Public/Private layer with each of the event layers listed below to create one file that contains all the necessary fields.  
      Functional System, LRSID, RouteID, UrbanRural, ThroughLanes, AADT, ControlSection, AccessControl, NHS, LocationID, DOTDDistrict, ShoulderWidth, StationID, and LocationID_Legacy will all be processed using this method.  
      1. If appropriate, handle primary vs. secondary direction events

         1. Separate primary and secondary into separate layers  
         2. Erase direction 1 from direction 2 using default geodatabase tolerances  
         3. Combine direction 1 and the product of the erase operation  
      2. Dissolve event on Route ID and necessary fields for that event  
      3. Check for gaps and overlaps  

         1. Run Topology, Must Not Overlap. Delete the unneeded segment of each overlap.  
      4. Run the Identity process (spatial overlay) of the latest output and the dissolved event  
      5. Explode multipart to singlepart  
      6. Dissolve the results on the required fields entered so far  
      7. Remove segments to clear if appropriate  

         1. Remove records where RoadUse = 21 (Ferry). Ferries should not be included in final output.  
      8. Example sequence:  
         1. Dissolve Route Event (RoadUse) with only the Route ID and necessary fields (RoadUse, Divided).  
         2. Run Topology, Must Not Overlap. Delete the unneeded segment of each overlap.  
            1. Note: Overlaps at this stage are caused by overlapping events in the RoadUse event. Determine which is correct.  
               False overlaps may also be at the tip of the V in a V intersection configuration. Snap these to StatewideRoutes.  
         3. Identity with the Functional System + Public/Private file. Dissolve the results.  
         4. Investigate and populate slivers where RoadUse is Null.  
         5. Remove records where RoadUse = 21 (Ferry). Ferries should not be included in final output.

   5. Event order  
      1. Road Use  

         1. This is not an HPMS event, so it will not be pre-cleaned. Address gaps and overlaps as part of the process.  
      2. Number of Lanes  

         1. Has overlapping (secondary direction) events  
         2. Number of lanes is never odd, so no interest in what a number might be on a non-dominant route  
         3. ThroughLanes field from the NumberOfLanes event becomes NumberofLanes field in Highway Class.  
      3. LouisianaRoadways  

         1. Use a script that Alison made to clean up all the RouteName data  
            1. Note: The source data has RouteName ex. HWY 123, STATE RTE 123, STATE HWY 123 etc.  
               We want these to show LA 123 instead so ended up using last year's data (SafetySegments) to get this data.  
               LocationIDs should not break on this data.  
         2. This one should retain RouteID and necessary fields  
            (State_L, St_PreDir, St_Name, St_PosTyp, FullName, St_PreDir1, St_Name1, St_PosType1, Fullname1) when dissolving.  
      4. Medians  

         1. Has overlapping (secondary direction) events, but for both directions.  
      5. AADT  

         1. Prior to running this script, MS4 data should be located, split into events, and then loaded into R&H.  
            For all AADT related events below, use the current data that matches the HPMS submittal.  
         2. Make temporary event layer: ONLY direction 1  
         3. For direction 2 where it's a mainline (not ramps, not frontage roads), apply the value of direction 1,  
            no matter if direction 2 is on its own geometry (divided) or not (undivided)  
         4. AADTMotorcycle Event  
         5. Add AADTCombination and AADTSingleUnit Events. Identity with AADTCombination with AADTSingleUnit.  
            Add field AADT_Truck and calculate as AADTSingleUnit + AADTCombination.  
            Will become AADT_Truck in HighwayClass.  
         5. Note: LocationIDs should not break on AADT_Truck data.  
      6. Shoulder  

         1. ShoulderInside is Left Shoulder  
         2. ShoulderOutside is Right Shoulder  
      7. ManagedLanes event  

         1. Managed Lanes event populates the HOV Lanes fields  
      8. CityParish data  

         1. Use this process for CityParish data:  
            `file:///\\dotd-statewide.swe.la.gov\FS_GIS_RnH\Processes\HighwayClass\CityParish_BoundaryBufferProcess.docx`  
         2. Routes that are outside these boundaries will have null values. Assign to the nearest boundary.  
            CityFIPS should be null where the record is not in a city.  
            All other fields should be populated for all records.  
         3. Note: Route segments that run along a boundary may retrieve more than one record — one in and one out of the city.  
      9. DOTDDistrict use BNDY_DOTD_Districts from RH.Basemap  

         1. Make sure DOTDDistrict field is formatted correctly.  
      10. Troop data  

         1. The latest Troop data is in:  
            `\\DOTD-Statewide.swe.la.gov\FS_GIS_RnH\FileTransfer\FromArcadis\2023_06_26_HighwayClass`  
            An older version is in:  
            `\\dotd-statewide.swe.la.gov\FS_GIS_RnH\FileTransfer\FromArcadis\2021_10_14_SafetySegment\StatePoliceTroops.gdb`  
         2. Use the BNDY_LSP_StatePoliceTroops feature class from that location  
         3. Routes that are outside these boundaries will have null values. Assign to the nearest boundary.  
      11. Previous year LocationID  

         1. Yue is making this an event, but it isn't available yet.

   6. Run Topology, Must Not Overlap. Delete the unneeded segment of each overlap.

   7. Check for any missing records and extremely short records  
      1. Run Symmetrical Difference between cleaned up Highway Class file with all the events and the original FunctionalClass + Public or Private.  
         Clean up any areas where the files don’t match. (Except RoadUse = 21 - Ferry)  
      2. Check Total Mileage, Shape_Length → Statistics.  
         Should have the same total mileage as the input file (excluding RoadUse = 21 - Ferry).  
      3. Identify segments that are less than 5 feet. (Shape_Length < 1.524).  
         Merge these segments with an adjacent segment with matching LocationID.  
      4. Summarize on LocationID.  
         Review where there is more than one segment of each LocationID.  
         Records should be merged unless RoadUse, UrbanRural, FunctionalClass, or NumberofLanes are different on the segments.  
         In general merge to the longer segment. See previous year’s Highway Class if unsure.  
         Where RoadUse, UrbanRural, FunctionalClass, or NumberofLanes are different,  
         a new LocationID will be assigned and the old ID carried in the LocationID Legacy fields.

   8. Locate on SWR to get From/ToMeasure

   9. Locate on LRSID to get Begin/EndLogMile  
      1. The original record could get segmented, if this happens, update the SWR From/ToMeasure  
      2. Check for null values. Fill in if possible.

   10. Look for duplicate LocationIDs  
      1. These will need to be assigned new Location IDs.  
         Old Location ID will be carried in LocationID_Legecy_1 field.

   11. Create an empty copy of HighwayClass schema  
      1. Then load data working file into this schema. Check field mapping. Make sure everything maps correctly in the schema.

   12. Populate Calculated and Joined Fields  
      1. Join to StatewideRoutes on RouteID.  
         Populate FeatureTypeCode and SystemCode. Remove Join.  
      2. Do not populate SpeedLimit or Curve fields.  
      3. Calculate EventID with this Python script:
         <code style="padding: 0 !important; margin-top: 0 !important; line-height: 1.2rem;">
         def CalcGUID():
         import uuid
         return str(uuid.uuid4()) 
         </code>
      4. Calculate TrafficWayDivision  
         1. If MedianType = 1 AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 000  
         2. If MedianType = 2 AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 100  
         3. If MedianType IN {3, 4, 5, 6, 7} AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 101  
         4. If RoadUse = 5 AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 001  
         5. If RoadUse IN (3a, 3b, 8) AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 000  
         6. If Divided = N AND TrafficWayDivision IS NULL → Then TrafficWayDivision = 000  
         7. If TrafficWayDivision IS NULL → Then TrafficWayDivision = 999  
      5. Calculate TrafficwayTravelDirection
         1. #### Table 9: TrafficwayTravelDirection
            |Where      | Expression (Selected Records View)       |
            |-----------|------------------------------------------|
            |RoadUse = 1| TrafficwayTravelDirection = 100 (One-Way)|
            |RoadUse = 2| TrafficwayTravelDirection = 200 (Two-Way)|
         6. Calculate Traffic Direction
            1. Join to Statewide Routes on RouteID. Calculate TrafficDirection based on Statewide Routes.InventoryDirection field.
         7. Calculate RoadClassification
            1. #### Table 10: RoadClassification
               |Where                                          |Expression (Selected Records View)       |
               |-----------------------------------------------|-----------------------------------------|
               |RouteID LIKE 999_I%                            | RoadClassification = 100 (Interstate)   |
               |RouteID LIKE 999_US%                           | RoadClassification = 101 (US Highway)   |
               |RouteID LIKE 999_LA%                           | RoadClassification = 102 (State Highway)|
               |RouteID NOT LIKE 999_% AND CityFIPS IS NULL    | RoadClassification = 103 (Parish Road)  |
               |RouteID NOT LIKE 999_% AND CityFIPS IS NOT NULL| RoadClassification = 104 (City Street)  |
               |Private Roads Calculated Separately in 2022 thus not used in the Named Routes file | RoadClassification = 200 (Off Road / Private Road)|
         8. Calculate RoadwaySubType
            1. Note: Some records were still null where RoadUse was Roundabout or Connector. Not sure if these segments should have an assigned RoadwaySubType?
            2. #### Table 11: RoadwaySubType
               |Where                                                           |Expression (Selected Records View)                            |
               |----------------------------------------------------------------|--------------------------------------------------------------|
               |RoadUse IN (1, 2, 3a, 3b, 4a, 4b, 5) AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 100 (Mainline)               |
               |RoadUse IN (6a, 6b, 6c, 6e, 6f) AND RoadwaySubType IS NULL      | Highway Safety.RoadwaySubType = 300 (Frontage/Service Roads) |
               |FeatureTypeCode IN (A_, B_, G_, H_) AND RoadwaySubType IS NULL  | Highway Safety.RoadwaySubType = 200 (On-Ramp)                |
               |FeatureTypeCode IN (C_, D_, E_, F_) AND RoadwaySubType IS NULL  | Highway Safety.RoadwaySubType = 201 (Off-Ramp)               |
               |RoadUse IS NULL AND RoadwaySubType IS NULL                      | Highway Safety.RoadwaySybType = 970 (Not Applicable)         |
         9. Calculate HighwayClass according to the table below. Alison has a process for this.
            1. #### Table 12: HighwayClass
               |NewCode|CODE_DESCRIPTION|FULL_CODE_DESC|NEW QUERY DETAIL|QueryUsed|
               |-------|----------------|--------------|----------------|---------|
               | 1   | Rural 1-way 1-lane | 1 - Rural 1-way 1-lane | UrbanRural = 'R' AND ThroughLanes = 1 AND RoadUse In ('1','7','8') | UrbanRural = 'R' AND NumberofLanes = 1 AND RoadUse In ('1','7','8') AND HighwayClass Is Null |
               | 2   | Urban 1-way 1-lane | 2 - Urban 1-way 1-lane | UrbanRural = 'U' AND ThroughLanes = 1 AND RoadUse Not In ('4a','4b','2','6c','0') | UrbanRural = 'U' AND NumberofLanes = 1 AND RoadUse Not In ('4a','4b','2','6c','0') AND HighwayClass Is Null |
               | 3   | Rural 1-way 2-lane | 3 - Rural 1-way 2-lane | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse In ('1','7','8') | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse In ('1','7','8') AND HighwayClass Is Null |
               | 4   | Urban 1-way 2-lane | 4 - Urban 1-way 2-lane | (UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse IN ('1' ,'6a','6b','7','8')) | (UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse IN ('1' ,'6a','6b','7','8')) AND HighwayClass Is Null |
               | 5   | Rural 1-way 3-lane | 5 - Rural 1-way 3-lane | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalClass <> '1' AND RoadUse = '1' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass <> '1' AND RoadUse = '1' AND HighwayClass Is Null |
               | 6   | Urban 1-way 3-lane | 6 - Urban 1-way 3-lane | (UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalClass <> '1' AND RoadUse = '1') | (UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass <> '1' AND RoadUse = '1') AND HighwayClass Is Null |
               | 7   | Rural 1-way 4-lane | 7 - Rural 1-way 4-lane | UrbanRural = 'R' AND ThroughLanes = 4 AND FunctionalClass <> '1' AND RoadUse = '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND FunctionalClass <> '1' AND RoadUse = '1' AND HighwayClass Is Null |
               | 8   | Urban 1-way 4-lane | 8 - Urban 1-way 4-lane | (UrbanRural = 'U' AND ThroughLanes = 4 AND FunctionalClass <> '1' AND RoadUse = '1') | (UrbanRural = 'U' AND NumberofLanes = 4 AND FunctionalClass <> '1' AND RoadUse = '1') AND HighwayClass Is Null |
               | 9   | Urban 2-lane Interstate | 9 - Urban 2-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 2 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 2 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 10  | Rural 3-lane Interstate | 10 - Rural 3-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 11  | Urban 3-lane Interstate | 11 - Urban 3-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 12  | Rural 4-lane Interstate | 12 - Rural 4-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 4 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 13  | Urban 4-lane Interstate | 13 - Urban 4-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 4 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 4 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 14  | Urban 5-lane Interstate | 14 - Urban 5-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 5 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 5 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 15  | Rural 6-lane Interstate | 15 - Rural 6-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 6 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 6 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 16  | Urban 6-lane Interstate | 16 - Urban 6-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 6 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 6 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 17  | Rural 8-lane Interstate | 17 - Rural 8-lane Interstate | UrbanRural = 'R' AND ThroughLanes = 8 AND FunctionalSystem = '1' | UrbanRural = 'R' AND NumberofLanes = 8 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 18  | Urban 8-lane Interstate | 18 - Urban 8-lane Interstate | UrbanRural = 'U' AND ThroughLanes = 8 AND FunctionalSystem = '1' | UrbanRural = 'U' AND NumberofLanes = 8 AND FunctionalClass = '1' AND HighwayClass Is Null |
               | 19  | Rural 2-lane | 19 - Rural 2-lane | (UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND Divided = 'N') | (UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND (RoadUse <> '4a' AND RoadUse <> '4b')) AND HighwayClass Is Null |
               | 20  | Urban 2-lane | 20 - Urban 2-lane | (UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND Divided = 'N') | (UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND (RoadUse <> '4a' AND RoadUse <> '4b')) AND HighwayClass Is Null |
               | 21  | Rural 4-lane | 21 - Rural 4-lane | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse <> '5' AND FunctionalSystem <> '1' AND Divided = 'N' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse <> '5' AND FunctionalClass <> '1' AND (RoadUse <> '4a' AND RoadUse <> '4b') AND HighwayClass Is Null |
               | 22  | Urban 4-lane | 22 - Urban 4-lane | (UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem NOT IN ('1', '2') AND Divided = 'N') | (UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass NOT IN ('1', '2') AND (RoadUse <> '4a' AND RoadUse <> '4b')) AND HighwayClass Is Null |
               | 23  | Rural 4-lane Divided | 23 - Rural 4-lane Divided | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse <> '5' AND FunctionalSystem <> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse <> '5' AND FunctionalClass <> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 24  | Urban 4-lane Divided | 24 - Urban 4-lane Divided | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem NOT IN ('1', '2') AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass NOT IN ('1', '2') AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 25  | Urban 4-lane Freeway | 25 - Urban 4-lane Freeway | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem = '2' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse NOT IN ('1', '5') AND FunctionalClass = '2' AND HighwayClass Is Null |
               | 26  | Rural 2-lane Divided | 26 - Rural 2-lane Divided | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse <> '5' AND FunctionalSystem <> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse <> '5' AND FunctionalClass <> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 27  | Urban 2-lane Divided | 27 - Urban 2-lane Divided | UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem <> '1' AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse NOT IN ('1', '5') AND FunctionalClass <> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 28  | Rural 3-lane | 28 - Rural 3-lane | UrbanRural = 'R' AND ThroughLanes = 3 AND FunctionalSystem <> '1' AND NOT Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 3 AND FunctionalClass <> '1' AND NOT (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 29  | Urban 3-lane | 29 - Urban 3-lane | UrbanRural = 'U' AND ThroughLanes = 3 AND FunctionalSystem <> '1' AND NOT Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 3 AND FunctionalClass <> '1' AND NOT (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 30  | Rural 3-lane Divided | 30 - Rural 3-lane Divided | UrbanRural = 'R' AND ThroughLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem <> '1' AND Divided = 'Y' | UrbanRural = 'R' AND NumberofLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalClass <> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 31  | Urban 3-lane Divided | 31 - Urban 3-lane Divided | UrbanRural = 'U' AND ThroughLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalSystem <> '1' AND Divided = 'Y' | UrbanRural = 'U' AND NumberofLanes = 3 AND RoadUse NOT IN ('1', '5') AND FunctionalClass <> '1' AND (RoadUse = '4a' OR RoadUse = '4b') AND HighwayClass Is Null |
               | 32  | Rural 6-lane | 32 - Rural 6-lane | UrbanRural = 'R' AND ThroughLanes = 6 AND RoadUse = '2' AND FunctionalSystem <> '1' | UrbanRural = 'R' AND NumberofLanes = 6 AND RoadUse = '2' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 33  | Urban 6-lane | 33 - Urban 6-lane | UrbanRural = 'U' AND ThroughLanes = 6 AND RoadUse = '2' AND FunctionalSystem <> '1' | UrbanRural = 'U' AND NumberofLanes = 6 AND RoadUse = '2' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 34  | Rural >=6-lane Divided | 34 - Rural >=6-lane Divided | UrbanRural = 'R' AND ThroughLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalSystem <> '1' | UrbanRural = 'R' AND NumberofLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 35  | Urban >=6-lane Divided | 35 - Urban >=6-lane Divided | UrbanRural = 'U' AND ThroughLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalSystem <> '1' | UrbanRural = 'U' AND NumberofLanes >= 6 AND RoadUse in ('4a','4b') AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 36  | Rural 2-lane Cont Turn | 36 - Rural 2-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes = 2 AND RoadUse = '5' AND FunctionalSystem <> '1' | UrbanRural = 'R' AND NumberofLanes = 2 AND RoadUse = '5' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 37  | Urban 2-lane Cont Turn | 37 - Urban 2-lane Cont Turn | (UrbanRural = 'U' AND ThroughLanes = 2 AND RoadUse = '5' AND FunctionalSystem <> '1') | (UrbanRural = 'U' AND NumberofLanes = 2 AND RoadUse = '5' AND FunctionalClass <> '1') AND HighwayClass Is Null |
               | 38  | Rural 4-lane Cont Turn | 38 - Rural 4-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes = 4 AND RoadUse = '5' AND FunctionalSystem <> '1' | UrbanRural = 'R' AND NumberofLanes = 4 AND RoadUse = '5' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 39  | Urban 4-lane Cont Turn | 39 - Urban 4-lane Cont Turn | UrbanRural = 'U' AND ThroughLanes = 4 AND RoadUse = '5' AND FunctionalSystem <> '1' | UrbanRural = 'U' AND NumberofLanes = 4 AND RoadUse = '5' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 40  | Rural >=6-lane Cont Turn | 40 - Rural >=6-lane Cont Turn | UrbanRural = 'R' AND ThroughLanes >= 6 AND RoadUse = '5' AND FunctionalSystem <> '1' | UrbanRural = 'R' AND NumberofLanes >= 6 AND RoadUse = '5' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 41  | Urban >=6-lane Cont Turn | 41 - Urban >=6-lane Cont Turn | UrbanRural = 'U' AND ThroughLanes >= 6 AND RoadUse = '5' AND FunctionalSystem <> '1' | UrbanRural = 'U' AND NumberofLanes >= 6 AND RoadUse = '5' AND FunctionalClass <> '1' AND HighwayClass Is Null |
               | 42  | Other Rural Roads | 42 - Other Rural Roads | (UrbanRural = 'R' AND HighwayClass NOT IN ('U', 'X', 'D', 'E', 'F', 'G', 'H', 'R', 'S', 'A', 'B', 'C', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18')) | UrbanRural = 'R' AND HighwayClass Is Null |
               | 43  | Other Urban Roads | 43 - Other Urban Roads | (UrbanRural = 'U' AND HighwayClass NOT IN ('U', 'X', 'D', 'E', 'F', 'G', 'H', 'R', 'S', 'A', 'B', 'C', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18')) | UrbanRural = 'U' AND HighwayClass Is Null |

   ### Non-CPM Routes
   These are the routes that are in Highway Class, but not included in Certified Public Mileage for HPMS. These

   1. Erase the CPM routes from previous years Highway Class to create file of Non=CPM routes.

      1. This file contains all the fields from Highway Class.

   2. Calculate new EventID using Python script.

```
def CalcGUID():
import uuid
return { + str(uuid.uuid4()) + }
```

   3. Identity with each Event / source file

      1. CityParish\_Polygons\_wDomains

      2. BNDY\_DOTD\_Districts

      3. BNDY\_LSP\_StatePoliceTroops

      4. LRSID\_Routes

      5. LouisianaRoadways

      6. FunctionalSystem

      7. NHS

      8. AADT (Current Year data)

      9. AADTMotorcycle (Current Year data)

      10. AADTCombination (Current Year data)

      11. LaneWidth

      12. NumberofLanes

      13. ManagedLanes (Should be null on non-CPM)

      14. ShoulderOutside

      15. ShoulderInside

      16. AccessControl

   4. Join each Identity file to HighwayClass\_non-CPM on EventID.

   5. Field Calculate the relevant fields from the Identity file.

   6. Remove Join.

   7. Calculate ControlSection if any of the routes have Control Section based RouteIDs.

   8. Leave SpeedLimit and Curve data null.

   9. Join to StatewideRoutes on RouteID. Populate FeatureTypeCode and SystemCode. Remove Join.

   10. Calculate TrafficWayDivision as with CPM data

   11. Calculate TrafficwayTravelDirection as with CPM data

   12. Calculate TrafficDirection

      1. Join to Statewide Routes on RouteID. Calculate TrafficDirection based on StatewideRoutes.InventoryDirection field.

   13. Calculate RoadClassification. as with CPM data

   14. Calculate RoadwaySubType

      1. Some records were still null where RoadUse was Roundabout or Connector. Not sure if these segments should have an assigned RoadwaySubType?

      2. #### Table 13. Calculate RoadwaySubType.

         | WHERE | Expression (Selected Records View) |
         | --- | --- |
         | RoadUse IN (1, 2, 3a, 3b, 4a, 4b, 5) AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 100  <br>(Mainline) |
         | RoadUse  <br>IN (6a, 6b, 6c, 6e, 6f) AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 300  <br>(Frontage/ServiceRoads) |
         | FeatureTypeCode IN (A\_, B\_, G\_, H\_) AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 200  <br>(On-Ramp) |
         | FeatureTypeCode IN (C\_, D\_, E\_, F\_) AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 201  <br>(Off-Ramp) |
         | RoadUse IS NULL AND RoadwaySubType IS NULL | Highway Safety.RoadwaySubType = 970  <br>(Not Applicable) |

   15. Calculate HighwayClass.

      1. See Table 11 Calculate HighwayClass above.

      2. Alison has a process for this.

   16. Locate on SWR to get From/ToMeasure

   17. Locate on LRSID to get Begin/EndLogMile

      1. The original record could get segmented, if this happens, update the SWR From/ToMeasure

      2. Check for null values. Fill in if possible.

   18. Append Highway Class CPM and HighwayClass Non-CPM files together.

      1. Centerline measures can be processed as one file.

   ### Processing AADT for direction 2 Records

   AADT was not provided for Direction 2 routes where Facility Type is 5 or 6. The way the data was collected and provided, all the AADT data for both directions was assigned to the Direction 1 route.

   1. Separate the data where AADT is NULL and where AADT is NOT NULL. Export into two different feature class. Files need only fields: RouteNameFull, RouteID, ID, and AADT

   2. Create a buffer on file that has AADT.

   3. Run Spatial Join between the file with No AADT and the Buffer using One to Many Relationship.

   4. From the Join file, select where RouteNameFull = RouteNameFull\_1. These are the records to carry forward. Export to new file.

   5. Add a field (Long) and calculate as AADT/2

   6. Join the new AADT/2 field back to the original file using the ID from the No AADT file.

   ### Processing Centerline Route and Measures for direction 2 Records

   It has been requested that Direction 2 records include the Route ID and Measures for the corresponding Direction 1 route in both RouteID and LRSID. Ramps and frontage roads will include measures along the Direction 1 mainline. These referred to as RouteIDCenterLine and LRSIDCenterLine and their associated measures.

   1. Make sure that data contains UniqueID, if not, add one.
   2. Create New Selevtion: RoadwaySubType = 100 AND RoadUse IN (3b, 4b, 15).
   3. Add to Current Selection: RoadwaySubType IN (200, 201, 300) AND RouteID LIKE 999\_%
   4. Export selected Records to a new file. These are the records that need RouteIDCenterLines.
   5. Export a subset of StatewideRoutes where FeatureTypeCode = 1\_
   6. Join to StatewideRoutes where FeatureTypeCode = 1\_on RouteFullName and populate RouteIDCenterLine with Direction 1 RouteID.
   7. Use Vertex to Point tool to create a Point file of the Beginning Point of each segment
   8. Use Vertex to Point tool to create a Point file if the End Point of each segment.
   9. Locate Begin Points along Exported StatewideRoutes. Start with 0.5 mile as the search distance. May need to increase it if that doesnt retrieve all the records.
   10. Exclude any unneeded records by deleting records where RID<>RouteIDCenterline
   11. Locate End Points along Exported StatewideRoutes
   12. Exclude any unneeded records by deleting records where RID<>RouteIDCenterline
   13. Join Begin Measure file on UniqueID to Highway Class file and calculate FromMeasureCenterLine = MEAS. Round to 3 decimal places. Remove Join.
   14. Join End Measure file on UniqueID to Highway Class file and calculate ToMeasureCenterLine as MEAS. Round to 3 decimal places. Remove Join.
   15. Where necessary, reverse the measures so the minimum measure (of FromMeasureCenterLineand ToMeasureCenterLine) is the FromMeasureCenterLine and the maximim measure is ToMeasureCenterLine
   16. For remaining records where RouteID = RouteIDCenterline, calculate FromMeasureCenterline as FromMeasure and ToMeasureCenterline as ToMeasure. Direction 1 records have the same value in both places, nothing changes.

   17. Repeat steps for LRSID\_Routes replacing StatewideRoutes with LRSID\_Routes.

   18. Join to LRSID Route on ControlSection and populate LRSIDCenterLine with Direction 1 LRSID. The rest of the process is the same.

</div>
   

## QC Tasks

List of QC tasks performed. These are some of the QC issues that have come up in the past. Some of the notes above should prevent some of these issues.

<p class="abnormal">

1. ControlSection should be the first 6 characters of the RouteID for On System Routes and null for Off System Routes. Make sure ControlSection is populated correctly.

2. Check CityParish Check where CityParish is null. Fill in CityParish and City if needed. Some route segments are outside the Parish Boundary.
   1. All CityParish should be populated even where outside the city boundary.

3. Check Control Section Many of these had NULL as a value rather than actually being null.

4. After realizing that checked all fields for vs <null> and changed all blank values to <null> in all fields.

5. Identity with Troop polygon and join with EventID to insert Troop values.

6. Check Road Use for missing values.

7. Check LouisianaRoadways fields for missing values.

   1. Note: Where Louisiana Roadways data is missing RoadNameDir, RoadName, and RoadNameType, use the RouteNameFull field from StatewideRoutes to fill in these values. Used formula !RouteNameFull! .split(" ")\[0\] to split on spaces.

8. Calculate RoadClassification from RouteID and CityFIPS (Null/ Not Null)

9. Calculate the calculated fields.
   1. TrafficWayDivision
   2. TrafficWayTravelDirection
   3. TrafficDirection
   4. RoadClassification
   5. RoadwaySubtype
   6. HighwayClass

10. Double Check Road Use. Make Sure it matches source data.

11. Segments should not break for SecondaryRoadName. Recalculate SecondaryRouteName to be all caps and dissolve.
      1. Need to recalculate Measures after dissolve.

12. For RoadNameFull, want LA 1091, not HWY 1091.
      1. Joined on LocationID\_Legacy to get from last year

13. Ascending and Descending (4a/4b) side of the highways should have same HighwayClass. Check HighwayClass for 4a/4b. Changed NumberofLanes on 4b record to match 4a record if not the same. Then changed HighwayClass.

14. Symmetrical Difference with NeedsOverlay file to make sure no records went missing. Compare total Shape\_Length.

15. Recalculate TrafficWayDivision. I dont think I ever got the formula right for this. In the end Shirin decided to do it herself.

16. Compare to City/Parish file. Seems like most of the issues here were routes that run right along the edge of a city. There were also some issues where the city was misspelled. I selected by location all the records that were within that boundary and calculated the City Name to match the boundary file. Then I did some checks between Parish, ParishCode, ParishFIPS to make sure they all match. City, CityFIPS to make sure they all match.

17. Road Classification. Once City was corrected, these were corrected to be CityStreets when inside the city boundary.

18. Some DOTDDistrict records were LL. These were outside the boundary.

19. There were some null values in Troop. These were also outside the boundary.

20. Control Section had some incorrect values. Should be the first 6 characters of the route name for On System Routes and null for Off System routes.

21. Recalculate RoadwaySubType.

22. Review AADT Motorcycle values. Did Identity then looked at records where AADT Motorcycle <> to AADT Motorcycle\_1

23. Once all the data is cleaned up, dissolve on all fields except EventID, FromMeasure, ToMeasure, BeginLogMile, EndLogMile.

24. Summarize on LocationID, take a look at any LocationID that has more than one record.

25. Merge Location IDs. I merged location IDs where the break was not caused by RoadUse or NumberofLanes.

26. Recalculate HighwayClass 
      1. Shirin decided to do this herself.
         1. \\\\dotd-statewide.swe.la.gov\\FS\_GIS\_RnH\\GeodatabaseMaintenance\\SchemaChanges\\HighwayClassCodes\_20220407.xlsx

27. After I gave the file to Shirin, she filled in the gaps in RoadUse where it was null in the source data.

28. After Shirin cleaned up RoadUse there were more LocationID records that needed to be merged.

</div>

| Version # | Created By | Created Date | Approved By | Approved Date | Reason |
| --- | --- | --- | --- | --- | --- |
| 1.0 | Marisa Mailand | 12/16/2022 |     |     | Initial draft |
| 1.1 | Marisa Mailand | 9/27/2023 |     |     | Added AADT and Centerline sections |
| 2.0 | Alison Mynsberge | 3/7/2024 |     |     | Added field definition/ calculation table and references to automated processes |
| 2.1 | Alison Mynsberge | 4/14/2024 |     |     | Added notes from in-person meeting |
