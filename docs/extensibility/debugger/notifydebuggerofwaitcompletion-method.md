---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a3280a24ad7f9d4045c9a1bff6ca2b44c724325
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350637"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Metoda symbolu zastępczego używany jako obiekt docelowy punkt przerwania przez debuger. Ta metoda nie może być śródwierszowa lub zoptymalizowane.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Uwagi
 Wszystkie operacje łączenia z zadaniem powinna wywołać tę metodę, jeśli ustawiono bit powiadomienia ich debugera.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)