---
title: 'IDebugPendingBreakpoint2:: setcondition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9db02ada04b236ec190d11568eb1f4f35db6244
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201042"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ustawia lub zmienia warunek skojarzony z oczekującym punktem przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bpCondition`  
 podczas Struktura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , która określa warunek do ustawienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie warunki, które wcześniej były skojarzone z oczekującym punktem przerwania, zostaną utracone. Wszystkie punkty przerwania powiązane z tym oczekującym punktem przerwania są wywoływane, aby ustawić ich warunek na wartość określoną w `bpCondition` parametrze.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
