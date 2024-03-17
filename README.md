Zip File Processor for Databricks

This Scala script is designed for use in Databricks notebooks to automate the extraction of ZIP files stored in DBFS (Databricks File System). It filters out previously processed files, extracts new ZIP files to a specified directory, and logs processed files to prevent redundant operations.

Features

ZIP File Identification: Automatically identifies ZIP files in a specified DBFS directory.
Duplicate Avoidance: Keeps a log of processed ZIP files to prevent re-processing.
Extraction & Logging: Extracts new ZIP files to a specified location and logs their names.
Requirements

Databricks Runtime environment with Scala support.
Access to DBFS paths where ZIP files are stored and where extracted files will be placed.
Sufficient DBFS storage space for extracted content.
Setup

Import the Script: Copy the provided Scala script into a Databricks notebook.
Configure Paths: Set directoryPathDbfs, extractionPathDbfs, and processedFilesLogPath to your specific DBFS paths.
Usage

Initialization: Ensure all paths (directoryPathDbfs, extractionPathDbfs, and processedFilesLogPath) are correctly set to your DBFS structure.
Execution: Run the notebook or call the extractZipFromDbfsToDbfs function directly with the appropriate parameters.
Monitoring: Check the output for processing logs and errors.
Functions

readProcessedFilesLog(logPath: String): Set[String]: Reads the log file at logPath and returns a set of processed file names.
appendToProcessedFilesLog(logPath: String, fileName: String): Appends a fileName to the log file at logPath.
extractZipFromDbfsToDbfs(directoryPathDbfs: String, extractionPathDbfs: String, processedFilesLogPath: String): Main function to process new ZIP files from directoryPathDbfs, extract them to extractionPathDbfs, and log the processed files in processedFilesLogPath.
Notes

Temporary Directory: The script uses a temporary directory on the local file system for extraction. Ensure the Databricks cluster has enough local storage to accommodate the extracted files.
Error Handling: The script includes basic error handling. Customize the error handling logic as needed for your use case.
DBFS Paths: All paths should be in DBFS format. For example, dbfs:/mnt/my-data/.
