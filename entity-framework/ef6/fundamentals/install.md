---
title: Obtener Entity Framework - EF6
author: divega
ms.date: 10/23/2016
ms.assetid: 122c38a2-f9e8-4ecc-9c72-a83bc9af7814
ms.openlocfilehash: 7f840a4f9e437ec12f699184339e386976e1528b
ms.sourcegitcommit: 2b787009fd5be5627f1189ee396e708cd130e07b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45490665"
---
# <a name="get-entity-framework"></a>Obtener Entity Framework
Entity Framework está formado por EF Tools para Visual Studio y EF runtime.

## <a name="ef-tools-for-visual-studio"></a>EF Tools para Visual Studio

Entity Framework Tools para Visual Studio incluyen EF Designer y el EF Model Wizard y son necesarios para los flujos de trabajo _database first_ y _model first_. EF Tools es includo en todas las versiones recientes de Visual Studio. Si lleva a cabo una instalación personalizada de Visual Studio, deberá asegurarse el elemento "Entity Frameworks 6 Tools" está seleccionado eligiendo un _workload_ que lo incluya o seleccionandolo como un componente individual.

Para algunas versiones anteriores de Visual Studio, EF Tools actualizadas están disponibles como descarga. Consulte [versiones de Visual Studio](~/ef6/what-is-new/visual-studio.md) para obtener instrucciones sobre cómo obtener la versión más reciente disponible de EF Tools para su versión de Visual Studio.

## <a name="ef-runtime"></a>EF runtime

La versión más reciente de Entity Framework está disponible como [EntityFramework NuGet package](http://nuget.org/packages/EntityFramework/). Si no está familiarizado con el Administrador de paquetes NuGet, le recomendamos que lea [información general sobre NuGet](https://docs.microsoft.com/nuget/consume-packages/overview-and-workflow).

### <a name="installing-the-ef-nuget-package"></a>Instalar EF NuGet package

Puede instalar Entity Framework package con el botón secundario sobre el directorio **References** del proyecto y seleccionando **Administrar paquetes NuGet...**

![Administrar paquetes NuGet](~/ef6/media/managenugetpackages.png)

### <a name="installing-from-package-manager-console"></a>Instalación desde Package Manager Console

Como alternativa, puede instalar EntityFramework ejecutando el siguiente comando en el [Package Manager Console](http://docs.nuget.org/docs/start-here/using-the-package-manager-console).

``` powershell
Install-Package EntityFramework
```

## <a name="installing-a-specific-version-of-ef"></a>Instalar una versión concreta de EF

De EF 4.1 y versiones posteriores, se publican nuevas versiones del tiempo de ejecución EF como [EntityFramework NuGet Package](https://www.nuget.org/packages/EntityFramework/). Cualquiera de estas versiones se pueden agregar a un proyecto basado en .NET Framework ejecutando el siguiente comando en Visual Studio [Package Manager Console](http://docs.nuget.org/docs/start-here/using-the-package-manager-console):

``` powershell
Install-Package EntityFramework -Version <number>
```

Tenga en cuenta que `<number>` representa la versión específica de EF para instalar. Por ejemplo, la 6.2.0 es la versión del número de EF 6.2.   

Los EF runtimes anteriores a 4.1 formaban parte de .NET Framework y no se puede instalar por separado.

### <a name="installing-the-latest-preview"></a>Instalar la última versión preliminar

Los métodos anteriores le proporcionarán la versión más reciente totalmente compatible con la versión de Entity Framework. A menudo hay versiones preliminares disponibles de Entity Framework que nos encantaría que probara y de las que puede enviarnos sus comentarios.

Para instalar la versión preliminar más reciente de Entity Framework puede seleccionar **Incluir versión preliminar** en la ventana Administrar paquetes NuGet. Si no hay ninguna versión preliminar disponible automáticamente obtendrá la última versión compatible de Entity Framework.

![Incluir versión preliminar](~/ef6/media/includeprerelease.png)

Como alternativa, puede ejecutar el siguiente comando en el [Package Manager Console](http://docs.nuget.org/docs/start-here/using-the-package-manager-console).

``` powershell
Install-Package EntityFramework -Pre
```
