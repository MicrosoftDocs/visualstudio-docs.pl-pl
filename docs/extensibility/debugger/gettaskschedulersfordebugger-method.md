---
title: GetTaskSchedulersForDebugger — Metoda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b9826681d2d322b1b240abb4062de007b564619
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921267"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger, metoda
Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne w tym elemencie <xref:System.AppDomain> .

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczna wątkowo i nie należy jej używać jednocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler> . Wywołaj tę metodę z debugera tylko wtedy, gdy debuger zatrzymał wszystkie pozostałe wątki.

## <a name="see-also"></a>Zobacz też
- [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
