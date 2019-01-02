---
title: IEEVisualizerService::GetValueDisplayStringCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8af1b785e56d5efba2505b0cdbd5a9474b5c261b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957952"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Pobiera liczbę wartości ciągów dla określonej właściwości lub pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `displayKind`  
 [in] Wartość z [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) wyliczenia.  
  
 `propertyOrField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejs, który reprezentuje właściwość lub pole.  
  
 `pcelt`  
 [out] Zwraca liczbę ciągi wartości do wyświetlenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)