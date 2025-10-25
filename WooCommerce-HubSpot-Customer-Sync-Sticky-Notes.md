# WooCommerce-HubSpot Customer Sync - Sticky Notes

## Yellow Sticky Note (Main Explanation)

**Template Purpose**: Automatically synchronize WooCommerce customer data with HubSpot contacts

**High-Level Functionality**:
- Real-time customer creation via webhooks
- Batch customer synchronization via polling
- Smart duplicate detection and handling
- Configurable update behavior for existing contacts
- Multi-store support with origin tracking

**Key Features and Benefits**:
- 🔄 Dual trigger support (webhook + scheduled)
- 🎯 Email-based contact matching
- 🏷️ Origin site tracking for multi-store setups
- ⚙️ Configurable update behavior
- 🔔 Optional notifications
- 🛡️ Error handling and logging

## White Sticky Notes (Node Explanations)

### Trigger Section
**How it works**: Multiple trigger options for different use cases
- **Webhook Trigger**: Real-time sync when customers are created in WooCommerce
- **Schedule Trigger**: Periodic sync of all customers
- **Manual Trigger**: On-demand execution
- **Workflow Trigger**: Integration with other workflows

**Configuration**:
- Webhook: Set up WooCommerce webhook for "customer.created" events
- Schedule: Configure interval based on sync frequency needs

### Configuration Node
**How it works**: Central hub for all synchronization settings

**Configuration**:
- `sync_origin_metadata`: Enable/disable WooCommerce domain tracking
- `update_existing_contacts`: Choose update behavior for existing contacts
- `notifications`: Enable/disable workflow notifications

**Technical Details**:
- Create `origin_site` contact property in HubSpot first
- Existing values are preserved (no overwrite)

### Data Processing Section
**How it works**: Processes customer data and handles duplicates

**Key Functions**:
- Extract customer information from WooCommerce
- Look up existing contacts in HubSpot by email
- Separate new vs. existing contacts
- Handle batch processing for large datasets

**Configuration**:
- Adjust batch size based on API limits
- Modify field mappings as needed

### HubSpot Integration
**How it works**: Creates or updates contacts in HubSpot

**Configuration**:
- Map WooCommerce fields to HubSpot properties
- Configure error handling for API failures
- Set up custom properties in HubSpot

**Technical Details**:
- Uses email as primary matching field
- Supports custom property updates
- Handles API rate limiting

## Blue Sticky Notes (Credentials Configuration)

### WooCommerce Credentials
**Configuration Steps**:
1. Generate API credentials in WooCommerce (Consumer Key & Secret)
2. Configure authentication in HTTP Request nodes
3. Test connection with sample requests

**Security**:
- Store credentials securely in n8n
- Use HTTPS for all API calls
- Monitor API usage and limits

### HubSpot Credentials
**Configuration Steps**:
1. Create HubSpot App Token or OAuth2 credentials
2. Configure authentication in HubSpot nodes
3. Set appropriate permissions for contact management

**Security**:
- Use app tokens for server-to-server communication
- Configure OAuth2 for user-level permissions
- Monitor API usage and rate limits

### Domain Configuration
**How it works**: Sets the WooCommerce store domain for API calls

**Configuration**:
- Set the full domain of your WooCommerce website
- For multi-store setups, duplicate workflow and update domains
- Ensure domain format is correct (e.g., www.yourstore.com)

## Additional Notes

### Error Handling
- Detailed error logging for troubleshooting
- Graceful handling of API failures
- Continue processing other records when errors occur

### Performance Optimization
- Batch processing for large customer lists
- Configurable update behavior to reduce API calls
- Smart duplicate detection to prevent unnecessary updates

### Customization Options
- Field mapping between WooCommerce and HubSpot
- Notification methods (email, Slack, etc.)
- Sync frequency and scheduling
- Multi-store configuration