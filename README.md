[![Build Status](https://travis-ci.org/rubensa/reservas-client.svg)](https://travis-ci.org/rubensa/reservas-client)
[![codecov](https://codecov.io/gh/rubensa/reservas-client/branch/master/graph/badge.svg)](https://codecov.io/gh/rubensa/reservas-client)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Plataforma web para la gestión de reservas de aulas y espacios comunes en la Escuela Politécnica de Ingeniería de Gijón

Los administradores de la plataforma podrán definir los recursos disponibles (tales como aulas, salas de reuniones, etc.), así como definir el calendario o las fechas en las que estos recursos pueden ser utilizados. Los usuarios de la plataforma podrán visualizar las reservas efectuadas, así como conocer la disponibilidad de un determinado recurso en un período de tiempo dado o para una fecha concreta. La plataforma soportará carga masiva de datos, para lo que se definirán ficheros de intercambio con las herramientas actuales de gestión de horarios de la Escuela y del sistema de gestión académica SIES.

Las tecnologías a utilizar serán **Java** para la parte del back-end usando como framework de desarrollo **Spring** y **Java Script** para la parte del front-end usando como framework de desarrollo **Angular**.

## Desarrollo

Este proyecto está configurado para ser editado en **[VSCode](https://code.visualstudio.com/)** y sus extensiones para **[Desarrollo Remoto](https://code.visualstudio.com/docs/remote/remote-overview)**.

Concretamente el desarrollo se realiza en un contenedor **Docker** (es necesario tener instalado Docker en tu equipo) con una imagen con **Node 12**.

Antes de abrir el proyecto en el contedor usando **VSCode**, es necesario adaptar los siguiente parámetros en el fichero **./devcontainer/devcontainer.json**:
*  **runArgs**
    *  **"-u", "1000:1000"**: 1000:1000 se debe cambiar por tu UID, GID.  Para conocerlos puedes ejecutar el comando `echo "$(id -u):$(id -g)"` en una consola.
*   **"--group-add", "1001"**: 1001 se debe cambiar por el GID del grupo **docker**.  Para conocerlo puedes ejecutar el comando `cut -d: -f3 < <(getent group docker)` en una consola.
*   **"--mount", "type=bind,source=/usr/local/bin/docker,target=/home/user/.local/bin/docker"**: Asegúrate que **/usr/local/bin/docker** es la ruta correcta al binario de tu instalación de docker local.  Si no es así, actualíza dicha ruta.

Además, deben existir los siguientes directorios en tu directorio **HOME**:
*  **.nvm/.cache**: Se usa para compartir las distribuciones descargadas de Node entre el host y el contenedor.
*  **.ssh**: Se usa para compartir las credenciales ssh entre el host y el contenedor.
*  **.gitconfig**: Se usa para compartir la configuración de git entre el host y el contenedor.

## Instalación de dependencias

Para descargar las dependencias de la aplicación es necesario ejecutar (solo la primera vez) el comando `npm install`.

## Servidor de desarrollo

Ejecuta `ng serve` para arrancar el serviodr de desarrollo. Navega a `http://localhost:4200/`. La aplicación se recargará automáticamente si modificas algún fichero fuente.

## Generación de código

Ejecuta `ng generate component component-name` para generar un nuevo componente. También puedes usar `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Construcción

Ejecuta `ng build` para construir el projecto. La construcción se generará en el directorio `dist/`. Usa el flag `--prod` para una construcción para producción.

## Ejecutando tests unitarios

Ejecuta `ng test` para ejecutar los test unitarios usando [Karma](https://karma-runner.github.io).

## Ejecutando tests end-to-end

Ejecuta `ng e2e` para ejecutar tests end-to-end usando [Protractor](http://www.protractortest.org/).

## Ayuda adicional

Para obtener ayuda adicional de Angular CLI usa `ng help` o visita el [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
