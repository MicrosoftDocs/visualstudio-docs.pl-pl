---
title: IEnumDebugThreads2::Clone | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25d8874b853b3d8930d99fa8f3099f22f2da9f4d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957731"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię wyliczenia ma ten sam stan, co oryginalny w czasie, którego ta metoda jest wywoływana. Jednak stany kopiowania i oryginalne są niezależne i można zmieniać indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)