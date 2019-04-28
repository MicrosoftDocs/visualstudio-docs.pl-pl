---
title: IDebugMethodField::EnumArguments | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf62392118ed3ddfb2dfbfca06588f0935f3192d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918723"
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

#### <a name="parameters"></a>Parametry
 `ppParams`

 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę typów argumentów. Zwraca wartość null, jeśli nie wymaga argumentów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli istnieją bez argumentów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący typy każdego parametru. Wywołaj [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodę, aby pobrać informacje o typie każdego parametru.

 Jeśli nazwa parametru jest potrzebny wraz z typem, następnie wywołać [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)