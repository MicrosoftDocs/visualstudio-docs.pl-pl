---
title: Równoległe wewnętrzne rozszerzenia dla .NET Framework | Microsoft Docs
description: Te zasoby opisują typy wewnętrzne, metody i pola klas używanych do implementowania niestandardowego debugera dla równoległych rozszerzeń .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 858bf85e65cd761e7f881856286578495db6143a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903011"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Równoległe wewnętrzne rozszerzenia dla .NET Framework
W tej sekcji opisano typy wewnętrzne, metody i pola klas, które ułatwiają implementowanie niestandardowego debugera dla rozszerzeń równoległych .NET Framework.

## <a name="in-this-section"></a>W tej sekcji
 [Task, klasa](../../extensibility/debugger/task-class-internal-members.md) Opisuje wewnętrzne składowe danych <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy.

 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md) Opisuje wewnętrzne składowe danych <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy.

 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md) Opisuje wewnętrzne składowe danych `System.Threading.Tasks.ContingentProperties` klasy.

 [AsyncTaskMethodBuilder, struktura](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> członkowskie struktury.

 [AsyncTaskMethodBuilder \<TResult> structure (Struktura AsyncTaskMethodBuilder)](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) Opisuje wewnętrzne składowe <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.

 [AsyncVoidMethodBuilder, struktura](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> członkowskie struktury.

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio rozszerzalność debugera](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
