# SaaS User Behavior SQL Codebook

---

## Overview

This codebook defines the schema used in the SaaS User Behavior Analysis project. It documents tables and fields across accounts, subscriptions, feature usage, and churn events.

---

## 1. ACCOUNTS Table

Stores account-level information for each customer.

| Column | Description |
|------|-------------|
| account_id | Unique identifier for each account |
| account_name | Name of the customer account or organization |
| industry | Industry category of the account |
| country | Geographic location of the account |
| signup_date | Date the account was created |
| referral_source | Channel through which the user was acquired |
| plan_tier | Current subscription tier of the account |
| seats | Number of seats/licenses associated with the account |
| is_trial | Indicates whether the account is in trial state |
| churn_flag | Indicates whether the account has churned |

---

## 2. SUBSCRIPTIONS Table

Tracks subscription lifecycle and billing information.

| Column | Description |
|------|-------------|
| subscription_id | Unique identifier for each subscription |
| account_id | Reference to the associated account |
| start_date | Subscription start date |
| end_date | Subscription end date (if applicable) |
| plan_tier | Subscription plan level |
| seats | Number of seats included in subscription |
| mrr_amount | Monthly recurring revenue per account |
| arr_amount | Annual recurring revenue per account |
| is_trial | Indicates whether subscription is a trial |
| upgrade_flag | Indicates if subscription was upgraded |
| downgrade_flag | Indicates if subscription was downgraded |
| churn_flag | Indicates whether subscription ended due to churn |
| billing_frequency | Billing cycle (monthly, yearly, etc.) |
| auto_renew_flag | Indicates whether subscription auto-renews |

---

## 3. FEATURE USAGE Table

Captures product interaction events at feature level.

| Column | Description |
|------|-------------|
| usage_id | Unique identifier for each usage event |
| subscription_id | Reference to subscription tied to usage |
| usage_date | Date of feature interaction |
| feature_name | Name of the feature used |
| usage_count | Number of times a feature was used in a session/day |
| usage_duration_secs | Time spent using the feature |
| error_count | Number of errors encountered during usage |
| is_beta_feature | Indicates whether the feature is in beta |

---

## 4. CHURN EVENTS Table

Captures churn-related events and behavioral signals around exit.

| Column | Description |
|------|-------------|
| churn_event_id | Unique identifier for churn event |
| account_id | Reference to the associated account |
| churn_date | Date when churn occurred |
| reason_code | Coded reason for churn (if available) |
| refund_amount_usd | Refund amount issued at churn (if applicable) |
| preceding_upgrade_flag | Indicates if an upgrade occurred before churn |
| preceding_downgrade_flag | Indicates if a downgrade occurred before churn |
| is_reactivation | Indicates if the account reactivated after churn |

---

## Notes

- All tables are connected through `account_id` and `subscription_id`
- Feature usage represents granular behavioral interaction data
- Churn events capture both behavioral and financial exit signals

---

## Future Extension

Support ticket and feedback data can be added in future iterations to analyze sentiment-driven churn and customer experience signals.
