# DNS-sistTest
La siguiente práctica tiene un servidor DNS maestro, otro esclavo con una zona directa e inversa.


1. Creamos un archivo .gitignore para que ignore el directorio .vagrant y los ficheros de backup (.back y *~)

2. Crear las máquinas Venus y Tierra con bullseye64
    ![imagen](images/confMaquinas.png)

    2.1 Necesito copiar los archivos de las máquinas para que se puedan subir a GitHub
    ![imagen](images/copiarArchivos.png)
        (Aquí solo copié un archivo)

3. Datos del DNS 
    1. Escucha del protocolo IPv4
    2. dnssec-validation a yes
    3. Permitir consultas recursivas con acl

      ![imagen](images/conf1.png)


    4. tierra.sistema.tes es el servidor maestro
        a. Configura la zona directa e indirecta
       ![imagen](/images/Maestro1.png) 

        b. Archivo de zona directa
       ![imagen](/images/zona-sistTest.png)
            En este archivo hay un error, falta poner un registro A para tierra.sistema.test
        c. Archivo de zona indirecta
       ![imagen](/images/Maestro2.png)

    5. Configuración servidor esclavo    
        a. En el fichero named.conf.local. También índica el maestro
        ![imagen](/images/esclavo1.png) 

    6. Configurar el tiempo en caché de las respuestas negativas a dos horas
        a. Zona directa
        ![image](/images/tiempo.png)

        b. Zona indirecta
        ![image](/images/tiempo2.png)

    7. Reenviar consultas que no pueda resolver al servidor de OpenDNS (208.67.222.222).
        ![image](/images/forwarder.png)

    8. a. ns1.sistema.test. será un alias de tierra.sistema.test.
        b. ns2.sistema.test. será un alias de venus.sistema.test..
    9. mail.sistema.test. será un alias de marte.sistema.test.
         ![image](/images/alias.png)

    10. El equipo marte.sistema.test. actuará como servidor de correo del dominio de correo
        sistema.test.
          ![image](/images/correo.png)


    COMPROBACIONES
    A. Comprobar los registros A
         ![image](/images/c1.png)
         
    B. Comprobar resolución inversa
         ![image](/images/c2.png)
         
    C. Comprobar alias
         ![image](/images/c3.png)
         
    D. Comprobar los servidores NS
         ![image](/images/c4.png)
         
    E. Comprobar el servidor MX
         ![image](/images/c5.png)
         
    F. Comprobar la transferencia de zona
         ![image](/images/c6.png)
         
    G. Comprobar la resolución en maestro y esclavo
         ![image](/images/c7t.png)
         ![image](/images/c7v.png)
         