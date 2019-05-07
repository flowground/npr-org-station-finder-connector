# ![LOGO](logo.png) NPR Station Finder Service **flow**ground Connector

## Description

A generated **flow**ground connector for the NPR Station Finder Service API (version 3).

Generated from: https://api.apis.guru/v2/specs/npr.org/station-finder/3/swagger.json<br/>
Generated at: 2019-05-07T17:43:18+03:00

## API Description

Allows clients to look up NPR member station information

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### List stations close to you or filter by search criteria

> This endpoint has two main use cases:<br/>
> <br/>
> - If no query parameters passed in, it returns a list of stations that are geographically closest to the calling client (based on GeoIP information)<br/>
> - If one or more query parameters are passed in, it performs a search of NPR stations that match those search criteria (not taking into account the client's physical location)<br/>
> <br/>
> Clients wanting to implement a 'Change Station' UI should use this endpoint to power their search. In most cases, you'll want to build a search interface that uses one of the 3 provided schemas: `lat` and `lon` (using e.g. the HTML5 Geolocation API), `city` and `state`, _or_ the generic `q` query which can accept a station name, call letters, network name, or zip code. Technically speaking, `q` can also take in either a city name or a state name, but using the `city` and `state` parameters together will yield more accurate geographic search results than `q={cityName}`.<br/>
> <br/>
> The `lat` and `lon` query parameters should always be passed in together (otherwise the API will return a 400 error), and if included in the query, they will take precedence over any other search criteria; that is, `lat` and `lon` will do a purely geographic search and not take into account `q`, `city` or `state`.<br/>
> <br/>
> Similarly, `city` and/or `state` will take precedence over (and ignore) `q`.<br/>
> <br/>
> If clients want to be able to offer multiple types of searches (e.g. 'Search for a station name, city or zipcode') using a *single* search input form, `q` should be used. But again, be aware that using `city` and `state` together will yield more accurate search results than `q={cityName}`.

*Tags:* `stationfinder`

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `q` - _optional_ - Search terms to search on; can be a station name, network name, call letters, or zipcode
* `city` - _optional_ - A city to look for stations from; intended to be paired with `state`
* `state` - _optional_ - A state to look for stations from (using the 2-letter abbreviation); intended to be paired with `city`
* `lat` - _optional_ - A latitude value from a geographic coordinate system; only works if paired with `lon`
* `lon` - _optional_ - A longitude value from a geographic coordinate system; only works if paired with `lat`

### Retrieve metadata for the station with the given numeric ID

> This endpoint retrieves information about a given station, based on its numeric ID, which is consistent across all of NPR's APIs.<br/>
> <br/>
> A typical use case for this data is for clients who want to create a dropdown menu, modal/pop-up or dedicated page displaying more information about the station the client is localized to, including, for example, links to the station's homepage and donation (pledge) page.

*Tags:* `stationfinder`

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `stationId` - _required_ - The numeric ID of a station

## License

**flow**ground :- Telekom iPaaS / npr-org-station-finder-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
