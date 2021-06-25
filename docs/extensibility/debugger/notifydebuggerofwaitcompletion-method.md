---
title: NotifyDebuggerOfWaitCompletion, metoda | Microsoft Docs
description: Dowiedz się więcej o metodzie NotifyDebuggerOfWaitCompletion, która jest symbolem zastępczym używanym jako element docelowy punktu przerwania przez debuger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9d6b5fbdcb8195709a751117056bcaa0617eff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904220"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion, metoda
Metoda symbolu zastępczego używana jako element docelowy punktu przerwania przez debuger. Ta metoda nie może być wsadowa ani zoptymalizowana.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

## <a name="syntax"></a>Składnia

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Uwagi
 Wszystkie operacje sprzężenia z zadaniem powinny wywołać tę metodę, jeśli ich bit powiadomień debugera jest ustawiony.

## <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też
- [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
