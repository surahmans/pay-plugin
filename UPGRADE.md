# Upgrade guide

- [Upgrading to 1.1 from 1.0](#upgrade-1.1)

There are some housekeeping items that have been addressed in this version.

The `InvoiceStatus::getByCode` method has been renamed to `InvoiceStatus::findByCode`.

These methods have been removed from the `InvoiceStatus` model:

- getStatusDraft
- getStatusApproved
- getStatusPaid
- getStatusVoid

Use the `findByCode` method instead, eg:

    InvoiceStatus::findByCode(InvoiceStatus::STATUS_DRAFT)

##### Updates to Offline, Skrill and Paypal Standard gateway partials

The `getFormAction`, `getHiddenFields` and `getPaymentInstructions` methods no longer take the host as the first name as this argument is redundant. Perform these replacements in your theme:

    // Replace
    paymentMethod.getFormAction(paymentMethod) 

    // With
    paymentMethod.getFormAction()

    // Replace
    paymentMethod.getHiddenFields(paymentMethod, invoice)

    // With
    paymentMethod.getHiddenFields(invoice)

    // Replace
    paymentMethod.getPaymentInstructions(paymentMethod, invoice)

    // With
    paymentMethod.getPaymentInstructions(invoice)