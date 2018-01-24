---
title: Proveedores de bases de datos - EF Core
author: rowanmiller
ms.author: divega
ms.date: 10/27/2016
ms.assetid: 14fffb6c-a687-4881-a094-af4a1359a296
ms.technology: entity-framework-core
uid: core/providers/index
ms.openlocfilehash: 19c275b7e89c62e79c8bded977e39b2cfb2b439a
ms.sourcegitcommit: 01a75cd483c1943ddd6f82af971f07abde20912e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="database-providers"></a><span data-ttu-id="eccf2-102">Proveedores de bases de datos</span><span class="sxs-lookup"><span data-stu-id="eccf2-102">Database Providers</span></span>

<span data-ttu-id="eccf2-103">Entity Framework Core usa un modelo de proveedor para permitir que se use EF para acceder a muchas bases de datos diferentes.</span><span class="sxs-lookup"><span data-stu-id="eccf2-103">Entity Framework Core uses a provider model to allow EF to be used to access many different databases.</span></span> <span data-ttu-id="eccf2-104">Algunos conceptos son comunes a la mayoría de las bases de datos y se incluyen en los componentes principales de EF Core.</span><span class="sxs-lookup"><span data-stu-id="eccf2-104">Some concepts are common to most databases, and are included in the primary EF Core components.</span></span> <span data-ttu-id="eccf2-105">Estos conceptos incluyen la expresión de consultas en LINQ, las transacciones y el seguimiento de cambios en objetos una vez cargados desde la base de datos.</span><span class="sxs-lookup"><span data-stu-id="eccf2-105">Such concepts include expressing queries in LINQ, transactions, and tacking changes to objects once they are loaded from the database.</span></span> <span data-ttu-id="eccf2-106">Algunos conceptos son específicos de un proveedor determinado.</span><span class="sxs-lookup"><span data-stu-id="eccf2-106">Some concepts are specific to a particular provider.</span></span> <span data-ttu-id="eccf2-107">Por ejemplo, el proveedor de SQL Server permite configurar tablas optimizadas para memoria (una característica específica de SQL Server).</span><span class="sxs-lookup"><span data-stu-id="eccf2-107">For example, the SQL Server provider allows you to configure memory-optimized tables (a feature specific to SQL Server).</span></span> <span data-ttu-id="eccf2-108">Otros conceptos son específicos de una clase de proveedores.</span><span class="sxs-lookup"><span data-stu-id="eccf2-108">Other concepts are specific to a class of providers.</span></span> <span data-ttu-id="eccf2-109">Por ejemplo, los proveedores de EF Core para bases de datos relacionales se basan en la biblioteca común `Microsoft.EntityFrameworkCore.Relational`, que proporciona API para configurar asignaciones de tabla y columna, restricciones de clave externa, etc.</span><span class="sxs-lookup"><span data-stu-id="eccf2-109">For example, EF Core providers for relational databases build on the common `Microsoft.EntityFrameworkCore.Relational` library, which provides APIs for configuring table and column mappings, foreign key constraints, etc.</span></span>

<span data-ttu-id="eccf2-110">Los proveedores de EF Core se componen de una serie de orígenes.</span><span class="sxs-lookup"><span data-stu-id="eccf2-110">EF Core providers are built by a variety of sources.</span></span> <span data-ttu-id="eccf2-111">No todos los proveedores se mantienen como parte del proyecto Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="eccf2-111">Not all providers are maintained as part of the Entity Framework Core project.</span></span> <span data-ttu-id="eccf2-112">Al considerar un proveedor de terceros, evalúe la calidad, las licencias, el soporte técnico, etc. a fin de asegurarse de que satisface los requisitos.</span><span class="sxs-lookup"><span data-stu-id="eccf2-112">When considering a third party provider, be sure to evaluate quality, licensing, support, etc. to ensure they meet your requirements.</span></span>