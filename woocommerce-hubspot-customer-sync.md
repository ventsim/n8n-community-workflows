# Sync WooCommerce Customers to HubSpot Automatically 🔄

Automatically synchronize WooCommerce customer data with HubSpot contacts in real-time or scheduled batches.

## Who Is This For?

- E-commerce store owners using WooCommerce
- Marketing teams needing customer data in HubSpot
- Businesses wanting automated customer relationship management
- Teams managing multiple WooCommerce stores

## What Does This Workflow Solve?

- 🔄 **Automates customer synchronization** between WooCommerce and HubSpot
- ⚡ **Real-time updates** via webhooks for immediate contact creation
- 📊 **Batch processing** for existing customer migration
- 🎯 **Smart duplicate handling** prevents contact duplication
- 🏷️ **Origin tracking** identifies which store customers came from
- 🔧 **Configurable updates** control whether existing contacts get updated

## Setup Guide

### Prerequisites
- WooCommerce store with API access
- HubSpot account with API permissions
- Custom HubSpot contact properties (if using origin tracking)

### Step-by-Step Configuration

1. **Configure Credentials**
   - Set up WooCommerce API credentials
   - Configure HubSpot App Token or OAuth2 credentials

2. **Choose Trigger Method**
   - **Real-time**: Activate WooCommerce webhook trigger
   - **Scheduled**: Set up schedule trigger for batch processing
   - **Manual**: Use manual trigger for one-time syncs

3. **Workflow Configuration**
   - Set `sync_origin_metadata`: Enable/disable WooCommerce domain tracking
   - Set `update_existing_contacts`: Control whether to update existing contacts
   - Set `notifications`: Enable/disable workflow notifications

4. **Field Mapping**
   - Verify WooCommerce → HubSpot field mappings
   - Add custom properties in HubSpot if needed

## Requirements

- **WooCommerce API Credentials** (Consumer Key & Secret)
- **HubSpot API Credentials** (App Token or OAuth2)
- **Custom HubSpot Properties** (for origin tracking)
- **n8n Workflow Access**

## How to Customize the Workflow

- **Multiple Stores**: Duplicate workflow and change domain/credentials
- **Custom Fields**: Add additional WooCommerce → HubSpot field mappings
- **Notifications**: Replace placeholder nodes with email, Slack, or other notification methods
- **Error Handling**: Customize error logging and alerting
- **Batch Size**: Adjust pagination settings for large customer databases

This workflow provides both real-time synchronization for new customers and batch processing for existing customer migration, making it ideal for e-commerce businesses looking to streamline their CRM integration.