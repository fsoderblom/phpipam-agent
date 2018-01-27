## Description
phpipam-agent is a scanning agent for phpipam server to be deployed to remote servers

## License
phpipam is released under the GPL v3 license, see misc/gpl-3.0.txt.

## Requirements
 - PHP version 5.2+ with following modules (On windows php 5.3 is required!)
    - pdo, pdo_mysql : Adds support for mysql connections (if type=mysql)
    - gmp            : Adds support for dev-libs/gmp (GNU MP library) -> to calculate IPv6 networks
    - json           : Adds supports for JSON data-interexchange format
    - pcntl          : Adds supports for threading via cli ( not supported by windows )
 - PHP PEAR support (dev-php/pear)

## Install
Just run index.php script with discover or update as argument.

 - Make sure this client has read/write access to main phpipam database.
    ```SQL
    GRANT SELECT on `phpipam`.* TO 'username'@'hostname' identified by "password";
    GRANT INSERT,UPDATE on `phpipam`.`ipaddresses` TO 'username'@'hostname' identified by "password";
    GRANT UPDATE on phpipam.scanAgents TO 'username'@'hostname' identified by "password";
    ```
 - If you will remove inactive dhcp/autodiscovered also this is needed
    ```SQL
    GRANT DELETE on `phpipam`.`ipaddresses` TO 'username'@'hostname' identified by "password";
    ```

## Scheduled scans
For scheduled scans you have to run script from cron. Add something like following to your cron to scan
each 15 minutes:

 `*/15 * * * * php /where/your/agent/index.php update`

## Contact
`miha.petkovsek@gmail.com`
