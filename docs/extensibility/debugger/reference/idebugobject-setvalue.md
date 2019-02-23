---
title: IDebugObject::SetValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccfea65f7f24b3d48fc5ec5d68028c72b9b4eece
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692658"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Ustawia wartość obiektu z kolejnych serię bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

#### <a name="parameters"></a>Parametry
 `pValue`

 [in] Tablica bajtów reprezentujący nową wartość.

 `nSize`

 [in] Rozmiar wartość w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartości w tablicy są kopiowane do tego [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektu, zastępując dowolnym istniejącą wartość. Rozmiar nową wartość może być większy lub mniejszy niż istniejąca wartość. To `IDebugObject` nie może być odwołaniem o wartości null.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)