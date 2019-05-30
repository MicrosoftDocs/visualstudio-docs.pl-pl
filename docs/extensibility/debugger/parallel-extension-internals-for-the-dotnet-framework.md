---
title: Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351481"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework
W tej sekcji opisano wewnętrznych typów, metod i pól klasy, które ułatwiają wdrożenie niestandardowego debugera dla rozszerzenia równoległe w .NET Framework.

## <a name="in-this-section"></a>W tej sekcji
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md) opisuje elementów członkowskich danych wewnętrznych <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy.

 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md) opisuje elementów członkowskich danych wewnętrznych <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy.

 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md) opisuje elementów członkowskich danych wewnętrznych `System.Threading.Tasks.ContingentProperties` klasy.

 [AsyncTaskMethodBuilder, struktura](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) opisuje wewnętrznych członków <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.

 [AsyncTaskMethodBuilder\<TResult > Struktura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) opisuje wewnętrznych członków <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.

 [AsyncVoidMethodBuilder, struktura](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) opisuje wewnętrznych członków <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.

## <a name="see-also"></a>Zobacz także
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)