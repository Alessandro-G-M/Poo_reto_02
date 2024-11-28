# POO_reto_02 Diagramas de clases: Banco

####  El sistema bancario representado por los diagramas de clases gestionan las operaciones de un banco, los empleados y los clientes a través de varias clases interconectadas. El Banco administra las cuentas de los clientes, gestiona a los empleados y realiza transferencias de fondos. Los Empleados del banco, como gerentes, guardias y cajeros, tienen distintos roles y responsabilidades, como gestionar cuentas, realizar transacciones y mantener la seguridad. Los Clientes pueden abrir y cerrar cuentas, realizar retiros, consultar saldos y solicitar préstamos. Además, las Cuentas pueden ser de ahorro o corrientes, con características específicas como intereses o sobregiros. El sistema asegura una correcta administración de cuentas, seguridad, pagos a empleados y atención al cliente,

### Composición de un Banco, con sus cuentas, clientes y empleados


```mermaid
classDiagram
    
    class Bank {
        +str id
        +str name
        +list employees
        +float money_held
        +manage_accounts()
        +transfer_funds()
        +manage_employees()
        +pay_employees()
    }

    class Employee {
        +str rank
        +float salary
        +str id
        +int hoursworked
        +recievePay()
        +get_in(time)
        +get_out(time)
    }

    class Account {
        +str acc_type
        +str acc_number
        +float money_held
        +bool is_blocked
        +tranfer_money()
        +get_balance()
        +update_account_info()
        +close_account()
    }

    class Client {
        +str acc_number
        +str client_name
        +open_account()
        +close_account()
        +withdraw_money()
        +check_balance()
        +log_in()
        +log_out()
        +apply_for_loan()
    }

    Bank "1" *-- "*" Employee : 
    Bank "1" *-- "*" Account : 
    Bank "1" *-- "*" Client : 

```

### Relaciones de clases

````mermaid
classDiagram

    class Bank {
    +str id
    +str name
    +list employees
    +float money_held
    +manage_accounts()
    +transfer_funds()
    +manage_employees()
    +pay_employees()
    }

    class Account {
        +str acc_type
        +str acc_number
        +float money_held
        +bool is_blocked
        +tranfer_money()
        +get_balance()
        +update_account_info()
        +close_account()
    }

    class Client {
        +str acc_number
        +str client_name
        +open_account()
        +close_account()
        +withdraw_money()
        +check_balance()
        +log_in()
        +log_out()
        +apply_for_loan()
    }

    Client "" --> "" Account: manage()
    Bank "" --> "" Account: operate()
````

### Relaciones Cuentas y empleados (herencias)

````mermaid

classDiagram

    Account <|-- SavingsAccount
    Account <|-- CheckingAccount
    Employee <|-- Manager
    Employee <|-- Guard
    Employee <|-- Cashier

    class Account {
        +str acc_type
        +str acc_number
        +float money_held
        +bool is_blocked
        +tranfer_money()
        +get_balance()
        +update_account_info()
        +close_account()
        +deposit()
        +withdraw()
    }

    class SavingsAccount{
        +float interest_rate
        +float minimum_balance
        +str last_interest_date
        +apply_interest()
        +calculate_balance_interest()
    }

    class CheckingAccount{
        +float overdraft_limit
        +float montly_fee
        +bool cheque_book_available
        withraw_w_overdraft()
        charge_montly_fee()
    }

    class Employee {
        +str rank
        +float salary
        +str id
        +int hoursworked
        +recievePay()
        +get_in(time)
        +get_out(time)
    }

    class Manager{
        +str department
        +list employee_list
        +float bonus_percentage
        +assign_task()
        +evaluate_performance() 
    }

    class Guard{
        +str shift_schedule
        +str assigned_area
        +bool weapon_permit
        +patrol_area()
        +report_incident()
        +check_cameras()
    }

    class Cashier{
        +int stransaction_count
        +float service_rating
        +str clearance_level
        +process_deposit()
        +process_withdrawal()
        +generate_receipt()

    }
````

### Diagrama completo

````mermaid
classDiagram

    Account <|-- SavingsAccount
    Account <|-- CheckingAccount
    Employee <|-- Manager
    Employee <|-- Guard
    Employee <|-- Cashier
    
    class Bank {
        +str id
        +str name
        +list employees
        +float money_held
        +manage_accounts()
        +transfer_funds()
        +manage_employees()
        +pay_employees()
    }

    class Employee {
        +str rank
        +float salary
        +str id
        +int hoursworked
        +recievePay()
        +get_in(time)
        +get_out(time)
    }

    class Account {
        +str acc_type
        +str acc_number
        +float money_held
        +bool is_blocked
        +tranfer_money()
        +get_balance()
        +update_account_info()
        +close_account()
    }

    class Client {
        +str acc_number
        +str client_name
        +open_account()
        +close_account()
        +withdraw_money()
        +check_balance()
        +log_in()
        +log_out()
        +apply_for_loan()
    }

    class Manager{
        +str department
        +list employee_list
        +float bonus_percentage
        +assign_task()
        +evaluate_performance() 
    }

    class Guard{
        +str shift_schedule
        +str assigned_area
        +bool weapon_permit
        +patrol_area()
        +report_incident()
        +check_cameras()
    }

    class Cashier {
        +int transaction_count
        +float service_rating
        +str clearance_level
        +process_deposit()
        +process_withdrawal()
        +generate_receipt()
    }

    class SavingsAccount {
        +float interest_rate
        +float minimum_balance
        +str last_interest_date
        +apply_interest()
        +calculate_balance_interest()
    }

    class CheckingAccount{
        +float overdraft_limit
        +float montly_fee
        +bool cheque_book_available
        withraw_w_overdraft()
        charge_montly_fee()
    }

    Bank "1" *-- "*" Employee : 
    Bank "1" *--> "*" Account : operate()
    Bank "1" *-- "*" Client : 
    Client "" --> "" Account: manage()
````

