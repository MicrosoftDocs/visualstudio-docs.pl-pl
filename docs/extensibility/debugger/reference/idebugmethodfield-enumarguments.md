---
title: IDebugMethodField::EnumArguments | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f0c5f95267948b6fb2c1cab1a7d79a2e62b9e3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346782"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Tworzy moduł wyliczający typ każdego argumentu wymaganych do wywołania metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę typów argumentów. Zwraca wartość null, jeśli nie wymaga argumentów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli istnieją bez argumentów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący typy każdego parametru. Wywołaj [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodę, aby pobrać informacje o typie każdego parametru.

 Jeśli nazwa parametru jest potrzebny wraz z typem, następnie wywołać [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)