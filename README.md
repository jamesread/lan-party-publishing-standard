# lan-party-publishing-standard

This is repository that contains a specification for publishing LAN parties in a JSON format, making your events machine readable. The idea is that it can be used by syndication sites like https://lanlist.info without humans having to manually do anything!

## Examples & Reference Implementations

This repository only contains the text standard, and some example json files. You can use whatever you like to generate a JSON file that matches the standard, and validate your output against the JSON schema linked in this repository. However, it is much easier to generate the JSON file using a library;

* PHP: [lan-party-publisher-php](https://github.com/jamesread/lan-party-publisher-php) library

## Formal specification

The formal JSON Specification is here; [lan-party-publishing-standard-v1.schema](lan-party-publishing-standard-v1.schema). You should be able to validate your JSON output against this JSON schema file to test for bugs.

## Human readable specification documentation

The JSON structure is very simple;

* 1x [Organisation](#organisation)
    * 1 - Many [Venue(s)](#venue)
        * 1 - Many [Event(s)](#event)
            * 0 - Many [Attendees](#attendee)

## Types

### Base

The base type, from which all types inherit, have the following attributes;

| Property Name | Description | Examples |
|---------------|-------------|----------|
| apiVersion    | An API version to aid in future compatibility.  |          |
| apiType       | One of the standard type names.                 |          |
| name          | A "friendly" name, like a title, or username.   |          |
| siteUniqueId  | An ID that is unique in your database.           |          |

### Organisation

| Property Name | Description | Examples |
|---------------|-------------|----------|
| name          | The name of your oranisation                    | `mylan`  |
| siteUniqueId  | An ID that is unique in your databse.           | `mylan`  |
| venues        | The venues this organisation uses.              | -  |

### Venue

| Property Name | Description | Examples |
|---------------|-------------|----------|
| name          | The name of your venue, normally a hall.        | `My Village Hall` |
| siteUniqueId  | An ID that is unique in your database.          | `2`               |
| gpsLatitude   | Because the site works in multiple countries, a post code, or street name won't be enough to put your venue on the map. See http://getlatlng.com to find your venue lat/lng easily.    | `2`               |
| gpsLongditude | See above.                                      | See above.        |
| events        | The events at this venue.                       | -       |

### Event

| Property Name | Description | Examples |
|---------------|-------------|----------|
| name          | The name of your event, normally a hall.        | `Awesome Lan 001` |
| siteUniqueId  | An ID that is unique in your database.          | `1337`               |
| start         | The date the event starts. ISO 8601 format.     | `2005-08-15T15:52:01+0000`        |
| finish        | The date the event finishes. ISO 8601 format.   | `2005-08-15T15:52:01+0000`        |
| attendees     | An (optional) list of attendees. 8601 format.   | Attendee array        |

### Attendee (optional)

| Property Name | Description | Examples |
|---------------|-------------|----------|
| name          | The name of your event, normally a hall.        | `Awesome Lan 001` |
| siteUniqueId  | An ID that is unique in your database.          | `1337`               |



