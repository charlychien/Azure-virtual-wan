# Virtual Hub Deployment Script

This PowerShell script automates the creation of an Azure Virtual Hub in a specified resource group and region, associating it with an existing Virtual WAN.

## Prerequisites
- Azure PowerShell module ([Az](https://docs.microsoft.com/powershell/azure/new-azureps-module-az?view=azps-10.0.0)) installed
- Sufficient permissions to create resources in the target Azure subscription
- Existing Virtual WAN resource

## Script Overview
- Sets variables for subscription, resource group, hub name, location, address space, and Virtual WAN ID
- Creates a Virtual Hub in the specified resource group and region
- Associates the hub with the provided Virtual WAN

## Usage
1. Edit the variable values at the top of the script to match your environment:
    - `$subscriptionId`: Your Azure subscription ID
    - `$hubRg`: Resource group for the Virtual Hub
    - `$hubName`: Name for the Virtual Hub
    - `$hubLocation`: Azure region for the Virtual Hub
    - `$hubAddressCidr`: Address space for the Virtual Hub
    - `$wanId`: Resource ID of the existing Virtual WAN
2. Run the script in a PowerShell session with Azure permissions:

```powershell
# Login to Azure if not already logged in
Connect-AzAccount

# (Optional) Set the subscription context
Set-AzContext -SubscriptionId <your-subscription-id>

# Run the script
./ps.ps1
```

## Example
```
$subscriptionId = "a8fce891-6b03-4c65-845b-aa0b784eb86a"
$hubRg  = "rg-virtualhub-eastasia"
$hubName = "vhub-eastasia"
$hubLocation = "East Asia"
$hubAddressCidr = "10.160.0.0/23"
$wanId = "/subscriptions/a8fce891-6b03-4c65-845b-aa0b784eb86a/resourceGroups/rg-brk-vwan-001/providers/Microsoft.Network/virtualWans/brk-vwan-hub-001"
```

## Notes
- The script uses the `New-AzVirtualHub` cmdlet to create the Virtual Hub.
- The Virtual Hub can be created in a different resource group than the Virtual WAN.
- Adjust the `-Sku` parameter as needed (e.g., "Standard").

## References
- [Azure Virtual WAN documentation](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about)
- [New-AzVirtualHub cmdlet](https://docs.microsoft.com/powershell/module/az.network/new-azvirtualhub)
