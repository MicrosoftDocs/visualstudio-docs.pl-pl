---
title: IDebugBinder3::GetMemoryObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5386d6b4d32b34b708b7d213cf1a6e96ec0651a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327045"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Ta metoda pobiera obiekt pamięci, który reprezentuje ten obiekt jest powiązany z pamięci.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pField`\
[in] Określa pole, które można pobrać obiektu pamięci dla.

`uConstant`\
[in] Reprezentuje adres pamięci lub wartość stałej wartości.

`ppObject`\
[out] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący pamięci, którą jest powiązany ten obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)