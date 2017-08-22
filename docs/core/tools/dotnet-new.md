---
title: "Команда dotnet-new — CLI .NET Core | Документы Майкрософт"
description: "Команда dotnet-new создает проекты .NET Core в текущем каталоге."
keywords: "dotnet-new, CLI, команда CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: Human Translation
ms.sourcegitcommit: 68fbe2e9895825bbbb41cfe025bfdf1d4f9d3d04
ms.openlocfilehash: 14279ea6fdf4af52c0492f2dad1171d8150ac95b
ms.contentlocale: ru-ru
ms.lasthandoff: 05/05/2017

---

# <a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>Имя

`dotnet-new` — создает проект, файл конфигурации или решений на основе указанного шаблона.

## <a name="synopsis"></a>Краткий обзор

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>Описание

Команда `dotnet new` предоставляет удобный способ инициализации проекта .NET Core. 

Она вызывает [подсистему шаблонов](https://github.com/dotnet/templating), чтобы создать артефакты на диске на основе заданных параметров и шаблона.

## <a name="arguments"></a>Аргументы

`TEMPLATE`

Шаблон для создания экземпляров при вызове команды. Каждый шаблон может иметь отдельные параметры, доступные для передачи. Дополнительные сведения см. в разделе [Параметры шаблона](#template-options).

Команда содержит список шаблонов по умолчанию. Используйте `dotnet new -all`, чтобы получить список доступных шаблонов. В следующей таблице представлены шаблоны, которые устанавливаются вместе с пакетом SDK. Язык по умолчанию для шаблона указан внутри квадратных скобок.

|Описание шаблона  | Имя шаблона  | Языки |
|----------------------|----------------|-----------|
| Консольное приложение  | console        | [C#], F#  |
| Библиотека классов        | classlib       | [C#], F#  |
| Проект модульного теста    | mstest         | [C#], F#  |
| Проект теста xUnit   | xunit          | [C#], F#  |
| Пустой ASP.NET Core   | web            | [C#]      |
| Веб-приложение ASP.NET Core | mvc            | [C#], F#  |
| Веб-API ASP.NET Core | webapi         | [C#]      |
| Конфигурация Nuget         | nugetconfig    |           |
| Веб-конфигурация           | webconfig      |           |
| Файл решения        | sln            |           |

## <a name="options"></a>Параметры

`-h|--help`

Распечатывает справку для команды. Его можно вызвать для самой команды `dotnet new` или для любого шаблона, например `dotnet new mvc --help`.

`-l|--list`

Перечисляет шаблоны с указанным именем. При вызове для команды `dotnet new` перечисляет возможные шаблоны, доступные для заданного каталога. Например, если каталог уже содержит проект, он не будет перечислять все шаблоны проекта.

`-lang|--language {C#|F#}`

Язык создаваемого шаблона. Допустимый язык зависит от шаблона (см. значения по умолчанию в разделе об [аргументах](#arguments)). Не является допустимым для некоторых шаблонов.

`-n|--name <OUTPUT_NAME>`

Имя создаваемых выходных данных. Если имя не указано, используется имя текущего каталога.

`-o|--output <OUTPUT_DIRECTORY>`

Расположение, в котором размещаются созданные выходные данные. Значением по умолчанию является текущий каталог.

`-all|--show-all`

Показывает все шаблоны определенного типа проекта при запуске в контексте одной только команды `dotnet new`. При запуске в контексте конкретного шаблона, например `dotnet new web -all`, `-all` интерпретируется как флаг принудительного создания. Это требуется, когда выходной каталог уже содержит проект.

## <a name="template-options"></a>Параметры шаблона

Каждый шаблон проекта может содержать дополнительные доступные параметры. Основные шаблоны имеют следующие параметры:

**console, xunit, mstest, web, webapi**

`-f|--framework` — указывает целевую [платформу](../../standard/frameworks.md). Значения: `netcoreapp1.0` или `netcoreapp1.1` (по умолчанию: `netcoreapp1.0`)

**mvc**

`-f|--framework` — указывает целевую [платформу](../../standard/frameworks.md). Значения: `netcoreapp1.0` или `netcoreapp1.1` (`Default: netcoreapp1.0`)

`-au|--auth` — тип проверки подлинности. Значения: `None` или `Individual` (по умолчанию: `None`)

`-uld|--use-local-db` — указывает, следует ли использовать LocalDB вместо SQLite. Значения: `true` или `false` (по умолчанию: `false`)

**classlib**

`-f|--framework` — указывает целевую [платформу](../../standard/frameworks.md). Значения: `netcoreapp1.0`, `netcoreapp1.1` или с `netstandard1.0` по `netstandard1.6` (по умолчанию: `netstandard1.4`)

## <a name="examples"></a>Примеры

Создание проекта консольного приложения F# в текущем каталоге:

`dotnet new console -lang f#` 
   
Создайте проект приложения ASP.NET Core C# MVC в текущем каталоге без проверки подлинности для .NET Core 1.0:  

`dotnet new mvc -au None -f netcoreapp1.0`
 
Создайте приложение XUnit, предназначенное для .NET Core 1.1:

`dotnet new xunit --Framework netcoreapp1.1`

Перечислите все шаблоны, доступные для MVC:

`dotnet new mvc -l`

