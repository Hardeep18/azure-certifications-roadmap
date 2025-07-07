# AZ-104: Microsoft Azure Administrator Certification Roadmap

## 🎯 Introduction

The **AZ-104 Microsoft Azure Administrator** certification validates your skills in managing Azure resources, implementing security, and maintaining Azure infrastructure. This exam is designed for professionals who want to demonstrate their expertise in Azure administration.

### Who is this certification for?
- **Azure Administrators** managing day-to-day Azure operations
- **System Administrators** transitioning to cloud
- **IT Professionals** seeking cloud infrastructure expertise
- **DevOps Engineers** needing Azure administration skills

### Certification Benefits
- ✅ **Industry Recognition** - Globally recognized Microsoft credential
- ✅ **Career Advancement** - Average 25% salary increase
- ✅ **Practical Skills** - Hands-on Azure management expertise
- ✅ **Foundation for Advanced Certs** - Prerequisite for AZ-305 and other expert-level certifications

---

## 📅 5-Week Intensive Learning Roadmap

> **Trainer's Note:** This roadmap is based on 15-20 hours of study per week. Focus on hands-on practice over theory - Azure is learned by doing, not just reading!

### **Week 1: Identity Management & Governance**
**🎯 Key Topics:**
- Azure Active Directory (AAD) fundamentals
- User and group management
- Role-Based Access Control (RBAC)
- Azure Policy and Management Groups
- Azure Resource Manager (ARM) templates

**🧪 Hands-on Labs:**
```bash
# Create a new user in Azure AD
az ad user create \
  --display-name "John Doe" \
  --user-principal-name "john.doe@yourdomain.com" \
  --password "TempPassword123!" \
  --force-change-password-next-login true

# Assign RBAC role to user
az role assignment create \
  --assignee john.doe@yourdomain.com \
  --role "Virtual Machine Contributor" \
  --scope /subscriptions/{subscription-id}/resourceGroups/myRG
```

**🔧 Azure Services to Configure:**
- Azure Active Directory
- Management Groups
- Azure Policy
- Resource Groups
- RBAC assignments

**📝 Practice Exercises:**
1. Create a custom RBAC role for VM operators
2. Implement Azure Policy to enforce resource tagging
3. Set up conditional access policies
4. Configure self-service password reset

