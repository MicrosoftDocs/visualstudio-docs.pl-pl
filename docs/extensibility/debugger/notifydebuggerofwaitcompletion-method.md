---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679544"
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