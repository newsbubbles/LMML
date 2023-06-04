# LMML
LMML (Language Model Markup Language) is a proposed and open standard for giving agential configuration to a predictive API call on any large language model. As it is an open standard, we invite anyone to join, fork, and contribute to this repository.

## The LMML Engine
The LMML Engine acts as an interpreter between a standardized document format for autonomous agent configuration and the final text prompt fed to the API endpoint of a Large Language Model. In other words, as the world of AI assisted applications builds up, [Prompting is Programming](https://arxiv.org/abs/2212.06094); meaning that in order to get the results one wants directly from an LLM (Large Language Model), one has to know exactly how to warm up the model with system prompts, and coerce the model to output what one wants.

In short, the niche that LMML Engine fits is to Agentialize and intialize AI prompt streams (conversations with different chat agents) that can be defined by an LMML document sitting at a standard internet URI. The LMML Engine can power a new type of chat based browser that simply loads in LMML documents and then uses the user's own API credentials from the user device to perform API calls, or uses the App developer credentials from the server.

## Why another standard?

I am of the opinion that HTML is a language which is easy to learn, concise, and serves a purpose of showing a web page. Prompting, being the future of programming is going to need some standards that put this explosion of prompt types and state-of-the-art into an easy to remember and reference format which has all of the caveats of a web browser. The future of AI and AGI based agents online will be an open standard, and we might as well stick closely to one we already know.

## What does LMML look like?

It looks a lot like HTML except it is tailored toward the types of things people want to put into a prompt for a large language model such as Chat-GPT, 

```xml
<LMML version="1.0">
	<AGENT api="openai" model="gpt-3.5-turbo" name="Researcher" id="researcher">
		<SELF>
			<EXTEND src="https://some.site/some/agent.lmml"></EXTEND>
			<ABOUT>You are a researcher who excels at generating search terms and finding lists of possible leads to solve a given problem or provide research reports on a recent topic. Leads are delivered in the form of a list of the most likely URLs. You can also find leads in the form of contacts. You self improve through self reflection and learning from mistakes.</ABOUT>
		</SELF>
		<MEMORY>
			<TASK id="" name="Search">
				<MESSAGE id="">Search for "<INPUT name="" label=""/>"</MESSAGE>
				<OUTPUT>
					<IMPERATIVE name="reflect" >REFLECT</IMPERATIVE>
					<IMPERATIVE name="mostlikely">MOST LIKELY</IMPERATIVE>

				</OUTPUT>
			</TASK>
			<TASK id="get_contact_details" src="./contact_finder.lmml"/>
		</MEMORY>
	</AGENT>
</LMML>
```
