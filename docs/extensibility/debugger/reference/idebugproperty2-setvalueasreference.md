---
description: Ustawia wartość tej właściwości na wartość danego odwołania.
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b370b4caa43ce6522b415233714eb15899b3051
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064777"
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
podczas Tablica argumentów do przekazania do metody ustawiającej właściwości kodu zarządzanego. Jeśli Metoda ustawiająca właściwość nie przyjmuje argumentów lub jeśli ten obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nie odwołuje się do takiej metody ustawiającej, `rgpArgs` powinna być wartością null. Ten parametr jest zwykle wartością null.

`dwArgCount`\
podczas Liczba argumentów w `rgpArgs` tablicy.

`pValue`\
podczas Odwołanie w formie obiektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) do wartości, która ma zostać użyta do ustawienia tej właściwości.

`dwTimeout`\
podczas Jak długo należy wykonać, aby ustawić wartość w milisekundach. Typowa wartość to `INFINITE` . Ma to wpływ na długość czasu, jaki może być możliwy do dokonania oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu, zazwyczaj jedną z następujących czynności:

|Błąd|Opis|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Ustawianie wartości z odwołania nie jest obsługiwane.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można ustawić wartości, ponieważ ta właściwość odwołuje się do metody.|
|`E_SETVALUE_VALUE_IS_READONLY`|Wartość jest tylko do odczytu i nie można jej ustawić.|
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|

## <a name="see-also"></a>Zobacz też
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
