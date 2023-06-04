LMML (Language Model Markup Language) Standard

Version 1.0

1. Introduction

LMML (Language Model Markup Language) is an open standard for providing agential configuration to a predictive API call on any large language model. This document specifies the structure and syntax of LMML, enabling the creation of autonomous agents using large language model APIs in a standardized and interoperable manner.

2. LMML Engine

The LMML Engine acts as an interpreter between a standardized document format for autonomous agent configuration and the final text prompt fed to the API endpoint of a Large Language Model (LLM). It facilitates the interaction between users and AI agents by enabling the specification of prompts, system prompts, and desired outputs.

3. LMML Syntax

LMML documents are structured using XML-like tags. The following tags are defined:

3.1. `<LMML>`
   - The root element of an LMML document.
   - Contains the entire LMML configuration.

3.2. `<AGENT>`
   - Defines an AI agent within the LMML configuration.
   - Attributes:
     - `api`: Specifies the API provider for the agent.
     - `model`: Specifies the specific language model to be used.
     - `name`: Specifies the name of the agent.
     - `id`: Specifies a unique identifier for the agent.

3.3. `<SELF>`
   - Represents the agent's self-configuration.
   - Contains information about the agent's capabilities, purpose, and self-improvement mechanisms.

3.4. `<EXTEND>`
   - Allows the agent to extend its configuration from an external LMML document.
   - Attributes:
     - `src`: Specifies the URI of the external LMML document.

3.5. `<ABOUT>`
   - Provides a description of the agent's capabilities and characteristics.

3.6. `<MEMORY>`
   - Represents the agent's memory configuration.
   - Contains one or more `<TASK>` elements.

3.7. `<TASK>`
   - Defines a specific task or conversation context within the agent's memory.
   - Attributes:
     - `id`: Specifies a unique identifier for the task.
     - `name`: Specifies the name of the task.
     - `src`: Specifies the URI of an external LMML document for the task configuration (optional).

3.8. `<MESSAGE>`
   - Represents a message prompt within a task.
   - Attributes:
     - `id`: Specifies a unique identifier for the message (optional).
   - Contains the text of the prompt.

3.9. `<INPUT>`
   - Represents an input field within a message prompt.
   - Attributes:
     - `name`: Specifies the name of the input field.
     - `label`: Specifies a label for the input field.

3.10. `<OUTPUT>`
   - Represents the desired output or response within a task.
   - Contains one or more `<IMPERATIVE>` elements.

3.11. `<IMPERATIVE>`
   - Specifies an imperative or desired action for the agent to perform.
   - Attributes:
     - `name`: Specifies the name of the imperative.

4. Example LMML Document

The following example demonstrates the structure and syntax of an LMML document:

```xml
<LMML version="1.0">
    <AGENT api="openai" model="gpt-3.5-turbo" name="Researcher" id="researcher">
        <SELF>
            <EXTEND src="https://some.site/some/agent.lmml"></EXTEND>
            <ABOUT>You are a researcher who excels at generating search terms and finding lists of possible leads to solve a given problem or provide research reports on a recent topic. Leads are delivered in the form of a list of the most likely URLs. You

 can also find leads in the form of contacts. You self-improve through self-reflection and learning from mistakes.</ABOUT>
        </SELF>
        <MEMORY>
            <TASK id="search" name="Search">
                <MESSAGE id="">Search for "<INPUT name="" label=""/>"</MESSAGE>
                <OUTPUT>
                    <IMPERATIVE name="reflect">REFLECT</IMPERATIVE>
                    <IMPERATIVE name="mostlikely">MOST LIKELY</IMPERATIVE>
                </OUTPUT>
            </TASK>
            <TASK id="get_contact_details" src="./contact_finder.lmml"/>
        </MEMORY>
    </AGENT>
</LMML>
```

5. Conclusion

LMML provides a standardized approach for configuring autonomous agents using large language models. By adhering to the LMML standard, developers can create interoperable agents that can seamlessly interact with users and other agents. The LMML Engine serves as an interpreter, enabling the utilization of LMML documents to initiate AI prompt streams. The adoption of LMML promotes a more unified and efficient ecosystem for AI-assisted applications.

6. References

[Provide references and resources related to LMML and its implementations, if available.]

Please note that this document serves as a formal specification for the LMML standard and is subject to updates and revisions in future versions.
