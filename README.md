# SMOCKIN Version 1.0

The Web Service Simulation Framework for application development and QA testing


OVERVIEW

    SMOCKIN is a light framework that can be used for setting up mock RESTful web service simulations.
    for use in either development or QA testing.

    Whether you are a mobile developer who needs to simulate a remote server or working with a complex SOA, SMOCKIN 
    can help by simulating any services that may be otherwise difficult / time consuming to set up.

    With the ability to vary the output of your web service by using easy to set up sequences and rules, SMOCKIN can 
    help to simulate all of your different use cases.

    Written in Java using Spring Boot, the application runs as a small web app which can be hosted either locally on a 
    developers machine or centrally on a development teams' server.

    Features include:

        - An Internal Mocking Server which is used to serve your mocked endpoints.

        - The Admin UI for:
            -- Creating and editing your mocked endpoints.
            -- Applying 'rules' or 'sequenced responses' to your mocked endpoints.
            -- Configuring, Starting and Stopping the Internal Mocking Server.



GETTING STARTED

    Requirements:

        - Java 8
        - Maven 3

        Please Note
            -   All bash scripts were written and tested on GNU Bash version 3.2.57(1)-release.
            -   All BAT files were were written and tested on Windows 7.


    Installing:

        - From GitHub, clone or download and unpack to a suitable location.

        Linux / OSX

            - Ensure the script 'install.sh' is executable:

                chmod +x install.sh

            - Run the script 'install.sh'.

        Windows

            - Run the script 'install.bat'.


        This creates a config directory under your user called .smockin, containing a H2 JAR and db.properties file. 
        The H2 DB file will also be situated from here, if you choose to use the default DB config.)

        To use your own DB vendor:

            - Remove the default H2 JDBC driver file (i.e. h2-1.4.194.jar) from '.smockin/db/driver'.

            - Copy your chosen JDBC driver to this same location '.smockin/db/driver'.

            - Edit the properties file '.smockin/db/db.properties' with your connectivity details.


    Running:

        - Ensure ports 8000 (used by Admin UI), 8001 (used by Mock Server) and 9092 (used by H2 TCP DB) are all available on the 
        local machine.

          (If required the 'Admin UI' and 'H2 DB' ports can be changed by editing the ''.smockin/app.properties' file. The 'Mock 
          Server' port can be changed from within the application from the Dashboard.)

        Linux / OSX

            - Once installed, ensure the scripts 'start.sh' and 'shutdown.sh' are both executable:

                chmod +x start.sh
                chmod +x shutdown.sh

            - Run the script 'start.sh' to build and run SMOCKIN like so (this also launches the default H2 database in TCP 
            mode.):

        Windows

            - Run the script 'start.bat' to build and run SMOCKIN like so (this also launches the default H2 database in TCP 
            mode.):


        SMOCKIN runs off port 8000 by default and accessible from this address:

            http://localhost:8000/index.html


        If you simply want to see SMOCKIN in action, there is a script available which will add a small
        data set of predefined mocked endpoints and rules to the DB. To install this, please see the section
        'DEVELOPMENT SCRIPTS > Sample Data' below.


    Stopping:

        Linux / OSX

            - Both SMOCKIN and the H2 database can be easily shutdown by launching the 'shutdown.sh' script:

        Windows

            - Simply close the respective command shells for both the H2 database and Smockin.


    Uninstalling:

        - To uninstall Smockin, firstly shutdown both the Smockin application and then H2 database (See 'Stopping' above).

        - Then run the following script:

            Linux / OSX

                Run the script 'uninstall.sh'

            Windows

                Run the script 'uninstall.bat'

        (This will remove any config and db files relating to Smockin from your system.)

        - Finally you can simply erase the main Smockin application directory from wherever you copied it on your system.


    Development Modes (Linux & OSX & running from source only):

        By default 'start.sh' starts the SMOCKIN asynchronously (in the background) using a H2 DB (in TCP mode).

        To aid development, SMOCKIN can also be started in the following modes:

            DEBUG        Allows remote debugging on port 8008.
                e.g:     ./start.sh -DEBUG

            INMEM        Uses an in-memory DB, instead of TCP.
                e.g:     ./start.sh -INMEM

        These commands can also be combined.

            e.g.

                ./start.sh -DEBUG             will enable the debug port and use the main DB.
                ./start.sh -DEBUG -INMEM      will enable the debug port and use an in-memory DB.



DEVELOPMENT SCRIPTS (Linux & OSX only)

    A few utility scripts can be found under the 'client_scripts' dir.

    (these scripts all assume SMOCKIN, is running locally from port 8000.)


    Sample Data:

        To install the sample data set to the SMOCKIN DB:

            -  Navigate to the 'client_scripts' dir.

            - Ensure the the script is executable:

                chmod +x apply_sample_data.sh

            - Assuming both SMOCKIN (and the H2 DB if applicable) are running, execute the script:

                ./apply_sample_data.sh

            - To put these changes into effect, restart the RESTFul mock server. You can do this from
               either the Admin UI or using via the following scripts:

                ./shutdown_rest_mock_server.sh
                ./start_rest_mock_server.sh



LICENCE


    Smockin is licensed according to the terms of the Apache License, Version 2.0.

    The full text of this license can be found at https://www.apache.org/licenses/LICENSE-2.0



ACKNOWLEDGEMENTS / THIRD PARTIES

    SMOCKIN is built upon the following open source frameworks:

        Spring Boot   -    https://projects.spring.io/spring-boot
        Hibernate     -    http://hibernate.org
        Spark         -    http://sparkjava.com
        Maven         -    https://maven.apache.org
        AngularJS     -    https://angularjs.org
        UI Bootstrap  -    https://angular-ui.github.io/bootstrap
        vkBeautify    -    https://github.com/vkiryukhin/vkBeautify
        H2            -    http://www.h2database.com
        HikariCP      -    https://brettwooldridge.github.io/HikariCP
        JUnit         -    http://junit.org
        Mockito       -    http://site.mockito.org/



ABOUT

    SMOCKIN is designed and actively maintained by MG Tech Software Ltd.

    Why the name SMOCKIN? Whilst it may sound like an old english middle ages embroidery technique, the name
    actually came about more in relation to a classic Jim Carey movie quote 'Smokin'. We then added the extra
    letter to play on the concept of software mocking and there you have it. 
    
    Yes, way too much thought went into that...
