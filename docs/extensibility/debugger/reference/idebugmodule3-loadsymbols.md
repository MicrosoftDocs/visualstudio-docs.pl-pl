---
title: IDebugModule3::LoadSymbols | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726774"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Ładuje symbole dla bieżącego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda powiedzie się, zwraca `S_OK`. Jeśli to się nie powiedzie, zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda ładuje symbole z bieżącej ścieżki wyszukiwania (które można zmienić, wywołując [Metodę SetSymbolPath).](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

 Ta metoda jest preferowana w stosunku do [metody ReloadSymbols_Deprecated.](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)

## <a name="see-also"></a>Zobacz też
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
