---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8cd1b59c084ad306870288461d5576395293145
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023710"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Zwraca liczbę typu argumenty parametrów dla tego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcArgs`  
 [out w] Liczba argumentów do parametrów typu dla tego wystąpienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład jeśli lista\<int >, ta metoda zwraca wartość 1 i, jeśli lista\<int, float2 > Ta metoda zwraca wartość 2. Ta metoda zwraca wartość 0, jeśli nie wymaga argumentów typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)