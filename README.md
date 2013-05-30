# OAuth 2.0 Example Auth Server

## Setup

1. Setup a MySQL database and edit db.php with the connection settings
1. Run the following commands on the database:
    ```sql
    CREATE TABLE `oauth_client_endpoints` (
      `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
      `client_id` varchar(255) DEFAULT NULL,
      `redirect_uri` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=latin1;
    
    CREATE TABLE `oauth_clients` (
      `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
      `secret` varchar(255) DEFAULT NULL,
      `name` varchar(255) DEFAULT NULL,
      `auto_approve` int(11) DEFAULT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
    
    CREATE TABLE `oauth_scopes` (
      `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
      `scope` varchar(255) DEFAULT NULL,
      `name` varchar(255) DEFAULT NULL,
      `description` text,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
    
    INSERT INTO oauth_clients (id, secret, name, auto_approve) VALUE ('I6Lh72kTItE6y29Ig607N74M7i21oyTo', 'dswREHV2YJjF7iL5Zr5ETEFBwGwDQYjQ', 'Hello World App', 0);
    INSERT INTO oauth_client_endpoints (client_id, redirect_uri) VALUE ('I6Lh72kTItE6y29Ig607N74M7i21oyTo', 'http://client.dev/signin/redirect');
    INSERT INTO oauth_scopes (scope, NAME, description) VALUES ('user', 'User details', 'Retrieves a user\'s details');
    ```
1. Install [Composer](http://getcomposer.org/) and run `composer install`

The source code is fully documented and should be a good starting base for your own OAuth auth server.
