# Galway City Public WCs
## Data Representation and Querying Project 2015
### Jason McTigue

## Introduction
This project provides the design and documentation for the dataset Galway City Public WCs(Water closets) which is available at [data.gov.ie](https://data.gov.ie/dataset/galway-city-public-wcs)

I would imagine that this API would be very useful to everyone and especially those who would require wheelchair accessible WCs. I designed this API with wheelchair accessible needs in mind as I know not every public WC would have access for wheelchairs. It would be especially useful for tourists and people who are visiting Galway for the day and wouldn't be that familiar with the city.

This API is extremely simple to use and gives the user information such as the location, the type, the charge to use and whether it is wheelchair accessible or not.

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

## The different HTTP methods

| **Value**       | **Description** |
| ------------- |:-------------:|
| **Get**:     | he GET method is used to retrieve information from the given server using a given URI. Requests using GET should only retrieve data and should have no other effect on the data. |
| **Head**: | Same as GET, but transfers the status line and header section only. |
| **Post**: | A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms. |
| **Put**: | Replaces all current representations of the target resource with the uploaded content. |
| **Delete**: | Removes all current representations of the target resource given by a URL. |

REF- *http://www.tutorialspoint.com/http/http_methods.htm*

## List of wheelchair accessible WCs
You can get a list of wheelchair accessible WCs using the **GET** method at the following URL:
*http://galwayWCs.ie/Wheelchair-accessible/[value]*
where you replace [value] with the Wheelchair.
For example, the URL:
*http://galwayWCs.ie/Wheelchair-accessible/wheelchair*
will return a list of Wheelchair-accessible WCs.
The data will be returned in JSON format, with the following properties for each WC:

    - Location: the location of the WC.
    - Type: the type of WC (Automated or Conventional).
    - Opening Hours: The opening hours of the WC
    
An example of a response would be:

    ```json
    [{"Location": Eyre Sqaure, 
    "Type": "Automated",
    "Opening Hours": "24hrs",}]
    ```
    
## Location of WCs
You can get a list of all WCs in a given area using the **GET** method at the following URL:
*http://galwayWCs.ie/location/[value]*
where you replace [value] with the area.
For example, the URL:
*http://galwayWCs.ie/location/eyresquare*
will return a list of WCs in Eyre Square.
The data will be returned in JSON format, with the following properties for each WC:

    - Location: the location of the WC.
    - Type: the type of WC: Automated or Conventional.
    - Opening Hours: The opening hours of the WC
    
An example of a response would be:

    ```json
    [{"Location": Eyre Square, 
    "Type": "Automated",
    "Opening Hours": "24hrs",}]
    ```
    
## WCs that are free to use
You can get a list of all WCs in a given area using the **GET** method at the following URL:
*http://galwayWCs.ie/charge/[value]*
where you replace [value] with free/charge.
For example, the URL:
*http://galwayWCs.ie/location/free*
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

To add new data to the dataset you need to use a **POST** method. 

So for example if I wanted to add a new location to the dataset I would do a post call on the following URL: *http://galwayWCs.ie/newWC*

    -POST /GalwayWCs/newWC HTTP/1.1
    -Host: galwayWCs.ie
    -id="9"&location="Renmore"&type="automated"&wheelchair="accessible"&openinghours="24hr"&charge="free"

This would then add all this new data to the table.

Post requests are a more secure way of adding new data as a get request isnt very secure.

    POST requests are never cached
    POST requests do not remain in the browser history
    POST requests cannot be bookmarked
    POST requests have no restrictions on data length
    REF - http://www.w3schools.com/tags/ref_httpmethods.asp

## Deleting Data from the dataset.

To delete data from the dataset you need to use a **DELETE** method.

You may need to use the delete method if someone adds some wrong data to the dataset by mistake or if for some reason a WC is no longer in use or has been replaced by something else.

- You would delete the the WC from the dataset by using the unique id that is associated  with the WC you want to delete.

- You would need to use the DELETE method at the following URL: http://galwayWCs.ie/delete/[Id]

- Where you replace Id with the id of the WC you want to delete.

For example, the URL: http://galwaycarparks.ie/delete/Id=5
will delete the car park with the Object ID of 5.

   An example of a response would be:

    ```
     HTTP/1.1 200 OK
     URL DELETED
    ```
    
    A HTTP responce with 200 indicates that the resource was deleted successfully.
