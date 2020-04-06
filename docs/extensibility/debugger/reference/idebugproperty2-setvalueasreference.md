---
title: IDebugProperty2::SetValueAsReference | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721253"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Ustawia wartość tej właściwości na wartość danego odwołania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametry
`rgpArgs`\
[w] Tablica argumentów do przekazania do ustawiacza właściwości kodu zarządzanego. Jeśli setter właściwości nie przyjmuje argumentów lub jeśli ten obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) `rgpArgs` nie odwołuje się do takiego settera właściwości, powinna być wartością null. Ten parametr jest zazwyczaj wartością null.

`dwArgCount`\
[w] Liczba argumentów w `rgpArgs` tablicy.

`pValue`\
[w] Odwołanie, w postaci obiektu [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) do wartości używanej do ustawiania tej właściwości.

`dwTimeout`\
[w] Jak długo trzeba czekać, aby ustawić wartość w milisekundach. Typową wartością jest `INFINITE`. Wpływa to na czas, jaki może potrwać każda możliwa ocena.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu, zazwyczaj jeden z następujących:

|Błąd|Opis|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Ustawienie wartości z odwołania nie jest obsługiwane.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można ustawić wartości, ponieważ ta właściwość odwołuje się do metody.|
|`E_SETVALUE_VALUE_IS_READONLY`|Wartość jest tylko do odczytu i nie można jej ustawić.|
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
