# create resource group
New-AzResourceGroup -Name 'myResourceGroup' -Location 'centralindia'

# create vm
New-AzVm `
    -ResourceGroupName 'myResourceGroup' `
    -Name 'myVM' `
    -Location 'centralindia' `
    -Image 'MicrosoftWindowsServer:WindowsServer:2022-datacenter-azure-edition:latest' `
    -Size 'Standard_B1s' `
    -VirtualNetworkName 'myVnet' `
    -SubnetName 'mySubnet' `
    -SecurityGroupName 'myNetworkSecurityGroup' `
    -PublicIpAddressName 'myPublicIpAddress' `
    -OpenPorts 80,3389

# check status of vm
Get-AzVM -ResourceGroupName "myResourceGroup" -Name "myVM" -Status


# find the ip
Get-AzPublicIpAddress -ResourceGroupName "myResourceGroup" | Select-Object
Name, IpAddress


# remove vm and it resource
Remove-AzResourceGroup -Name 'myResourceGroup'