---
title: Comparar Entity Framework 6 y Entity Framework Core
description: Proporciona orientación para elegir entre Entity Framework 6 y Entity Framework Core.
author: rowanmiller
ms.date: 10/27/2016
ms.assetid: a6b9cd22-6803-4c6c-a4d4-21147c0a81cb
uid: efcore-and-ef6/index
ms.openlocfilehash: d5fe9b388707f653fdeb2d6a5daa7215ced71c1d
ms.sourcegitcommit: b3c2b34d5f006ee3b41d6668f16fe7dcad1b4317
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51688724"
---
# <a name="compare-ef-core--ef6"></a>Comparar EF Core y EF6

Entity Framework es un mapeador relacional de objetos (O/RM) para .NET. En este artículo se comparan las dos versiones: Entity Framework 6 y Entity Framework Core.

## <a name="entity-framework-6"></a>Entity Framework 6

Entity Framework 6 (EF6) es una tecnología de acceso a datos probada. Se publicó por primera vez en 2008, como parte de .NET Framework 3.5 SP1 y Visual Studio 2008 SP1. A partir de la versión 4.1, se ha distribuido como paquete NuGet [EntityFramework](https://www.nuget.org/packages/EntityFramework/). EF6 se ejecuta en .NET Framework 4.x, lo que significa que solo lo hace en Windows. 

EF6 sigue siendo un producto que recibe soporte técnico para el que seguirá habiendo correcciones de errores y pequeñas mejoras.

## <a name="entity-framework-core"></a>Entity Framework Core

Entity Framework Core (EF Core) es una reescritura completa de EF6 que se publicó por primera vez en 2016. Se incluye en los paquetes Nuget, el principal de los cuales es [Microsoft.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/). EF Core es un producto multiplataforma que se puede ejecutar en .NET Core o .NET Framework.

EF Core se diseñó para proporcionar una experiencia de desarrollo similar a EF6. La mayoría de las API de nivel superior siguen igual, por lo que EF Core resultará familiar para los desarrolladores que hayan usado EF6.

## <a name="feature-comparison"></a>Comparación de características

EF Core ofrece características nuevas que no se implementarán en EF6 (como [claves alternativas](xref:core/modeling/alternate-keys), [actualizaciones por lotes](xref:core/what-is-new/ef-core-1.0#relational-batching-of-statements) y [evaluación combinada de clientes y bases de datos en consultas LINQ](xref:core/querying/client-eval). Aunque como se trata de un nuevo código base, también carece de algunas características de EF6.

En las tablas siguientes se comparan las características disponibles en EF Core y EF6. Es una comparación general que no muestra todas las características ni explica las diferencias entre la misma característica en las distintas versiones de EF.

La columna EF Core indica la versión del producto en la que la característica apareció por primera vez.

### <a name="creating-a-model"></a>Creación de un modelo

| **Característica**                                           | **EF 6** | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| Asignación de clase básica                                   | Sí      | 1.0                                   |
| Constructores con parámetros                          |          | 2.1                                   |
| Conversiones de valores de propiedad                            |          | 2.1                                   |
| Tipos asignados sin claves (tipos de consulta)               |          | 2.1                                   |
| Convenciones                                           | Sí      | 1.0                                   |
| Convenciones personalizadas                                    | Sí      | 1.0 (parcial)                         |
| Anotaciones de datos                                      | Sí      | 1.0                                   |
| API fluida                                            | Sí      | 1.0                                   |
| Herencia: tabla por jerarquía (TPH)                | Sí      | 1.0                                   |
| Herencia: tabla por tipo (TPT)                     | Sí      |                                       |
| Herencia: tabla por clase concreta (TPC)           | Sí      |                                       |
| Propiedades de estado reemplazadas                               |          | 1.0                                   |
| Claves alternativas                                        |          | 1.0                                   |
| Varios a varios sin entidad de combinación                      | Sí      |                                       |
| Generación de claves: base de datos                              | Sí      | 1.0                                   |
| Generación de claves: cliente                                |          | 1.0                                   |
| Tipos complejos/de propiedad                                   | Sí      | 2.0                                   |
| Datos espaciales                                          | Sí      | 2.2                                   |
| Visualización gráfica de modelo                      | Sí      |                                       |
| Editor de modelo gráfico                                | Sí      |                                       |
| Formato de modelo: código                                    | Sí      | 1.0                                   |
| Formato de modelo: EDMX (XML)                              | Sí      |                                       |
| Crear un modelo desde base de datos: línea de comandos              | Sí      | 1.0                                   |
| Crear un modelo desde base de datos: asistente de VS                 | Sí      |                                       |
| Actualizar modelo desde base de datos                            | Parcial  |                                       |
| Filtros de consulta global                                  |          | 2.0                                   |
| División de tablas                                       | Sí      | 2.0                                   |
| División de entidades                                      | Sí      |                                       |
| Asignación de función escalar de base de datos                      | Insuficiente     | 2.0                                   |
| Asignación de campos                                         |          | 1.1                                   |

### <a name="querying-data"></a>Consulta de datos

| **Característica**                                           | **EF6**  | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| Consultas LINQ                                          | Sí      | 1.0 (en curso para consultas complejas) |
| SQL generado legible                                | Insuficiente     | 1.0                                   |
| Evaluación combinada de cliente/servidor                        |          | 1.0                                   |
| Traslación de GroupBy                                   | Sí      | 2.1                                   |
| Carga de datos relacionados: diligente                           | Sí      | 1.0                                   |
| Carga de datos relacionados: carga diligente de tipo derivados |          | 2.1                                   |
| Carga de datos relacionados: diferida                            | Sí      | 2.1                                   |
| Carga de datos relacionados: explícita                        | Sí      | 1.1                                   |
| Consultas SQL sin formato: tipos de entidad                         | Sí      | 1.0                                   |
| Consultas SQL sin formato: tipos sin entidad (tipos de consulta)       | Sí      | 2.1                                   |
| Consultas SQL sin procesar: componer con LINQ                  |          | 1.0                                   |
| Consultas compiladas de manera explícita                           | Insuficiente     | 2.0                                   |
| Lenguaje de consulta basado en texto (Entity SQL)                | Sí      |                                       |

### <a name="saving-data"></a>Guardado de datos

| **Característica**                                           | **EF6**  | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| Seguimiento de cambios: instantánea                             | Sí      | 1.0                                   |
| Seguimiento de cambios: notificación                         | Sí      | 1.0                                   |
| Seguimiento de cambios: servidores proxy                              | Sí      |                                       |
| Acceso al estado con seguimiento                               | Sí      | 1.0                                   |
| Simultaneidad optimista                                | Sí      | 1.0                                   |
| Transacciones                                          | Sí      | 1.0                                   |
| Procesamiento de instrucciones por lotes                                |          | 1.0                                   |
| Asignación de procedimientos almacenados                              | Sí      |                                       |
| Grafo desconectado: API de bajo nivel                     | Insuficiente     | 1.0                                   |
| Grafo desconectado: de un extremo a otro                         |          | 1.0 (parcial)                         |

### <a name="other-features"></a>Otras características

| **Característica**                                           | **EF6**  | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| Migraciones                                            | Sí      | 1.0                                   |
| API de creación o eliminación de la base de datos                       | Sí      | 1.0                                   |
| Datos de inicialización                                             | Sí      | 2.1                                   |
| Resistencia de conexión                                 | Sí      | 1.1                                   |
| Enlaces de ciclo de vida (eventos, intercepción)                | Sí      |                                       |
| Registro simple (Database.Log)                         | Sí      |                                       |
| Agrupación de DbContext                                     |          | 2.0                                   |

### <a name="database-providers"></a>Proveedores de bases de datos

| **Característica**                                           | **EF6**  | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| SQL Server                                            | Sí      | 1.0                                   |
| MySQL                                                 | Sí      | 1.0                                   |
| PostgreSQL                                            | Sí      | 1.0                                   |
| Oracle                                                | Sí      | 1.0 <sup>(1)</sup>                    |
| SQLite                                                | Sí      | 1.0                                   |
| SQL Server Compact                                    | Sí      | 1.0 <sup>(2)</sup>                    |
| DB2                                                   | Sí      | 1.0                                   |
| Firebird                                              | Sí      | 2.0                                   |
| Jet (Microsoft Access)                                |          | 2.0 <sup>(2)</sup>                    |
| En memoria (para pruebas)                               |          | 1.0                                   |

<sup>1</sup> Actualmente existe un proveedor de pago disponible para Oracle. Se está trabajando en un proveedor oficial gratuito para Oracle.

<sup>2</sup> Los proveedores de SQL Server Compact y Jet solo funcionan en .NET Framework (no en .NET Core).

### <a name="net-implementations"></a>Implementaciones de .NET

| **Característica**                                           | **EF6**  | **EF Core**                           |
|:------------------------------------------------------|:---------|:--------------------------------------|
| .NET Framework (consola, WinForms, WPF, ASP.NET)      | Sí      | 1.0                                   |
| .NET Core (consola, ASP.NET Core)                     |          | 1.0                                   |
| Mono y Xamarin                                        |          | 1.0 (en curso)                     |
| UWP                                                   |          | 1.0 (en curso)                     |

## <a name="guidance-for-new-applications"></a>Guía para las aplicaciones nuevas

Considere el uso de EF Core para una nueva aplicación si se cumplen las dos condiciones siguientes:
* La aplicación necesita las funcionalidades de .NET Core. Para obtener más información, vea [Selección entre .NET Core y .NET Framework para aplicaciones de servidor](https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server).
* EF Core es compatible con todas las características que necesita la aplicación. Si falta alguna característica que quiera, vea el [Mapa de ruta de Entity Framework Core](xref:core/what-is-new/roadmap) para averiguar si existen planes de admitirla en el futuro. 

Considere el uso de EF6 si se cumplen las dos condiciones siguientes:
* La aplicación se va a ejecutar en Windows y .NET Framework 4.0 o posterior.
* EF6 es compatible con todas las características que necesita la aplicación.

## <a name="guidance-for-existing-ef6-applications"></a>Guía para las aplicaciones existentes de EF6

Debido a los cambios fundamentales en EF Core, no se recomienda migrar una aplicación de EF6 a EF Core salvo que exista una razón apremiante para hacerlo. Si quiere migrar a EF Core para usar características nuevas, asegúrese de conocer sus limitaciones. Para obtener más información, vea [Portabilidad de EF6 a EF Core](porting/index.md). **La migración de EF6 a EF Core es más una portabilidad que una actualización.** 

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, vea la documentación:
* <xref:core/index>
* <xref:ef6/index>