**🔗 Microsoft Learn Path:**
- [Manage identities and governance in Azure](https://docs.microsoft.com/learn/paths/az-104-manage-identities-governance/)

---

### **Week 2: Storage & Virtual Machines**
**🎯 Key Topics:**
- Azure Storage accounts and services
- Virtual Machine deployment and management
- VM sizing and scaling
- Disk management and snapshots
- Backup and disaster recovery

**🧪 Hands-on Labs:**
```bash
# Create a storage account
az storage account create \
  --name mystorageaccount \
  --resource-group myRG \
  --location eastus \
  --sku Standard_LRS

# Deploy a VM with custom script extension
az vm create \
  --resource-group myRG \
  --name myVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys \
  --custom-data cloud-init.txt

# Create and attach a data disk
az vm disk attach \
  --vm-name myVM \
  --resource-group myRG \
  --disk myDataDisk \
  --new \
  --size-gb 64
```

**🔧 Azure Services to Configure:**
- Storage Accounts (Blob, File, Queue, Table)
- Virtual Machines (Windows/Linux)
- Azure Backup
- Azure Site Recovery
- Managed Disks

**📝 Practice Exercises:**
1. Set up geo-redundant storage with lifecycle policies
2. Deploy VMs using ARM templates
3. Configure Azure Backup for VMs
4. Implement VM auto-scaling

**🔗 Microsoft Learn Path:**
- [Deploy and manage virtual machines in Azure](https://docs.microsoft.com/learn/paths/az-104-manage-virtual-machines/)

---

### **Week 3: Networking & Security**
**🎯 Key Topics:**
- Virtual Networks (VNets) and subnets
- Network Security Groups (NSGs)
- Azure Firewall and Application Gateway
- VPN Gateway and ExpressRoute
- DNS and Load Balancing

**🧪 Hands-on Labs:**
```bash
# Create a VNet with subnets
az network vnet create \
  --resource-group myRG \
  --name myVNet \
  --address-prefix 10.0.0.0/16 \
  --subnet-name mySubnet \
  --subnet-prefix 10.0.1.0/24

# Create NSG and security rules
az network nsg create \
  --resource-group myRG \
  --name myNSG

az network nsg rule create \
  --resource-group myRG \
  --nsg-name myNSG \
  --name allowHTTP \
  --protocol tcp \
  --priority 100 \
  --destination-port-range 80 \
  --access allow

# Set up VPN Gateway
az network vnet-gateway create \
  --resource-group myRG \
  --name myVPNGateway \
  --public-ip-address myGatewayIP \
  --vnet myVNet \
  --gateway-type Vpn \
  --vpn-type RouteBased \
  --sku VpnGw1
```

**🔧 Azure Services to Configure:**
- Virtual Networks
- Network Security Groups
- Azure Firewall
- VPN Gateway
- Load Balancer
- Application Gateway

**📝 Practice Exercises:**
1. Design a hub-and-spoke network topology
2. Configure site-to-site VPN
3. Set up Azure Firewall with custom rules
4. Implement traffic routing with UDRs

**🔗 Microsoft Learn Path:**
- [Configure and manage virtual networks for Azure administrators](https://docs.microsoft.com/learn/paths/az-104-manage-virtual-networks/)

---

### **Week 4: Monitoring & Backup**
**🎯 Key Topics:**
- Azure Monitor and Log Analytics
- Application Insights
- Azure Backup strategies
- Disaster recovery planning
- Cost management and optimization

**🧪 Hands-on Labs:**
```bash
# Create Log Analytics workspace
az monitor log-analytics workspace create \
  --resource-group myRG \
  --workspace-name myLogAnalytics \
  --location eastus

# Enable VM insights
az vm extension set \
  --resource-group myRG \
  --vm-name myVM \
  --name OmsAgentForLinux \
  --publisher Microsoft.EnterpriseCloud.Monitoring \
  --settings '{
    "workspaceId": "'$(az monitor log-analytics workspace show --resource-group myRG --workspace-name myLogAnalytics --query customerId -o tsv)'"
  }'

# Create alert rule
az monitor metrics alert create \
  --name "High CPU Alert" \
  --resource-group myRG \
  --scopes /subscriptions/{subscription-id}/resourceGroups/myRG/providers/Microsoft.Compute/virtualMachines/myVM \
  --condition "avg Percentage CPU > 80" \
  --description "Alert when CPU exceeds 80%"
```

**🔧 Azure Services to Configure:**
- Azure Monitor
- Log Analytics
- Azure Backup
- Azure Site Recovery
- Cost Management

**📝 Practice Exercises:**
1. Set up comprehensive monitoring dashboard
2. Configure automated backup policies
3. Implement disaster recovery runbooks
4. Create cost alerts and budgets

**🔗 Microsoft Learn Path:**
- [Monitor and back up Azure resources](https://docs.microsoft.com/learn/paths/az-104-monitor-backup-resources/)

---

### **Week 5: Final Preparation & Mock Tests**
**🎯 Focus Areas:**
- **Day 1-2:** ARM template mastery and troubleshooting
- **Day 3-4:** PowerShell/CLI command practice
- **Day 5-6:** Mock exams and weak area review
- **Day 7:** Final review and exam preparation

**🧪 Real-World Case Studies:**
1. **Scenario 1:** Migrate on-premises infrastructure to Azure
2. **Scenario 2:** Implement disaster recovery for multi-tier application
3. **Scenario 3:** Optimize costs for over-provisioned resources
4. **Scenario 4:** Secure multi-tenant Azure environment

**📊 Mock Test Schedule:**
- **Practice Test 1:** MeasureUp or Whizlabs (Monday)
- **Practice Test 2:** Microsoft Official Practice Test (Wednesday)
- **Practice Test 3:** Kaplan or Transcender (Friday)
- **Final Review:** Weak areas identified from mock tests (Weekend)

**🔧 Troubleshooting Tips:**
```bash
# Common troubleshooting commands
az vm get-instance-view --resource-group myRG --name myVM
az network nic show-effective-route-table --resource-group myRG --name myNIC
az storage account check-name --name mystorageaccount
az policy state list --resource-group myRG
```

---

## 🛠️ Practical Learning Strategy

### **Hands-On First Approach**
1. **Always use CLI/PowerShell** - Don't rely only on portal
2. **Practice with ARM templates** - Infrastructure as Code is crucial
3. **Implement monitoring early** - Every resource should be monitored
4. **Focus on troubleshooting** - 40% of exam questions involve problem-solving

### **Essential Commands to Master**
```bash
# Resource Management
az group create --name myRG --location eastus
az resource list --resource-group myRG --output table

# Identity Management
az ad user list --output table
az role assignment list --assignee user@domain.com

# Storage Management
az storage blob upload --account-name mystorageaccount --container-name mycontainer --name myblob --file myfile.txt

# VM Management
az vm start --resource-group myRG --name myVM
az vm deallocate --resource-group myRG --name myVM
```

---

## 📚 Essential Resources

### **Official Microsoft Resources**
- [Microsoft Learn AZ-104 Learning Path](https://docs.microsoft.com/learn/certifications/exams/az-104)
- [Azure Documentation](https://docs.microsoft.com/azure/)
- [Azure Architecture Center](https://docs.microsoft.com/azure/architecture/)

### **Hands-On Labs**
- [Microsoft Learn Sandbox](https://docs.microsoft.com/learn/browse/?roles=administrator&products=azure)
- [Azure Free Account](https://azure.microsoft.com/free/) - $200 credit for 30 days
- [Azure Citadel Labs](https://azurecitadel.com/) - Community-driven labs

### **Practice Tests**
- [MeasureUp AZ-104 Practice Test](https://www.measureup.com/az-104-microsoft-azure-administrator.html)
- [Whizlabs AZ-104 Practice Tests](https://www.whizlabs.com/microsoft-azure-certification-az-104/)
- [Microsoft Official Practice Test](https://www.mindhub.com/az-104-microsoft-azure-administrator-microsoft-official-practice-test/p/MU-AZ-104)

### **GitHub Repositories**
- [Azure Samples](https://github.com/Azure-Samples)
- [Azure QuickStart Templates](https://github.com/Azure/azure-quickstart-templates)
- [Azure CLI Samples](https://github.com/Azure/azure-cli-samples)

### **Sandbox Environments**
- [Azure Cloud Shell](https://shell.azure.com/)
- [Azure DevTest Labs](https://azure.microsoft.com/services/devtest-lab/)
- [Pluralsight Azure Sandbox](https://www.pluralsight.com/cloud-guru/azure-cloud-sandbox)

---

## 🎓 Final Success Tips

### **Week Before Exam**
1. **Review all CLI commands** - Practice without looking at documentation
2. **Focus on scenarios** - Think like an Azure administrator solving problems
3. **Time management** - Practice completing mock tests within time limits
4. **Get proper rest** - Don't cram the night before

### **Day of Exam**
1. **Read questions carefully** - Look for keywords like "most cost-effective", "most secure"
2. **Eliminate wrong answers** - Process of elimination is your friend
3. **Flag and review** - Don't spend too long on one question
4. **Trust your hands-on experience** - Practical knowledge trumps memorization

---

## 💡 Trainer's Final Advice

> **"The AZ-104 exam tests your ability to be a competent Azure administrator. Focus on practical scenarios, not just theoretical knowledge. Every service you learn should be something you can deploy, configure, and troubleshoot. Remember, Microsoft wants administrators who can solve real business problems with Azure."**

### **Key Success Metrics**
- ✅ Can deploy and manage VMs without documentation
- ✅ Comfortable with ARM templates and CLI commands
- ✅ Understand security and compliance requirements
- ✅ Can troubleshoot common Azure issues
- ✅ Scoring 85%+ on practice tests consistently

---

🔗 **[Download Practice Papers & Cheatsheets (Google Drive)](https://drive.google.com/drive/folders/10fb8pUjmNxyx_1AGrswROj8Dmdjh6BKS?usp=drive_link)**

---

**Good luck with your AZ-104 certification journey! Remember, this certification is about proving you can manage Azure infrastructure effectively. Focus on hands-on practice and real-world scenarios.**

*Last updated: December 2024* 