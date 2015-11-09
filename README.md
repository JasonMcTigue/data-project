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
    
## WCs that are free to use
You can get a list of all WCs in a given area using the GET method at the following URL:
*http://galwayWCs.ie/charge/[value]*
where you replace [value] with free/charge.
For example, the URL:
*http://galwayWCs.ie/location/[free]*
will return a list of WCs in Galway city that area free to use.
The data will be returned in JSON format, with the following properties for each WC:

    - Location: the location of the WC.
    - Charge: What it costs to use the WC
    
An example of a response would be:

    ```json
    [{"Location": Silverstrand, 
    "Charge": Free,},
    {"Location": Ballyloughan,
    "Charge" Free,}]
    ```
    
##Adding new data to the dataset

To add new data to the dataset you need to use a post call. 

So for example if I wanted to add a new location to the dataset I would do a post call on the follwing URL: *http://galwayWCs.ie/newWC*

    -POST /GalwayWCs/newWC HTTP/1.1
    -Host: galwayWCs.ie
    -id="9"&location="Renmore"&type="automated"&wheelchair="accessible"&openinghours="24hr"&charge="free"

This would then add all this new data to the table.

Post requests are a more secure way of adding new data as a get request isnt very secure.

POST requests are never cached
POST requests do not remain in the browser history
POST requests cannot be bookmarked
POST requests have no restrictions on data length

