# cedarlog
Log file generator for Python

## Overview
A Python module that contains a single function to generate a log file for capturing print output from a main Python program.

Essentially the function works as follows:

**Opening the Log File**
- First it grabs the system date / time.
- Then it generates  a log file name by prefixing the date / time to a user-defined log file title.
- It then redirects the Python standard ouput to the generated log file.

**Closing the Log File**
- The function closes the log file and reverts the Python standard ouput back to default.
- It then reads back the saved log file and prints it to the default standard ouput.

## Calling the Function
As an example, place the following lines in your main program.

First load the module:

    # Local imports
    import cedarlog

Then set the variables for your desired log file title and folder location:

    log_file_title = 'Log_File_Example_Title' # Sys date and time will be prefixed
    log_file_location = "log_files" # Relative path


In your main() code:

    def main (your_param1, your_param2, etc, log_file_title, log_file_location):

      # Open log file and store the returned log file parameters (returned as a tuple)

      log_file_params=cedarlog.use_log_file(switch='open', title=log_file_title, location=log_file_location)

      ...

      <Your main code here>

      ...

      # Close log file. Grab values for log_file_name and stdout_fileno from the log_file_params tuple

      log = log_file_params # Apply short name
      cedarlog.use_log_file(switch='close', log_file_name=log[0], stdout_fileno=log[1], location=log[2])

      return

Call your main() code:

    if __name__ == "__main__":

      main (your_param1, your_param2, etc, log_file_title, log_file_location)


## Log File Location
Note that you will need to *manually* create a folder for the log files relative to your main Python code.

For example:

        /my_python_code_folder
            /log_files
            my_main_prog.py
            cedarlog.py
            ...

## Reference Code
Some of the code used was inspired by this article:

[Ask Python - Print to File](https://www.askpython.com/python/built-in-methods/python-print-to-file)

## Questions and Comments
More than happy to respond to questions and comments. Plese feel free to drop me a line.

## License
Copyright 2022 Cedarwood Insights Limited.

Licensed under the Apache License, Version 2.0: https://www.apache.org/licenses/LICENSE-2.0
