---
title: IDebugSymbolProvider::GetTypeByName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetTypeByName method
ms.assetid: b9d88d3b-8b75-484a-b9cc-dc8c0fbb4bc8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ec98b9c206975b122511648017f920a28905b09
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207098"
---
# <a name="idebugsymbolprovidergettypebyname"></a>IDebugSymbolProvider::GetTypeByName
Ta metoda mapuje nazwę na symbol typ symbolu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetTypeByName( 
   LPCOLESTR     pszClassName,
   NAME_MATCH    nameMatch,
   IDebugField** ppField
);
```

```csharp
int GetTypeByName(
   string          pszClassName,
   NAME_MATCH      nameMatch,
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`pszClassName`\
[in] Nazwa symbolu.

`nameMatch`\
[in] Wybiera typ dopasowania, na przykład wielkość liter. Wartość z zakresu od [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) wyliczenia.

`ppField`\
[out] Zwraca typ symbolu jako [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest ogólna wersja [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md).

## <a name="see-also"></a>Zobacz także
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)