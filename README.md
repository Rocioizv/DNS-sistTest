# DNS-sistTest
La siguiente práctica tiene un servidor DNS maestro, otro esclavo con una zona directa e inversa.


1. Creamos un archivo .gitignore para que ignore el directorio .vagrant y los ficheros de backup (.back y *~)

2. Crear las máquinas Venus y Tierra con bullseye64
    ![Texto alternativo](images/confMaquinas.png)

    2.1 Necesito copiar los archivos de las máquinas para que se puedan subir a GitHub
    ![Texto alternativo](images/copiarArchivos.png)
        (Aquí solo copié un archivo)

3. Datos del DNS 
    1. Escucha del protocolo IPv4
    2. dnssec-validation a yes
    3. Permitir consultas recursivas con acl
    ![Texto alternativo](images/conf1.png)

