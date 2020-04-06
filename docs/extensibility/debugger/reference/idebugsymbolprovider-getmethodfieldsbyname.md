---
title: IDebugSymbolProvider::GetMethodFieldsByName | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf123c1e7e83264a2ae4a8ef8c2b4b3207a62a5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719222"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Ta metoda pobiera pole reprezentujące w pełni kwalifikowaną nazwę metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`pszFullName`\
[w] Nazwa metody.

`nameMatch`\
[w] Wybiera typ dopasowania, na przykład z uwzględnieniem wielkości liter.

`ppEnum`\
[na zewnątrz] Zwraca [wyliczenie IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) dla pól skojarzonych z tą metodą.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Metoda może być skojarzona z wieloma polami, jeśli jest przeciążona, na przykład.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
