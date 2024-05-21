# uml_gestion_hotel

Diagramme use case: 

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
