# routing-configuration static and dynamic (RIP / EIGRP / OSPF)

## STATIC :
the topology is 2 networks and link them with a 3d network between 2 routers :

<img width="424" height="290" alt="image" src="https://github.com/user-attachments/assets/0baa09d2-7ac8-446e-95bb-70798ba28293" />

configuring @IPs first then static routes after then testing : 

 left router :
 
  network 1 interface :
  
  <img width="299" height="44" alt="image" src="https://github.com/user-attachments/assets/68ffa500-99a6-4d33-bc0c-3cc0b5d90c2e" />
  
  gateway network interface :
  
  <img width="312" height="53" alt="image" src="https://github.com/user-attachments/assets/2906c608-c951-4996-b24c-85c87a92ca04" />

  adding static route from network1 to network2 :

  <img width="410" height="59" alt="image" src="https://github.com/user-attachments/assets/58457674-4c97-4719-9eb1-9cc9398370ea" />

  testing this route with ping from pc2 192.168.10.2 to pc3 192.168.20.3 :
  
  <img width="308" height="140" alt="image" src="https://github.com/user-attachments/assets/a943987e-7bfb-4541-b2a1-ea3de83a7c72" />

  final routing table :

  <img width="339" height="89" alt="image" src="https://github.com/user-attachments/assets/1ba08f99-59b9-4c40-aa2e-a1f27b93ba07" />

   interfaces status :
  
  <img width="429" height="52" alt="image" src="https://github.com/user-attachments/assets/96e17f8c-b15b-45d2-b8e3-26fd09d54c01" />

  passwords setup example :
  
  <img width="371" height="149" alt="image" src="https://github.com/user-attachments/assets/7abd65e1-74e3-4644-85a9-8dacf4805879" />

  
 right router :
 
  network 2 interface :
  
  <img width="317" height="60" alt="image" src="https://github.com/user-attachments/assets/596eb222-389b-4cd0-b326-59bd36a021e1" />
  
  gateway network interface :
  
  <img width="326" height="50" alt="image" src="https://github.com/user-attachments/assets/28cc68ec-de1c-4674-9515-39540b05fd97" />

  static route from 192.168.20.0 to 192.168.10.0 :

  <img width="348" height="30" alt="image" src="https://github.com/user-attachments/assets/c7438883-4c9f-44db-ad2a-82108897a66f" />
  
  test ping from pc3 in network2 to pc2 in network1 :

  <img width="316" height="146" alt="image" src="https://github.com/user-attachments/assets/405a4947-32d7-4b1b-ba07-7746751a509d" />

  final routing table :
  
  <img width="346" height="92" alt="image" src="https://github.com/user-attachments/assets/e963ebd1-8057-4dee-bbce-e09ae3f6ff83" />
  
   2nd example also preparation for rip :

   topology 
  
  <img width="636" height="366" alt="image" src="https://github.com/user-attachments/assets/de472c39-1c14-4a81-bf97-cb581dd46013" />

  one router interfaces set up example :
  
  <img width="413" height="259" alt="image" src="https://github.com/user-attachments/assets/25892039-4061-4ab6-bc85-61d53b55f09c" />

  i set up static routes , here is the network now and a test for the static routing :

  <img width="959" height="477" alt="Capture d&#39;écran 2026-10-19 162846" src="https://github.com/user-attachments/assets/0c4b9dd9-5eec-4e2e-a1da-33fa99ca5a20" />

## DYNAMIC :

### RIP v1

topology :

<img width="473" height="366" alt="image" src="https://github.com/user-attachments/assets/815f4d8f-4138-4e13-8e8f-4aaf0b4ec86c" />

test after deleting all the static routes :

<img width="434" height="56" alt="image" src="https://github.com/user-attachments/assets/ce032329-b619-4232-8418-bd5667b761de" />

all the subnets have the same mask (/24) so rip v1 is enough, no need for v2.

on each router i only declare the serial links and its own lan. `10.0.0.0` is class A so one line covers all the links :

```
router rip
 network 10.0.0.0
 network 192.168.x.0      (lan of this router)
```

router 1 :

<img width="254" height="30" alt="image" src="https://github.com/user-attachments/assets/f63ebaea-9117-48a5-91fc-c9970d01e81a" />

router 2 :

