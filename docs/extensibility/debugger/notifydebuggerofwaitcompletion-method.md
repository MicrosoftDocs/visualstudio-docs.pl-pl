---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738331"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Metoda zastępcza używana jako miejsce docelowe punktu przerwania przez debuger. Ta metoda nie może być inlined lub zoptymalizowane.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Uwagi
 Wszystkie operacje sprzężenia z zadaniem należy wywołać tę metodę, jeśli ich bit powiadomienia debugera jest ustawiony.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też
- [Klasa zadań](../../extensibility/debugger/task-class-internal-members.md)
