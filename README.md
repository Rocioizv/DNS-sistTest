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
