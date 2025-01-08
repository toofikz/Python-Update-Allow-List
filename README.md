# Python Project: Automating IP Address Removal from Allow List

## Project Description

In this project, I created a Python algorithm to automate the process of updating an "allow_list.txt" file that contains approved IP addresses. The algorithm removes IP addresses from the allow list that are also present in a separate "remove_list". This ensures that restricted content is only accessible to authorized IP addresses.

## Steps in the Algorithm

1. **Open the Allow List File**  
   The first step is to open the "allow_list.txt" file to read the current list of allowed IP addresses.

    ```python
    import_file = "allow_list.txt"
    with open(import_file, "r") as file:
        ip_addresses = file.read()
    ```

   - The `with` statement ensures the file is automatically closed after reading.
   - The `.read()` method converts the file contents into a string format.

2. **Convert the String into a List**  
   To make it easier to remove IP addresses, the string of IP addresses is split into a list.

    ```python
    ip_addresses = ip_addresses.split()
    ```

   - The `.split()` method splits the string by whitespace and stores the IP addresses as individual list elements.

3. **Iterate Through the Remove List**  
   The next step is to loop through the IP addresses in the "remove_list" and remove them from the `ip_addresses` list.

    ```python
    for element in remove_list:
        if element in ip_addresses:
            ip_addresses.remove(element)
    ```

   - The `for` loop checks each IP address in the `remove_list` and removes it from the `ip_addresses` list if it exists.

4. **Update the Allow List File**  
   After removing the unwanted IP addresses, the updated list is written back to the "allow_list.txt" file.

    ```python
    with open(import_file, "w") as file:
        file.write("\n".join(ip_addresses))
    ```

   - The `.join()` method combines the list of IP addresses back into a string, with each IP address on a new line.
   - The `with open(..., "w")` statement opens the file in write mode to overwrite its contents with the updated list.

## Summary

This Python algorithm automates the process of managing an IP allow list. It reads the current list of allowed IP addresses, removes any IP addresses that should no longer have access (from the "remove_list"), and then updates the allow list file. This ensures that only authorized IP addresses can access restricted content.

## How to Run the Project

1. Ensure you have a file named `allow_list.txt` with a list of IP addresses (one per line).
2. Create a list called `remove_list` containing the IP addresses you want to remove.
3. Run the Python script to automatically update the allow list.
