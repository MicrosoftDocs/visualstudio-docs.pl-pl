---
title: 'IEnumDebugPorts2:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96bf6bd5277e6683bf793de17e608802c6c01034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155049"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pomija określoną liczbę elementów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba elementów do pominięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` wartość `celt` , jeśli jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `celt` wartość jest większa niż liczba pozostałych elementów, Wyliczenie zostanie ustawione na koniec i `S_FALSE` zostanie zwrócone.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
