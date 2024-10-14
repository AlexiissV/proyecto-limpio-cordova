
# Proyecto limpio de cordova

este proyecto funciona el barcode escanner y el lector de huellas en android
recuerda cambiar el nombre en todo el proyecto **"new-name"**

## Dependencias
es recomendable usar **NVM** por si se manejan varios proyectos, si es el unico proyecto a trabajar omitir la instalcion de **NVM**

- **NVM** [instalación/ Configuración](https://github.com/nvm-sh/nvm)
- **Node js** [Node js CLI](https://nodejs.org/es) version 16.14.0.
```bash
  nvm install v16.14.0
```
- **Ionic CLI**: 6.20.9
```bash
  npm i -g @ionic/cli@6
```
- **npm**: 8.3.1

## --OPCIONAL-- Link para generar splash and icon
En el caso necesario de que tengas que personalizar el splash y/o icono de la aplicación
- necesitas tener el splash en 2732x2732 pixeles
- necesitas tener el Icon en 1024x1024 pixeles
- **link generador de resources** [Splash/Icon](https://apetools.webprofusion.com/#/tools/imagegorilla)

## Información Util Adicional

- [Android Platform Guide](https://cordova.apache.org/docs/en/dev/guide/platforms/android/index.html)
- [Plugins Cordova](https://danielsogl.gitbook.io/awesome-cordova-plugins)
- [Doc- implementación en ionic](https://ionic-docs-5utg8ms4c-ionic1.vercel.app/docs/v5/native)

## Comandos IONIC-CORDOVA
### primero hay que colocar un nombre y su identificador unico de aplicación

En la raíz del proyecto se encuentra el archivo **config.xml** donde tenemos que configurar el nombre y el ID unico de aplicación
para preparar el proyecto ya sea "android" o "ios"

```bash
<widget id="com.ifnb.recepcion" version="0.0.1" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
```
En la siguiente linea es donde se coloca el nombre que va aparecer en los dispositivos que este instalada
```bash
<name>IFNB Recepción</name>
```
una vez configurando estos apartados ya podemos ejecutar la siguiente lista de comandos:

```bash
ionic cordova platform add Android
```
```bash
ionic cordova prepare android
```
generar resources splash y icon
```bash
ionic cordova resources -- force
```
si usas nvm puede que no funcione entonces tines que seguir la opcion de la pagina web mencionada anteriormente
```bash
ionic cordova build android --prod
```
Despues de todos los comandos anteriores podemos abrir e proyecto en android studio y suerte para que no te marque ningun error.

## En algun punto me han llegado a slir errores al instlar dependecnias o plugins

```bash
npm install @angular/cli --legacy-peer-deps
```
```bash
npm install @ionic/app-scripts@latest --save-dev --legacy-peer-deps
```
```bash
npm install @awesome-cordova-plugins/core --save --legacy-peer-deps
```
## Comentarios de configuracion android

con esta linea en el **build.gradel** llega ha funcionar
- classpath "com.android.tools.build:gradle:7.2.1"
Podemos configurar varias variables según se requiera con un archivo de configuracion especifico **"cdv-gradle-config"** path:/node_modules/cordova-android/framework/cdv-gradle-config-defaults.json

```bash
{
  "MIN_SDK_VERSION": 22,
  "SDK_VERSION": 34, 
  "GRADLE_VERSION": "7.3.3",
  "MIN_BUILD_TOOLS_VERSION": "34",
  "BUILD_TOOLS_VERSION": "34.0.0",
  "AGP_VERSION": "7.2.1",
  "KOTLIN_VERSION": "1.5.21",
  "ANDROIDX_APP_COMPAT_VERSION": "1.3.1",
  "ANDROIDX_WEBKIT_VERSION": "1.4.0",
  "GRADLE_PLUGIN_GOOGLE_SERVICES_VERSION": "4.3.8",
  "IS_GRADLE_PLUGIN_GOOGLE_SERVICES_ENABLED": false,
  "IS_GRADLE_PLUGIN_KOTLIN_ENABLED": false
}

```
### Esta es la version antiguia por si algo no funciona regresas todas la variables y vuleves a correr el build desde 0

```bash
{
    "MIN_SDK_VERSION": 22,
    "SDK_VERSION": 34,
    "GRADLE_VERSION": "7.3.3",
    "MIN_BUILD_TOOLS_VERSION": "34.0.0",
    "AGP_VERSION": "7.2.1",
    "KOTLIN_VERSION": "1.5.21",
    "ANDROIDX_APP_COMPAT_VERSION": "1.6.1",
    "ANDROIDX_WEBKIT_VERSION": "1.7.0",
    "GRADLE_PLUGIN_GOOGLE_SERVICES_VERSION": "4.3.8",
    "IS_GRADLE_PLUGIN_GOOGLE_SERVICES_ENABLED": false,
    "IS_GRADLE_PLUGIN_KOTLIN_ENABLED": false
}
```
Este json configura las necesidaes de tu proyecto y las configuraciones para que se pueda compilar correctamente has que tener en cuenta que cada uno de los parametros tienen que ser compatibles entre todos

- project structure
- **dependecias TODAS DEBEN DECIR "implementation"**