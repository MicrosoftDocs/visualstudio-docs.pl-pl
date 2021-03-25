---
title: NotifyDebuggerOfWaitCompletion — Metoda | Microsoft Docs
description: Dowiedz się więcej na temat metody NotifyDebuggerOfWaitCompletion, która jest symbolem zastępczym używanym jako docelowy punkt przerwania przez debuger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d58bb7a5e3a3395b534e5679ec303e5d93d5dc85
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054741"
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

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
