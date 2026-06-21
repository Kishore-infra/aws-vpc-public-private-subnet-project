# AWS VPC Public & Private Subnet Architecture Project

## Project Overview

This project demonstrates the design and implementation of a secure AWS VPC architecture using Public and Private Subnets.

The architecture includes:

- Custom VPC
- Public Subnet
- Private Subnet
- Internet Gateway (IGW)
- NAT Gateway
- Elastic IP
- Public Route Table
- Private Route Table
- Bastion Host
- Private EC2 Instance
- Security Groups

The goal of this project is to provide secure access to resources in a Private Subnet while allowing outbound internet connectivity through a NAT Gateway.

---

## Architecture

```text
Internet
   │
   ▼
Internet Gateway (IGW)
   │
   ▼
Public Subnet (10.0.1.0/24)
   │
   ├── Bastion Host
   │
   └── NAT Gateway + Elastic IP
   │
   ▼
Private Subnet (10.0.2.0/24)
   │
   └── Private EC2
```

---

## AWS Services Used

- Amazon VPC
- Amazon EC2
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Security Groups

---

## VPC Configuration

| Component | Value |
|------------|------------|
| VPC CIDR | 10.0.0.0/16 |
| Public Subnet | 10.0.1.0/24 |
| Private Subnet | 10.0.2.0/24 |

---

## Route Tables

### Public Route Table

| Destination | Target |
|------------|------------|
| 10.0.0.0/16 | local |
| 0.0.0.0/0 | Internet Gateway |

### Private Route Table

| Destination | Target |
|------------|------------|
| 10.0.0.0/16 | local |
| 0.0.0.0/0 | NAT Gateway |

---

## Security Configuration

### Bastion Host Security Group

Inbound:

- SSH (22) from My IP

### Private EC2 Security Group

Inbound:

- SSH (22) from Bastion Host Security Group

---

## Project Steps

### Step 1

Created custom VPC:

```
10.0.0.0/16
```

### Step 2

Created Public Subnet:

```
10.0.1.0/24
```

### Step 3

Created Private Subnet:

```
10.0.2.0/24
```

### Step 4

Created and attached Internet Gateway.

### Step 5

Configured Public Route Table:

```
0.0.0.0/0 → IGW
```

### Step 6

Associated Public Subnet with Public Route Table.

### Step 7

Launched Bastion Host in Public Subnet.

### Step 8

Created Private Route Table.

### Step 9

Associated Private Subnet with Private Route Table.

### Step 10

Launched Private EC2 in Private Subnet.

### Step 11

Connected to Private EC2 through Bastion Host.

### Step 12

Created Elastic IP.

### Step 13

Created NAT Gateway in Public Subnet.

### Step 14

Configured Private Route Table:

```
0.0.0.0/0 → NAT Gateway
```

### Step 15

Verified internet access from Private EC2.

---

## Connectivity Validation

### Bastion Host Access

Successfully connected using SSH:

```bash
ssh -i mykey.pem ubuntu@<Public-IP>
```

### Bastion to Private EC2

Successfully connected using:

```bash
ssh -i mykey.pem ubuntu@<Private-IP>
```

### NAT Gateway Validation

Verified outbound internet access:

```bash
sudo apt update
```

Successfully downloaded package indexes from Ubuntu repositories.

---

## Troubleshooting Experience

### Issue

Private EC2 could not access the internet through NAT Gateway.

### Root Cause

Private Subnet was not associated with the Private Route Table.

### Resolution

Associated Private Subnet with Private Route Table.

After association:

```text
Private EC2
    │
Private Route Table
    │
NAT Gateway
    │
Internet
```

Internet access worked successfully.

---

## Key Learnings

- VPC Design
- CIDR Planning
- Public vs Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Subnet Associations
- Security Groups
- Bastion Host Architecture
- SSH Authentication
- Public and Private Key Concepts
- AWS Network Troubleshooting

---

## Outcome

Successfully built a production-style AWS VPC architecture with secure access to private resources using a Bastion Host and NAT Gateway.# AWS VPC Public & Private Subnet Architecture Project

## Project Overview

This project demonstrates the design and implementation of a secure AWS VPC architecture using Public and Private Subnets.

