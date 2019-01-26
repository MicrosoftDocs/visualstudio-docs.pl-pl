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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8393eb7bc712de28e2378a9ad09081efe76eca6b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933948"
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