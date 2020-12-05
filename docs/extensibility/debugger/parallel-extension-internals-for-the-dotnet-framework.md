---
title: Wewnętrzne rozszerzenia równoległe dla .NET Framework | Microsoft Docs
description: Te zasoby opisują typy wewnętrzne, metody i pola klas używanych do implementowania niestandardowego debugera dla rozszerzeń równoległych do .NET Framework.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f9625af464e2695c6dd4302f4f7590d20e8f6af7
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606596"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Wewnętrzne rozszerzenia równoległe dla .NET Framework
W tej sekcji opisano typy wewnętrzne, metody i pola klas, które ułatwiają zaimplementowanie niestandardowego debugera dla rozszerzeń równoległych do .NET Framework.

## <a name="in-this-section"></a>W tej sekcji
 [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie danych <xref:System.Threading.Tasks.Task?displayProperty=fullName> klasy.

 [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie danych <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy.

 [Klasa ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Opisuje wewnętrzne elementy członkowskie danych `System.Threading.Tasks.ContingentProperties` klasy.

 [AsyncTaskMethodBuilder, struktura](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.

 [ \<TResult> Struktura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.

 [AsyncVoidMethodBuilder, struktura](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Opisuje wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.

## <a name="see-also"></a>Zobacz także
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
