---
title: IDebugObject::SetValue | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726359"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Ustawia wartość obiektu z kolejnych serii bajtów.

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

## <a name="parameters"></a>Parametry
`pValue`\
[w] Tablica bajtów reprezentująca nową wartość.

`nSize`\
[w] Rozmiar wartości w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartości w tablicy są kopiowane do tego obiektu [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) zastępując dowolną istniejącą wartość. Rozmiar nowej wartości może być większy lub mniejszy niż istniejąca wartość. Nie `IDebugObject` może to być odwołanie null.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
