---
title: Metoda SetNotificationForWaitCompletion | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712873"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion, metoda
Ustawia lub czyści bit stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true`, aby ustawić bit; `false` , aby odłączyć bit.

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi
 Debuger ustawia ten bit, aby pomóc wyjść z treści metody asynchronii. Jeśli `enabled` `true`tak , ta metoda musi być wywoływana tylko dla zadania, które nie zostało jeszcze ukończone. Gdy `enabled` `false`jest , ta metoda może być wywołana na ukończonych zadań. W obu przypadkach powinien być używany tylko do zadań w stylu obietnicy.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też
- [Klasa zadań](../../extensibility/debugger/task-class-internal-members.md)
