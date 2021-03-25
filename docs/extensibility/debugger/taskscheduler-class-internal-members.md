---
title: Klasa TaskScheduler — wewnętrzne elementy członkowskie | Microsoft Docs
description: Dowiedz się więcej o wewnętrznych elementach członkowskich klasy System. Threading. Tasks. TaskScheduler, które ułatwiają implementację niestandardowego debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 45e2aff7d16826a631bb5126447d60b8b2468455
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057874"
---
# <a name="taskscheduler-class---internal-members"></a>Klasa TaskScheduler — wewnętrzne elementy członkowskie
W tym artykule opisano wewnętrzne elementy członkowskie <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> klasy, które ułatwiają zaimplementowanie niestandardowego debugera. Aby uzyskać ogólne informacje o tej klasie, zobacz <xref:System.Threading.Tasks.TaskScheduler> artykuł referencyjny.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z .NET Framework, następująca składnia jest udostępniana w typowym języku pośrednim (CIL).

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
- [Wewnętrzne rozszerzenia równoległe dla .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
