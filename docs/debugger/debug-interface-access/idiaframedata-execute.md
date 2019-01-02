---
title: Idiaframedata::EXECUTE — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6be6c631f9ea0db47829f305f90bd1c296de2f28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958749"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Wykonuje odwijanie stosu i zwraca wyniki w interfejsie ramki przeszukiwania stosu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `frame`  
 [in] [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md) obiekt, który zawiera stan rejestrów ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Nie można wykonać ramkę stosu w kodzie prologu.|  
|E_DIA_SYNTAX|Błąd wystąpił w programie ramki analizy.|  
|E_DIA_FRAME_ACCESS|Nie można rejestrów dostępu lub pamięci.|  
|E_DIA_VALUE|Wystąpił błąd podczas obliczania wartości (na przykład, dzielenie przez zero).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana podczas debugowania do odkręcanie stosu. [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md) obiektu jest implementowany przez aplikację klienta, aby otrzymywać aktualizacje w rejestrach i dostarcza metod używanych przez `execute` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)