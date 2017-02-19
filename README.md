# GULPFILE
El gulpfile es donde se guardan las tareas que se van a llevar a cabo de un proyecto.
El fichero gulpfile se divide en dos partes bien diferenciadas
* Dependencias: donde se llamaran a los plugin que van a ser utilizados para llevar a cabo acciones.
Un ejemplo de dependencia puede ser:
var gulp = require('gulp');

* Tareas: Aquí pondremos cada tarea la cual tendrá una estructura común.

> gulp.task('nombre de la tarea', function() {
>  // código de la tarea por defecto
> });
Donde task es un ejemplo de método que puede ser utilizado.



# DESCRIPCION FICHERO GULPFILE

*	Dependencia  

Dependencia para llamar a gulp  

> var gulp = require("gulp");  

Dependencia para llamar al método shell   
> var shell = require('gulp-shell');  
Dependencia para llamar al plugin ghpages  

> var ghPages = require('gulp-gh-pages');  

*	Tareas  
Se llama al plugin gh-pages y se hace un recorrido en profundida (/**/*) para construir las gh-pages (simplifica el proceso de despliegue de gh-pages) es decir  Todos los archivos y directorios dentro de / gh-pages  serán enviados a la rama gh-pages aunque podría ser cambiada a master  

> gulp.task('gh-pages', function() {  
>   return gulp.src('./gh-pages/**/*')  
>   .pipe(ghPages());  
> });  

Tarea que se utiliza para construir el libro por media de línea de comandos con los comandos de boilerplate (# npm run generate-gitbook && npm run generate-wiki)  

> gulp.task('build',shell.task([  
> 'npm run build'  
> ]));  

Tarea que se utiliza para desplegar el libro por media de línea de comandos con los comandos de boilerplate (# npm run deploy-gitbook && npm run deploy-wiki)  

> gulp.task('deploy',shell.task([  
>   'npm run deploy'  
> ]));  

Tarea que se utiliza para montar el servidor de prueba del libro  por media de línea de comandos  
> gulp.task('serve',shell.task([  
>   'gitbook serve'  
> ]));  
Tarea por defecto donde se ejecutará el deploy y el build solamente  
> gulp.task('default', [ 'deploy','build' ]);
