# HWF Widget App
## Requirements
In versions 2.3* of DHIS2 the following functionalities where needed:
 - Aggregate/Dis-aggregate by data element as if it was a category combination. Ex: Source type in HWF Modules.
 - Display DHIS2 native comments and custom DE comments from the data entry values.
 - Display and manage audit information on the data values: Authorship and history.
 - Display customizable reports (HTML based reports) in Dashboard page as any other PivotTable/Chart.

## General approach
DHIS2 supports the management and development of widget apps by the MANIFEST file. The main approach involves the develop of a simple App inheriting from the [skeleton app](https://github.com/EyeSeeTea/dhis2-app-skeleton) embedding DHIS2 standard HTML-based reports.

DHIS2 widget apps are implemented as Iframes in the Dashboard. They receive two parameters (to be check in the following versions of DHIS2): *dashboardItem [Unique identifier of this app instance in a dashboard] and organisationUnit [user-based organisation that can be changed in the dashboard filter]*

The *dashboardItem* attribute can be used to add a new key:value element in the data store repository where initially the user can define which report and which filters are required in the app. After the initial configuration, the app will always load the desired visualization as any other dashboard item.

The *organisationUnit* can be transferred to the report by means of query string parameter and be used as the initial value for the visualization (although the user might require other levels in the orgUnit tree)

The desired visualization is then propagated to the HTML-based report engine and their functionalities. The app will always integrate the report into the widget frame.

## Structure of the repository

- [custom-reports](custom-reports/) contains the developed reports available in the Widget app. Each report contains a source .html file and a README file for deployment and correct usage.
- *to be added* src folder for the widget app + docs

## Custom reports
- [Extended pivot table](custom_reports/extended_pivot_table/README.md) Implementing a data table extracted directly from the existing pivot tables list and adding HWF requirements: Source type aggregation and audit.
