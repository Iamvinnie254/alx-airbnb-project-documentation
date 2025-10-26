## Flowchart — User Registration Process

This flowchart illustrates the backend workflow for handling user registration in the Property Booking System, from form submission to account creation and confirmation.

```mermaid
flowchart TD
    %% Start and End
    A([Start]) --> B[User fills in registration form]

    %% Input Validation
    B --> C{Are all fields valid?}
    C -- No --> D[Show error message to user]
    D --> B
    C -- Yes --> E[Hash the user's password]

    %% Database Operations
    E --> F[Check if email already exists in User Database]
    F -->|Exists| G[Display “Email already registered” message]
    G --> B
    F -->|Does not exist| H[Save new user data in User Database]

    %% Confirmation
    H --> I[Send verification email to user]
    I --> J{Did email send successfully?}
    J -- No --> K[Log error and retry sending]
    K --> I
    J -- Yes --> L[Display registration success message]
    L --> M([End])
