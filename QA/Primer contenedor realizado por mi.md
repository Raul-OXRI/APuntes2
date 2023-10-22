en este aparatdo probe he intente hacer un despliegue en docker en este caso use las siguientes tecnologias:
- Docker 
- Nginx
- HTML
![](https://i.imgur.com/2Zg216J.png)

## Docker
en est eva ser lo que vamso a usar para hacer el despliegue y contenerizar el prodcuto 
en este caso contenerizamos un nginx lo que se uso en la carpeta fue un #dockerfile

en el cockerfile se puso todo los pasos
### dockerfile
![](https://i.imgur.com/1KRTlyP.png)
```dockerfile
# Usa la imagen base oficial de Nginx
FROM nginx
# Copia tus archivos de configuración personalizados (si los tienes) al contenedor
# Si no tienes archivos personalizados, este paso es opcional
COPY nginx.conf /etc/nginx/nginx.conf
# Expone el puerto 80 para que el servidor web Nginx sea accesible
EXPOSE 80
# Comando para iniciar Nginx una vez que se ejecute el contenedor
CMD ["nginx", "-g", "daemon off;"]
```

### nginx.confi
en este caso tambien puso las configuraciones necesarios para hacer los pasos necesarios donde uno puede deployar el nginx

![](https://i.imgur.com/LZ6OG6R.png)

```Nginx
# Definición de eventos que afectan al servidor Nginx
events {
    worker_connections 1024; # Número máximo de conexiones simultáneas por trabajador
}
# Configuración principal del servidor
http {
    # Configuración de tipos MIME
    include       mime.types;
    default_type  application/octet-stream;
    # Configuración de registros (logs)
    access_log  /var/log/nginx/access.log;
    error_log   /var/log/nginx/error.log;
    # Configuración del servidor web
    server {
        listen       80; # Puerto en el que Nginx escuchará las solicitudes
        # Ruta al directorio raíz de tu sitio web
        root         /usr/share/nginx/html;
        # Nombre de archivo predeterminado cuando se accede a un directorio
        index        index.html;
        # Configuración de ubicación para controlar las rutas
        location / {
            try_files $uri $uri/ /index.html;
        }
        # Configuración para manejar las solicitudes PHP (si es necesario)
        # location ~ \.php$ {
        #     fastcgi_pass   php-fpm-container:9000;
        #     fastcgi_index  index.php;
        #     fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
        #     include        fastcgi_params;
        # }
    }
}
```

### terminal 
![](https://i.imgur.com/cOoEFY7.png)
![](https://i.imgur.com/Y9Xw6J3.png)
![](https://i.imgur.com/njb7kE1.png)
![](https://i.imgur.com/N7KU3IE.png)
![](https://i.imgur.com/jmpzkTo.png)
![](https://i.imgur.com/1QJqAue.png)
![](https://i.imgur.com/3g7IDAF.png)
Nota: al momento de parar el docker se debe de colocar el ID no el nombre del deppliegue