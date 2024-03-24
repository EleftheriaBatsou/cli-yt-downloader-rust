## Quick explanation of the structure and logic.

### **main.rs**

1. **Dependencies**: The main.rs file imports the necessary external crates and local modules (download.rs and errors.rs) with mod statements.
2. **Command Line Interface (CLI) Setup**: It uses the clap crate to set up command-line argument parsing for the CLI application. Command-line arguments are parsed using the Arg struct from the clap crate.
3. **Main Function**: The main function is the entry point of the program. It first parses the command-line arguments provided by the user. Then, it retrieves the values of these arguments and sets default values if not provided.
4. **Debugging**: If the DEBUG flag is set to true, debug information is printed to the console.
5. **Mode Selection**: Based on the mode specified by the user (auto or audio), it calls the corresponding function from the download module to start the download process.
6. **Error Handling**: If invalid mode or missing required arguments are detected, it calls the create_end function from the errors module to print an error message and exit the program.

### **download.rs**

1. **Dependencies**: Imports external crates (reqwest and serde_json) required for HTTP requests and JSON parsing.
2. **Type Aliases**: Defines a Result type alias for handling errors.
3. **Auto and Audio Functions**: Contains auto and audio functions for initiating the download process. These functions construct a request body, send an HTTP POST request to a specified API URL, and handle the response.
4. **getstream Function**: Sends an HTTP POST request to the API URL to get the stream URL for downloading the video or audio. It handles response parsing and error checking.
5. **downloadfromstream Function**: Downloads the video or audio stream from the provided URL and saves it to the specified path. It handles file creation, content copying, and error handling.

### **errors.rs**

**Error Handling Function**: Defines a function create_end to print error messages and exit the program. It takes a message string as input, prints it to the console, and exits the program.

Overall, the program uses HTTP requests to communicate with an API for fetching video/audio stream URLs, downloads the streams using reqwest, and saves them to the specified path. It utilizes command-line arguments for user configuration and clap for parsing these arguments. Error handling is implemented to handle invalid user input or HTTP request failures gracefully.

### **To run it:**

`cargo run -- -m auto -u "https://www.youtube.com/watch?v=dQw4w9WgXcQ"`

You can download any video you want. In the example above I'm using only the mandatory features (`-m auto -u `) but you can make many modifications.
