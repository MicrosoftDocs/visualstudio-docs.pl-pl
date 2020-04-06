---
title: Wewnętrzne rozszerzenia równoległego dla .NET Framework | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738276"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Wewnętrzne rozszerzenia równoległego dla programu .NET Framework
W tej sekcji opisano wewnętrzne typy, metody i pola klas, które ułatwiają implementowanie niestandardowego debugera dla równoległych rozszerzeń do programu .NET Framework.

## <a name="in-this-section"></a>W tej sekcji
 [Klasa zadań](../../extensibility/debugger/task-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie <xref:System.Threading.Tasks.Task?displayProperty=fullName> danych klasy.

 [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> danych klasy.

 [Klasa Właściwości warunkowe](../../extensibility/debugger/contingentproperties-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie `System.Threading.Tasks.ContingentProperties` danych klasy.

 [AsyncTaskMethodBuilder struktura](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> członkowskie struktury.

 [AsyncTaskMethodBuilder\<TResult> struktura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) Opisuje wewnętrzne <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> elementy członkowskie struktury.

 [Struktura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> członkowskie struktury.

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
