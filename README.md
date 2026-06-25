# silo-cli

Cliente de línea de comandos para [Silo](https://github.com/osdaeg/silo), el gestor de enlaces autoalojado.

## Requisitos

- `bash`
- `curl`
- `python3` (solo para formatear la salida)

## Instalación

```bash
chmod +x silo-cli
sudo cp silo-cli /usr/local/bin/silo
```

## Configuración

Mediante variables de entorno, por ejemplo en `~/.bashrc` o `~/.zshrc`:

```bash
export SILO_HOST=http://192.168.1.10:7123
export SILO_TOKEN=tu_token
```

Si no se definen, usa los valores por defecto: `http://192.168.1.10:7123` y `changeme`.

## Uso

```
silo <comando> [opciones]
```

### Comandos

| Comando | Descripción |
|---|---|
| `list` | Lista enlaces |
| `list --col ID` | Filtra por colección |
| `list --q TEXTO` | Busca enlaces |
| `add <URL>` | Agrega un enlace |
| `add <URL> --title T` | Agrega con título |
| `add <URL> --desc D` | Agrega con descripción |
| `add <URL> --col ID` | Agrega en una colección |
| `del <ID>` | Elimina un enlace |
| `move <ID> <COL_ID>` | Mueve un enlace a otra colección |
| `cols` | Lista colecciones |
| `col-add <NOMBRE>` | Crea una colección |
| `col-del <ID>` | Elimina una colección |
| `sync` | Fuerza sincronización con Raindrop |

### Ejemplos

```bash
# Listar todos los enlaces
silo list

# Buscar
silo list --q "docker"

# Listar por colección
silo list --col 2

# Agregar un enlace
silo add https://example.com --title "Ejemplo" --col 1

# Mover enlace ID 5 a colección ID 3
silo move 5 3

# Ver colecciones disponibles
silo cols

# Forzar sync con Raindrop
silo sync
```

## Servidor

Este cliente requiere una instancia de [Silo](https://github.com/osdaeg/silo) corriendo y accesible.
