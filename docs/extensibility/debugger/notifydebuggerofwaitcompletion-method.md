---
title: NotifyDebuggerOfWaitCompletion — Metoda | Microsoft Docs
description: Dowiedz się więcej na temat metody NotifyDebuggerOfWaitCompletion, która jest symbolem zastępczym używanym jako docelowy punkt przerwania przez debuger.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606635"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion, Metoda
Metoda zastępcza używana jako docelowy punkt przerwania przez debuger. Ta metoda nie może być wbudowana ani zoptymalizowana.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Uwagi
 Wszystkie operacje Join z zadaniem powinny wywołać tę metodę, jeśli ustawiono bit powiadomień debugera.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz także
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
