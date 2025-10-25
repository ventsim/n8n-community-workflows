# Sync WooCommerce Customers to HubSpot Contacts Automatically

## Who Is This For?

This workflow is designed for e-commerce businesses using WooCommerce who want to:
- Automatically sync customer data to HubSpot CRM
- Maintain accurate customer records across platforms
- Support multi-store setups with origin tracking
- Reduce manual data entry and improve marketing efficiency

## What Does This Workflow Solve?

- **Automates customer data sync** 🤖 - Eliminates manual copying between WooCommerce and HubSpot
- **Real-time synchronization** ⚡ - New customers appear in HubSpot immediately via webhooks
- **Smart duplicate handling** 🎯 - Prevents duplicate contacts using email-based matching
- **Multi-store support** 🏪 - Tracks which WooCommerce store each contact originated from
- **Configurable updates** ⚙️ - Choose whether to update existing contacts or only create new ones
- **Error handling** 🛡️ - Gracefully handles API failures and provides detailed error information

## Setup Guide

### Prerequisites
1. WooCommerce store with API access enabled
2. HubSpot account with appropriate permissions
3. n8n instance with internet access

### Step-by-Step Configuration

**1. Configure Credentials**
- Set up WooCommerce API credentials in the "Get all WooCommerce customers" node
- Configure HubSpot App Token or OAuth2 credentials in all HubSpot nodes

**2. Choose Your Trigger Method**
- **Real-time (Recommended)**: Set up WooCommerce webhook for "customer.created" events
- **Scheduled**: Configure the Schedule Trigger for periodic syncs (e.g., every 6 hours)
- **Manual**: Use the "Execute workflow" button for on-demand syncs

**3. Configure Workflow Settings**
- In the "Conf" node, set:
  - `sync_origin_metadata`: Enable/disable WooCommerce domain tracking
  - `update_existing_contacts`: Choose whether to update existing HubSpot contacts
  - `notifications`: Enable/disable workflow notifications

**4. Test the Workflow**
- Create a test customer in WooCommerce
- Execute the workflow manually
- Verify the contact appears in HubSpot

## Requirements

- **WooCommerce API Credentials**: Consumer Key and Consumer Secret
- **HubSpot Credentials**: App Token or OAuth2 credentials
- **HubSpot Custom Properties**: Create `origin_site` property if using origin tracking
- **n8n Access**: Working n8n instance with internet connectivity

## How to Customize the Workflow

**Field Mapping**: Modify the "Create or update a Contact" node to map additional WooCommerce fields to HubSpot properties

**Notification Methods**: Replace the placeholder notification nodes with your preferred method (Email, Slack, Teams, etc.)

**Sync Frequency**: Adjust the Schedule Trigger interval based on your needs

**Error Handling**: Customize error logging and alerting based on your monitoring requirements

**Multi-Store Setup**: Duplicate the workflow for additional WooCommerce stores and update domain configurations

This workflow provides a robust foundation for keeping your WooCommerce customer data synchronized with HubSpot, ensuring your marketing and sales teams always have access to the latest customer information.