%%-----------------------------------------------------------
%% USE CASE DIAGRAM — PROPERTY BOOKING SYSTEM
%%-----------------------------------------------------------

%% Define actors
actor User as U
actor Admin as A
actor "Payment System" as P

%% Define use cases
usecase "Register / Login" as UC1
usecase "Search & Filter Properties" as UC2
usecase "View Property Details" as UC3
usecase "Book Property" as UC4
usecase "Process Payment" as UC5
usecase "Cancel Booking" as UC6
usecase "Manage Properties (Add/Edit/Delete)" as UC7
usecase "View Reports" as UC8

%% Relationships: User interactions
U --> UC1
U --> UC2
U --> UC3
U --> UC4
U --> UC5
U --> UC6

%% Relationships: Admin interactions
A --> UC7
A --> UC8
A --> UC3

%% External system interaction
UC5 --> P

%% Optional relationship hints
UC4 --> UC5 : <<include>>  %% Payment is part of booking
UC4 --> UC6 : <<extend>>   %% Cancellation may follow booking
