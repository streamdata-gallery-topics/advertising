---
swagger: "2.0"
x-collection-name: Google Adsense
x-complete: 0
info:
  title: Google Adsense API Get Ad Clients
  version: 1.0.0
  description: List all hosted ad clients in the specified hosted account.
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /accounts:
    get:
      summary: Get Accounts
      description: List hosted accounts associated with this AdSense account by ad
        client id.
      operationId: adsensehost.accounts.list
      x-api-path-slug: accounts-get
      parameters:
      - in: query
        name: filterAdClientId
        description: Ad clients to list accounts for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /accounts/{accountId}:
    get:
      summary: Get Account
      description: Get information about the selected associated AdSense account.
      operationId: adsensehost.accounts.get
      x-api-path-slug: accountsaccountid-get
      parameters:
      - in: path
        name: accountId
        description: Account to get information about
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /accounts/{accountId}/adclients:
    get:
      summary: Get Ad Clients
      description: List all hosted ad clients in the specified hosted account.
      operationId: adsensehost.accounts.adclients.list
      x-api-path-slug: accountsaccountidadclients-get
      parameters:
      - in: path
        name: accountId
        description: Account for which to list ad clients
      - in: query
        name: maxResults
        description: The maximum number of ad clients to include in the response,
          used for paging
      - in: query
        name: pageToken
        description: A continuation token, used to page through ad clients
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Clients
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