---
title: "Introducción a .NET Core: base de datos nueva - EF Core"
author: rick-anderson
ms.author: riande
ms.author2: tdykstra
description: "Introducción a .NET Core con Entity Framework Core"
keywords: .NET Core, Entity Framework Core, VS Code, Visual Studio Code, Mac, Linux
ms.date: 04/05/2017
ms.assetid: 099d179e-dd7b-4755-8f3c-fcde914bf50b
ms.technology: entity-framework-core
uid: core/get-started/netcore/new-db-sqlite
ms.openlocfilehash: 22fc0446dee71dd0d2402b47d76cc8b7307fbe5f
ms.sourcegitcommit: 5e2d97e731f975cf3405ff3deab2a3c75ad1b969
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="getting-started-with-ef-core-on-net-core-console-app-with-a-new-database"></a><span data-ttu-id="48fa6-104">Introducción a EF Core en la aplicación de consola de .NET Core con una base de datos nueva</span><span class="sxs-lookup"><span data-stu-id="48fa6-104">Getting Started with EF Core on .NET Core Console App with a New database</span></span>

<span data-ttu-id="48fa6-105">En este tutorial, creará una aplicación de consola de .NET Core que realiza el acceso a datos básicos en una base de datos SQLite mediante Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="48fa6-105">In this walkthrough, you will create a .NET Core console app that performs basic data access against a SQLite database using Entity Framework Core.</span></span> <span data-ttu-id="48fa6-106">Usará las migraciones para crear la base de datos a partir del modelo.</span><span class="sxs-lookup"><span data-stu-id="48fa6-106">You will use migrations to create the database from your model.</span></span> <span data-ttu-id="48fa6-107">Consulte [ASP.NET Core: base de datos nueva](xref:core/get-started/aspnetcore/new-db) para una versión de Visual Studio mediante ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="48fa6-107">See [ASP.NET Core - New database](xref:core/get-started/aspnetcore/new-db) for a Visual Studio version using ASP.NET Core MVC.</span></span>

