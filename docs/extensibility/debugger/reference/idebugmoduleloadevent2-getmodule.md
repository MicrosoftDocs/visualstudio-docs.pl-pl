---
title: IDebugModuleLoadEvent2::GetModule | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726727"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Pobiera moduł, który jest ładowany lub zwolniony.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parametry
`pModule`\
[na zewnątrz] Zwraca obiekt [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) który reprezentuje moduł, który jest ładowanie lub zwalnianie.

`pbstrDebugMessage`\
[w, na zewnątrz] Zwraca opcjonalny komunikat opisujący to zdarzenie. Jeśli ten parametr jest wartością null, nie jest wymagany żaden komunikat.

`pbLoad`\
[w, na zewnątrz] Nonzero`TRUE`( ) jeśli moduł jest`FALSE`załadunku i zero ( ) jeśli moduł jest rozładunku. Jeśli ten parametr jest wartością null, nie jest wymagany stan.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