The architecture includes:

- Custom VPC
- Public Subnet
- Private Subnet
- Internet Gateway (IGW)
- NAT Gateway
- Elastic IP
- Public Route Table
- Private Route Table
- Bastion Host
- Private EC2 Instance
- Security Groups

The goal of this project is to provide secure access to resources in a Private Subnet while allowing outbound internet connectivity through a NAT Gateway.

---

## Architecture

```text
Internet
   │
   ▼
Internet Gateway (IGW)
   │
   ▼
Public Subnet (10.0.1.0/24)
   │
   ├── Bastion Host
   │
   └── NAT Gateway + Elastic IP
   │
   ▼
Private Subnet (10.0.2.0/24)
   │
   └── Private EC2
```

---

## AWS Services Used

- Amazon VPC
- Amazon EC2
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Security Groups

---

## VPC Configuration

| Component | Value |
|------------|------------|
| VPC CIDR | 10.0.0.0/16 |
| Public Subnet | 10.0.1.0/24 |
| Private Subnet | 10.0.2.0/24 |

---

## Route Tables

### Public Route Table

| Destination | Target |
|------------|------------|
| 10.0.0.0/16 | local |
| 0.0.0.0/0 | Internet Gateway |

### Private Route Table

| Destination | Target |
|------------|------------|
| 10.0.0.0/16 | local |
| 0.0.0.0/0 | NAT Gateway |

---

## Security Configuration

### Bastion Host Security Group

Inbound:

- SSH (22) from My IP

### Private EC2 Security Group

Inbound:

- SSH (22) from Bastion Host Security Group

---

## Project Steps

### Step 1

Created custom VPC:

```
10.0.0.0/16
```

### Step 2

Created Public Subnet:

```
10.0.1.0/24
```

### Step 3

Created Private Subnet:

```
10.0.2.0/24
```

### Step 4

Created and attached Internet Gateway.

### Step 5

Configured Public Route Table:

```
0.0.0.0/0 → IGW
```

### Step 6

Associated Public Subnet with Public Route Table.

### Step 7

Launched Bastion Host in Public Subnet.

### Step 8

Created Private Route Table.

### Step 9

Associated Private Subnet with Private Route Table.

### Step 10

Launched Private EC2 in Private Subnet.

### Step 11

Connected to Private EC2 through Bastion Host.

### Step 12

Created Elastic IP.

### Step 13

Created NAT Gateway in Public Subnet.

### Step 14

Configured Private Route Table:

```
0.0.0.0/0 → NAT Gateway
```

### Step 15

Verified internet access from Private EC2.

---

## Connectivity Validation

### Bastion Host Access

Successfully connected using SSH:

```bash
ssh -i mykey.pem ubuntu@<Public-IP>
```

### Bastion to Private EC2

Successfully connected using:

```bash
ssh -i mykey.pem ubuntu@<Private-IP>
```

### NAT Gateway Validation

Verified outbound internet access:

```bash
sudo apt update
```

Successfully downloaded package indexes from Ubuntu repositories.

---

## Troubleshooting Experience

### Issue

Private EC2 could not access the internet through NAT Gateway.

### Root Cause

Private Subnet was not associated with the Private Route Table.

### Resolution

Associated Private Subnet with Private Route Table.

After association:

```text
Private EC2
    │
Private Route Table
    │
NAT Gateway
    │
Internet
```

Internet access worked successfully.

---

## Key Learnings

- VPC Design
- CIDR Planning
- Public vs Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Subnet Associations
- Security Groups
- Bastion Host Architecture
- SSH Authentication
- Public and Private Key Concepts
- AWS Network Troubleshooting

---
## Architecture Diagram
[VPC Architecture] 
(VPC-Architecure.png) 

## Implementation Screenshots

### Public and Private Subnet
|Subnet|(screenshots/Public-Private-Subnet.png)

### public Route Table
|Public Route Table|(Screenshots/public-route-table-png)

### Private Route Table
|Private Route Table|(screenshots/05-private-route-table.png)


## Outcome

Successfully built a production-style AWS VPC architecture with secure access to private resources using a Bastion Host and NAT Gateway.
