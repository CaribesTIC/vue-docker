# Modo Prueba

>Para este entorno en realidad no hay nada de que preocuparse, ya que simplemente aprovecharemos paralelamente el mismo entorno `development`.

Echemos un vistazo a la última instrucción de la plantilla de desarrollo.

📃docker-compose.dev.yml
```js
# omitted for brevity ...
command: sh -c "cd /app; npm install; npm run dev"
```


Tenga en cuenta que mientras no cancelemos el `npm run dev` que ejecutamos como último comando en modo `development`, el contenedor se mantendrá vivo. Por lo que podemos abrir otro terminal y entrar dentro del contenedor con el siguiente comando:

```sh
docker exec -it vue_dev_env bash
```
Listo, ya estamos dentro del contenedor.

```sh
root@4e31d8b8d95b:/app#
```

Por lo que, si ya tenemos instalado correctamente Vitest y Vue Test Utils, como se [indicó](../guide/simple-example.html) previamente, entonces podemos probar la aplicación.

Ejecutemos la instrucción `npm run test:unit`.

```sh
root@4e31d8b8d95b:/app# npm run test:unit

> docker-vue-example@0.0.0 test:unit
> vitest --environment jsdom


 DEV  v0.21.1 /app

 ✓ src/components/__tests__/HelloWorld.spec.ts (1)

Test Files  1 passed (1)
     Tests  1 passed (1)
  Start at  23:01:38
  Duration  3.60s (setup 1ms, collect 381ms, tests 25ms)

                                                                                                                                     
 PASS  Waiting for file changes...                                                                                                   
       press h to show help, press q to quit
```

>Presione `Ctrl-C` para detener la prueba y ejecute `exit` para salir del contenedor.
>Presione `Ctrl-C` para detener el contenedor en modo `development`.

