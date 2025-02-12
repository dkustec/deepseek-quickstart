### DeepSeek Quick Start Tutorial 🐋  
#### Overview  
 - This repository contains a powerful coding assistant application that integrates the DeepSeek API, capable of handling user conversations and generating structured JSON responses. Users can read local file content, create new files, and modify existing files in real time through a command-line interface.  

#### Key Features  

1. **DeepSeek Client Configuration**  
   - Automatically configures the API client to connect to DeepSeek services using a valid `DEEPSEEK_API_KEY`.  
   - Streams GPT-style responses based on the DeepSeek endpoint specified via environment variables.  

2. **Data Models**  
   - Uses Pydantic for type-safe file operations, including:  
     - **FileToCreate**: Describes files to create or update.  
     - **FileToEdit**: Describes code snippets to replace in existing files.  
     - **AssistantResponse**: Structured chat responses with optional file operations.  

3. **System Prompt**  
   - A comprehensive system prompt (`system_PROMPT`) guides conversations to ensure strict adherence to JSON output formats, including file creation/editing instructions.  

4. **Utility Functions**  
   - **`read_local_file`**: Reads and returns the content of a specified file as a string.  
   - **`create_file`**: Creates/overwrites files with user-provided content.  
   - **`show_diff_table`**: Displays proposed file changes in a tabular format.  
   - **`apply_diff_edit`**: Applies snippet-level modifications to existing files.  

5. **`/add` Command**  
   - Use `/add path/to/file` to quickly read a file's content and insert it into the conversation.  
   - Use `/add path/to/folder` to add all files in a directory (excluding binaries/hidden files) to the conversation.  

6. **Conversation Flow**  
   - Maintains a `conversation_history` list to track user/assistant messages.  
   - Streams assistant responses via the DeepSeek API, parsed into JSON for text replies and file operation instructions.  

7. **Interactive Session**  
   - Run the script (e.g., `python3 main.py`) to start an interactive loop.  
   - Enter requests or coding questions; use `/add path/to/file` to inject file content.  
   - Approve/reject file changes when proposed by the assistant.  
   - Type `exit` or `quit` to end the session.  

#### Quick Start  
0. If you don’t have a `DEEPSEEK_KEY`, register at [https://api-docs.deepseek.com/](https://api-docs.deepseek.com/) (takes ~5 minutes). New accounts typically receive 10 CNY credits.  

1. Configure the `.env` file with your DeepSeek API key:  
   ```plaintext  
   DEEPSEEK_KEY=your_api_key_here  
   ```  

2. Install dependencies and run (choose one method):  

   - **Using pip**:  
     ```bash  
     git clone --depth 1 https://github.com/dkustec/deepseek-quickstart  
     pip install -r requirements.txt  
     python3 main.py  
     ```  

3. Experience features like multi-line streaming responses, `/add path/to/file` for file injection, and precise file edits after approval.  

#### Reasoning Edition (`main-r1.py`)  

The `main-r1.py` script uses DeepSeek’s reasoning model (`deepseek-reasoner`) with **Chain-of-Thought (CoT)** support:  
- Displays reasoning steps before final answers.  
- Retains all file operations and diff-editing capabilities.  
- Shows intermediate reasoning while logging only final conclusions.  

Start with `python3 main-r1.py` for an enhanced reasoning experience.  

> **Note**: This is an experimental project by **xiaomingx** to test DeepSeek v3 API features. Use as a rapid prototyping tool with caution.  

# Official Resources  
 - Official DeepSeek repository: [https://github.com/deepseek-ai](https://github.com/deepseek-ai)  
 - *I’m still exploring the API myself!* 🚀
