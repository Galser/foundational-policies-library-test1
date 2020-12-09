# foundational-policies-library-test1
Sentinel for Terrafor - Foundational policies library test number 1


# Test run : 

## Top=level : 

```
 passed	foundational-policies-library-test1/azure-cis-6.1-networking-deny-public-rdp-nsg-rules
 advisory failed	foundational-policies-library-test1/azure-cis-6.2-networking-deny-public-ssh-nsg-rules
 passed	foundational-policies-library-test1/azure-cis-6.3-networking-deny-any-sql-database-ingress
 passed	foundational-policies-library-test1/azure-cis-7.1-compute-managed-disk-encryption-is-enabled
```
 
 ## Detailed : 
 
 ```
 ========== Results for policy set: foundational-policies-library-test1 =========

Sentinel Result: true

This result means that Sentinel policies returned true and the protected
behavior is allowed by Sentinel policies.

4 policies evaluated.

## Policy 1: foundational-policies-library-test1/azure-cis-6.2-networking-deny-public-ssh-nsg-rules (advisory)

Result: false (allowed failure based on level)

Print messages:

CIS 6.2: Ensure that SSH access is restricted from the internet

FALSE - ./azure-cis-6.2-networking-deny-public-ssh-nsg-rules.sentinel:71:1 - Rule "main"
  FALSE - ./azure-cis-6.2-networking-deny-public-ssh-nsg-rules.sentinel:54:7 - sr.destination_port_range is "*"
  TRUE - ./azure-cis-6.2-networking-deny-public-ssh-nsg-rules.sentinel:54:43 - sr.destination_port_range is port
## Policy 2: foundational-policies-library-test1/azure-cis-6.1-networking-deny-public-rdp-nsg-rules (advisory)

Result: true

Print messages:

CIS 6.1: Ensure that RDP access is restricted from the internet

TRUE - ./azure-cis-6.1-networking-deny-public-rdp-nsg-rules.sentinel:71:1 - Rule "main"
  FALSE - ./azure-cis-6.1-networking-deny-public-rdp-nsg-rules.sentinel:54:7 - sr.destination_port_range is "*"
  FALSE - ./azure-cis-6.1-networking-deny-public-rdp-nsg-rules.sentinel:54:43 - sr.destination_port_range is port
## Policy 3: foundational-policies-library-test1/azure-cis-6.3-networking-deny-any-sql-database-ingress (advisory)

Result: true

Print messages:

CIS 6.3: Ensure no SQL Databases allow ingress 0.0.0.0/0

TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:25:1 - Rule "main"
  TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:26:2 - deny_any_local_start_ip_address
    TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:20:2 - all allSQLFirewallRules as _, firewall_rule {
	firewall_rule.change.after.start_ip_address is not "0.0.0.0"
}
  TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:27:2 - deny_access_to_azure_services
    TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:13:2 - all allSQLFirewallRules as _, firewall_rule {
	firewall_rule.change.after.start_ip_address is not "0.0.0.0" and
		firewall_rule.change.after.end_ip_address is not "0.0.0.0"
}

TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:12:1 - Rule "deny_access_to_azure_services"

TRUE - ./azure-cis-6.3-networking-deny-any-sql-database-ingress.sentinel:19:1 - Rule "deny_any_local_start_ip_address"
## Policy 4: foundational-policies-library-test1/azure-cis-7.1-compute-managed-disk-encryption-is-enabled (advisory)

Result: true

Print messages:

CIS 7.1: Ensure that managed disks are encrypted

TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:27:1 - Rule "main"
  TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:28:2 - deny_undefined_encryption_settings
    TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:13:2 - all allManagedDisks as _, disks {
	keys(disks.change.after) contains "encryption_settings" and
		length(disks.change.after.encryption_settings) != 0
}
  TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:29:2 - deny_unencrypted_managed_disk
    TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:20:2 - all allManagedDisks as _, disks {
	all disks.change.after.encryption_settings as encryption_settings {
		encryption_settings.enabled is true
	}
}

TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:12:1 - Rule "deny_undefined_encryption_settings"

TRUE - ./azure-cis-7.1-compute-managed-disk-encryption-is-enabled.sentinel:19:1 - Rule "deny_unencrypted_managed_disk"


 ```