> [!NOTE]  
> <span data-ttu-id="48fa6-108">El [SDK de .NET Core](https://www.microsoft.com/net/download/core) ya no es compatible con `project.json` ni con Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="48fa6-108">The [.NET Core SDK](https://www.microsoft.com/net/download/core) no longer supports `project.json` or Visual Studio 2015.</span></span> <span data-ttu-id="48fa6-109">Se recomienda [migrar de project.json a csproj](https://docs.microsoft.com/dotnet/articles/core/migration/).</span><span class="sxs-lookup"><span data-stu-id="48fa6-109">We recommend you [migrate from project.json to csproj](https://docs.microsoft.com/dotnet/articles/core/migration/).</span></span> <span data-ttu-id="48fa6-110">Si usa Visual Studio, se recomienda migrar a [Visual Studio 2017](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="48fa6-110">If you are using Visual Studio, we recommend you migrate to [Visual Studio 2017](https://www.visualstudio.com/downloads/).</span></span>

> [!TIP]  
> <span data-ttu-id="48fa6-111">Puede ver un [ejemplo](https://github.com/aspnet/EntityFramework.Docs/tree/master/samples/core/GetStarted/NetCore/ConsoleApp.SQLite) de este artículo en GitHub.</span><span class="sxs-lookup"><span data-stu-id="48fa6-111">You can view this article's [sample](https://github.com/aspnet/EntityFramework.Docs/tree/master/samples/core/GetStarted/NetCore/ConsoleApp.SQLite) on GitHub.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48fa6-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="48fa6-112">Prerequisites</span></span>

<span data-ttu-id="48fa6-113">Deberá cumplir los requisitos previos siguientes para completar este tutorial:</span><span class="sxs-lookup"><span data-stu-id="48fa6-113">The following prerequisites are needed to complete this walkthrough:</span></span>
* <span data-ttu-id="48fa6-114">Un sistema operativo compatible con .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48fa6-114">An operating system that supports .NET Core.</span></span>
* <span data-ttu-id="48fa6-115">El [SDK 2.0 de .NET Core](https://www.microsoft.com/net/core) (a pesar de que las instrucciones se pueden usar para crear una aplicación con una versión anterior con muy pocas modificaciones).</span><span class="sxs-lookup"><span data-stu-id="48fa6-115">[The .NET Core SDK](https://www.microsoft.com/net/core) 2.0 (although the instructions can be used to create an application with a previous version with very few modifications).</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="48fa6-116">Crear un proyecto nuevo</span><span class="sxs-lookup"><span data-stu-id="48fa6-116">Create a new project</span></span>

* <span data-ttu-id="48fa6-117">Cree una carpeta `ConsoleApp.SQLite` nueva para el proyecto y use el comando `dotnet` para rellenarlo con una aplicación de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48fa6-117">Create a new `ConsoleApp.SQLite` folder for your project and use the `dotnet` command to populate it with a .NET Core app.</span></span>

``` Console
mkdir ConsoleApp.SQLite
cd ConsoleApp.SQLite/
dotnet new console
```

## <a name="install-entity-framework-core"></a><span data-ttu-id="48fa6-118">Instalación de Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="48fa6-118">Install Entity Framework Core</span></span>

<span data-ttu-id="48fa6-119">Para usar EF Core, instale el paquete correspondiente a los proveedores de bases de datos a los que desea dirigirse.</span><span class="sxs-lookup"><span data-stu-id="48fa6-119">To use EF Core, install the package for the database provider(s) you want to target.</span></span> <span data-ttu-id="48fa6-120">Este tutorial usa SQLite.</span><span class="sxs-lookup"><span data-stu-id="48fa6-120">This walkthrough uses SQLite.</span></span> <span data-ttu-id="48fa6-121">Para una lista de los proveedores disponibles, consulte [Proveedores de bases de datos](../../providers/index.md).</span><span class="sxs-lookup"><span data-stu-id="48fa6-121">For a list of available providers see [Database Providers](../../providers/index.md).</span></span>

* <span data-ttu-id="48fa6-122">Instale Microsoft.EntityFrameworkCore.Sqlite y Microsoft.EntityFrameworkCore.Design</span><span class="sxs-lookup"><span data-stu-id="48fa6-122">Install Microsoft.EntityFrameworkCore.Sqlite and Microsoft.EntityFrameworkCore.Design</span></span>

``` Console
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.EntityFrameworkCore.Design
```

* <span data-ttu-id="48fa6-123">Edite `ConsoleApp.SQLite.csproj` manualmente para agregar DotNetCliToolReference a Microsoft.EntityFrameworkCore.Tools.DotNet:</span><span class="sxs-lookup"><span data-stu-id="48fa6-123">Manually edit `ConsoleApp.SQLite.csproj` to add a DotNetCliToolReference to Microsoft.EntityFrameworkCore.Tools.DotNet:</span></span>

  ``` xml
  <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="2.0.0" />
  </ItemGroup>
  ```

 <span data-ttu-id="48fa6-124">Nota: Una versión futura de `dotnet` admitirá DotNetCliToolReferences a través de `dotnet add tool`</span><span class="sxs-lookup"><span data-stu-id="48fa6-124">Note: A future version of `dotnet` will support DotNetCliToolReferences via `dotnet add tool`</span></span>

<span data-ttu-id="48fa6-125">`ConsoleApp.SQLite.csproj` ahora debe contener lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="48fa6-125">`ConsoleApp.SQLite.csproj` should now contain the following:</span></span>

[!code[Main](../../../../samples/core/GetStarted/NetCore/ConsoleApp.SQLite/ConsoleApp.SQLite.csproj)]

 <span data-ttu-id="48fa6-126">Nota: Los números de versión anteriormente usados eran los correctos en el momento de la publicación.</span><span class="sxs-lookup"><span data-stu-id="48fa6-126">Note: The version numbers used above were correct at the time of publishing.</span></span>

*  <span data-ttu-id="48fa6-127">Ejecute `dotnet restore` para instalar los paquetes nuevos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-127">Run `dotnet restore` to install the new packages.</span></span>

## <a name="create-the-model"></a><span data-ttu-id="48fa6-128">Creación del modelo</span><span class="sxs-lookup"><span data-stu-id="48fa6-128">Create the model</span></span>

<span data-ttu-id="48fa6-129">Defina un contexto y clases de entidad que constituirán el modelo.</span><span class="sxs-lookup"><span data-stu-id="48fa6-129">Define a context and entity classes that make up your model.</span></span>

* <span data-ttu-id="48fa6-130">Cree un archivo *Model.cs* nuevo con el contenido siguiente.</span><span class="sxs-lookup"><span data-stu-id="48fa6-130">Create a new *Model.cs* file with the following contents.</span></span>

[!code-csharp[Main](../../../../samples/core/GetStarted/NetCore/ConsoleApp.SQLite/Model.cs)]

<span data-ttu-id="48fa6-131">Sugerencia: En una aplicación real, colocaría cada clase en un archivo independiente y la cadena de conexión en un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="48fa6-131">Tip: In a real application you would put each class in a separate file and put the connection string in a configuration file.</span></span> <span data-ttu-id="48fa6-132">Para la simplicidad del tutorial, colocaremos todos estos elementos en un solo archivo.</span><span class="sxs-lookup"><span data-stu-id="48fa6-132">To keep the tutorial simple, we are putting everything in one file.</span></span>

## <a name="create-the-database"></a><span data-ttu-id="48fa6-133">Crear la base de datos</span><span class="sxs-lookup"><span data-stu-id="48fa6-133">Create the database</span></span>

<span data-ttu-id="48fa6-134">Una vez que ya tiene un modelo, puede usar las [migraciones](https://docs.microsoft.com/aspnet/core/data/ef-mvc/migrations#introduction-to-migrations) para crear una base de datos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-134">Once you have a model, you can use [migrations](https://docs.microsoft.com/aspnet/core/data/ef-mvc/migrations#introduction-to-migrations) to create a database.</span></span>

* <span data-ttu-id="48fa6-135">Ejecute `dotnet ef migrations add InitialCreate` para aplicar scaffolding a una migración y crear el conjunto inicial de tablas para el modelo.</span><span class="sxs-lookup"><span data-stu-id="48fa6-135">Run `dotnet ef migrations add InitialCreate` to scaffold a migration and create the initial set of tables for the model.</span></span>
* <span data-ttu-id="48fa6-136">Ejecute `dotnet ef database update` para aplicar la migración nueva a la base de datos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-136">Run `dotnet ef database update` to apply the new migration to the database.</span></span> <span data-ttu-id="48fa6-137">Este comando crea la base de datos antes de aplicar las migraciones.</span><span class="sxs-lookup"><span data-stu-id="48fa6-137">This command creates the database before applying migrations.</span></span>

> [!NOTE]  
> <span data-ttu-id="48fa6-138">Cuando use rutas de acceso relativas con SQLite, la ruta de acceso será relativa al ensamblado principal de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="48fa6-138">When using relative paths with SQLite, the path will be relative to the application's main assembly.</span></span> <span data-ttu-id="48fa6-139">En este ejemplo, el binario principal es `bin/Debug/netcoreapp2.0/ConsoleApp.SQLite.dll`, por lo que la base de datos SQLite estará en `bin/Debug/netcoreapp2.0/blogging.db`.</span><span class="sxs-lookup"><span data-stu-id="48fa6-139">In this sample, the main binary is `bin/Debug/netcoreapp2.0/ConsoleApp.SQLite.dll`, so the SQLite database will be in `bin/Debug/netcoreapp2.0/blogging.db`.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="48fa6-140">Uso del modelo</span><span class="sxs-lookup"><span data-stu-id="48fa6-140">Use your model</span></span>

* <span data-ttu-id="48fa6-141">Abra *Program.cs* y reemplace el contenido por el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="48fa6-141">Open *Program.cs* and replace the contents with the following code:</span></span>

 [!code-csharp[Main](../../../../samples/core/GetStarted/NetCore/ConsoleApp.SQLite/Program.cs)]

* <span data-ttu-id="48fa6-142">Pruebe la aplicación:</span><span class="sxs-lookup"><span data-stu-id="48fa6-142">Test the app:</span></span>

 `dotnet run`

 <span data-ttu-id="48fa6-143">Un blog se guarda en la base de datos y los detalles de todos los blogs se muestran en la consola.</span><span class="sxs-lookup"><span data-stu-id="48fa6-143">One blog is saved to the database and the details of all blogs are displayed in the console.</span></span>

  ``` Console
  ConsoleApp.SQLite>dotnet run
  1 records saved to database

  All blogs in database:
   - http://blogs.msdn.com/adonet
  ```

### <a name="changing-the-model"></a><span data-ttu-id="48fa6-144">Cambios del modelo:</span><span class="sxs-lookup"><span data-stu-id="48fa6-144">Changing the model:</span></span>

- <span data-ttu-id="48fa6-145">Si hace cambios en el modelo, puede usar el comando `dotnet ef migrations add` para aplicar scaffolding a una [migración](https://docs.microsoft.com/aspnet/core/data/ef-mvc/migrations#introduction-to-migrations) nueva con el fin de hacer los cambios de esquema correspondientes a la base de datos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-145">If you make changes to your model, you can use the `dotnet ef migrations add` command to scaffold a new [migration](https://docs.microsoft.com/aspnet/core/data/ef-mvc/migrations#introduction-to-migrations)  to make the corresponding schema changes to the database.</span></span> <span data-ttu-id="48fa6-146">Una vez que compruebe el código con scaffold (y haya hecho los cambios necesarios), puede usar el comando `dotnet ef database update` para aplicar los cambios a la base de datos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-146">Once you have checked the scaffolded code (and made any required changes), you can use the `dotnet ef database update` command to apply the changes to the database.</span></span>
- <span data-ttu-id="48fa6-147">EF usa una tabla `__EFMigrationsHistory` en la base de datos para realizar un seguimiento de cuáles son las migraciones que ya se aplicaron a la base de datos.</span><span class="sxs-lookup"><span data-stu-id="48fa6-147">EF uses a `__EFMigrationsHistory` table in the database to keep track of which migrations have already been applied to the database.</span></span>
- <span data-ttu-id="48fa6-148">SQLite no admite todas las migraciones (cambios de esquema) debido a las limitaciones de SQLite.</span><span class="sxs-lookup"><span data-stu-id="48fa6-148">SQLite does not support all migrations (schema changes) due to limitations in SQLite.</span></span> <span data-ttu-id="48fa6-149">Consulte [Limitaciones de SQLite](../../providers/sqlite/limitations.md).</span><span class="sxs-lookup"><span data-stu-id="48fa6-149">See [SQLite Limitations](../../providers/sqlite/limitations.md).</span></span> <span data-ttu-id="48fa6-150">En el caso de un desarrollo nuevo, considere eliminar la base de datos y cree una nueva en lugar de usar migraciones cuando cambie el modelo.</span><span class="sxs-lookup"><span data-stu-id="48fa6-150">For new development, consider dropping the database and creating a new one rather than using migrations when your model changes.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="48fa6-151">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="48fa6-151">Additional Resources</span></span>

* <span data-ttu-id="48fa6-152">[.NET Core: base de datos nueva con SQLite](xref:core/get-started/netcore/new-db-sqlite), un tutorial de EF para la consola multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="48fa6-152">[.NET Core - New database with SQLite](xref:core/get-started/netcore/new-db-sqlite) -  a cross-platform console EF tutorial.</span></span>
* [<span data-ttu-id="48fa6-153">Introducción a ASP.NET Core MVC en Mac o Linux</span><span class="sxs-lookup"><span data-stu-id="48fa6-153">Introduction to ASP.NET Core MVC on Mac or Linux</span></span>](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app-xplat/index)
* [<span data-ttu-id="48fa6-154">Introducción a ASP.NET Core MVC con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48fa6-154">Introduction to ASP.NET Core MVC with Visual Studio</span></span>](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/index)
* [<span data-ttu-id="48fa6-155">Introducción a ASP.NET Core y Entity Framework Core con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48fa6-155">Getting started with ASP.NET Core and Entity Framework Core using Visual Studio</span></span>](https://docs.microsoft.com/aspnet/core/data/ef-mvc/index)