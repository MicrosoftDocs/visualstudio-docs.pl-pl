---
title: Klasa TaskScheduler - Członkowie wewnętrzni | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712568"
---
# <a name="taskscheduler-class---internal-members"></a>Klasa TaskScheduler — elementy wewnętrzne
W tym artykule opisano <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> wewnętrznych członków klasy, które pomagają zaimplementować debugera niestandardowego. Aby uzyskać ogólne informacje na <xref:System.Threading.Tasks.TaskScheduler> temat tej klasy, zobacz artykuł referencyjny.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

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
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są aktualnie aktywne.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Wewnętrzne rozszerzenia równoległego dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
