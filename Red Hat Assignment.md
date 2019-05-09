# ownCloud Installation and Usage QuickStart Guide #**



**About the Document**

This document provides instructions on how to install and configure ownCloud server. You require administrator privileges to perform the steps for installation and configuration.

**Install ownCloud**

**Prerequisites**

- **Memory**
  - 128 MB RAM memory. For better performance, 512 MB RAM memory is recommended.
- **Database**
  -  MySQL or MariaDB 5.5+
  -  Oracle 11g
  -  PostgreSQL 9 (versions 10 and higher are not supported)
  -  SQLite
- **PHP Runtime**
  - 5.6
  - 7.0
  - 7.1
  - 7.2
- **Web server**
  - Apache 2.4 with prefork and mod\_php.
- **Operating system**
  - Ubuntu 16.04 and 18.04
  - Debian 7, 8 and 9
  - SUSE Linux Enterprise Server 12 with SP1, SP2 and SP3
  - Red Hat Enterprise Linux/Centos 6.9, 7.3, 7.4, and 7.5
  - Fedora 27, 28 and 29
  - openSUSE Leap 42.3 and 15

**Installation Overview**

You can install ownCloud using one of the following available options.

- Install ownCloud using Docker
- Install ownCloud manually
- Install ownCloud using Linux Package Manager
- Install ownCloud using the Installation Wizard
- Install ownCloud using Command Line



**Install ownCloud using Docker**

