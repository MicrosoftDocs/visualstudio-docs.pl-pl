---
title: IDebugObject::GetValue | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726539"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Pobiera wartość obiektu jako kolejnej serii bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametry
`pValue`\
[w, na zewnątrz] Tablica wypełniona kolejną serią bajtów reprezentującą wartość obiektu.

`nSize`\
[w] Maksymalna liczba bajtów do pobrania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pobierz całkowitą liczbę bajtów wartości, które mogą być pobierane przez wywołanie [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
