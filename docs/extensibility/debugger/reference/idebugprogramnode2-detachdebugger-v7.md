---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
description: Ta metoda to stara, przestarzała forma metody odłączenia używana przed Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16630be49dd884f8bcc82da2fead158eb3a25e5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053558"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Przestarzałe. NIE NALEŻY UŻYWAĆ.

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

Implementacja powinna zawsze zwrócić `E_NOTIMPL` .

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Począwszy od programu Visual Studio 2005, ta metoda nie jest już używana i zawsze powinna zostać zwrócona `E_NOTIMPL` .

Ta metoda jest wywoływana, gdy debuger nieoczekiwanie kończy pracę. Po wywołaniu tej metody DE powinien wznowić program tak, jakby został odłączony przez użytkownika. Nie należy wysyłać więcej zdarzeń debugowania. Program powinien znajdować się w stanie, w którym jest możliwy do dołączenia z innego wystąpienia debugera.

## <a name="see-also"></a>Zobacz też

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