You can install ownCloud using [ownCloud Docker image](https://hub.docker.com/r/owncloud/server/). The configurations enable the HTTP connections through 8080 port and mounts the data and MYSQL data directories on the host system for efficient storage.

To install ownCloud, complete the following steps.

1. Create a new directory and download docker-compose.yml from the [ownCloud Docker GitHub repository](https://github.com/owncloud-docker/server).
2. Create a configuration file with the following settings.

| Settings | Description | Example |
| --- | --- | --- |
| OWNCLOUD\_VERSION | The ownCloud version | Latest |
| OWNCLOUD\_DOMAIN | The ownCloud domain | Localhost |
| ADMIN\_USERNAME | The admin username | Admin |
| ADMIN\_PASSWORD | The admin user&#39;s password | Admin |
| HTTP\_PORT | The HTTP port to bind to | 8080 |
| OWNCLOUD\_VERSION | The ownCloud version | Latest |

1. Start the container using [Docker Compose](https://docs.docker.com/compose/). For details, see the [GitHub](https://github.com/owncloud-docker/server#launch-with-plain-docker).
2. Run docker-compose ps and verify whether all containers are started.

**Log in to ownCloud**

To log in to ownCloud, complete the following steps.

1. Open [http://localhost:8080](http://localhost:8080/) in a browser.
2. Enter the admin credentials that you have stored in the environment file previously.

**Install ownCloud manually**

To install ownCloud manually, complete the following steps.

1. Install packages.
2. Obtain and extract the files.
3. Configure the web server.
4. Enable SSL.
5. Configure NGINX.
6. Complete your installation.

**Install packages**

Before you install ownCloud, install the following packages.

- Ubuntu 18.04 LTS Server. For details, see the [Ubuntu 18.04 Guide](https://doc.owncloud.org/server/10.1/admin_manual/installation/server_prep_ubuntu_18.04.html).
- RHEL (RedHat Enterprise Linux) 7.2
- CentOS 7
- SLES (SUSE Linux Enterprise Server) 12
- APCu
- Redis

**Obtain and extract the files**

To download the current version of ownCloud, complete the following steps.

1. In the ownCloud Download page, navigate to **Download ownCloud Server \&gt; Download \&gt; Archive file** and download either the tar.bz2 or .zip archive.
2. For the owncloud-x.y.z.tar.bz2 or owncloud-x.y.z.zip (where x.y.z is the version number) files, download the corresponding checksum files. For example, owncloud-x.y.z.tar.bz2.md5, or owncloud-x.y.z.tar.bz2.sha256.
3. Verify the MD5 or SHA256 sum or PGP signature.
4. Run the following unpacking command to extract the contents of archive. Replace &quot;/path/to/webserver/document-root&quot; with the appropriate document root of the web server.

cp -r owncloud /path/to/webserver/document-root

**Note**   It is recommended that you install ownCloud outside of the document root on other HTTP servers.

**Configure Web Server**

To configure the Web Server, complete the following steps.

1. Configure Apache. Under /etc/apache2/sites-available, create an owncloud.conf file.
2. Replace the \&lt;Directory\&gt; and other file paths with the appropriate ones.
3. Enable mod\_rewrite module by running a2enmod rewrite. You can enable the following recommended modules by running the associated commands.

| Modules | Commands |
| --- | --- |
| mod\_headers | a2enmod headers |
| mod\_env | a2enmod env  |
| mod\_dir | a2enmod dir |
| mod\_mime | a2enmod mime |
| mod\_unique\_id | a2enmod unique\_id |

**Enable SSL**

You must use SSL/TSL to encrypt the server&#39;s data and login information for the users. You can enable the ssl module and the default site by opening a terminal and running the following command.

a2enmod ssl

a2ensite default-ssl

service apache2 reload

**Configure NGINX**

To enable the Application Tracing functionality, add the following code to the ownCloud NGINX configuration. Restart the Apache.

fastcgi\_param UNIQUE\_ID $request\_id;

**Complete the installation**

You can complete the installation by using one of the following options.

- **Installation wizard**.  See the [Installation wizard document](https://doc.owncloud.org/server/10.1/admin_manual/installation/installation_wizard.html).
- **Run the**  **occ**  **command under the command line**. See the [Command line installation document](https://doc.owncloud.org/server/10.1/admin_manual/installation/command_line_installation.html).

**Install ownCloud using Linux Package Manager**

You can install ownCloud using Linux Package Managers for single-server setups. For Production environments, you must install from the [tar archive](https://owncloud.org/download/#owncloud-server-tar-ball). The owncloud-files package installs ownCloud only. It is recommended that you do not update the owncloud-files package automatically during system updates.

**Install ownCloud Community Edition**

To install ownCloud Community Edition, complete the following steps.

- Install the LAMP stack and follow the system requirements to see the recommended ownCloud platforms.
- Update package manager&#39;s configuration.  The following configurations are available.
  - Ubuntu 14.04 &amp; 16.04
  - Debian 7 &amp; 8
  - RHEL 6 &amp; 7
  - CentOS 7.2 &amp; 7.3
  - SLES 11SP4 &amp; 12SP2
  - openSUSE Leap 42.2 &amp; 42.3
- Install ownCloud using the instructions provided on the Download page. Follow
- Run the Installation Wizard. See the [Installation wizard document](https://doc.owncloud.org/server/10.1/admin_manual/installation/installation_wizard.html).

**Install ownCloud Enterprise Edition**

To install ownCloud Enterprise edition, follow the instructions provided in the [Enterprise Installation Guide](https://doc.owncloud.org/server/10.1/admin_manual/enterprise/installation/install.html).

**Install ownCloud using the Installation Wizard**

If you choose to install ownCloud using the Installation Wizard, your access must be authorized with secure credentials.

Ensure that you follow the prerequisites for installation and download the required files before completing the installation using the Installation Wizard.

To complete the installation using Installation Wizard, complete the following steps.

1. Go to [http://localhost/owncloud.occ](http://localhost/owncloud.occ)
2. Provide your login credentials.
3. Click **Finish Setup**.

**Install ownCloud using Command Line**

Ensure that you follow the prerequisites for installation and download the required files before completing the installation using the command line.

To install ownCloud using Command Line, complete the following steps.

1. Run the cc command from the root directory of the ownCloud source. If you want to run cc command from another directory, use the data- dir switch.
2. Set the required privileges to your files and directories.

**Configure ownCloud**

**Configure Database**

**Configure Database on Linux**

The single-server systems support SQLite, whereas the large systems do not support SQLite. You must convert your database to MYSQL, MARIADB, or PostgreSQL using [occ](https://doc.owncloud.org/server/10.1/admin_manual/configuration/server/occ_command.html#database-conversion) command.

The following databases are supported.

- MYSQL/MariaDB
- PostgreSQL
- Oracle for ownCloud Enterprise Edition

**Configure MYSQL/MariaDB**

Before you configure MYSQL/MariaDB, perform the following actions.

1. Install and enable the pdo\_mysql extension in PHP.
2. Point the mysql.default\_socket to the correct socket if you want to run the database on the same server as ownCloud.

The following is a sample configuration.

# configuration for PHP MySQL module

extension=pdo\_mysql.so

[mysql]

mysql.allow\_local\_infile=On

mysql.allow\_persistent=On

mysql.cache\_size=2000

mysql.max\_persistent=-1

mysql.max\_links=-1

mysql.default\_port=

mysql.default\_socket=/var/lib/mysql/mysql.sock  # Debian squeeze: /var/run/mysqld/mysqld.sock

mysql.default\_host=

mysql.default\_user=

mysql.default\_password=

mysql.connect\_timeout=60

mysql.trace\_mode=Off

**Configure PostgreSQL database**

Before you configure PostgreSQL database, ensure that you install and enable PostgreSQL extension in PHP. The following is a sample configuration.

# configuration for PHP PostgreSQL module

extension=pdo\_pgsql.so

extension=pgsql.so

[PostgresSQL]

pgsql.allow\_persistent = On

pgsql.auto\_reset\_persistent = Off

pgsql.max\_persistent = -1

pgsql.max\_links = -1

pgsql.ignore\_notice = 0

pgsql.log\_notice = 0

**Add a user account**

In ownCloud Web UI, you can create new users. User accounts possess the following properties.

- **Login Name or Username**. The unique ID of the user.
- **Full Name**. The full name of the user that displays on the screen.
- **Password**. Initially, the administrators create the password. You can reset them later.
- **Groups**. You can create groups. By default, the users are not assigned to any users.
- **Group admins**. They possess administrator privileges.
- **Quota**. It is the maximum space which is assigned to any user.

To create a new user account, complete the following steps.

1. Provide a new login name and password to the user. Ensure the following points.
  1. The password is not blank.
  2. The login names can contain letters (a-z, A-Z), numbers (0 to 9), dashes, (-), underscores (­\_), periods (.) and symbols (@).
2. Create Group memberships.
3. Click **Create**.

**Configure the ownCloud Desktop client**

Desktop Clients are available for installation on ownCloud website. They enable connection to ownCloud server through desktop. You can create files and folders on the desktop clients and the changes are synchronized to the server. All the changes made are automatically synced to the server.

To configure the desktop client, complete the following steps

**Prerequisite**  Install the Desktop client depending on your browser requirements.

1. Launch the Desktop client.
2. In the **ownCloud Connection Wizard** page, in the **Server Name** box, type the server address.
3. Type your username and password and click **Next**.
4. Select one of the options.

- **Sync everything from the server**. This syncs everything from the server
- **Choose what to sync**.  This syncs only the desired files.

1. Type the path of the local folder.
2. Click **Connect** and **Finish**. This connects to an ownCloud server.

**ownCloud Mobile apps**

You can connect ownCloud server and access files through a web interface. However, you can also access ownCloud through both iOS and Android mobile apps. ownCloud for mobile provides you the ability to view and access your files and folders located on the ownCloud server.

**ownCloud iOS and Android App**

To connect to ownCloud server through an iOS and Android app, complete the following steps.

1. For iOS, go to the App Store and install the ownCloud app.
2. For Android, go to Google Play and install the ownCloud app.
3. Login to the server using your credentials.