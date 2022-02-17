Mermaid Experiments
===================

Experimenting with Mermaid diagrams for documentation


New User Log-In
---------------


```mermaid
sequenceDiagram
    autonumber
    participant User as Joe User
    participant Portal
    participant DB as Postgres
    participant CAS
    participant LDAP

    User ->> Portal: Requests Home Page
    Note right of Portal: The redirection is actually more complex:<br/> / → /login → /auth/cas → CAS itself
    Portal -->> User: redirects to CAS authentication
    User -->> CAS: 
    CAS -->> User: Returns CAS authentication page
    User ->> CAS: Logs in

    Note right of CAS: CAS likely depends on<br/> LDAP and other services,<br/> but we are not concerned<br/> with those details.
    %% CAS -->> LDAP: looks up user
    %% LDAP -->> CAS: returns user information
    
    Portal -->> DB: Looks up User
    DB -->> Portal: returns no results
    Portal -->> LDAP: looks up User
    LDAP -->> Portal: Returns user information
    Portal -->> DB: Creates user record
    Portal -->> User: Returns home page
```


Visualizing Statistics
----------------------


```mermaid
pie title Campus Populations
    "Employees"     : 50021
    "Contractors"   : 10397
    "Students"      : 192252
```





Cron Jobs
---------

It doesn't look like Gantt charts will work for visualizing cron jobs, yet.  They apparently can't use anything other than specific dates.  

```mermaid
gantt
dateFormat HH:MM
section UC Path
6AM Update   :done,    job6am, 6AM,1m
9AM Update   :done,    job9am, after job6am,1m
section Blazer
Parallel 1   :         job6pm, after job9am, 1m
Parallel 2   :         des4, 6AM Update, 1m
%% Parallel 3   :         des5, after des3, 1m
%% Parallel 4   :         des6, after des4, 1m
section Reports
Parallel 1   :         job6pm, after job9am, 1m
Parallel 2   :         des4, 6AM Update, 1m

```
