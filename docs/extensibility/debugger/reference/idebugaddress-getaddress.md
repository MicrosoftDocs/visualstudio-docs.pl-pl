---
title: IDebugAddress::GetAddress | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cff380759163a38129b92f07752e72904f6bbaf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684458"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Zwraca strukturę opisujący obiekt i jego lokalizację w jego zakres lub kontenera.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

#### <a name="parameters"></a>Parametry
 `pAddress`

 [out w] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) strukturę, która jest wypełniane przez tę metodę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury jest przekazywany do tej metody, która wypełnia go przy użyciu odpowiednich informacji. Interpretacji tych informacji, zależy od rodzaju informacje zwrócone i symbol program obsługi. Zobacz [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)