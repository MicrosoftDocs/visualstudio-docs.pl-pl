---
title: IDebugAddress::GetAddress | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e91b90fd54ea70aed729707e927ad2394d756139
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917682"
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
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)