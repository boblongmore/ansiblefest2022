# Platform Pete Industries - Network Documentation
## Incident ID: INC0010053 - 2022-10-04

## Router Interfaces

#### **rtr-branch1**
| Interface Name | status | line protocol
| -------------- | ------- | ------------ |
| GigabitEthernet1 | up | up |
| GigabitEthernet2 | administratively down | down |
| GigabitEthernet3 | administratively down | down |
| GigabitEthernet4 | up | up |
| Loopback1 | up | up |
#### **rtr-branch2**
| Interface Name | status | line protocol
| -------------- | ------- | ------------ |
| GigabitEthernet1 | administratively down | down |
| GigabitEthernet2 | administratively down | down |
| GigabitEthernet3 | administratively down | down |
| GigabitEthernet4 | up | up |
| Loopback1 | up | up |
#### **rtr-branch3**
| Interface Name | status | line protocol
| -------------- | ------- | ------------ |
| GigabitEthernet1 | up | up |
| GigabitEthernet2 | administratively down | down |
| GigabitEthernet3 | administratively down | down |
| GigabitEthernet4 | up | up |
| Loopback1 | up | up |
#### **rtr-core**
| Interface Name | status | line protocol
| -------------- | ------- | ------------ |
| GigabitEthernet1 | up | up |
| GigabitEthernet2 | up | up |
| GigabitEthernet3 | up | up |
| GigabitEthernet4 | up | up |
| Loopback1 | up | up |

## OSPF Neighbors

### **rtr-branch1**
| Interface Name | Neighbor Router ID | State
| ---------------- | ------------------ | -------- |
| GigabitEthernet1 | 100.1.1.1 | FULL/DR
### **rtr-branch2**
| Interface Name | Neighbor Router ID | State
| ---------------- | ------------------ | -------- |
| No OSPF int found | No Neighbors Found | None
### **rtr-branch3**
| Interface Name | Neighbor Router ID | State
| ---------------- | ------------------ | -------- |
| GigabitEthernet1 | 100.1.1.1 | FULL/DR
### **rtr-core**
| Interface Name | Neighbor Router ID | State
| ---------------- | ------------------ | -------- |
| GigabitEthernet1 | 192.168.1.1 | FULL/BDR
| GigabitEthernet3 | 1.1.1.3 | FULL/BDR

## OSPF Interface Validation errors
| Router Name | Process/Area/Interface | State Found |
| ----------- | ------------------------ | ---------- |
| rtr-branch2 | 100.areas.0.0.0.0.interfaces.GigabitEthernet1.state | DOWN

## Default Route status for Branch Routers
| Router Name | Default route Present? 
| -------------- | ------- | 
| rtr-branch1 | True
| **rtr-branch2** | **False**
| rtr-branch3 | True

## Branch routers pinging **rtr_core**
| Router Name | successful pings 
| -------------- | ------- | 
| rtr-branch1 | All Pings Successful
| **rtr-branch2** | **0**
| rtr-branch3 | All Pings Successful
