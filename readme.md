
# GoSense Data Manager Tools
The Data Manager Tools is a software package with a collection of command line tools that are used for ...
* Direct access (read & write) to the Modbus slaves connected to the Data Manager using a Modbus TCP Gateway.
* Remote configuration and control of the Data Manager over Internet TCP connection
* Local manipulation of configuration files for the Data Manager
* Local manipulation of data log files that have been downloaded form the Data Manager

Each of these tools are described in more detail in the following subsections.

## Related Projects
Name                | GitHub Project
--------------------|-----------------------------------------------------------
gosense_dm_tools    | [GoSense Data Manager Tools](https://github.com/greengo/gosense_dm_tools)
gosense_dm          | [GoSense Data Manager](https://github.com/greengo/gosense_dm)
gosense             | [GoSense](https://github.com/greengo/gosense)

```c
#include <stdio.h>
int main()
{
    printf("Hello World!\n");
    return 0;
}
```


## Folder Structure

```
gosense_dm_tools/
    README.md
    Makefile
    build.xml

    bin/
        ...             # Linux and Windows command line tools.
        gosense/
            ...         # Linux command line tools for low-level access to GoSense slaves.
    doc/
        README.html
        github.css
        doxyfile
        html/
            index.html
            ...
    lib/
        ...
    src/                # Java source code.
        ...
    test/
        ...
    build/
        ...
    dist/
        ...
    tmp/
        ...
    matlab/             # MATLAB toolbox.
        ...
    examples/           # Examples of how to use the command line and MATLAB tools.
        ...
```

## Development
The Data Manager Tools have been implemented in Java ...

* Linux System
[Cygwin](https://www.cygwin.com)
* IDE
[NetBeans 8.1](https://netbeans.org)
[Java SE SDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* Documentation
[Doxygen](https://github.com/doxygen/doxygen)
[Graphviz](http://www.graphviz.org)

FIXME: Makefile - for creating a binary distribution for installation

## Command line Tools
FIXME: Requirement for running the command line tools (Linux/Cygwin, Windows, JAVA)
FIXME: bin/ folder

### Modbus TCP Master Tool
The Modbus TCP Master is a command line tool for accessing Modbus Slaves (GoSense and Generic) remotely over Internet TCP connection through a Modbus TCP Gateway.
This tool has been developed for making it possible to debug and test the implementation of the firmware in GoSense, especially the Modbus interface, FLASH memory functionality and the System controller.
This tool has mainly been used with the Modbus TCP Gateway that has been implemented in the Data Manager, but it should also work with other standard Modbus TCP Gateways such as MOXA MGate MB3270.

*modbus_tcp_master_tool.sh*
**modbus_tcp_master_tool.cmd**

```
Usage: [-h] [-v] [-of format] [-H host] [-p port] [-T timeout] [-P password] [-uid id] -fcn function ...

Option (* = required)        Description
---------------------        -----------
-H <host>                    Host IP Address (default: 80.251.205.239)
-P <password>                Password
-T <Integer: timeout>        Blocking read timeout [ms] (default: 5000)
* --fcn <Integer: function>  Modbus Function: 1,2,3,4,5,6,15,16
-h, --help                   Show this help message
--of <format>                Output Format: hex, dec, char (default: hex)
-p <Integer: port>           TCP Port Number (default: 502)
--uid <Integer: id>          Modbus Slave Address (default: 7)
-v                           Verbose

1-bit, Table 1xxxx, Read
    READ_DISCRETE_INPUTS
        -fcn 2 address num

1-bit, Table 0xxxx, Read/Write
    READ_COILS
        -fcn 1 address num

    WRITE_SINGLE_COIL
        -fcn 5 address data

    WRITE_MULTIPLE_COILS
        -fcn 15 address data ... data

16-bit, Table 3xxxx, Read
    READ_INPUT_REGISTERS
        -fcn 4 address num

16-bit, Table 4xxxx, Read/Write
    READ_HOLDING_REGISTERS
        -fcn 3 address num

    WRITE_SINGLE_REGISTER
        -fcn 6 address data

    WRITE_MULTIPLE_REGISTERS
        -fcn 16 address data ... data
```

### Command Tool
This tool implements a set of commands for remote configuration and control of the Data Manager over Internet TCP connection.

command_tool.sh
command_tool.cmd

```
Usage: [-h] [-v] [-H host] [-p port] [-T timeout] [-P password] command [arguments]

Option                 Description
------                 -----------
-H <host>              Host IP Address (default: 95.209.146.66)
-P <password>          Password
-T <Integer: timeout>  Blocking read timeout [ms] (default: 10000)
-h, --help             Show this help message
-p <Integer: port>     TCP Port Number (default: 1234)
-v                     Verbose

SYSTEM COMMANDS
  system_info
 *system_reboot

SYSTEM LOGFILE COMMANDS
  system_logfile_get <file>
 *system_logfile_clear

CONFIGURATION COMMANDS
  config_get <file>
 *config_set <file>

DATA LOGGER COMMANDS
  data_logger_info
 *data_logger_enable
 *data_logger_disable
 *data_logger_slave_enable <slave addr>
 *data_logger_slave_disable <slave addr>
 *data_logger_period_enable
 *data_logger_period_disable

DATA LOGFILE COMMANDS
  data_logfile_info
 *data_logfile_cache <file>
 *data_logfile_flush <file>
 *data_logfile_done

TIMEZONE COMMANDS
  timezone_get
 *timezone_set <timezone>

CLOCK COMMANDS
  clock_get

DEBUG COMMANDS
  debug_info
 *debug_set <flag>
 *debug_clr <flag>
    <flag>
      0x01 = DISABLE_MARK_FLUSH
      0x02 = DISABLE_UPDATE_GOSENSE_CLOCK

NOTE: The commands marked with * can only be executed when the admin password is used.
```

### Data Collector Tool
The Data Collector Tool is used to download data log files from one or more Data Managers with full handshaking and to store the file(s) in the file system on the local computer.
This tool is mainly intended to be called on periodic basis by the Server to download binary data log files from the data Managers.

data_collector_tool.sh
data_collector_tool.cmd

```
Usage: [-h] [-v] [-rm] [-r retries] [-s sleep] [-o path] infile

Option                 Description
------                 -----------
-h, --help             Show this help message
-o <path>              Output path
-r <Integer: retries>  Retries (default: 3)
--rm                   Remove intermediate files (cache, flush).
-s <Integer: sleep>    Sleep time between retries [sec] (default: 10)
-v                     Verbose
```

### Data Log Tool
This tool is used to manipulate data log file(s) that have been downloaded from the Data Manager and present them in different forms depending on the use-case.
This tool is mainly intended to be called on periodic basis by the Server to convert download binary data log files to SQL or CSV format for entry into the Database.

data_log_tool.sh
data_log_tool.cmd

```
Usage: [-h] [-r] [-i] [-euid id] [-suid id] [-srsp_id id] [-stype id] [-physical] [-c] [-rsp id:handler] [-tz timezone] [-o path] [-a atime] [-color] infile

Option                        Description
------                        -----------
-a <Integer: time>            Animation Time [ms] (default: 0)
-c                            Convert input file according to Response ID
--color                       Enable coloring of console output
--euid <Integer: id>          Exclude specific Unit ID (Slave Address)
-h, --help                    Show this help message
-i                            Show information about input file
-o <path>                     Output path
--physical                    Enable Physical scaling of values. Default Raw
                                values
-r                            Assume RAW input format (No version, dm_id and
                                dm_tz)
--rsp <handler | id:handler>  Set default Response Handler | Map response ID to
                                Response Handler
--srsp_id <Integer: id>       Select specific Response ID
--stype <Integer: id>         Select specific Type
--suid <Integer: id>          Select specific Unit ID (Slave Address)
--tz <timezone>               Timezone: gmt, local (Data Manager timezone)
                                (default: gmt)

Type:          0 (Generic), 1 (GoSense)
Response ID:   0..253, 254 (DataLogger Message), 255 (Modbus Exception)
Unit ID:       1..255 (Slave Address)

Response Handler:
  Binary                Binary datalog format
  String                String data in ASCII
  Message               DataLogger message in ASCII
  Modbus                Modbus data in ASCII (** Default **)
  ModbusCSV             Modbus data in CSV
  GoSense               GoSense data in ASCII                  (Default: Raw values)
 xGoSense               Extended GoSense data in ASCII         (Default: Raw values)
  GoSenseCSV            GoSense data in CSV                    (Default: Raw values)
 xGoSenseCSV            Extended GoSense data in CSV           (Default: Raw values)
  GoSenseSQL            GoSense data as SQL script             (Default: Raw values)
 xGoSenseSQL            Extended GoSense data as SQL script    (Default: Raw values)
  GoSenseMatlab         GoSense data as Matlab script          (Default: Raw values)
 xGoSenseMatlab         Extended GoSense data as Matlab script (Default: Raw values)
  GoSenseSweepMatlab    GoSenseSweep data as Matlab script

The Data Log Tool supports three basic operations: INFORMATION, FILTERING and CONVERSION.

INFORMATION: Show information about binary data log file
  Example-1:
    data_log_tool.sh foo.bin -i

FILTERING: Apply exclude and select options and write resulting binary data log file.
  Example-1: Exclude slave with address 1, Select only Response ID's 254, Save result in binary data log file bar/baz.bin
    data_log_tool.sh foo.bin -euid 1 -srsp_id 254 -o bar/baz

CONVERSION: Apply exclude and select options and ... write separate file for each response ID.
  Example-1: Map all Response ID's to Modbus ASCII, Save in separate files prefixed with bar
    data_log_tool.sh foo.bin -c -o bar

  Example-2: Select only slave with address 1, Map Response ID 0 to GoSenseSQL and Response ID 254 to Message, Save in separate files prefixed with bar
    data_log_tool.sh foo.bin -c -suid 1 -rsp 0:GoSenseSQL -rsp 254:Message -o bar

  Example-3: Convert all Response ID's of 0 to GoSense ASCII and animate with 200ms interval and show in color
    data_log_tool.sh foo.bin -c -rsp 0:GoSense -a 200 -color
```

### Password Hash Tool
This tool is used to encrypt a human readable password using a cryptographic hash function.
This encrypted password is placed in the configuration file for the Data Manager. The Data Manager then uses this encrypted password to check if incoming TCP connections should be accepted.

password_hash_tool.sh
password_hash_tool.cmd

```
Usage: [-h] [-t type] password

Option      Description
------      -----------
-h, --help  Show this help message
-t <type>   Type: md5, sha-1, sha-256 (default: sha-256)
```

### Configuration Listing Tool
This tool is used to list the contents of a configuration text file for the Data Manager in a human readable form so that it is easy to inspect how the Data Manager is configured.

config_list_tool.sh
config_list_tool.cmd

```
Usage: [-h] file

Option      Description
------      -----------
-h, --help  Show this help message
```

## MATLAB Tools
FIXME: Requirement for running the MATLAB tools (JAVA)
FIXME: matlab/ folder

gosense_plot.m
gosense_sweep_plot.m
gosense_sweep_tool.m
gosense_sweep_init.m
gosense_sweep_demo.m

id_info_get.m
sys_par_get.m
hw_par_get.m

flash_buf_state_regs_get.m
flash_buf_data_regs_get.m
