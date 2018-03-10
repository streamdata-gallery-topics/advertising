---
swagger: "2.0"
info:
  title: Google Doubleclick Merged API
  version: 1.0.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /userprofiles/{profileId}/floodlightActivityGroups:
    get:
      summary: Get Floodlight Activity Groups
      description: Retrieves a list of floodlight activity groups, possibly filtered
      operationId: dfareporting.floodlightActivityGroups.list
      parameters:
      - in: query
        name: advertiserId
        description: Select only floodlight activity groups with the specified advertiser
          ID
      - in: query
        name: floodlightConfigurationId
        description: Select only floodlight activity groups with the specified floodlight
          configuration ID
      - in: query
        name: ids
        description: Select only floodlight activity groups with the specified IDs
      - in: query
        name: maxResults
        description: Maximum number of results to return
      - in: query
        name: pageToken
        description: Value of the nextPageToken from the previous result page
      - in: path
        name: profileId
        description: User profile ID associated with this request
      - in: query
        name: searchString
        description: Allows searching for objects by name or ID
      - in: query
        name: sortField
        description: Field by which to sort the list
      - in: query
        name: sortOrder
        description: Order of sorted results, default is ASCENDING
      - in: query
        name: type
        description: Select only floodlight activity groups with the specified floodlight
          activity group type
      responses:
        200:
          description: OK
      tags:
      - advertising
      - floodlight activity group
definitions: []
x-collection-name: Google Doubleclick
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---