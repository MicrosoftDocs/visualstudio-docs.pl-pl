---
title: IDebugProgram2::CanDetach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c4c691da4b7f624b7d70f65ef59b537e8502251
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916075"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Określa, jeśli aparat debugowania (DE) można odłączyć od program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli można odłączyć zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` Jeśli DE nie można odłączyć od program.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)