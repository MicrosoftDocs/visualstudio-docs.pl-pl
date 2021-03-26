---
title: SetNotificationForWaitCompletion — Metoda | Microsoft Docs
description: Dowiedz się, jak debuger używa bitu stanu, aby ułatwić wyjście z metody asynchronicznej do zadań w stylu obietnicy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e189a2c12e262b81f93f7f8de5e58ea22b1277c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079439"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion, metoda
Ustawia lub czyści bit stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true` Aby ustawić bit; `false` w celu nieustawienia bitu.

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi
 Debuger ustawia ten bit, aby ułatwić wyjście z metody asynchronicznej. Jeśli `enabled` jest `true` , ta metoda musi być wywoływana tylko w zadaniu, które nie zostało jeszcze ukończone. Gdy `enabled` tak jest `false` , ta metoda może być wywoływana dla ukończonych zadań. W każdym z tych zdarzeń powinien być używany tylko w przypadku zadań w stylu obietnicy.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
