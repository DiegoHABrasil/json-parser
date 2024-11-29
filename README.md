⚙️ Project: Multithreaded JSON Parser (C)
Objective:
Create a program that efficiently parses a large JSON file by dividing the workload among multiple threads. Each thread processes a different part of the JSON, enabling faster overall processing.

🛠️ Project Outline:
1. JSON Chunking and Thread Management:
Divide the JSON file into chunks:
Split the file into manageable segments, ensuring each chunk starts and ends at a valid JSON boundary (e.g., objects or arrays).
Create and manage threads:
Use pthread to spawn threads for processing different chunks concurrently.
2. Parsing Logic:
Thread-Specific Parsing:
Each thread parses its assigned chunk. You can use a JSON library like Jansson or cJSON to simplify parsing.
Handle nested structures:
Ensure that nested objects or arrays spanning chunks are correctly handled by combining partial data.
3. Synchronization and Data Aggregation:
Combine results:
Use mutexes to protect shared resources when threads merge their partial results (e.g., constructing a final data structure).
Handle shared structures:
Ensure threads safely add parsed data to a global structure or database.
🔑 Key Concepts to Explore:
Thread Synchronization:
Protect shared data structures using mutexes (pthread_mutex_t), ensuring data integrity when threads write concurrently.

Memory Management:
Handle dynamic memory allocation carefully to avoid leaks or corruption when threads parse and store data.

Error Handling:
Implement robust error handling for scenarios like invalid JSON or file read errors.

Boundary Handling:
Ensure that each thread’s chunk is correctly aligned with JSON objects or arrays to avoid parsing errors.

**🧠 Steps Breakdown:
File Reading and Splitting:

Read the file in chunks of a fixed size.
Adjust chunk boundaries to ensure valid JSON syntax (e.g., ensuring you don’t split within an object or string).
Thread Implementation:

Create worker threads using pthread_create.
Each thread parses its chunk and extracts relevant information.
Combine Results:

Use thread-safe data structures (protected by mutexes) to merge partial results.
Combine or print the parsed data once all threads finish processing.
💡 Bonus Challenges:
Parallel Data Extraction:
Extract specific fields (e.g., all names or IDs) from a massive JSON array of objects.

Performance Benchmarking:
Compare your multithreaded parser with a single-threaded version to measure performance gains.

Error Recovery:
Handle errors gracefully if a thread encounters an invalid JSON section.

🔍 Example Workflow:
Load JSON File: Split a large JSON file into equal-sized chunks.
Thread Processing: Each thread parses one chunk independently.
Merge Results: Combine parsed data from all threads into the final structure.
