---
title: Metoda SetNotificationForWaitCompletion | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d9bee2579cc3a93f657291551955f0c9b7565b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348583"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion, metoda
Ustawia lub czyści stan TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true` Aby ustawić bitu; `false` do nie ustawiono bitu.

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi
 Debuger ustawia ten bit ułatwiające kroku poza treści metody asynchronicznej. Jeśli `enabled` jest `true`, ta metoda musi zostać wywołana tylko na zadanie, które nie zostało jeszcze zakończone. Gdy `enabled` jest `false`, ta metoda może być wywoływana na ukończone zadania. W obu przypadkach można stosować tylko dla zadań promise stylu.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)