---
title: IEEDataStorage::GetSize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87818a12945e76f68ba3b96a7f90c38640a0aa39
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199250"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Zwraca liczbę bajtów zawartych w tym obiekcie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parametry
`size`\
[out] Liczba bajtów zawartych w tym obiekcie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Użyj [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) metodę, która pobierze bajtów rzeczywistych danych.

## <a name="see-also"></a>Zobacz także
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)