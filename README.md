# Resolve-IP-to-Hostnames
# Powershell script to resolve target IP addresses to hostnames

# During each iteration, a new object '$obj' is created with three properties, 'IPAddress', 'IPConnectionTest' and 'Hostname', set as empty strings. A 'try {}' block is used to attempt to retrieve 
# the 'Hostname' value using a name resoltuon command. If it succeeds, 'Hostname' will be assigned the value returned by the command. If that throws an exception, it will be caught by the 
# 'catch {}' block. In side 'catch {}', the 'Hostname' property is given a value of 'Unknown Host'. Then 'IPAddress' is assigned the current item processed ($_) from the file disctate by'Get-Content'.

# A second 'try {}' block is used carry out a connection test, with a single packet, return either 'True' or 'False' if the ping was succesful or not. Another 'catch {}' block incase an exception is thrown, for example
# if a hostname is placed in the content file instead of an IP address.

# All objects are exported to 'IP-to-Hostname-Log.csv' via 'Export-Csv'. The '-NoType' switch prevents data type information from being printed at the top of the CSV file.
