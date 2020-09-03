---
title: 'IEnumCodePaths2:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c38c492572504d7fe49f9557aa2b9eb948d00f67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192002"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
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
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
