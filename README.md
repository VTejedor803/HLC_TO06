# Tarea Online 06 PMDM

## Configuración

Para configurar el entorno se deberán seguir los siguientes pasos. En primer lugar nos conectaremos al servidor ssh, en mi caso:

> ssh victor@rivastejedor.com

Descargamos, extraemos y copiamos los ficheros a la carpeta deseada en el servidor web:

> cd /var/www/html
> sudo wget https://github.com/VTejedor803/HLC_TO06/archive/refs/heads/main.zip
> sudo unzip main.zip
> sudo rm main.zip
> sudo mv HLC_TO06-main notas
> sudo chown -R www-data:www-data notas

Crear la base de datos. El fichero migracion.sql está situado en la carpeta data

> mysql -u root -p < notas/data/migracion.sql

Crear el usuario alumno y darle permiso para usar la base de datos tutorial_crud:

> mysql -u root -p;
> CREATE USER 'alumno'@'localhost' IDENTIFIED BY 'Malaga20*';
> GRANT ALL PRIVILEGES ON tutorial_crud.* TO 'alumno'@'localhost';

Modificar el fichero config.php con el usuario y password elegidos:

><?php
>return [
>  'db' => [
>    'host' => 'localhost',
>    'user' => 'alumno',
>    'pass' => 'Malaga20*',
>    'name' => 'tutorial_crud',
>    'options' => [
>        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION
>    ]
>  ]
>];

Y ya lo tendremos disponible y podremos acceder a la web desde el navegador

	nombredelaweb/notas


## Características del dominio utilizado:

![N|Solid](https://i.gyazo.com/7ea3729079ecde06a5898da863bf7745.png)
![N|Solid](https://i.gyazo.com/68512af44eb27ac0484b8dc7be6150a4.png)

## Mi dominio:

> alumnos.rivastejedor.com


