---
title: TaskScheduler, klasa — składowe | Microsoft Docs
description: Dowiedz się więcej o wewnętrznych składowych klasy System.Threading.Tasks.TaskScheduler, które ułatwiają implementowanie debugera niestandardowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900151"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler, klasa — składowe wewnętrzne
W tym artykule opisano wewnętrzne składowe klasy, które ułatwiają <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> implementowanie debugera niestandardowego. Aby uzyskać ogólne informacje o tej klasie, zobacz <xref:System.Threading.Tasks.TaskScheduler> artykuł referencyjny.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Pobiera tablicę wszystkich zaplanowanych zadań.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Równoległe wewnętrzne rozszerzenia dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
