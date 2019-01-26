---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d7de9a5a6d159987db5816341a048e74065c128
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954673"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Wywołuje funkcję i zwraca wartość wynikowa jako obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 [in] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekty reprezentujące parametrów wejściowych. Każdy z tych parametrów został utworzony przy użyciu jednego z `Create` metody [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.  
  
 `dwParams`  
 [in] Liczba parametrów w `ppParams` tablicy.  
  
 `dwTimeout`  
 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.  
  
 `ppResult`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wartość funkcji jako obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda konfiguruje i wykonuje wywołanie funkcji, reprezentowane przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)