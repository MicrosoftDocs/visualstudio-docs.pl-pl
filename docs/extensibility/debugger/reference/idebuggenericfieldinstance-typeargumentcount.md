---
title: IDebugGenericFieldInstance::TypeArgumentCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d0c980124fdaab07b38273517df3f2cf29f69a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846915"
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