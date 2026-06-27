# COMMANDS

Open  2 Tabs on terminal and on first tab the cmds you need to write is Ollama serve

```
ollama serve
```

The `ollama serve` command **starts the local Ollama background server, turning your machine into an AI host.
Think of it as the backend service of Ollama.**

## on tab 2 run these cmds

```
ollama --version

jigneshsingh@jigneshs-MacBook-Air ~ % ollama --version
ollama version is 0.30.10
```

**The command `ollama --version` simply prints the currently installed version of the Ollama software in your terminal or command prompt.**

```
**ollama ps**

jigneshsingh@jigneshs-MacBook-Air ~ % ollama ps
NAME               ID              SIZE      PROCESSOR    CONTEXT    UNTIL              
llama3.2:latest    a80c4f17acd5    2.5 GB    100% GPU     4096       4 minutes from now    
```

The `ollama ps` command **displays a list of all AI models that are currently active in your system's memory (RAM or VRAM)**. It acts like the `ps` command in Linux but specifically tracks Ollama's local LLMs. 

```
**ollama list**

jigneshsingh@jigneshs-MacBook-Air ~ % ollama list
NAME               ID              SIZE      MODIFIED   
llama3.2:latest    a80c4f17acd5    2.0 GB    6 days ago    ****
```

The `ollama list` command (or `ollama ls`) **displays a complete inventory of all the AI models currently downloaded and stored on your local machine**. 

```
**ollama show llama3.2**

jigneshsingh@jigneshs-MacBook-Air ~ % ollama show llama3.2
  Model
    architecture        llama     
    parameters          3.2B      
    context length      131072    
    embedding length    3072      
    quantization        Q4_K_M    

  Capabilities
    completion    
    tools         

  Parameters
    stop    "<|start_header_id|>"    
    stop    "<|end_header_id|>"      
    stop    "<|eot_id|>"             

  License
    LLAMA 3.2 COMMUNITY LICENSE AGREEMENT                 
    Llama 3.2 Version Release Date: September 25, 2024    
    ...                                                   

jigneshsingh@jigneshs-MacBook-Air ~ % 

```

The command `ollama show llama3.2` **displays the technical specifications, architecture, parameters, and capabilities of the Llama 3.2 model installed on your system**

```
**ollama run llama3.2**

jigneshsingh@jigneshs-MacBook-Air ~ % ollama run llama3.2
>>> hello llama
Hello! It's nice to meet you. I'm here to help and chat with you about anything that's on your mind. How can I assist you today?

```

The `ollama run llama3.2` command **downloads and launches Meta's Llama 3.2 AI model directly on your local machine**. It sets up a local interactive chat session in your terminal, letting you run the AI entirely offline without relying on cloud servers. 

```
ollama rm llama3.2 
```

The command `ollama rm <model>` **permanently deletes a locally stored Large Language Model (LLM) and its associated files from your computer's hard drive**,