# External ID Keeper

This CiviCRM extension prevents deletion of contacts that have external ID values.

## How it works

* The standard *"CiviCRM: delete contacts"* permission is changed so that users cannot delete contacts that have external ID values.

* A new permission *"CiviCRM External ID Keeper: delete contacts with external ID values"* is added to allow administrators to delete all contacts.

* The "Merge contacts" form will halt the a contact merge if any External ID values are being deleted or overwritten during the merge.

## Setup

1. Install this extension.
1. For users who should not be able to delete any contacts:
    1. Revoke the following permissions:
        * *"CiviCRM: delete contacts"*
        * *"CiviCRM External ID Keeper: delete contacts with external ID values"*
1. For users who should only be able to delete contacts that don't have external ID values:
    1. Grant the *"CiviCRM: delete contacts"* permission.
    1. Revoke the *"CiviCRM External ID Keeper: delete contacts without external ID values"* permission.
1. For users who should be able to delete all contacts, even if they have external ID values:
    1. Grant the following permissions:
        * *"CiviCRM: delete contacts"*
        * *"CiviCRM External ID Keeper: delete contacts with external ID values"*

## Requirements

* CiviCRM 4.7+
* PHP 5.4+

## Limitations

The safeguard which prevents contacts from being deleted is only in place on a couple forms.

This extension effectively prevents loss of "External Identifier" data while...

* clicking the "Delete" or "Delete Permanently" buttons on contact records.
* choosing the "Delete Contacts" or "Delete Permanently" actions from a contact search.
* manually merging two contacts.

But "External Identifier" data can still be lost...

* if contacts are deleted through the API.
* when "force merging" during a batch merge of duplicate contacts.
* when manually editing the "External Identifier" field.
