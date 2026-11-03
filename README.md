# Dado giratorio

Aplicación web sencilla que muestra un dado (un cuadrado sin florituras) que gira y devuelve un número aleatorio.
Es el proyecto de la práctica **P1.1 Estrategias de branching. GitFlow** del módulo de *Puesta en Producción Segura*.
El objetivo no es el diseño, sino aplicar GitFlow en equipo sobre un caso de uso real.

## Tecnologías

- **HTML** y **CSS**: estructura y animación del dado.
- **JavaScript**: botón "Tirar" y actualización del resultado sin recargar la página.
- **PHP**: generación del número aleatorio en el servidor.

## Estructura del proyecto

```
.
├── index.php     # Página principal con el dado
├── style.css     # Estilos y animación de giro
├── script.js     # Lógica del botón "Tirar"
├── tirar.php     # Devuelve el resultado de la tirada
└── README.md
```

## Cómo ejecutarlo

Requisitos: PHP 8 o superior.

```bash
git clone <URL-del-repositorio>
cd <carpeta-del-repositorio>
php -S localhost:8000
```

Después, abre <http://localhost:8000> en el navegador y pulsa **Tirar**.

## Modelo de ramas (GitFlow)

| Rama | Uso |
|------|-----|
| `main` | Producción. Solo recibe fusiones de `release/*` y `hotfix/*`. Cada versión lleva un tag (`v1.0.0`). |
| `develop` | Integración. Aquí se fusionan las funcionalidades terminadas. |
| `feature/*` | Una funcionalidad por rama. Sale de `develop` y vuelve a `develop`. |
| `release/x.y.z` | Preparación de una versión. Sale de `develop` y se fusiona en `main` y `develop`. |
| `hotfix/x.y.z` | Corrección urgente en producción. Sale de `main` y se fusiona en `main` y `develop`. |

### Ramas de este proyecto

| Rama | Contenido |
|------|-----------|
| `feature/dado-giro` | Animación CSS del giro y botón "Tirar" con JavaScript |
| `feature/resultado-php` | `tirar.php` genera el número aleatorio y el JS lo muestra en el dado |
| `release/1.0.0` | Versión visible en la página y documentación actualizada |
| `hotfix/1.0.1` | Corrección de seguridad: validación de los parámetros recibidos en `tirar.php` |

## Flujo de trabajo

1. Nadie trabaja directamente en `main` ni en `develop`.
2. Cada cambio se hace en su rama, con commits pequeños y descriptivos.
3. Las fusiones se hacen mediante **pull request** revisada por otro miembro del equipo.
4. Todas las fusiones usan **merge commit** (sin squash ni rebase), para que el flujo se vea en el historial.
5. Las versiones se etiquetan en `main` con versionado semántico (`MAJOR.MINOR.PATCH`).

### Convención de commits

```
feat(ambito): descripción corta     # nueva funcionalidad
fix(ambito): descripción corta      # corrección de un error
chore(ambito): descripción corta    # mantenimiento, versiones, documentación
```

## Versiones

| Versión | Descripción |
|---------|-------------|
| `v1.0.0` | Primera versión: dado que gira y devuelve un resultado aleatorio |
| `v1.0.1` | Hotfix: validación de entrada en `tirar.php` |

Versión actual: **0.1.0** (en desarrollo).

## Equipo

- [Nombre y apellidos del miembro 1]
- [Nombre y apellidos del miembro 2]
- [Nombre y apellidos del miembro 3]

## Contexto académico

Módulo: Puesta en Producción Segura · Práctica P1.1 (RA5.a, b y g).
