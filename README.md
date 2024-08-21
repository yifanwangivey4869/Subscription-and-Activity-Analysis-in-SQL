# SQL Script: Subscription and Activity Analysis

## Overview

This SQL script is designed to retrieve and analyze subscription data for specific products, along with the latest activity data (e.g., phone calls) associated with each company. The script calculates the latest subscriptions and the most recent customer interaction (activity) for each company, allowing for detailed analysis of subscription lifecycles and customer engagement.

## Key Components

1. **Start Date Calculation**:
   - The script begins by calculating the last Saturday's date, which is used as a reference (`@StartDate`) for filtering subscriptions.

2. **Latest Subscriptions Extraction**:
   - The `LatestSubscriptions` CTE (Common Table Expression) is used to select the most recent subscription information for each company.
   - The subscription data includes information such as the `CompanyId`, `Product`, `StartDate`, `EndDate`, and pricing details.
   - The logic ensures that the subscription’s end date accounts for potential cancellation dates.

3. **Activity Data Retrieval**:
   - The `Activity` CTE retrieves the most recent phone call activities for each company from the CRM system.
   - The activities are ranked to ensure only the latest activity is selected.

4. **Final Data Selection**:
   - The main `SELECT` statement combines the latest subscription data with the most recent activity data.
   - It joins the `LatestSubscriptions` with the `Activity` data on `CompanyId`, providing a comprehensive view of each company’s latest subscription details alongside their most recent customer interaction.

## Input Parameters

- **@StartDate**: The script calculates this date as the last Saturday before the current date.

## Key Fields in the Output

- **CompanyId**: Unique identifier for the company.
- **Product**: The product associated with the subscription (e.g., 'VHR', 'VHR Verified').
- **SubscriptionId**: Unique identifier for the subscription.
- **StartDate**: The start date of the subscription.
- **EndDate**: The calculated end date of the subscription, considering potential cancellations.
- **monthlyprice**: The monthly price associated with the subscription.
- **hasicbcsubscription**: Indicates whether the subscription is part of an ICBC bundle.
- **SubscriptionProductBundleId**: Identifier for the product bundle associated with the subscription.
- **LastTouchDescription**: Description of the most recent activity.
- **LastTouchDate**: Date of the most recent activity.

## Usage

1. **Data Retrieval**:
   - Run the script in an environment connected to the relevant databases to retrieve the most recent subscription and activity data for each company.

2. **Analysis**:
   - Use the output to analyze subscription trends, evaluate customer engagement, and identify potential areas for intervention based on the timing and type of recent activities.

## Dependencies

- The script relies on specific database schemas and tables like `Subscription`, `SubscriptionProduct`, `SubscriptionProductType`, `FilteredAccount`, and `FilteredPhoneCall`. Ensure these tables and schemas are accessible in your database environment.

## Author
- Yifan Wang

## Contact
- Email: [yifanwang.msc2024@ivey.ca](mailto:yifanwang.msc2024@ivey.ca)
- LinkedIn: [linkedin.com/in/yifanwang4869](https://linkedin.com/in/yifanwang4869)
