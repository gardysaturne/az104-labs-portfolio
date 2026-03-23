
---

## `ex01-availability-set-load-balancer/README.md`
```md
# Exercise 1 - Availability Set + Load Balancer for Regional VM Resiliency

## Goal
Implement a highly available regional VM-based web tier using:
- an Availability Set
- two virtual machines
- an Azure Load Balancer

## Scenario
A support portal is used by IT operations staff in New York and Tampa. The portal must remain available during host maintenance or hardware failure inside the region. Traffic should be distributed only to healthy VM instances.

## Why this lab matters
This lab reinforces:
- regional high availability thinking
- Availability Set behavior
- health probes
- Load Balancer role in production web-tier design

---

## Do (Portal)

### Part 1 - Create the resource group
1. In the Azure portal, go to **Resource groups**.
2. Click **Create**.
3. Resource group name: `rg-compute-americas-prod`
4. Region: `East US`
5. Click **Review + create** and then **Create**.

### Part 2 - Create the virtual network
1. Search for **Virtual networks**.
2. Click **Create**.
3. Resource group: `rg-compute-americas-prod`
4. Name: `vnet-americas-web`
5. Region: `East US`
6. Address space: `10.50.0.0/16`
7. Add subnet:
   - Subnet name: `snet-web`
   - Subnet range: `10.50.1.0/24`
8. Review + create.

### Part 3 - Create the Availability Set
1. Search for **Availability sets**.
2. Click **Create**.
3. Resource group: `rg-compute-americas-prod`
4. Name: `as-americas-web`
5. Region: `East US`
6. Keep default fault domains and update domains.
7. Create the Availability Set.

### Part 4 - Create VM 1
1. Go to **Virtual machines**.
2. Click **Create** -> **Azure virtual machine**.
3. Resource group: `rg-compute-americas-prod`
4. VM name: `vm-web-01`
5. Region: `East US`
6. Availability options: **Availability set**
7. Select Availability Set: `as-americas-web`
8. Image: choose a small lab-friendly image
9. Size: choose a low-cost size
10. Create administrator credentials
11. Inbound ports: allow only what is needed for the lab
12. Networking:
    - VNet: `vnet-americas-web`
    - Subnet: `snet-web`
13. Review + create.

### Part 5 - Create VM 2
Repeat the VM deployment:
- VM name: `vm-web-02`
- Same Availability Set: `as-americas-web`
- Same VNet/Subnet

### Part 6 - Install a web server on each VM
After deployment:
1. Open `vm-web-01`.
2. Go to **Operations** -> **Run command**.
3. Use the appropriate script option for the OS.
4. Install the web server and make the landing page identify the VM.
5. Repeat for `vm-web-02`.

### Part 7 - Create the Load Balancer
1. Search for **Load balancers**.
2. Click **Create**.
3. Resource group: `rg-compute-americas-prod`
4. Name: `lb-americas-web`
5. Type: **Public**
6. SKU: **Standard**
7. Region: `East US`
8. Public IP: create `pip-lb-americas-web`
9. Review + create.

### Part 8 - Configure backend pool
1. Open `lb-americas-web`.
2. Go to **Backend pools**.
3. Click **Add**.
4. Name: `bepool-web`
5. Add the NICs for `vm-web-01` and `vm-web-02`.
6. Save.

### Part 9 - Create health probe
1. Go to **Health probes**.
2. Click **Add**.
3. Name: `hp-http`
4. Protocol: `HTTP`
5. Port: `80`
6. Path: `/`
7. Save.

### Part 10 - Create load-balancing rule
1. Go to **Load balancing rules**.
2. Click **Add**.
3. Name: `lbr-http`
4. Frontend IP: default public frontend
5. Backend pool: `bepool-web`
6. Protocol: `TCP`
7. Port: `80`
8. Backend port: `80`
9. Health probe: `hp-http`
10. Save.

---

## Screenshots
- Resource group overview
- Virtual network overview
- Availability Set overview
- VM creation screen showing Availability Set selection
- Load Balancer backend pool
- Health probe
- Load-balancing rule
- Browser view hitting the Load Balancer public IP

---

## What I should be able to explain
- An Availability Set improves availability inside a region.
- It helps protect against host and maintenance-related failure domains.
- It is not the same as disaster recovery.
- A Load Balancer distributes traffic only to healthy backend instances.
- Health probes are what allow the Load Balancer to make that decision.

---

## Talk track
For a regional support portal, I used an Availability Set because the requirement was to survive localized host-level failures inside East US, not a full regional outage. I paired that with an Azure Load Balancer so traffic only flows to healthy instances. This is the right pattern when the workload is still VM-based and the business needs HA without redesigning the application tier yet.
