---
title: IDebugProgramNode2::DetachDebugger_V7 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 0b7d97e277a3f7f327bf8830e49507d28e82568f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869841"
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

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)