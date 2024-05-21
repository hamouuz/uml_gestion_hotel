# uml_gestion_hotel

# Diagramme use case: 

@startuml
actor Client
actor ReservationAgent

usecase "Create Hotel" as UC1
usecase "Modify Hotel" as UC2
usecase "View Availability" as UC3
usecase "Make Reservation" as UC4
usecase "Confirm Reservation" as UC5
usecase "Client Check-In" as UC6
usecase "Record Consumption" as UC7
usecase "Generate Invoice" as UC8
usecase "Print Reports" as UC9

Client -- UC3
Client -- UC4
Client -- UC5
Client -- UC6

ReservationAgent -- UC3
ReservationAgent -- UC4
ReservationAgent -- UC5

UC1 -- UC2 : includes
UC3 -- UC4 : extends
UC4 -- UC5 : includes
UC6 -- UC7 : includes
UC7 -- UC8 : includes

@enduml

![image](https://github.com/hamouuz/uml_gestion_hotel/assets/118366904/7d3a8ca3-052e-41cb-b21d-e8c8cf1e9091)



#Diagramme de classe : 
@startuml
class Hotel {
  
String name
String address
String class
List<Room> rooms
+ create()+ modify()+ viewAvailability()
}

class Room {
  
String category
int capacity
boolean comfortLevel
boolean availability
+ reserve()
}

class Reservation {
  
String reservationCode
Date reservationDate
Client client
Hotel hotel
Room room
+ confirm()
}

class Client {
  
String name
String address
String phone
String email
+ makeReservation()
}

class Invoice {
  
String invoiceNumber
Date invoiceDate
double totalAmount
Client client
+ generate()
}

Hotel "1" -- "0..*" Room
Room "1" -- "0..1" Reservation
Reservation "1" -- "1" Client
Invoice "1" -- "1" Client
@enduml

![image](https://github.com/hamouuz/uml_gestion_hotel/assets/118366904/5c5d1510-e803-4bbf-806c-8fc7d7b64256)


#Diagramme d’activité : 

@startuml
start
:Client initiates reservation;
:Check room availability;
if (Room available?) then (yes)
  :Reserve room;
  :Confirm reservation;
  :Record advance payment;
else (no)
  :Notify client;
endif
stop
@enduml

![image](https://github.com/hamouuz/uml_gestion_hotel/assets/118366904/5890b386-8fab-486c-b94a-35cb10e2ae8b)



#Diagramme de sequence :

@startuml
actor Client
participant "Reservation System" as RS
participant Hotel
participant Room

Client -> RS: Initiate reservation
RS -> Hotel: Check availability
Hotel -> Room: Check status
Room --> Hotel: Return availability status
Hotel --> RS: Return availability status
RS -> Client: Notify availability

Client -> RS: Confirm reservation
RS -> Room: Reserve room
RS -> Client: Reservation confirmed

Client -> RS: Make payment
RS -> Client: Payment recorded
@enduml

![image](https://github.com/hamouuz/uml_gestion_hotel/assets/118366904/d5d7a2bf-4f0a-40e3-8689-7ac5c02c311e)




