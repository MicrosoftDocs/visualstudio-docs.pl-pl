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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b62b613950f9fd6c8ce18969c126a6e74a154b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851299"
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
