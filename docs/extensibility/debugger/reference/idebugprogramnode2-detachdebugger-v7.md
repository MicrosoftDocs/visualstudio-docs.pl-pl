---
title: IDebugProgramNode2::DetachDebugger_V7 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 603c459d39f8141789b22955e916e3e8520214fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924153"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Wartość zwracana

Implementacja zawsze powinna zwrócić `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Począwszy od programu Visual Studio 2005, ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`.

Ta metoda jest wywoływana, gdy debuger jest nieoczekiwanie zamykany. Gdy ta metoda jest wywoływana, DE powinna zostać wznowiona program, jak gdyby użytkownik jest odłączony od niego. Powinny być przesyłane bez więcej zdarzeń debugowania. Program, należy w stanie, gdy jest można dołączyć z innego wystąpienia debugera.

## <a name="see-also"></a>Zobacz też

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)