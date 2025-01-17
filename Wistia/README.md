# Indexing Wistia using the Coveo REST API connector

This guide explains how you can use the content of the [`SourceJSONConfig.json`](SourceJSONConfig.json) file in a [REST API source](https://docs.coveo.com/en/1896/) to index projects and videos. Your Coveo source will use this JSON configuration to customize HTTP requests for the Wistia v1 API and identify the specific content to extract from the responses.

## Advisory

When [adding a source of content](https://docs.coveo.com/en/3390/index-content/add-or-edit-a-source#add-a-source) in the [Coveo Administration Console](https://docs.coveo.com/en/1841/), Coveo may recommend, or not recommend, using a Coveo [REST API](https://docs.coveo.com/en/1896/) or [GraphQL API](https://docs.coveo.com/en/n6gh2329/) source along with the associated example JSON configuration from this library. Coveo’s recommendation depends on the extent of testing of the system example configuration in proofs of concept.

However, please note that all configurations in this library, including those recommended in the Coveo Administration Console, aren't actively maintained or officially supported. Consider them as starting points that will require adjustments to fit your specific use case.

## Prerequisites

To fully understand and effectively use the example JSON configuration, you must:
- Have a [Coveo organization](https://docs.coveo.com/en/185).
- Learn about [Coveo connectivity](https://docs.coveo.com/en/1702).
- Learn [how to configure a REST API source](https://docs.coveo.com/en/1896/).

## Instructions

1. Obtain crawling credentials: [The Wistia API](https://wistia.com/support/developers/data-api) supports either Basic Authentication or an access_token API Key. The API key can be found in the API Access section from your account settings.
2. [Create a REST API source](https://docs.coveo.com/en/1896/) and, in the **Authorization** section, fill in you username and the API key obtained in step 1. as the password.
3. Use the example in [`SourceJSONConfig.json`](SourceJSONConfig.json) as a base to build your source JSON configuration. Adjust it to your own needs. Wistia maintains a parent/child relationship between Project and Media objects, this leads to a single endpoint to index projects along with SubItem queries to indexed the related media objects.
4. [Create the appropiate fields and mappings](https://docs.coveo.com/en/1896/#completion).
5. Check whether your source indexes the desired content properly. You might find you need an [indexing pipeline extension](https://docs.coveo.com/en/1645/) to achieve the expected result.

## Reference

[Wistia API documentation](https://wistia.com/support/developers/data-api)
