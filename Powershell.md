# create resource group
New-AzResourceGroup -Name 'myResourceGroup' -Location 'centralindia'

# create vm
New-AzVm `
    -ResourceGroupName 'myResourceGroup' `
    -Name 'myVM' `
    -Location 'centralindia' `
    -Image 'MicrosoftWindowsServer:WindowsServer:2022-datacenter-azure-edition:latest' `
    -Size 'Standard_B1s' `
    -Credential $Credential `
    -VirtualNetworkName 'myVnet' `
    -AddressPrefix '10.0.0.0/16' `
    -SubnetName 'mySubnet' `
    -SubnetAddressPrefix '10.0.0.0/24' `
    -SecurityGroupName 'myNetworkSecurityGroup' `
    -PublicIpAddressName 'myPublicIpAddress' `
    -PublicIpAddressAllocationMethod 'Dynamic' `
    -OpenPorts 80, 3389 `
    -Tag @{ Environment = "Development"; Owner = "Admin" } `
    -AsJob

# check status of vm
Get-AzVM -ResourceGroupName "myResourceGroup" -Name "myVM" -Status


# find the ip
Get-AzPublicIpAddress -ResourceGroupName "myResourceGroup" | Select-Object
Name, IpAddress


# remove vm and it resource
Remove-AzResourceGroup -Name 'myResourceGroup'
