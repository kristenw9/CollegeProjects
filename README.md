# College Projects <!-- omit in toc -->

Welcome to my portfolio of projects! This repository catalogs my coding journey throughout my college experience, with links to my publicly available work. For transparency, it also includes descriptions of private or group projects that currently cannot be shared publicly. 

These projects span various programming languages and demonstrate my skills in areas such as algorithms, system development, application design, and data analysis.

# Table of Contents <!-- omit in toc -->
- [Languages Included](#languages-included)
- [Notable Projects](#notable-projects)
  - [Cursive OCR Pipeline (Python)](#cursive-ocr-pipeline-python)
  - [Driver Incentive Web App (C#)](#driver-incentive-web-app-c)
  - [Serverless Account API (Node.js)](#serverless-account-api-nodejs)
  - [DevOps Migration CI/CD Pipeline (Kubernetes/Github Actions)](#devops-migration-cicd-pipeline-kubernetesgithub-actions)
  - [Mips Assembler \& CPU Simulator (C++ \& Java)](#mips-assembler--cpu-simulator-c--java)
- [Project Overview and Progression](#project-overview-and-progression)
- [Project Stats For Data Nerds](#project-stats-for-data-nerds)


## Languages Included
Most of my projects are backend-heavy, and therefore are categorized by their respective backend language, but my more comprehensive projects also include frontend language implementation.
- [Java](./Java)
- [Python](./Python)
- [C#](./C#)
- [C++](./C++)
- [C](./C)
- [Ocaml/Prolog](./Ocaml)
  
## Notable Projects


### Cursive OCR Pipeline (Python)

```mermaid
  flowchart TB
    %% A: Input Stage
    A[Image Dataset Directory] --> B

    %% B: Preprocessing Stage
    subgraph B[Preprocessing]
        direction LR
        B1[Progressive Downscaling] --> B2[Denoising]
        B2 --> B3[Anomaly Removal]
        B3 --> B4[Contrast Enhancement]
        B4 --> B5[Normalization]
    end

    B --> C

    %% C: Dataset Creation Stage
    subgraph C[Dataset Creation]
        direction LR
        C1[Line-level Segmentation] --> C2[Word-level Segmentation]
        C2 --> C3[Transcription Label Matching]
        C3 --> C4[Data Cleaning]
        C4 --> C5[Image Augmentation]
    end

    C --> D

    %% D: CRNN Model Stage (Simplified but Distinct)
    subgraph D[CRNN Model Architecture]
        direction LR
        subgraph D1[CNN]
            D1A[Convolutional Layers] --> D1B[BatchNormalization] --> D1C[MaxPooling]
        end
        D1C --> D2[Flattening]
        subgraph D3[RNN]
            D3A[Bi-directional LSTM] --> D3B[Dropout]
        end
        D3B --> D4[CTC Loss Layer]
    end

    D --> E

    %% E: Prediction Stage (Detailed)
    subgraph E[Prediction]
        direction LR
        E1[Raw Character Predictions] --> E2[Beam-Search Decoding]
        E2 --> E3[Confidence Scoring]
    end

    E --> F[Output]

```
   - **Overview**: A cursive handwriting recognition AI for historical documents.
   - **Tech Stack**: Python, TensorFlow, OpenCV, Matplotlib, Keras, Pandas
   - **Link**: Currently private, reach out to me for further details!
   - **Skills Demonstrated**: Image preprocessing, Data cleaning, AI, machine learning, and text extraction.
   - **Features**:
     - Custom image preprocessing pipeline
       - progressive downscaling
       - denoising
       - anomaly removal
       - contrast enhancement
       - normalization
     - Custom image segmentation and labeling pipeline 
       - Line level image segmentation with horizontal projection profiling
       - Word level image segmentation with vertical projection profiling
       - Transcription label matching
       - Data cleaning
       - Image augmentation for expanding the small training dataset
     - CRNN model architecture
       - CNN for feature extraction
       - RNN for sequential information processing
       - CTC loss for end-to-end training
     - Data visualization
       - Dataset analytics
       - Model performance and accuracy metrics
       - Segmentation and prediction overlays for debugging and analysis
### Driver Incentive Web App (C#)
```mermaid
sequenceDiagram
    participant User as Browser
    participant Auth as Authentication
    participant Dashboard as Dashboard
    participant Catalog as Catalog
    participant Reports as Reports
    participant Notify as Notifications
    participant DB as Database
    participant eBay as eBay API

    %% Authentication Block
    Note over User, eBay: User Authentication
    User->>Auth: Submit login credentials
    Auth-->>DB: Validate & fetch user roles
    alt 2FA enabled
        Auth->>Notify: Generate 2FA code
        Notify-->>User: 2FA code via SMS/Email
        User->>Auth: Submit 2FA code
        Auth-->>DB: Verify code
    end
    Auth-->>User: JWT token with role access
    
    %% Driver Role Block
    Note over User, eBay: Role Based Access
    User->>Dashboard: Access user dashboard
    %% Sponsor Role Block
    rect rgba(255, 253, 184, 0.3)  
    alt User is a Guest
    Dashboard-->>DB: Apply to be a driver
    end
    end
    rect rgba(189, 221, 189, 0.25)
    alt User is a Driver
    Dashboard<<-->>DB: Fetch driver data
    Dashboard->>Catalog: Access catalog
    Catalog<<-->>eBay: Fetch & return product listings
    Catalog-->>Dashboard: Display products
    Catalog-->>DB: Redeem points
    Catalog-->>Notify: Confirm order
    end
    end

    %% Sponsor Role Block
    rect rgba(184, 209, 255, 0.3)  
    alt User is a Sponsor
    Dashboard<<-->>DB: Fetch company data
    Dashboard->>Catalog: Manage Company Catalog
    Catalog <<-->> eBay: Update Catalog Listings
    Dashboard->>DB: Manage drivers & points
    Dashboard->>Reports: Generate reports
    Reports<<-->>DB: Fetch & return data
    Dashboard->>Auth: Impersonate drivers
    end
    end

    %% Admin Role Block
    rect rgba(237, 223, 255, 0.34) 
    alt User is a Admin
    Dashboard->>Reports: View reports & activity logs
    Reports<<-->>DB: Fetch analytics
    Dashboard->>DB: Manage Users
    Dashboard->>Auth: Impersonate roles
    end
    end

    %% Notifications Block
    Notify-->>User: Send email/SMS for updates

```
   - **Overview**: An enterprise-level web application for managing driver incentives and rewards, designed with a multi-tier architecture pattern with RESTful APIs, authentication services, and real-time reporting.
   - **Tech Stack**: C#, .NET Core, AWS, MySQL, Typescript, Nginx, Certbot, 
   - **Link**: [Driver Incentive Web App](./C#/DriverIncentive)
   - **Skills Demonstrated**: Full-stack development, cloud infrastructure management, API design, database operations, and accessibility compliance.
  
   - **Features**:
     - Points Management with real-time tracking, allocation, and redemption of driver reward points
     - Accessibility Compliance
       -  Screen reader support
       -  keyboard navigation
       -  accessible color profile themes
       -  light/dark mode
     - Website security 
       - 2FA with email and SMS verification
       - JWT-based authentication with claims-based authorization
       - SSL Encryption
       - Audit logging for all system operations
       - Automated AWS S3 database backups
     - Responsive design for mobile and desktop users
     - Account management and user preferences
     - Real-time dashboards with analytics and data visualization components
     - Dynamic product catalog with eBay API integration
     - Multi-tenant architecture with role-based access for administrators, sponsors, and drivers
     - Comprehensive reporting with PDF and CSV export capabilities
     - Automated database migrations, notifications, and real-time updates.

### Serverless Account API (Node.js)
```mermaid
sequenceDiagram
    participant User as Browser
    participant AccountAPI as Account Service API
    participant NotifyAPI as Notification Service API
    participant SDK as AWS SDK
    participant DB as DynamoDB

    %% Authentication Block
    Note over User, AccountAPI: User Authentication
    User->>AccountAPI: Submit login credentials
    AccountAPI->>SDK: Call DynamoDB Client
    SDK->>DB: Validate and fetch user data
    alt Account Found
        SDK-->>AccountAPI: User data retrieved
        AccountAPI-->>User: Login successful
        User->>AccountAPI: Update preferences
        AccountAPI->>SDK: Execute UpdateCommand
        SDK-->>DB: Update preferences
        SDK-->>AccountAPI: Preferences updated
        AccountAPI-->>User: Preferences updated
    else Account Not Found
        SDK-->>AccountAPI: No data found
        AccountAPI-->>User: Invalid login
    end

    %% Notification Block
    Note over User, NotifyAPI: Notification Handling
    User->>NotifyAPI: Send notification request
    NotifyAPI->>SDK: Call DynamoDB Client
    SDK->>DB: Fetch notification template
    alt Template Found
        SDK-->>NotifyAPI: Template retrieved
        NotifyAPI->>AccountAPI: Get user preferences
        AccountAPI->>SDK: Call DynamoDB Client
        SDK->>DB: Fetch preferences
        SDK-->>AccountAPI: Preferences retrieved
        AccountAPI-->>NotifyAPI: Send preferences
        NotifyAPI->>SDK: Log notification
        SDK-->>DB: Execute PutCommand
        SDK-->>NotifyAPI: Log successful
        NotifyAPI-->>User: Notification sent
    else Template Not Found
        SDK-->>NotifyAPI: No template found
        NotifyAPI-->>User: Invalid message ID
    end

    %% Account Management Block
    Note over User, AccountAPI: Account Management
    User->>AccountAPI: Create account
    AccountAPI->>SDK: Call DynamoDB Client
    SDK->>DB: Insert account data
    alt Success
        SDK-->>AccountAPI: Insert successful
        AccountAPI-->>User: Account created
    else Failure
        SDK-->>AccountAPI: Insert failed
        AccountAPI-->>User: Error creating account
    end

    %% Account Deletion Block
    Note over User, AccountAPI: Account Deletion
    User->>AccountAPI: Delete account request
    AccountAPI->>SDK: Call DynamoDB Client
    SDK->>DB: Delete account
    alt Success
        SDK-->>AccountAPI: Deletion successful
        AccountAPI-->>User: Account deleted
    else Failure
        SDK-->>AccountAPI: Deletion failed
        AccountAPI-->>User: Error deleting account
    end

```
   - **Overview**: A serverless backend using AWS SDK for managing user accounts and notifications. It includes account creation, preference updates, login, and notification handling based on user preferences stored in DynamoDB.
   - **Tech Stack**: Node.js, AWS Lambda, AWS DynamoDB, AWS SDK
   - **Link**: Currently private
   - **Skills Demonstrated**: Serverless architecture, AWS SDK usage, REST API development, error handling, and notification systems.
   - **Features**:
   - Integrated AWS SDK for DynamoDB with asynchronous commands for data handling.
   - Account management with endpoints for CRUD requests
   - Secure login using email and password, with guest access for limited features.
   - Dynamic notifications via email or SMS based on user preferences.
   - Comprehensive error handling with custom messages for invalid requests.
   - Detailed OpenAPI documentation for all endpoints.

### DevOps Migration CI/CD Pipeline (Kubernetes/Github Actions)
```mermaid
flowchart LR
    A[Developer Code] --> G[GitHub Repo]
    
    G --> |New| Y[Github Action Worker]
    G --> |Legacy| J[Jenkins]
    J --> |Manual| C
    Y --> |Automatic Execution| L

    subgraph L[Build]
      direction LR
      L1[Build BWCE App] --> L2
      L2[Build Container Image] --> L3[Package Artifacts]
      L3 --> T[Publish to JFrog]
      T --> |Automatic Deployment|O[Tanzu/Azure]
    end

    subgraph C[Legacy CI/CD Process]
      direction LR
      C1{Jenkins Script Execution}
      C1 --> C2[Build BWCE App]
      C1 --> C3[Build Container Image]
      C1 --> C4[Package Artifact]
      C4 -->E[Publish to Nexus]
      E --> |Manual Deployment|N[OpenShift]
    end
  
    classDef legacy fill:#ffcccc,stroke:#ff0000
    classDef new fill:#ccffcc,stroke:#00cc00
    
    class C,J legacy
    class L,Y new
```
   - **Overview**: A CI/CD pipeline for cloud migration of Tibco BWCE Apps from OpenShift & Jenkins to Tanzu & Azure with support for JFrog Artifactory migration from Nexus.
   - **Tech Stack**: Kubernetes, GitHub Actions, Jenkins, Azure, JFrog Artifactory, Openshift, Tanzu
   - **Link**: This project was completed during a Co-Op assignment and is not available for external viewing.
   - **Skills Demonstrated**: cloud migration, container orchestration, and CI/CD pipeline design.
   - **Features**:
     - Simplified, scalable interface through github actions
     - Template-style architecture 
     - Base level code uses kuberenetes standards for maximum cloud integration potential.

### Mips Assembler & CPU Simulator (C++ & Java)
```mermaid
stateDiagram
    %% MIPS Assembler States
    direction LR
    state MIPS_Assembler {
        [*] --> ReadingAssemblyFile
        ReadingAssemblyFile --> TokenizingInstructions
        TokenizingInstructions --> ParsingInstruction
        ParsingInstruction --> GeneratingBinary
        GeneratingBinary --> CombiningBinaryInstructions
        CombiningBinaryInstructions --> WritingBinaryFile
        WritingBinaryFile --> [*]
    }

    %% CPU Simulator States
    state CPU_Simulator {
        [*] --> LoadingBinaryProgram
        LoadingBinaryProgram --> InitMemory&Registers
        InitMemory&Registers --> GUI_State

        state GUI_State {
            [*] --> WaitingForUserInput
            WaitingForUserInput --> StartSimulation : Start
            WaitingForUserInput --> StepSimulation : Step
            WaitingForUserInput --> StopSimulation : Stop
            WaitingForUserInput --> QuitSimulation : Quit
            
            StartSimulation --> FetchingInstruction
            StepSimulation --> FetchingInstruction
            StopSimulation --> WaitingForUserInput
            QuitSimulation --> [*]
        }

        %% Main Execution Loop with Detailed Execution States
        FetchingInstruction --> DecodingInstruction

        state DecodingInstruction {
            [*] --> ALU_Operation : R-type
            [*] --> LoadStore_Operation : I-type
            [*] --> Jump_Operation : J-type
            
            ALU_Operation --> MemoryAccess : Executing Op
            LoadStore_Operation --> MemoryAccess : Executing Op
            Jump_Operation --> UpdatingProgramCounter : Executing Op
        }

        MemoryAccess --> WriteBack
        WriteBack --> UpdatingProgramCounter

        %% Loop Back or Terminate
        UpdatingProgramCounter --> GUI_State : Update GUI
        UpdatingProgramCounter --> [*] : End of Program
    }

    %% Transition between Assembler and Simulator
    MIPS_Assembler --> CPU_Simulator : Binary File
```

   - **Overview**: A two-part project consisting of a MIPS Assembler in C++ and an interactive CPU Pipeline Simulator in Java. The assembler translates MIPS assembly language instructions into 32-bit machine code, which is then executed by the CPU simulator. The simulator supports instruction cycle tracking, memory reads/writes, and ALU operations.
   - **Tech Stack**: C++, Java, JavaFX, SceneBuilder, Maven
   - **Link**: Currently private
   - **Skills Demonstrated**: System-level programming, MVC architecture, and simulation design
   - **Features**:
     - MIPS Assembler:
       - Supports R-type, I-type, and J-type instructions.
     - CPU Simulator:
       - Supports single-step and full-cycle execution modes.
       - Implements an observer pattern for real-time view updates.
       - Tracks detailed ALU and memory operations.
       - GUI with JavaFX for interactive simulation.

## Project Overview and Progression

This repository reflects my progression in coding skills across various domains:
- **Early Projects**: Focused on fundamental programming concepts and small-scale applications.
- **Intermediate Projects**: Applied object-oriented principles, data structures, and algorithms to more complex problems.
- **Advanced Projects**: Explored system-level programming, machine learning, and distributed systems.

## Project Stats For Data Nerds

**Project Distribution By Language**
```mermaid
sankey-beta
    Individual, Java, 8
    Individual, Python, 20
    Individual, C++, 20
    Individual, C, 27
    Individual, OCaml/Prolog, 4
    Group, Java, 1
    Group, C#, 1
    Group, Python, 2
    

```