---
title: IDebugCustomAttribute::GetParentField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6bdb5daee7fa0c2b8dc5228998a8ac0fd22fec0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205321"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Pobiera pola, do której jest dołączony atrybut niestandardowy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
[out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt, który reprezentuje pole, do której jest dołączony atrybut niestandardowy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwracanego metody [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) jest obiekt, aby określić, które pole jest rodzaju obiektu nadrzędnego.

## <a name="see-also"></a>Zobacz także
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)