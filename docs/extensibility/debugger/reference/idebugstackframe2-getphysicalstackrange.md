---
title: IDebugStackFrame2::GetPhysicalStackRange | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56121c7a0e58d90fd3ab0384a39916c102056c50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958699"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Pobiera reprezentację zależnych od maszyny, zakresu adresów fizycznych skojarzonych z ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `paddrMin`  
 [out] Zwraca najniższy adres fizyczny skojarzone z tą ramką stosu.  
  
 `paddrMax`  
 [out] Zwraca najwyższy adres fizyczny skojarzone z tą ramką stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Informacje zwracane przez tę metodę jest używany przez Menedżer debugowania sesji (SDM) do sortowania ramki stosu.  
  
 Zakłada się, że stos wywołań rośnie, oznacza to, dodania nowej ramki stosu w coraz większym stopniu niższe adresów pamięci. Architektura środowiska wykonawczego, musisz podać zakresy adresów fizycznych stosu, które odpowiadają tym założeń.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)