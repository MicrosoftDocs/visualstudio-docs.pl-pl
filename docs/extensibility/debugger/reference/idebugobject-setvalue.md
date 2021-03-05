---
description: Ustawia wartość obiektu z kolejnej serii bajtów.
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 972281335b964679f38693182e42c4e64074dffa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167155"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Ustawia wartość obiektu z kolejnej serii bajtów.

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
podczas Tablica bajtów reprezentująca nową wartość.

`nSize`\
podczas Rozmiar wartości w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wartości w tablicy są kopiowane do tego obiektu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , zastępując wszystkie istniejące wartości. Rozmiar nowej wartości może być większy lub mniejszy niż istniejąca wartość. `IDebugObject`Nie może to być odwołanie o wartości null.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
