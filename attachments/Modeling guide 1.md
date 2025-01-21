# Content
1. [[#General]]
2. [[#Elements description]]
3. [[#Architecture]]
5. [[#Working with the model]]
8. [[#Modeling good practices]]

# General
Gaphor, enhanced with the SELT plugin, transforms diagrams into dynamic, interconnected models. Every element added to the diagramming window is automatically stored in the model database, allowing for seamless reuse across multiple diagrams. Any changes made to an element are propagated throughout the entire model, ensuring consistency. This functionality is especially valuable for projects that require frequent updates to model elements, as it simplifies modifications and maintains integrity across all diagrams. By using a model-based approach, you can create concise, readable diagrams—**ideally with no more than nine elements per diagram**. While this means you may need several diagrams to comprehensively describe your system, the ability to reuse existing elements eliminates redundancy and reduces the errors. This practice also supports traceability; for instance, if a requirement changes, you can easily identify and manage its impact across the entire system.

[[L1.png]] [[L2.png]]

# Core elements semantic
The **Systems Engineering Lightweight Toolkit (SELT)** approach emphasizes simplicity, clarity, and universal applicability in modeling. Key elements in this methodology are:
- **System**: The overarching entity being modeled, interacting with external entities (e.g., stakeholders or other systems) within a defined environment.
- **Sub-System**: A major structural or functional part of the system, enabling its overall operation.
- **Component**: The smallest, specific part of a sub-system, responsible for a precise function or operation.
- **Interface**: The connection point defining interactions between systems, sub-systems, or components. Interfaces may include data exchange, signals, or physical connections. Represent interfaces in the application using arrows, labeled to specify their purpose (e.g., "User Input" or "Power Delivery"). The "Technology" field specifies the interface. 
- **Person**: Captures stakeholder involvement and interaction with the system, ensuring the model reflects human or organizational influences. Each person you put in the model is your system **stakeholder** 
- **UniBlock**: A flexible, adaptable artifact used to represent any system-related element during the early or abstract phases of modeling. You can specify specify block type within the "Technology" field.
- **File item**: Is the reference to any document you decide to put in the model. It could be ConOps image, spreadsheet calculation, FEM analysis report and etc.

# Architecture
The model is the foundation of your project, serving as a reference point for mutual understanding among all stakeholders. It ensures clarity, helps uncover hidden challenges, and identifies potential requirements. By maintaining a clear and relevant core model, you create a **single source of truth** for your team, answering questions about each member's responsibilities within the system.

For a team of 5-6 people working on the course project, the model acts as a baseline that facilitates a shared vision of the system.

The methodology focuses on architecture as a **component view** of the system, supplemented by functional descriptions if needed.

**Architecture Levels:**  
There are three levels of detail in the architecture:

1. **System Level**
2. **Sub-system Level**
3. **Component Level**

These levels are explained in detail in the previous chapter. At each level, the modeler can use various element types to depict the composition of the system at that level.

**Key Practices for Modeling:**

- At the **System Level**, focus on the functional interactions between the system and external actors, such as the operator.
- At the **Sub-system Level**, zoom in to show specific sub-systems and their interactions with the operator or other key elements.
- Only include elements that are critical for the particular diagram.

For example:

- At the system level in a CubeSat project, show how the entire CubeSat interacts with the operator.
- At the sub-system level, illustrate the specific sub-system (e.g., the communication module) that interacts with the operator.

The definition of the "system" depends on the scope and granularity you choose. For instance, in the CubeSat example, the "system" block might represent the CubeSat as a whole, while additional systems (e.g., payload, communication, or power) can be detailed within it.

By following this structured approach, your model will effectively communicate the system’s architecture and its relationships across different levels of detail.

# Working with the model

To ensure smooth collaboration and effective system modeling in your project, follow these steps:

1. **Assign a System Engineer**
    
    - Each team should appoint a system engineer, usually the team leader, who will manage the modeling process.
    - While planning, architecture definition, and design decisions are a team effort, the system engineer plays a critical role by organizing project workflows and maintaining the baseline model for designers or structural engineers.
2. **Set Up a Shared Project Folder**
    
    - The system engineer should create a shared project folder and provide access to all team members.
    - It’s recommended to use **GitHub**, which offers free collaboration tools, version control, and a user-friendly GUI.
    - Alternatively, shared folders on platforms like **Google Drive** or **Yandex Disk** can be used, though they may introduce risks of version misalignment.
3. **Organize and Save Project Files**
    
    - Save the model in the project folder along with all relevant information, such as technology references, calculations, FEM analysis reports, and ConOps visuals.
    - For projects with more than 20 files, it’s helpful to include reference links within the model to quickly access key documents.
4. **Control Model Changes**
    
    - To ensure consistency, team members should only view the model in **read-only mode**.
    - The system engineer should be the sole person authorized to make changes.
    - This approach minimizes errors and prevents issues related to untracked changes, maintaining the model as the **single source of truth**.
5. **Use the Model in Review Presentations**
    
    - Leverage the model during review presentations to enhance stakeholder understanding.
    - The SELT tool’s primary purpose is to facilitate mutual understanding across all project stakeholders.
    - Consider creating a **Navigation Diagram** to structure and present your system engineering data effectively.

# Modeling good practices
1. **Keep Diagrams Simple**
    
    - Limit your diagrams to **fewer than 9 elements** to ensure clarity and readability.
    - For detailed system descriptions, use **encapsulation** (drill down into individual elements) or create **multiple diagrams** to provide different views of the system.
2. **Add Metadata for Exports**
    
    - When exporting a diagram, include a **metadata item** that records its creation and last update dates. This ensures traceability and clarity during reviews.
3. **Ensure Diagrams Are Self-Explanatory**
    
    - All dependencies in your diagram should have **meaningful names** that explain their purpose.
    - Component architecture blocks should include descriptions of the **functions** they perform.
4. **Use Legends for Repeated Elements**
    
    - If your diagram includes dependencies with the same meaning (e.g., hierarchical connections) or repeated blocks (e.g., use cases or needs), add a **legend** using a "Comment" item. This makes your diagram easier to interpret.
5. **Organize System Artifacts**
    
    - Group related system artifacts (e.g., requirements, needs, design alternatives) within a single **package** to maintain structure and streamline navigation.