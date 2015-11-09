# Galway City Public WCs
## Data Representation and Querying Project 2015
### Jason McTigue

## Introduction
This project provides the design and documentation for the dataset Galway City Public WCs which is available at [data.gov.ie](https://data.gov.ie/dataset/galway-city-public-wcs)

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [Galway City Public WCs](https://data.gov.ie/dataset/galway-city-public-wcs/resource/0e15c0e0-0c00-4650-aebc-c9304ae33ea0).

The CSV file contains 8 rows, the first being a header row with the names of each field.
There are 8 values on each line, which are as follows:

    
| **Value**       | **Description** |
| ------------- |:-------------:|
| **Id**:     | The unique id associated with the WC.|
| **Location**: | Where the WC is located.|
| **Type**: | Whether it is Automated or Conventional.|
| **Wheelchair-accessible**: | If it is wheelchair accessible or not.|
| **Opening hours**: | Times when the WCs are open.|
| **Charge**: | If there’s a charge to use the WC.|
| **Latitude**: | Location of the WC.|
| **Longitude**: | Location of the WC.|

## List of wheelchair accessible WCs
You can get a list of wheelchair accessible WCs using the GET method at the following URL:
*http://galwayWCs.ie/Wheelchair-accessible/[value]*
where you replace [value] with the Wheelchair.
For example, the URL:
*http://galwayWCs.ie/Wheelchair-accessible/[wheelchair]*
will return a list of Wheelchair-accessible WCs.
The data will be returned in JSON format, with the following properties for each WC:

    - Location: the location of the WC.
    - Type: the type of WC (Automated or Conventional).
    - Opening Hours: The opening hours of the WC
    
An example of a response would be:

    ```json
    [{"Location": Erye Sqaure, 
    "Type": "Automated",
    "Opening Hours": "24hrs",}]
    ```
    
## Location of WCs
You can get a list of all WCs in a given area using the GET method at the following URL:
*http://galwayWCs.ie/location/[value]*
where you replace [value] with the area.
For example, the URL:
*http://galwayWCs.ie/location/[eyresqaure]*
will return a list of WCs in Eyre Sqare.
The data will be returned in JSON format, with the following properties for each WC:

    - Location: the location of the WC.
    - Type: the type of WC: Automated or Conventional.
    - Opening Hours: The opening hours of the WC
    
An example of a response would be:

    ```json
    [{"Location": Erye Sqaure, 
    "Type": "Automated",
    "Opening Hours": "24hrs",}]
    ```
    

