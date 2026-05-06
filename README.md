# Contentsquare - GTM Tracking Customization Template

A powerful Google Tag Manager template from Contentsquare that enables seamless tracking implementation without any code modifications. Deploy multiple tracking actions with a simple click-and-configure interface.

## Overview

This template streamlines Contentsquare tracking integration by providing a unified configuration interface for all common tracking scenarios. Whether you're tracking artificial pageviews, dynamic variables, or e-commerce events, this template handles the complexity so you can focus on your analytics strategy.

**Brand**: contentsquare-ps  
**Template Type**: Google Tag Manager TAG  
**Container Context**: Web  
**License**: Apache License 2.0

## Features

This template supports six primary tracking actions, each accessible through an intuitive configuration interface:

### 1. **Artificial Pageviews**
Fire custom pageview events with customized query parameters without modifying page code.
- Customize the page URL with query parameters
- Optionally append hash fragments to URLs
- Fall back to default page URLs if no custom query is provided

### 2. **Dynamic Variables**
Send custom key-value pairs to Contentsquare's tracking system as dynamic variables.
- Add multiple dynamic variables in a single tag
- Specify value types (String or Integer)
- Type-safe value handling with automatic conversion

### 3. **Standard Page Events**
Track and fire standard page events for analytics measurement.
- Hard-code event values or use GTM variables
- Simple text-based configuration
- Direct integration with Contentsquare's page event system

### 4. **ETP (Event Trigger Recording - Progressive) Events**
Trigger ETP events for advanced event tracking scenarios.
- Custom ETP event values
- Support for data layer integration
- Automatic event prefix handling

### 5. **ETS (Event Trigger Recording - Standard) Events**
Fire ETS events for comprehensive session recording.
- Custom ETS event values
- Data layer variable support
- Automatic event prefix handling

### 6. **Add to Cart Events**
Track e-commerce add-to-cart actions (requires Contentsquare Merchandising license).
- SKU-based product tracking
- Merchandising integration
- Simple SKU input configuration

## Installation

1. **In Google Tag Manager:**
   - Navigate to **Templates** → **Tag Templates**
   - Click **Create New** or import this template
   - Locate the "Contentsquare - Tracking Customization" template
   - Click to use it in a new tag

2. **Create a Tag:**
   - Add a new tag in your GTM container
   - Select the "Contentsquare - Tracking Customization" template
   - Configure your tracking action (see Configuration below)
   - Save and publish

## Configuration

### Step 1: Select an Action Type

Choose the primary tracking action from the dropdown menu:
- Artificial pageview
- Dynamic variable
- Standard page event
- ETS page event
- ETP page event
- Add to cart

### Step 2: Configure Action-Specific Settings

Each action type has dedicated configuration fields:

#### For Artificial Pageviews
- **Artificial pageview query** (optional): Enter a custom query parameter to append to the page URL
- Leave empty to use the default page path

#### For Dynamic Variables
- **Add dynamic variables table**: 
  - Click "Add new dynamic variable" to add rows
  - **Key**: The variable key name (required)
  - **Value**: The variable value (required, supports GTM variables)
  - **Value Type**: Select "String" or "Integer" for type casting

#### For Standard, ETP, and ETS Page Events
- **Event Value** (required): Enter the event value
  - Supports hard-coded text
  - Use `{{Variable Name}}` syntax for GTM variables from your data layer

#### For Add to Cart
- **SKU** (required): Product SKU to track
- Note: Requires active Contentsquare Merchandising license

## How It Works

The template uses Google Tag Manager's Sandboxed JavaScript environment to interact with Contentsquare's tracking queue (`_uxa`). When a tag fires:

1. **Queue Creation**: Establishes connection to `_uxa` queue
2. **URL Processing**: Extracts page path and hash fragments
3. **Action Routing**: Routes to appropriate tracking function based on selected action type
4. **Data Transformation**: Converts and validates data according to value types
5. **Queue Push**: Sends formatted data to Contentsquare's tracking system
6. **Callback**: Triggers GTM success callback upon completion

### JavaScript API Reference

The template implements the following Contentsquare tracking methods:

| Method | Parameters | Use Case |
|--------|-----------|----------|
| `trackPageview` | `(path: string)` | Fire artificial pageviews |
| `trackDynamicVariable` | `({key: string, value: any})` | Send dynamic variables |
| `trackPageEvent` | `(value: string)` | Fire page events |
| `trackEventTriggerRecording` | `(event: string)` | Fire ETP/ETS events with `@ETP@` or `@ETS@` prefix |
| `ec:cart:add` | `({sku: string})` | Track cart additions (Merchandising) |

## Requirements

- **Google Tag Manager**: Active container with web property
- **Contentsquare Implementation**: `_uxa` queue must be loaded on your page
- **For Add to Cart Events**: Active Contentsquare Merchandising license
- **Browser Support**: Modern browsers (ES5+)

## Data Types

### Value Type Support

| Type | Description | Example |
|------|-------------|---------|
| String | Text values and data layer variables | `"Homepage"`, `{{Page Title}}` |
| Integer | Numeric values with automatic conversion | `"42"` → `42` |

## Permissions

The template requires the following GTM permissions:

- **Access to Globals**: Read/Write access to `_uxa` global variable
- **Get URL**: Access to URL parts and query parameters (unrestricted)
- **Logging**: Console logging for debugging

## Testing

The template includes built-in test scenarios for validation:

- **Dynamic Variable Tests**: Verify key-value pair transmission with type conversion
- **Artificial Pageview Tests**: Confirm URL path and hash fragment handling
- **Event Tests**: Validate event value formatting and queue transmission

## Support & Resources

- **Homepage**: https://contentsquare.com/
- **Documentation**: https://docs.contentsquare.com/uxa-en/
- **Report Issues**: Contact Contentsquare support

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.1+ | Latest | Updated company branding and logo |
| 1.0 | Initial | First stable release |

## Troubleshooting

### Tag Fires But Data Isn't Tracked
- Verify `_uxa` queue is loaded on your page before GTM fires
- Check browser console for error messages
- Ensure you've filled all required fields marked with `*`

### Dynamic Variables Show Incorrect Types
- Select appropriate "Value Type" (String vs Integer)
- For integers, ensure the input is numeric

### Add to Cart Events Not Working
- Confirm you have Contentsquare Merchandising license
- Verify SKU format matches your catalog structure

## License

Licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

---

**Created by**: Contentsquare Professional Services  
**Maintained by**: contentsquare-ps  
**Last Updated**: 2026
