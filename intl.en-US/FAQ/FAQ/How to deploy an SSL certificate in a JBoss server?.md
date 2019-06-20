# How to deploy an SSL certificate in a JBoss server? {#concept_jg2_fyv_ydb .concept}

1.  To confirm the JBoss version, it is recommended that you deploy the SSL certificate to JBoss 7.10 and later.
2.  Modify the service port. Go to standalone/configuration under the JBoss home directory and modify the standalone. xml file.

    ```
    <interfaces>
            <interface name="management">
                <inet-address value="${jboss.bind.address.management:127.0.0.1}"></inet>
            </interface>
             <! -- Open remote access -->
            <interface name="public">
                <inet-address value="${jboss.bind.address:0.0.0.0}"></inet>
            </interface>
            <interface name="unsecure">
                <inet-address value="${jboss.bind.address.unsecure:127.0.0.1}"></inet>
            </interface>
        </interfaces>
        <socket-binding-group name="standard-sockets" default-interface="public" port-offset="${jboss.socket.binding.port-offset:0}">
            <socket-binding name="management-native" interface="management" port="${jboss.management.native.port:9999}"></socket>
            <socket-binding name="management-http" interface="management" port="${jboss.management.http.port:9990}"></socket>
            <socket-binding name="management-https" interface="management" port="${jboss.management.https.port:9443}"></socket>
            <socket-binding name="ajp" port="8009"></socket>
             <! -- Modify http port -->
            <socket-binding name="http" port="80"></socket>
              <! -- Modify HTTPS port -->
            <socket-binding name="https" port="443"></socket>
            <socket-binding name="osgi-http" interface="management" port="8090"></socket>
            <socket-binding name="remoting" port="4447"></socket>
            <socket-binding name="txn-recovery-environment" port="4712"></socket>
            <socket-binding name="txn-status-manager" port="4713"></socket>
            <outbound-socket-binding name="mail-smtp">
                <remote-destination host="localhost" port="25"></remote>
            </outbound-socket-binding>
        </socket-binding-group>
    ```

3.  Go to the bin directory of the JBoss installation directory and execute `standalone.sh` to make sure the application has normal access.
4.  Get the certificate and convert to jks format.

    Download the tomcat certificate from Ali cloud, A non-system generated CSR needs to generate a pfx certificate key pair file. The extracted file includes:

    -   214362464370691.key
    -   214362464370691.pem
    -   214362464370691.pfx
    -   pfx-password.txt
    . Non-system generated CSR, converting certificate key pair files for pfx to jks format \(note Windows environment at %JAVA\_HOME%/jdk/bin 

    ```
    OpenSSL maid 214362464370691. pfx-inkey 214362464370691. Key-In 214362464370691. pem
    ```

    Enter the password for the jks format certificate set twice after entering, and then enter the password for the pfx certificate once. The password for the record.

5.  Deploy the certificate.
    1.  Enter standalone/configuration under the JBoss home directory, and create a new cer file, place the jks format certificate into the folder.

        ```
        #​cd /opt/jboss711/standalone/configuration
        #mkdir cert
        # pwd
        /opt/jboss711/standalone/configuration/cert
        #cp -rf /opt/keys/jboss.jks .
        ```

    2.  Modify the standalone.xml file to add the certificate-related configuration.

        ```
        <subsystem xmlns="urn:jboss:domain:web:1.1" default-virtual-server="default-host" native="false">
                 <connector name="http" protocol="HTTP/1.1" scheme="http" socket-binding="http"/>
                <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true">
                        <ssl name="https" password="214362464370691" certificate-key-file="../standalone/configuration/cert/jboss.jks" cipher-suite="TLS_RSA_WITH_AES_256_CBC_SHA,TLS_DHE_RSA_WITH_AES_256_CBC_SHA,TLS_DHE_DSS_WITH_AES_128_CBC_SHA,SSL_RSA_WITH_3DES_EDE_CBC_SHA,SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA,SSL_DHE_DSS_WITH_3DES_EDE_CBC_SHA" protocol="TLSv1,TLSv1.1,TLSv1.2"/>
                    </connector>
                    <virtual-server name="default-host" enable-welcome-root="true">
                        <alias name="localhost"/>
                        <alias name="example.com"/>
                    </virtual-server>
                </subsystem>
        ```

    3.  Restart the JBoss server. Go to the bin directory in the JBoss directory and execute the standalone.sh script.

        ```
        #pwd
        /opt/jboss711/bin
        #sh standalone.sh &
        ```

    4.  Verify.

        ![](images/4311_en-US.png)


