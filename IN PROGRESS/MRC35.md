# MRC 35 - Smart Function Callers as the Basis of Early Smart Agents

**Author(s)**: Teknium, karan4d

Link to Discord Discussion: [https://discord.com/channels/1151741790408429580/1215401416659832842/1238871504683401417](https://discord.com/channels/1151741790408429580/1238876323838165063)


## Summary

Morph-Caller is a state-of-the-art language model designed to perform function calling using a structured schema. It leverages a sophisticated system to parse and execute function calls, providing users with the ability to interact with the model in a more dynamic and utilitarian manner. The model differentiates itself by both excelling at function calling and also being unrestrained from model censorship.

## Capabilities
Morph-Caller excels in understanding and generating structured outputs based on function calling schemas. It can interpret user queries that involve function calls and respond with accurate and relevant information.
To interact with Morph-Caller, users should format their prompts according to the function calling schema provided in the repository below. The model can process these prompts and return structured data, making it an invaluable tool for developers and researchers who require programmatic access to language model capabilities.

## Community Expansion
We’re interested in Morph-Caller serving as the foundation for Smart Agents—to this end, we encourage discussion of tools, agents, and applications built using this model and future iterations.

## Dependencies 
[Hermes-Function-Calling Github Repo](https://github.com/NousResearch/Hermes-Function-Calling) - This repository covers the code, examples, and details behind the model’s predefined JSON schema for function calls. As a result, this is a dependency in the sense that it serves as a guide and tutorial for using the model.

[Morph Caller](https://huggingface.co/Morpheus-Function-Calling/Morph-Caller) - The model itself

[Morph Caller](https://huggingface.co/Morpheus-Function-Calling/Morph-Caller-GGUF) - The GGUF models (16 bit, 4 bit, 5 bit, 8 bit) for quantized universal inference

## New Weights Requested 
None at the moment—this may change with new model sizes, significant architectural changes, or otherwise. 

## Existing Weights
140,000 weights from MRI 2. This is not expected to change with iterative updates to new base models in the 7-10b category.

## Deliverables 
1) We plan to release iterative updates as new base models are released, which are covered by the existing weights.


## Background / Experience of Author / Implementer 
Teknium is a self taught AI expert on data-synthesis, post-training, and evaluations. He is known for creating the Hermes model series, the OpenHermes dataset, and reaching parity with multi-billion dollar companies' own tunes of their models through his work. Teknium formerly worked at Digi AI and Stability AI working on Stable Beluga at Carper LLM Lab. karan4d has been working on tuning, prompting, jailbreaking, and creating data for open-source LLMs since his initial encounters with gpt-2 in 2020. He previously worked on LAION's OpenAssistant, minted some of the earliest GAN and diffusion based NFTs, and popularized using LLMs-as-simulators with the creation of world_sim.

## Status
In Discussion

## Metadata
---
id: 35
title: Smart Function Callers as the Basis of Early Smart Agents
summary: Morph-Caller is a state-of-the-art language model designed to perform function calling using a structured schema. It leverages a sophisticated system to parse and execute function calls, providing users with the ability to interact with the model in a more dynamic and utilitarian manner. The model differentiates itself by both excelling at function calling and also being unrestrained from model censorship.
status: In Discussion
discussion_url: https://discord.com/channels/1151741790408429580/1215401416659832842/1238871504683401417
authors: ["Teknium", "karan4d"]
contact: 
keywords: ["smart agents"]
---