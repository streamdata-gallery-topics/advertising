---
swagger: "2.0"
x-collection-name: Google Doubleclick
x-complete: 0
info:
  title: Google Doubleclick API Update Ad
  version: 1.0.0
  description: Updates an existing ad.
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
      description: Retrieves the authenticated user's list of accounts.
      operationId: adexchangebuyer.accounts.list
      x-api-path-slug: accounts-get
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /accounts/{id}:
    get:
      summary: Get Account
      description: Gets one account by ID.
      operationId: adexchangebuyer.accounts.get
      x-api-path-slug: accountsid-get
      parameters:
      - in: path
        name: id
        description: The account id
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
    patch:
      summary: Update Account
      description: Updates an existing account. This method supports patch semantics.
      operationId: adexchangebuyer.accounts.patch
      x-api-path-slug: accountsid-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: confirmUnsafeAccountChange
        description: Confirmation for erasing bidder and cookie matching urls
      - in: path
        name: id
        description: The account id
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
    put:
      summary: Update Account
      description: Updates an existing account.
      operationId: adexchangebuyer.accounts.update
      x-api-path-slug: accountsid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: confirmUnsafeAccountChange
        description: Confirmation for erasing bidder and cookie matching urls
      - in: path
        name: id
        description: The account id
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /billinginfo:
    get:
      summary: Get Billing Info
      description: Retrieves a list of billing information for all accounts of the
        authenticated user.
      operationId: adexchangebuyer.billingInfo.list
      x-api-path-slug: billinginfo-get
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Billing
  /billinginfo/{accountId}:
    get:
      summary: Get Billing Info
      description: Returns the billing information for one account specified by account
        ID.
      operationId: adexchangebuyer.billingInfo.get
      x-api-path-slug: billinginfoaccountid-get
      parameters:
      - in: path
        name: accountId
        description: The account id
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Billing
  /billinginfo/{accountId}/{billingId}:
    get:
      summary: Get Budget Info
      description: Returns the budget information for the adgroup specified by the
        accountId and billingId.
      operationId: adexchangebuyer.budget.get
      x-api-path-slug: billinginfoaccountidbillingid-get
      parameters:
      - in: path
        name: accountId
        description: The account id to get the budget information for
      - in: path
        name: billingId
        description: The billing id to get the budget information for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Budget
    patch:
      summary: Get Budget Amount
      description: Updates the budget amount for the budget of the adgroup specified
        by the accountId and billingId, with the budget amount in the request. This
        method supports patch semantics.
      operationId: adexchangebuyer.budget.patch
      x-api-path-slug: billinginfoaccountidbillingid-patch
      parameters:
      - in: path
        name: accountId
        description: The account id associated with the budget being updated
      - in: path
        name: billingId
        description: The billing id associated with the budget being updated
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Budget
    put:
      summary: Update Budget Amount
      description: Updates the budget amount for the budget of the adgroup specified
        by the accountId and billingId, with the budget amount in the request.
      operationId: adexchangebuyer.budget.update
      x-api-path-slug: billinginfoaccountidbillingid-put
      parameters:
      - in: path
        name: accountId
        description: The account id associated with the budget being updated
      - in: path
        name: billingId
        description: The billing id associated with the budget being updated
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Budget
  /creatives:
    get:
      summary: Get Creatives
      description: Retrieves a list of the authenticated user's active creatives.
        A creative will be available 30-40 minutes after submission.
      operationId: adexchangebuyer.creatives.list
      x-api-path-slug: creatives-get
      parameters:
      - in: query
        name: accountId
        description: When specified, only creatives for the given account ids are
          returned
      - in: query
        name: buyerCreativeId
        description: When specified, only creatives for the given buyer creative ids
          are returned
      - in: query
        name: dealsStatusFilter
        description: When specified, only creatives having the given deals status
          are returned
      - in: query
        name: maxResults
        description: Maximum number of entries returned on one result page
      - in: query
        name: openAuctionStatusFilter
        description: When specified, only creatives having the given open auction
          status are returned
      - in: query
        name: pageToken
        description: A continuation token, used to page through ad clients
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Creative
    post:
      summary: Submit Creative
      description: Submit a new creative.
      operationId: adexchangebuyer.creatives.insert
      x-api-path-slug: creatives-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Creative
  /creatives/{accountId}/{buyerCreativeId}:
    get:
      summary: Get Creative Status
      description: Gets the status for a single creative. A creative will be available
        30-40 minutes after submission.
      operationId: adexchangebuyer.creatives.get
      x-api-path-slug: creativesaccountidbuyercreativeid-get
      parameters:
      - in: path
        name: accountId
        description: The id for the account that will serve this creative
      - in: path
        name: buyerCreativeId
        description: The buyer-specific id for this creative
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Creative
  /creatives/{accountId}/{buyerCreativeId}/addDeal/{dealId}:
    post:
      summary: Create Deal
      description: Add a deal id association for the creative.
      operationId: adexchangebuyer.creatives.addDeal
      x-api-path-slug: creativesaccountidbuyercreativeidadddealdealid-post
      parameters:
      - in: path
        name: accountId
        description: The id for the account that will serve this creative
      - in: path
        name: buyerCreativeId
        description: The buyer-specific id for this creative
      - in: path
        name: dealId
        description: The id of the deal id to associate with this creative
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /creatives/{accountId}/{buyerCreativeId}/listDeals:
    get:
      summary: List Deals
      description: Lists the external deal ids associated with the creative.
      operationId: adexchangebuyer.creatives.listDeals
      x-api-path-slug: creativesaccountidbuyercreativeidlistdeals-get
      parameters:
      - in: path
        name: accountId
        description: The id for the account that will serve this creative
      - in: path
        name: buyerCreativeId
        description: The buyer-specific id for this creative
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /creatives/{accountId}/{buyerCreativeId}/removeDeal/{dealId}:
    post:
      summary: Remove Deal
      description: Remove a deal id associated with the creative.
      operationId: adexchangebuyer.creatives.removeDeal
      x-api-path-slug: creativesaccountidbuyercreativeidremovedealdealid-post
      parameters:
      - in: path
        name: accountId
        description: The id for the account that will serve this creative
      - in: path
        name: buyerCreativeId
        description: The buyer-specific id for this creative
      - in: path
        name: dealId
        description: The id of the deal id to disassociate with this creative
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /performancereport:
    get:
      summary: Get Performance Report
      description: Retrieves the authenticated user's list of performance metrics.
      operationId: adexchangebuyer.performanceReport.list
      x-api-path-slug: performancereport-get
      parameters:
      - in: query
        name: accountId
        description: The account id to get the reports
      - in: query
        name: endDateTime
        description: The end time of the report in ISO 8601 timestamp format using
          UTC
      - in: query
        name: maxResults
        description: Maximum number of entries returned on one result page
      - in: query
        name: pageToken
        description: A continuation token, used to page through performance reports
      - in: query
        name: startDateTime
        description: The start time of the report in ISO 8601 timestamp format using
          UTC
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Performance Report
  /pretargetingconfigs/{accountId}:
    get:
      summary: Get Pretargeting Configs
      description: Retrieves a list of the authenticated user's pretargeting configurations.
      operationId: adexchangebuyer.pretargetingConfig.list
      x-api-path-slug: pretargetingconfigsaccountid-get
      parameters:
      - in: path
        name: accountId
        description: The account id to get the pretargeting configs for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
    post:
      summary: Update Pretargeting Config
      description: Inserts a new pretargeting configuration.
      operationId: adexchangebuyer.pretargetingConfig.insert
      x-api-path-slug: pretargetingconfigsaccountid-post
      parameters:
      - in: path
        name: accountId
        description: The account id to insert the pretargeting config for
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
  /pretargetingconfigs/{accountId}/{configId}:
    delete:
      summary: Delete Pretargeting Config
      description: Deletes an existing pretargeting config.
      operationId: adexchangebuyer.pretargetingConfig.delete
      x-api-path-slug: pretargetingconfigsaccountidconfigid-delete
      parameters:
      - in: path
        name: accountId
        description: The account id to delete the pretargeting config for
      - in: path
        name: configId
        description: The specific id of the configuration to delete
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
    get:
      summary: Get Pretargeting Config
      description: Gets a specific pretargeting configuration
      operationId: adexchangebuyer.pretargetingConfig.get
      x-api-path-slug: pretargetingconfigsaccountidconfigid-get
      parameters:
      - in: path
        name: accountId
        description: The account id to get the pretargeting config for
      - in: path
        name: configId
        description: The specific id of the configuration to retrieve
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
    patch:
      summary: Update Pretargeting Config
      description: Updates an existing pretargeting config. This method supports patch
        semantics.
      operationId: adexchangebuyer.pretargetingConfig.patch
      x-api-path-slug: pretargetingconfigsaccountidconfigid-patch
      parameters:
      - in: path
        name: accountId
        description: The account id to update the pretargeting config for
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: configId
        description: The specific id of the configuration to update
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
    put:
      summary: Update Pretargeting Config
      description: Updates an existing pretargeting config.
      operationId: adexchangebuyer.pretargetingConfig.update
      x-api-path-slug: pretargetingconfigsaccountidconfigid-put
      parameters:
      - in: path
        name: accountId
        description: The account id to update the pretargeting config for
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: configId
        description: The specific id of the configuration to update
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Pretargeting Config
  /privateauction/{privateAuctionId}/updateproposal:
    post:
      summary: Update Proposal
      description: Update a given private auction proposal
      operationId: adexchangebuyer.marketplaceprivateauction.updateproposal
      x-api-path-slug: privateauctionprivateauctionidupdateproposal-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: privateAuctionId
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /products/search:
    get:
      summary: Search
      description: Gets the requested product.
      operationId: adexchangebuyer.products.search
      x-api-path-slug: productssearch-get
      parameters:
      - in: query
        name: pqlQuery
        description: The pql query used to query for products
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Search
  /products/{productId}:
    get:
      summary: Get Product
      description: Gets the requested product by id.
      operationId: adexchangebuyer.products.get
      x-api-path-slug: productsproductid-get
      parameters:
      - in: path
        name: productId
        description: The id for the product to get the head revision for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Product
  /proposals/insert:
    post:
      summary: Insert Proposal
      description: Create the given list of proposals
      operationId: adexchangebuyer.proposals.insert
      x-api-path-slug: proposalsinsert-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /proposals/search:
    get:
      summary: Search Proposal
      description: Search for proposals using pql query
      operationId: adexchangebuyer.proposals.search
      x-api-path-slug: proposalssearch-get
      parameters:
      - in: query
        name: pqlQuery
        description: Query string to retrieve specific proposals
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /proposals/{proposalId}:
    get:
      summary: Get Proposal
      description: Get a proposal given its id
      operationId: adexchangebuyer.proposals.get
      x-api-path-slug: proposalsproposalid-get
      parameters:
      - in: path
        name: proposalId
        description: Id of the proposal to retrieve
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /proposals/{proposalId}/deals:
    get:
      summary: Get Proposal Deals
      description: List all the deals for a given proposal
      operationId: adexchangebuyer.marketplacedeals.list
      x-api-path-slug: proposalsproposaliddeals-get
      parameters:
      - in: query
        name: pqlQuery
        description: Query string to retrieve specific deals
      - in: path
        name: proposalId
        description: The proposalId to get deals for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /proposals/{proposalId}/deals/delete:
    post:
      summary: Delete Proposal Deal
      description: Delete the specified deals from the proposal
      operationId: adexchangebuyer.marketplacedeals.delete
      x-api-path-slug: proposalsproposaliddealsdelete-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: The proposalId to delete deals from
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /proposals/{proposalId}/deals/insert:
    post:
      summary: Insert Proposal Deal
      description: Add new deals for the specified proposal
      operationId: adexchangebuyer.marketplacedeals.insert
      x-api-path-slug: proposalsproposaliddealsinsert-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: proposalId for which deals need to be added
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /proposals/{proposalId}/deals/update:
    post:
      summary: Update Proposal Deal
      description: Replaces all the deals in the proposal with the passed in deals
      operationId: adexchangebuyer.marketplacedeals.update
      x-api-path-slug: proposalsproposaliddealsupdate-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: The proposalId to edit deals on
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /proposals/{proposalId}/notes:
    get:
      summary: Get Proposal Notes
      description: Get all the notes associated with a proposal
      operationId: adexchangebuyer.marketplacenotes.list
      x-api-path-slug: proposalsproposalidnotes-get
      parameters:
      - in: query
        name: pqlQuery
        description: Query string to retrieve specific notes
      - in: path
        name: proposalId
        description: The proposalId to get notes for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Note
  /proposals/{proposalId}/notes/insert:
    post:
      summary: Insert Proposal Notes
      description: Add notes to the proposal
      operationId: adexchangebuyer.marketplacenotes.insert
      x-api-path-slug: proposalsproposalidnotesinsert-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: The proposalId to add notes for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Note
  /proposals/{proposalId}/setupcomplete:
    post:
      summary: Update Proposal To Complete
      description: Update the given proposal to indicate that setup has been completed.
      operationId: adexchangebuyer.proposals.setupcomplete
      x-api-path-slug: proposalsproposalidsetupcomplete-post
      parameters:
      - in: path
        name: proposalId
        description: The proposal id for which the setup is complete
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /proposals/{proposalId}/{revisionNumber}/{updateAction}:
    patch:
      summary: Update Proposal Revision Number
      description: Update the given proposal. This method supports patch semantics.
      operationId: adexchangebuyer.proposals.patch
      x-api-path-slug: proposalsproposalidrevisionnumberupdateaction-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: The proposal id to update
      - in: path
        name: revisionNumber
        description: The last known revision number to update
      - in: path
        name: updateAction
        description: The proposed action to take on the proposal
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
    put:
      summary: Update Proposal Revision Number
      description: Update the given proposal
      operationId: adexchangebuyer.proposals.update
      x-api-path-slug: proposalsproposalidrevisionnumberupdateaction-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: proposalId
        description: The proposal id to update
      - in: path
        name: revisionNumber
        description: The last known revision number to update
      - in: path
        name: updateAction
        description: The proposed action to take on the proposal
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Proposal
  /publisher/{accountId}/profiles:
    get:
      summary: Get Publish Profiles
      description: Gets the requested publisher profile(s) by publisher accountId.
      operationId: adexchangebuyer.pubprofiles.list
      x-api-path-slug: publisheraccountidprofiles-get
      parameters:
      - in: path
        name: accountId
        description: The accountId of the publisher to get profiles for
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Profile
  /accounts/{accountId}:
    get:
      summary: Get Account
      description: Get information about the selected Ad Exchange account.
      operationId: adexchangeseller.accounts.get
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
      description: List all ad clients in this Ad Exchange account.
      operationId: adexchangeseller.accounts.adclients.list
      x-api-path-slug: accountsaccountidadclients-get
      parameters:
      - in: path
        name: accountId
        description: Account to which the ad client belongs
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
  /accounts/{accountId}/adclients/{adClientId}/customchannels:
    get:
      summary: Get Custom Channels
      description: List all custom channels in the specified ad client for this Ad
        Exchange account.
      operationId: adexchangeseller.accounts.customchannels.list
      x-api-path-slug: accountsaccountidadclientsadclientidcustomchannels-get
      parameters:
      - in: path
        name: accountId
        description: Account to which the ad client belongs
      - in: path
        name: adClientId
        description: Ad client for which to list custom channels
      - in: query
        name: maxResults
        description: The maximum number of custom channels to include in the response,
          used for paging
      - in: query
        name: pageToken
        description: A continuation token, used to page through custom channels
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Channels
  /accounts/{accountId}/adclients/{adClientId}/customchannels/{customChannelId}:
    get:
      summary: Get Custom Channels
      description: Get the specified custom channel from the specified ad client.
      operationId: adexchangeseller.accounts.customchannels.get
      x-api-path-slug: accountsaccountidadclientsadclientidcustomchannelscustomchannelid-get
      parameters:
      - in: path
        name: accountId
        description: Account to which the ad client belongs
      - in: path
        name: adClientId
        description: Ad client which contains the custom channel
      - in: path
        name: customChannelId
        description: Custom channel to retrieve
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Channels
  /accounts/{accountId}/adclients/{adClientId}/urlchannels:
    get:
      summary: Get URL Channels
      description: List all URL channels in the specified ad client for this Ad Exchange
        account.
      operationId: adexchangeseller.accounts.urlchannels.list
      x-api-path-slug: accountsaccountidadclientsadclientidurlchannels-get
      parameters:
      - in: path
        name: accountId
        description: Account to which the ad client belongs
      - in: path
        name: adClientId
        description: Ad client for which to list URL channels
      - in: query
        name: maxResults
        description: The maximum number of URL channels to include in the response,
          used for paging
      - in: query
        name: pageToken
        description: A continuation token, used to page through URL channels
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Channels
  /accounts/{accountId}/alerts:
    get:
      summary: Get Alerts
      description: List the alerts for this Ad Exchange account.
      operationId: adexchangeseller.accounts.alerts.list
      x-api-path-slug: accountsaccountidalerts-get
      parameters:
      - in: path
        name: accountId
        description: Account owning the alerts
      - in: query
        name: locale
        description: The locale to use for translating alert messages
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Alert
  /accounts/{accountId}/metadata/dimensions:
    get:
      summary: Get Dimensions
      description: List the metadata for the dimensions available to this AdExchange
        account.
      operationId: adexchangeseller.accounts.metadata.dimensions.list
      x-api-path-slug: accountsaccountidmetadatadimensions-get
      parameters:
      - in: path
        name: accountId
        description: Account with visibility to the dimensions
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Dimension
  /accounts/{accountId}/metadata/metrics:
    get:
      summary: Get Metrics
      description: List the metadata for the metrics available to this AdExchange
        account.
      operationId: adexchangeseller.accounts.metadata.metrics.list
      x-api-path-slug: accountsaccountidmetadatametrics-get
      parameters:
      - in: path
        name: accountId
        description: Account with visibility to the metrics
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Metric
  /accounts/{accountId}/preferreddeals:
    get:
      summary: Get Preferred Deals
      description: List the preferred deals for this Ad Exchange account.
      operationId: adexchangeseller.accounts.preferreddeals.list
      x-api-path-slug: accountsaccountidpreferreddeals-get
      parameters:
      - in: path
        name: accountId
        description: Account owning the deals
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /accounts/{accountId}/preferreddeals/{dealId}:
    get:
      summary: Get Preferred Deal
      description: Get information about the selected Ad Exchange Preferred Deal.
      operationId: adexchangeseller.accounts.preferreddeals.get
      x-api-path-slug: accountsaccountidpreferreddealsdealid-get
      parameters:
      - in: path
        name: accountId
        description: Account owning the deal
      - in: path
        name: dealId
        description: Preferred deal to get information about
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Deal
  /accounts/{accountId}/reports:
    get:
      summary: Get Reports
      description: Generate an Ad Exchange report based on the report request sent
        in the query parameters. Returns the result as JSON; to retrieve output in
        CSV format specify "alt=csv" as a query parameter.
      operationId: adexchangeseller.accounts.reports.generate
      x-api-path-slug: accountsaccountidreports-get
      parameters:
      - in: path
        name: accountId
        description: Account which owns the generated report
      - in: query
        name: dimension
        description: Dimensions to base the report on
      - in: query
        name: endDate
        description: End of the date range to report on in YYYY-MM-DD format, inclusive
      - in: query
        name: filter
        description: Filters to be run on the report
      - in: query
        name: locale
        description: Optional locale to use for translating report output to a local
          language
      - in: query
        name: maxResults
        description: The maximum number of rows of report data to return
      - in: query
        name: metric
        description: Numeric columns to include in the report
      - in: query
        name: sort
        description: The name of a dimension or metric to sort the resulting report
          on, optionally prefixed with + to sort ascending or - to sort descending
      - in: query
        name: startDate
        description: Start of the date range to report on in YYYY-MM-DD format, inclusive
      - in: query
        name: startIndex
        description: Index of the first row of report data to return
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Report
  /accounts/{accountId}/reports/saved:
    get:
      summary: Get Saved Reports
      description: List all saved reports in this Ad Exchange account.
      operationId: adexchangeseller.accounts.reports.saved.list
      x-api-path-slug: accountsaccountidreportssaved-get
      parameters:
      - in: path
        name: accountId
        description: Account owning the saved reports
      - in: query
        name: maxResults
        description: The maximum number of saved reports to include in the response,
          used for paging
      - in: query
        name: pageToken
        description: A continuation token, used to page through saved reports
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Report
  /accounts/{accountId}/reports/{savedReportId}:
    get:
      summary: Get Saved Report
      description: Generate an Ad Exchange report based on the saved report ID sent
        in the query parameters.
      operationId: adexchangeseller.accounts.reports.saved.generate
      x-api-path-slug: accountsaccountidreportssavedreportid-get
      parameters:
      - in: path
        name: accountId
        description: Account owning the saved report
      - in: query
        name: locale
        description: Optional locale to use for translating report output to a local
          language
      - in: query
        name: maxResults
        description: The maximum number of rows of report data to return
      - in: path
        name: savedReportId
        description: The saved report to retrieve
      - in: query
        name: startIndex
        description: Index of the first row of report data to return
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Report
  /reports/{reportId}/files/{fileId}:
    get:
      summary: Get Report
      description: Retrieves a report file by its report ID and file ID.
      operationId: dfareporting.files.get
      x-api-path-slug: reportsreportidfilesfileid-get
      parameters:
      - in: path
        name: fileId
        description: The ID of the report file
      - in: path
        name: reportId
        description: The ID of the report
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Report
  /userprofiles:
    get:
      summary: Get User Profiles
      description: Retrieves list of user profiles for a user.
      operationId: dfareporting.userProfiles.list
      x-api-path-slug: userprofiles-get
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
  /userprofiles/{profileId}:
    get:
      summary: Get User Profile
      description: Gets one user profile by ID.
      operationId: dfareporting.userProfiles.get
      x-api-path-slug: userprofilesprofileid-get
      parameters:
      - in: path
        name: profileId
        description: The user profile ID
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
  /userprofiles/{profileId}/accountActiveAdSummaries/{summaryAccountId}:
    get:
      summary: Get Account Active Ad Summary
      description: Gets the account's active ad summary by account ID.
      operationId: dfareporting.accountActiveAdSummaries.get
      x-api-path-slug: userprofilesprofileidaccountactiveadsummariessummaryaccountid-get
      parameters:
      - in: path
        name: profileId
        description: User profile ID associated with this request
      - in: path
        name: summaryAccountId
        description: Account ID
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Ad
  /userprofiles/{profileId}/accountPermissionGroups:
    get:
      summary: Get Account Permission Groups
      description: Retrieves the list of account permission groups.
      operationId: dfareporting.accountPermissionGroups.list
      x-api-path-slug: userprofilesprofileidaccountpermissiongroups-get
      parameters:
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Permissions Group
  /userprofiles/{profileId}/accountPermissionGroups/{id}:
    get:
      summary: Get Account Permission Group
      description: Gets one account permission group by ID.
      operationId: dfareporting.accountPermissionGroups.get
      x-api-path-slug: userprofilesprofileidaccountpermissiongroupsid-get
      parameters:
      - in: path
        name: id
        description: Account permission group ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Permissions Group
  /userprofiles/{profileId}/accountPermissions:
    get:
      summary: Get Account Permissions
      description: Retrieves the list of account permissions.
      operationId: dfareporting.accountPermissions.list
      x-api-path-slug: userprofilesprofileidaccountpermissions-get
      parameters:
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Permissions
  /userprofiles/{profileId}/accountPermissions/{id}:
    get:
      summary: Get Account Permissions
      description: Gets one account permission by ID.
      operationId: dfareporting.accountPermissions.get
      x-api-path-slug: userprofilesprofileidaccountpermissionsid-get
      parameters:
      - in: path
        name: id
        description: Account permission ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Permissions
  /userprofiles/{profileId}/accountUserProfiles:
    get:
      summary: Get Account Users
      description: Retrieves a list of account user profiles, possibly filtered. This
        method supports paging.
      operationId: dfareporting.accountUserProfiles.list
      x-api-path-slug: userprofilesprofileidaccountuserprofiles-get
      parameters:
      - in: query
        name: active
        description: Select only active user profiles
      - in: query
        name: ids
        description: Select only user profiles with these IDs
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
        description: Allows searching for objects by name, ID or email
      - in: query
        name: sortField
        description: Field by which to sort the list
      - in: query
        name: sortOrder
        description: Order of sorted results, default is ASCENDING
      - in: query
        name: subaccountId
        description: Select only user profiles with the specified subaccount ID
      - in: query
        name: userRoleId
        description: Select only user profiles with the specified user role ID
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
    patch:
      summary: Update Account User
      description: Updates an existing account user profile. This method supports
        patch semantics.
      operationId: dfareporting.accountUserProfiles.patch
      x-api-path-slug: userprofilesprofileidaccountuserprofiles-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: id
        description: User profile ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
    post:
      summary: Add Account User
      description: Inserts a new account user profile.
      operationId: dfareporting.accountUserProfiles.insert
      x-api-path-slug: userprofilesprofileidaccountuserprofiles-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
    put:
      summary: Update Account User
      description: Updates an existing account user profile.
      operationId: dfareporting.accountUserProfiles.update
      x-api-path-slug: userprofilesprofileidaccountuserprofiles-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
  /userprofiles/{profileId}/accountUserProfiles/{id}:
    get:
      summary: Get Account User
      description: Gets one account user profile by ID.
      operationId: dfareporting.accountUserProfiles.get
      x-api-path-slug: userprofilesprofileidaccountuserprofilesid-get
      parameters:
      - in: path
        name: id
        description: User profile ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - User
  /userprofiles/{profileId}/accounts:
    get:
      summary: Get Accounts
      description: Retrieves the list of accounts, possibly filtered. This method
        supports paging.
      operationId: dfareporting.accounts.list
      x-api-path-slug: userprofilesprofileidaccounts-get
      parameters:
      - in: query
        name: active
        description: Select only active accounts
      - in: query
        name: ids
        description: Select only accounts with these IDs
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
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
    patch:
      summary: Update Account
      description: Updates an existing account. This method supports patch semantics.
      operationId: dfareporting.accounts.patch
      x-api-path-slug: userprofilesprofileidaccounts-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: id
        description: Account ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
    put:
      summary: Update Account
      description: Updates an existing account.
      operationId: dfareporting.accounts.update
      x-api-path-slug: userprofilesprofileidaccounts-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /userprofiles/{profileId}/accounts/{id}:
    get:
      summary: Get Account
      description: Gets one account by ID.
      operationId: dfareporting.accounts.get
      x-api-path-slug: userprofilesprofileidaccountsid-get
      parameters:
      - in: path
        name: id
        description: Account ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Account
  /userprofiles/{profileId}/ads:
    get:
      summary: Get Ads
      description: Retrieves a list of ads, possibly filtered. This method supports
        paging.
      operationId: dfareporting.ads.list
      x-api-path-slug: userprofilesprofileidads-get
      parameters:
      - in: query
        name: active
        description: Select only active ads
      - in: query
        name: advertiserId
        description: Select only ads with this advertiser ID
      - in: query
        name: archived
        description: Select only archived ads
      - in: query
        name: audienceSegmentIds
        description: Select only ads with these audience segment IDs
      - in: query
        name: campaignIds
        description: Select only ads with these campaign IDs
      - in: query
        name: compatibility
        description: Select default ads with the specified compatibility
      - in: query
        name: creativeIds
        description: Select only ads with these creative IDs assigned
      - in: query
        name: creativeOptimizationConfigurationIds
        description: Select only ads with these creative optimization configuration
          IDs
      - in: query
        name: dynamicClickTracker
        description: Select only dynamic click trackers
      - in: query
        name: ids
        description: Select only ads with these IDs
      - in: query
        name: landingPageIds
        description: Select only ads with these landing page IDs
      - in: query
        name: maxResults
        description: Maximum number of results to return
      - in: query
        name: overriddenEventTagId
        description: Select only ads with this event tag override ID
      - in: query
        name: pageToken
        description: Value of the nextPageToken from the previous result page
      - in: query
        name: placementIds
        description: Select only ads with these placement IDs assigned
      - in: path
        name: profileId
        description: User profile ID associated with this request
      - in: query
        name: remarketingListIds
        description: Select only ads whose list targeting expression use these remarketing
          list IDs
      - in: query
        name: searchString
        description: Allows searching for objects by name or ID
      - in: query
        name: sizeIds
        description: Select only ads with these size IDs
      - in: query
        name: sortField
        description: Field by which to sort the list
      - in: query
        name: sortOrder
        description: Order of sorted results, default is ASCENDING
      - in: query
        name: sslCompliant
        description: Select only ads that are SSL-compliant
      - in: query
        name: sslRequired
        description: Select only ads that require SSL
      - in: query
        name: type
        description: Select only ads with these types
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Ad
    patch:
      summary: Update Ad
      description: Updates an existing ad. This method supports patch semantics.
      operationId: dfareporting.ads.patch
      x-api-path-slug: userprofilesprofileidads-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: id
        description: Ad ID
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Ad
    post:
      summary: Create Ad
      description: Inserts a new ad.
      operationId: dfareporting.ads.insert
      x-api-path-slug: userprofilesprofileidads-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Ad
    put:
      summary: Update Ad
      description: Updates an existing ad.
      operationId: dfareporting.ads.update
      x-api-path-slug: userprofilesprofileidads-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: profileId
        description: User profile ID associated with this request
      responses:
        200:
          description: OK
      tags:
      - Advertising
      - Ad
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