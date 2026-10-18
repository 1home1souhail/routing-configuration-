# routing-configuration-
all types of routing ways static and dynamic (RIP V1,2 / OSPF / EIGRP)

#STATIC :
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
  
 right router :
 
  network 2 interface :
  
  <img width="317" height="60" alt="image" src="https://github.com/user-attachments/assets/596eb222-389b-4cd0-b326-59bd36a021e1" />
  
  gateway network interface :
  
  <img width="326" height="50" alt="image" src="https://github.com/user-attachments/assets/28cc68ec-de1c-4674-9515-39540b05fd97" />

  static route from 192.168.20.0 to 192.168.10.0 :

  <img width="348" height="30" alt="image" src="https://github.com/user-attachments/assets/c7438883-4c9f-44db-ad2a-82108897a66f" />
  
  test ping from pc3 in network2 to pc2 in network1 :

  <img width="316" height="146" alt="image" src="https://github.com/user-attachments/assets/405a4947-32d7-4b1b-ba07-7746751a509d" />


  


