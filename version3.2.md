Data Collection and Section Classification Framework for Government Web Services by Weaven Inc.
# AI-Oriented UI Component Classification Guide v3.2
- Date: August 2025
- Authors: Prof. Hanjin Lee’s Research Team (Researchers: Son Gyeom, Kim Seoyeon, Hanjin Lee)

### 1. Core Philosophy and Principles
The goal of this guide is to provide a standardized classification framework that enables AI systems to learn the UI structures of Korean government websites efficiently and consistently. All analysis follows the principles outlined below.

- AI-First Approach: The criteria for classification are based not on human semantic interpretation but on the similarity of visual patterns as recognized by AI.
For example, visually similar components such as “bulletin board lists” and “simple tables,” even if semantically different, are both classified as Board_List to minimize confusion during AI training.

- Three-Stage Analysis Pipeline
Every section must be analyzed using the following three-step process:
	1.	Section Definition
	2.	Layout Analysis
	3.	Component Analysis
This structure guides AI to reason progressively from macro-level layouts to micro-level functional elements.

- Attribute System : To prevent uncontrolled creation of new component types and to maintain flexibility within the classification schema, all visual and functional variations must be expressed using supplementary attributes.

### 2. Detailed Explanation of the Three-Stage Analysis Pipeline
All section images must be analyzed according to the steps below.

- Stage 1: Section Definition
  - Criteria: Define the positional context that the section occupies within the overall webpage.
  - Types: Header, Body, or Footer. If the footer is visually divided into multiple blocks, it may be further subdivided as Footer-Block1, Footer-Block2, etc.
- Stage 2: Layout Analysis
  - Criteria: Describe how the major component clusters within the section are visually arranged.
  - Format: {layout: "layout-type"}
- Stage 3: Component Analysis
  - Criteria: Identify all functional components composing the section, including their combinations and detailed attributes.
  - Format: ComponentA + ComponentB + ...
  - Supplementary Attributes:
    - {style: “style-type”} Defines visual variations of a component(e.g., vertical, button, word-cloud)
	  - {contains: “component”} Indicates that one component contains another
	  - {interactive: true/false} Specifies whether functional interactions exist between components
	  - {content: “content-type”} Describes the type of content included (e.g., social-hub)

### 3. Tie-Breaking Rules (Priority Decision Principles)
When a component potentially fits multiple definitions, the following rules must be applied in order, ensuring consistent and confusion-free classification for AI. These rules function as the core decision-making algorithm, enabling AI to behave like a human expert in ambiguous cases.

- Rule 3.1: Container-First Principle
  - Description: If a component acts as a container holding other components, the container must take priority over the contents during classification.
  - Purpose: To encourage AI to identify the macro-structure of a page before focusing on individual elements—similar to identifying a living room before noticing the furniture within it.
  - Example: If a Tab_Menu contains a Board_List, the component should be classified as Tab_Menu, with the attribute
- Rule 3.2: Core Pattern Principle
  - Description: The most essential core visual pattern defined for each component must serve as the final criterion for classification.
  - Purpose: To prevent misclassification caused by minor design differences and to ensure that components are identified based on their fundamental structure.
  - Example: Even if a bulletin board list includes thumbnail images, if its primary structure follows the core pattern of repeating horizontal text blocks, it should be classified as Board_List, not Board_Tiled.

