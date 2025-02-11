# Práctica de Configuración de Servidor FTP con vsftpd

## Instalación de vsftpd

1. Instalamos el servidor FTP `vsftpd` en el servidor:

    ```sh
    apt-get update
    apt-get install vsftpd
    ```

## Creación de dos usuarios

1. Creamos dos usuarios en el servidor:

    ```sh
    adduser usuario1
    # Sigue las instrucciones para crear la contraseña
    adduser usuario2
    # Sigue las instrucciones para crear la contraseña
    ```

## Ejercicios

### 1. Diferencia entre usuarios

- La diferencia entre usuarios ya la tenemos clara.

### 2. Habilitamos escritura y reinicio del servidor

1. Editamos el archivo de configuración de `vsftpd` para habilitar la escritura:

    ```sh
    nano /etc/vsftpd.conf
    ```

    Asegúrate de que las siguientes líneas estén presentes y configuradas:

    ```plaintext
    write_enable=YES
    ```

2. Reiniciamos el servidor `vsftpd`:

    ```sh
    systemctl restart vsftpd
    ```

### 3. Reinicio del servidor

- Reiniciamos el servidor para aplicar los cambios:

    ```sh
    systemctl restart vsftpd
    ```

## Prueba de transferencia desde cliente

1. Desde el cliente, intentamos conectarnos al servidor FTP en `192.168.50.2`:

    ```sh
    ftp 192.168.50.2
    ```

2. Iniciamos sesión desde el cliente al FTP con el usuario `usuario1`:

    ```sh
    ftp 192.168.50.3
    Connected to 192.168.50.3.
    220 Bienvenido al Servicio FTP.
    Name (192.168.50.3:vagrant): usuario1
    331 Please specify the password.
    Password: 
    230 Login successful.
    ftp>
    ```

### 4. Prueba de transferencia desde cliente

1. En el cliente, creamos un archivo de prueba y lo transferimos al servidor FTP:

    ```sh
    echo "Prueba de FTP" > test.txt
    ftp <IP_DEL_SERVIDOR>
    put test.txt # Para subir el archivo
    get test.txt # Para descargar el archivo
    ```

### 5. Cambiar mensaje de bienvenida en el servidor

1. Editamos el archivo de configuración de `vsftpd` para cambiar el mensaje de bienvenida:

    ```sh
    nano /etc/vsftpd.conf
    ```

    Añadimos o modificamos la línea:

    ```plaintext
    ftpd_banner=Bienvenido al Servicio FTP.
    ```

2. Reiniciamos el servidor `vsftpd`:

    ```sh
    systemctl restart vsftpd
    ```

### 6. Enjaulamiento de usuarios en el servidor

1. Editamos el archivo de configuración de `vsftpd` para enjaular a los usuarios:

    ```sh
    nano /etc/vsftpd.conf
    ```

    Añadimos o modificamos las líneas:

    ```plaintext
    chroot_local_user=YES
    ```

2. Reiniciamos el servidor `vsftpd`:

    ```sh
    systemctl restart vsftpd
    ```

### 7. Configuración de userlist_enable y userlist_deny

1. Editamos el archivo de configuración de `vsftpd` para añadir `userlist_enable` y `userlist_deny`:

    ```sh
    nano /etc/vsftpd.conf
    ```

    Añadimos las líneas:

    ```plaintext
    userlist_enable=YES
    userlist_deny=YES
    ```

2. Reiniciamos el servidor `vsftpd`:

    ```sh
    systemctl restart vsftpd
    ```

### 8. Configurar acceso anónimo en el servidor

1. Editamos el archivo de configuración de `vsftpd` para permitir el acceso anónimo:

    ```sh
    nano /etc/vsftpd.conf
    ```

    Añadimos o modificamos la línea:

    ```plaintext
    anonymous_enable=YES
    ```

2. Reiniciamos el servidor `vsftpd`:

    ```sh
    systemctl restart vsftpd
    ```

## Fin de la Práctica
