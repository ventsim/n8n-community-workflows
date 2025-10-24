# WooCommerce-HubSpot Customer Sync - Sticky Notes

## Yellow Sticky Note (Main Explanation)

**Template Purpose**: Automatically synchronize WooCommerce customer data with HubSpot contacts

**High-Level Functionality**:
- Real-time customer creation via webhooks
- Batch customer synchronization via polling
- Smart duplicate detection and handling
- Configurable update behavior for existing contacts
- Multi-store support with origin tracking

**Key Features**:
- 🔄 Dual trigger support (webhook + scheduled)
- 🎯 Email-based contact matching
- 🏷️ Origin site tracking for multi-store setups
- ⚙️ Configurable update behavior
- 🔔 Optional notifications
- 🛡️ Error handling and logging

## White Sticky Notes (Node Explanations)

### Trigger Section
**WooCommerce Trigger**: Listens for new customer creation events via webhook
**Schedule Trigger**: Runs batch synchronization on a defined schedule
**Manual Trigger**: Allows manual execution for testing or one-time syncs

### Configuration Section
**Conf Node**: Central configuration hub with three main settings:
- `sync_origin_metadata`: Enable/disable WooCommerce domain tracking
- `update_existing_contacts`: Control whether to update existing contacts
- `notifications`: Enable/disable workflow notifications

### Data Processing Section
**Set Domain**: Configures the WooCommerce site domain for batch processing
**Extract customer origin and ID**: Processes webhook data to extract customer information
**Get all WooCommerce customers**: Paginates through all customers for batch sync

### Contact Matching Section
**Lookup in hubspot by email**: Checks if contact already exists in HubSpot
**Contact Exists**: Routes data based on contact existence
**Merge**: Combines webhook and polling data streams

### Batch Processing Section
**Split Out Customers**: Separates customer data for processing
**Extract email list**: Collects all customer emails for bulk lookup
**Lookup emails in hubspot contacts**: Bulk search for existing contacts
**Split out matching contacts**: Separates existing vs new contacts

### Contact Management Section
**Keep New Contacts**: Routes only new contacts for creation
**Keep Existing Contacts**: Routes existing contacts for potential updates
**Update Existing Contacts enabled**: Controls whether to update existing contacts
**Has Email**: Validates customer has email before processing

### HubSpot Integration Section
**Create or update a Contact**: Main HubSpot contact creation/update node
**If Custom Properties enabled**: Conditional logic for origin tracking
**Update Contacts with Origin Site**: Adds WooCommerce origin metadata

### Error Handling Section
**Error Details**: Captures and formats error information for logging
**Loop Over New Customers**: Processes contacts in batches to manage API limits

## Blue Sticky Notes (Credentials Configuration)

### WooCommerce Credentials
**Configuration**:
- Authentication: Predefined Credential Type
- Credential Type: WooCommerce API
- Required: Consumer Key and Consumer Secret
- Scope: Read customer data

**Setup**:
1. Generate API keys in WooCommerce settings
2. Create credential in n8n with key and secret
3. Assign to WooCommerce trigger and HTTP request nodes

### HubSpot Credentials
**Configuration**:
- Authentication: App Token or OAuth2
- Credential Type: HubSpot App Token / HubSpot OAuth2 API
- Required: App Token or OAuth2 credentials
- Scope: Contact read/write permissions

**Setup**:
1. Create private app in HubSpot or configure OAuth2
2. Generate app token or set up OAuth2 integration
3. Assign to HubSpot nodes and HTTP request nodes

### Custom Properties Setup
**Required for Origin Tracking**:
- `origin_site`: Text property for WooCommerce domain
- `origin_id`: Text property for WooCommerce customer ID

**Setup**:
1. Create custom properties in HubSpot contact object
2. Ensure property names match workflow configuration
3. Test with sample data to verify mapping