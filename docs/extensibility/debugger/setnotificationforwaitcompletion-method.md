---
title: SetNotificationForWaitCompletion, metoda | Microsoft Docs
description: Dowiedz się, jak debuger używa bitu stanu, aby pomóc wyjść z treści metody asynchronicznej dla zadań w stylu obietnic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ec469ed4f9c4fa2e503b2350235299a81a94bf9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902114"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion, metoda
Ustawia lub czyszczy bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION stanu.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametry
 `enabled`

 `true` w celu ustawienia bitu; `false` , aby unset bit.

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi
 Debuger ustawia ten bit, aby pomóc w wywrzeniu części treści metody asynchronicznej. Jeśli `enabled` to , ta metoda musi być `true` wywoływana tylko dla zadania, które nie zostało jeszcze ukończone. Gdy `enabled` to , ta metoda może być `false` wywoływana dla ukończonych zadań. W każdym przypadku powinna być używana tylko do zadań w stylu obietnic.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też
- [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
