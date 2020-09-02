---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99fc1e635691fa290d0a8e4506ef55d677e9ff78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547653"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera reprezentację zakresu adresów fizycznych skojarzonych z ramką stosu w zależności od maszyny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 określoną Zwraca najniższy adres fizyczny skojarzony z tą ramką stosu.  
  
 `paddrMax`  
 określoną Zwraca najwyższy adres fizyczny skojarzony z tą ramką stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Informacje zwrócone przez tę metodę są używane przez Menedżera debugowania sesji (SDM) do sortowania ramek stosu.  
  
 Przyjęto założenie, że stos wywołań powiększa się. oznacza to, że nowe ramki stosu są dodawane w coraz niższych adresach pamięci. Architektura czasu wykonywania musi udostępniać fizyczne zakresy stosu, które pasują do tego założeń.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