<img width="332" height="59" alt="image" src="https://github.com/user-attachments/assets/ce7a7fe4-6183-45c3-8d25-297577c476e2" />

router 3 :

<img width="280" height="32" alt="image" src="https://github.com/user-attachments/assets/a0fc5784-40ac-451c-863a-b227ec553a48" />

router 4 :

<img width="245" height="31" alt="image" src="https://github.com/user-attachments/assets/6bb5afd6-fb4a-455e-857a-093890f303e7" />

router 5 :

<img width="231" height="32" alt="image" src="https://github.com/user-attachments/assets/fbad8d10-d789-4321-b9c3-ac20540f3649" />

routing table of router 4 :

<img width="359" height="203" alt="image" src="https://github.com/user-attachments/assets/5fe32c6d-a549-440e-9324-2bb5d19710d1" />

tests, all routers up :

<img width="424" height="53" alt="image" src="https://github.com/user-attachments/assets/522af45c-5e0a-4bca-bdc1-d0afccc932f0" />

router r2 down :

<img width="424" height="53" alt="image" src="https://github.com/user-attachments/assets/ecaa7fe2-134f-47f2-8576-0469212fdd02" />

router r4 (the one in the center) down :

<img width="504" height="361" alt="image" src="https://github.com/user-attachments/assets/318d93e5-eb0c-40ec-a815-1accba822555" />

the first packet failed but then the same packet worked because r5 received the updates from his neighbor r1 :

<img width="425" height="56" alt="image" src="https://github.com/user-attachments/assets/83d52384-23bb-46f2-9cc0-e8553d345cfb" />

### RIP v2 (with VLSM)

175.10.1.0/24 split with vlsm : 4 lans (/25, /26, /27, /28) and 4 links (/30)

<img src="readme_images/images/rip2-vlsm-plan.png" width="350" alt="vlsm plan" />

<img src="readme_images/images/rip2-vlsm-topology.png" width="500" alt="vlsm topology" />

rip v1 doesnt send the subnet mask so it cant handle subnets of different sizes, the pings fail :

<img src="readme_images/images/rip1-vlsm-failed-test.png" width="500" alt="rip v1 failed" />

router 1 only learned one link, no lan :

<img src="readme_images/images/rip1-vlsm-hub-table.png" width="500" alt="router1 table rip v1" />

rip v2 sends the mask, so i just added these 2 lines on every router (`no auto-summary` so the subnets arent merged) :

```
router rip
 version 2
 no auto-summary
```

<img src="readme_images/images/rip2-config-router5.png" width="400" alt="rip v2 config" />

same network, same addresses, now everything works :

<img src="readme_images/images/rip2-vlsm-test.png" width="500" alt="rip v2 test" />

### EIGRP (with VLSM)

201.60.34.0/23 split in 5 lans and 7 links (/30) :

<img src="readme_images/images/eigrp-plan.png" width="350" alt="eigrp vlsm plan" />

<img src="readme_images/images/eigrp-topology.png" width="500" alt="eigrp topology" />

the network command uses a wildcard mask, and the same AS number (100) on all the routers. each router declares its lan and its links :

```
router eigrp 100
 network 201.60.35.128 0.0.0.31
 network 201.60.35.224 0.0.0.3
 network 201.60.35.228 0.0.0.3
 no auto-summary
```

<img src="readme_images/images/eigrp-config-pink.png" width="450" alt="eigrp config" />

routing table :

<img src="readme_images/images/eigrp-routing-table.png" width="500" alt="eigrp routing table" />

test :

<img src="readme_images/images/eigrp-test.png" width="500" alt="eigrp test" />

### OSPF (with VLSM)

same network and same addresses as eigrp. i removed eigrp first (`no router eigrp 100`) so only ospf is running, then every router in area 0 :

```
no router eigrp 100
router ospf 1
 network 201.60.35.128 0.0.0.31 area 0
 network 201.60.35.224 0.0.0.3 area 0
 network 201.60.35.228 0.0.0.3 area 0
```

<img src="readme_images/images/ospf-config.png" width="450" alt="ospf config" />

neighbors :

<img src="readme_images/images/ospf-neighbors.png" width="500" alt="ospf neighbors" />

routing table :

<img src="readme_images/images/ospf-routing-table.png" width="500" alt="ospf routing table" />

test :

<img src="readme_images/images/ospf-test.png" width="500" alt="ospf test" />
