---
title: IDebugMethodField::EnumArgument | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727265"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Tworzy wyliczyć dla typu każdego argumentu wymagane do wywołania metody.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę typów argumentów. Zwraca wartość null, jeśli nie ma żadnych argumentów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych argumentów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [obiektem IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentującym typy każdego parametru. Wywołanie [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metody, aby pobrać informacje o typie każdego parametru.

 Jeśli nazwa parametru jest potrzebna wraz z typem, należy wywołać [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
