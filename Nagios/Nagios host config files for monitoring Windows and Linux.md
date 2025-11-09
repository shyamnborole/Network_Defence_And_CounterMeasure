- nagios/etc/servers
- add a host named win_10-1.cfg
- ```
  define host {
	     use                  windows-server/linux-server
	     host_name            win_10-1/linux
	     alias                Windows 10 System 1/linux debian
	     address              192.168.x.x
	     max_check_attempts   5
  }
  
  define service {
			use                     generic-service
			host_name               win_10-1/linux
			service_description     NCPA Agent Version
 			check_command           check_ncpa!-t 'Password1234' -p -P 5693 -M   system/agent_version
  }
  
  define service {
			use                     generic-service
			host_name               win_10-1/linux
			service_description     CPU Average
			check_command           check_ncpa!-t 'Password1234' -p -P 5693 -M cpu/percent -w 20 -c 40 -q 'aggregate=avg'  
  }
  
  ```
