---
title: IDebugPointerField::GetDereferencedField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51ddd954e069ae2f6a683b727305808b8591d4f2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680337"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Ta metoda zwraca typ obiektu, na który wskazuje ten obiekt wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parametry
 `ppField`

 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące typ obiektu docelowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli na przykład [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) obiektu wskazuje na liczbę całkowitą, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) typu zwracanego przez tę metodę zawiera opis tego typu Liczba całkowita.

## <a name="see-also"></a>Zobacz też
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)