---
title: Azure SDK for Python (February 2020)
layout: post
date: February 2020
tags: python
sidebar: releases_sidebar
repository: azure/azure-sdk-for-python
---

The Azure SDK team is pleased to make available the February 2020 client library GA release. 

This release includes the following:

#### GA
- Storage (Blobs, File shares)

#### Preview

Text Analytics
Storage (DataLake)


## Installation Instructions

To install the latest preview version of the packages, copy and paste the following commands into a terminal:

```bash
pip install azure-appconfiguration
pip install --pre azure-eventhub
pip install --pre azure-eventhub-checkpointstoreblob-aio
pip install azure-storage-blob
pip install --pre azure-storage-file-datalake
pip install azure-storage-file-share
pip install azure-keyvault-certificates
pip install azure-keyvault-keys
pip install azure-keyvault-secrets
pip install azure-identity
pip install --pre azure-ai-textanalytics
```

## Feedback

If you have a bug or feature request for one of the libraries, please post an issue to [GitHub](https://github.com/azure/azure-sdk-for-python/issues).

## Changelog

Detailed change logs are linked to in the Quick Links below. Here are some critical call outs.


### Identity

- `ClientCertificateCredential` supports password-protected certificates.
- Added `CredentialUnavailableError` to distinguish cases when failure to obtain a token was expected. For example, `EnvironmentCredential.get_token()` will raise this error when environment variable configuration is incomplete.

### Key Vault

- This release contains bug fixes to improve quality.

### Storage

#### azure-storage-blob
- Added `api_version` parameter for all clients.
- Added support for encryption scopes that that could be used to encrypt blob content.
- Added `get_page_range_diff_for_managed_disk` API which returns the list of valid page ranges diff between a snapshot and managed disk or another snapshot.
#### azure-storage-file-share
- Added support for the 2019-07-07 service version, and added `api_version` parameter to clients.
- `ShareLeaseClient` was introduced to both sync and async versions of the SDK, which allows users to perform operations on file leases.
- `failed_handles_count` info was included in `close_handle` and `close_all_handles` result.
- Added support for obtaining premium file properties in `list_shares` and `get_share_properties`.
- Added support for additional `start_copy_from_url` parameters - `file_permission`, `permission_key`, `file_attributes`, `file_creation_time`, `file_last_write_time`, `ignore_read_only`, and `set_archive_attribute`.
- clear_range is working.
#### azure-storage-file-datalake
- azure-storage-file-datalake supports async APIs.

### Text Analytics [Changelog](https://github.com/Azure/azure-sdk-for-python/blob/master/sdk/textanalytics/azure-ai-textanalytics/CHANGELOG.md#100b2-2020-02-11)

- The single text, module-level operations have been removed from the client library.  Use the batching methods for optimal performance in production environments.
- New credential class `TextAnalyticsApiKeyCredential("<api_key>")` must be used if authenticating with an API key. It provides an `update_key()` method which allows you to update the API key for long-lived clients. Passing the API key as a string is no longer supported.
- The `TextAnalyticsError` model has been simplified to an object with only `code`, `message`, and `target` attributes.
- `__repr__` has been added to all of the response objects.
- An `AttributeError` with custom error message is now raised if you try to access a result attribute on a `DocumentError` object.


## Latest Releases

{% assign packages = site.data.releases.latest.python-packages %}
{% include python-packages.html %}

{% include refs.md %}
