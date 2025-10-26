## Data Flow Diagram — Property Booking System

This diagram shows how data flows between external entities, processes, and data stores for the core features:  
User Registration/Login, Property Search & Filtering, Property Viewing, Property Booking, Payment Processing, Booking Cancellation, and Admin Management.

```mermaid
flowchart TD
    %% External Entities
    User([User])
    Admin([Admin])
    PaymentGateway([Payment Gateway])
    PropertyOwner([Property Owner])

    %% Processes
    P1([User Registration and Login])
    P2([Search and View Properties])
    P3([Book Property])
    P4([Process Payment])
    P5([Manage Booking])
    P6([Admin Management])

    %% Data Stores
    D1[(User Database)]
    D2[(Property Database)]
    D3[(Booking Database)]
    D4[(Payment Records)]

    %% Data Flows
    User -->|Register/Login| P1
    P1 -->|Store user data| D1
    P1 -->|Authentication result| User

    User -->|Search criteria| P2
    P2 -->|Query properties| D2
    D2 -->|Property list| P2
    P2 -->|Display results| User

    User -->|Select property & enter details| P3
    P3 -->|Check availability| D3
    D3 -->|Availability status| P3
    P3 -->|Confirm booking| D3
    P3 -->|Proceed to payment| P4

    P4 -->|Send payment info| PaymentGateway
    PaymentGateway -->|Payment confirmation| P4
    P4 -->|Store payment data| D4
    P4 -->|Booking confirmation| User

    User -->|Cancel or modify booking| P5
    P5 -->|Update booking info| D3
    D3 -->|Updated status| P5
    P5 -->|Notify user| User

    Admin -->|Manage properties & users| P6
    P6 -->|Update records| D1
    P6 -->|Update property info| D2
    P6 -->|View reports| Admin
