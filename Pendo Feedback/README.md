# Indexing Pendo Feedback (formerly Receptive.io) using the Coveo REST API connector

This guide explains how you can use the content of the [`SourceJSONConfig.json`](SourceJSONConfig.json) file in a [REST API source](https://docs.coveo.com/en/1896/) to index features and feature comments. Your Coveo source will use this JSON configuration to customize HTTP requests for the Pendo Feedback API and identify the specific content to extract from the responses.

## Advisory

When [adding a source of content](https://docs.coveo.com/en/3390/index-content/add-or-edit-a-source#add-a-source) in the [Coveo Administration Console](https://docs.coveo.com/en/1841/), Coveo may recommend, or not recommend, using a Coveo [REST API](https://docs.coveo.com/en/1896/) or [GraphQL API](https://docs.coveo.com/en/n6gh2329/) source along with the associated example JSON configuration from this library. Coveo’s recommendation depends on the extent of testing of the system example configuration in proofs of concept.

However, please note that all configurations in this library, including those recommended in the Coveo Administration Console, aren't actively maintained or officially supported. Consider them as starting points that will require adjustments to fit your specific use case.

## Prerequisites

To fully understand and effectively use the example JSON configuration, you must:
- Have a [Coveo organization](https://docs.coveo.com/en/185).
- Learn about [Coveo connectivity](https://docs.coveo.com/en/1702).
- Learn [how to configure a REST API source](https://docs.coveo.com/en/1896/).

## Instructions

1. [Get a Pendo Feeback API key](https://support.pendo.io/hc/en-us/articles/14541867340571-Pendo-Feedback-API-Key).
2. [Create a REST API source](https://docs.coveo.com/en/1896/) and, in the **Authorization** section, provide the API key obtained in step 1.
3. Use the example in [`SourceJSONConfig.json`](https://github.com/coveooss/connectivity-library/blob/master/Pendo%20Feedback/SourceJSONConfig.json) as a base to build your source JSON configuration. Adjust it to your own needs.
4. Make sure you've changed all placeholders in the configuration with your own values.
5. [Create the appropiate fields and mappings](https://docs.coveo.com/en/1896/#completion).
6. Check whether your source indexes the desired content properly. You might find you need an additional [indexing pipeline extension](https://docs.coveo.com/en/1645/) to achieve the expected result.

## Pendo Feedback API specifics

* [API Documentation](https://feedbackapi.pendo.io/)
* Retrieving feature views and vote counts from the API requires retrieving the individual features in a sub query. This is not optimal. Therefore, if you don't need the view count in the search results, you can omit the sub queries.
You can use the sub query if you need additional data from features. Just add the metadata fields that are missing.
* In the example JSON configuration, private Feedback and private comments are ignored. You can remove the  `IndexingAction` if you want to include `private` items.
* You can view example Pendo API JSON responses for feature and comment calls in [`PendoApiResponseExamples.md`](./PendoApiResponseExamples.md).

## Reference

[Pendo Feedback API documentation](https://engageapi.pendo.io/?bash)
