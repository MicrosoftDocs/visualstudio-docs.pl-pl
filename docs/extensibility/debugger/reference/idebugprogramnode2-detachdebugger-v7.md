---
title: IDebugProgramNode2::DetachDebugger_V7 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722105"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Przestarzałe. NIE UŻYWAĆ.

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

Implementacja powinna `E_NOTIMPL`zawsze zwracać .

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Od programu Visual Studio 2005 ta metoda nie `E_NOTIMPL`jest już używana i zawsze powinna zwracać .

Ta metoda jest wywoływana, gdy debuger nieoczekiwanie kończy pracę. Gdy ta metoda jest wywoływana, DE należy wznowić program tak, jakby użytkownik odłączony od niego. Nie więcej zdarzeń debugowania powinny być wysyłane. Program powinien być w stanie, w którym można dołączyć z innego wystąpienia debugera.

## <a name="see-also"></a>Zobacz też

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
