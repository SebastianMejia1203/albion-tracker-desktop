# Albion Tracker Desktop

Adaptación de **AlbionOnline Statistics Analysis Tool (SAT)** para compartir estadísticas de Albion Online con una aplicación móvil en la red local.

Este repositorio deriva del trabajo de [Triky313 y los colaboradores de SAT](https://github.com/Triky313/AlbionOnline-StatisticsAnalysis). La integración móvil se desarrolla sobre esa base; se conserva la documentación original en [README.upstream.md](README.upstream.md).

## Qué aporta esta adaptación

- Servidor ASP.NET Core integrado en la aplicación de escritorio.
- Comunicación en tiempo real mediante SignalR.
- Hub móvil en `/mobilehub`.
- Descubrimiento del servidor en la red local mediante UDP.
- Endpoints `/health` y `/info` para consultar el estado.
- Intercambio de datos con [Albion Tracker Mobile](https://github.com/SebastianMejia1203/albion-tracker-mobile).

El servidor móvil utiliza el puerto `7777` de forma predeterminada. Las funciones de análisis de daño, recolección, mazmorras y registro provienen de SAT y de sus módulos.

## Requisitos

- Windows y SDK de .NET 9 para compilar.
- Para ejecutar una compilación dependiente del framework: .NET 9 Desktop Runtime.
- Albion Online y una configuración de captura compatible con SAT.
- PC y móvil conectados a la misma red para la integración móvil.

Las versiones publicadas por el proyecto original no necesariamente incluyen los cambios de este repositorio.

## Compilar desde el código

```bash
dotnet restore src/StatisticsAnalysisTool.sln
dotnet build src/StatisticsAnalysisTool.sln -c Release
```

También puedes abrir la solución en Visual Studio con soporte para WPF y .NET 9.

## Conexión con el móvil

1. Ejecuta esta adaptación de SAT y configura la captura del juego.
2. Inicia el servidor móvil desde la aplicación.
3. Conecta Albion Tracker Mobile mediante descubrimiento local o introduciendo la IP del PC y el puerto configurado.
4. Si no hay conexión, revisa el firewall y la conectividad entre ambos dispositivos.

El servidor está orientado a una red local de confianza. Su implementación escucha en las interfaces de red y no configura autenticación en el hub.

## Estructura

- `src/StatisticsAnalysisTool/`: aplicación WPF.
- `src/StatisticsAnalysisTool.MobileServer/`: servidor SignalR y descubrimiento.
- `src/StatisticsAnalysisTool.Network/`: procesamiento de eventos de red.
- `src/StatisticsAnalysisTool.UnitTests/`: pruebas.
- `docs/`: documentación y capturas.

## Créditos y licencia

Proyecto original: [AlbionOnline Statistics Analysis](https://github.com/Triky313/AlbionOnline-StatisticsAnalysis), de Triky313 y sus colaboradores. Se conserva el archivo [LICENSE](LICENSE), que contiene GNU GPL v3, y la documentación original con sus créditos.
