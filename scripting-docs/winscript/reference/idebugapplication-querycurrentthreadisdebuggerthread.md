---
title: IDebugApplication::QueryCurrentThreadIsDebuggerThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::QueryCurrentThreadIsDebuggerThread
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ed53bcdb5e0d613a757c0c60f4791b0c59e3476
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990817"
---
# <a name="idebugapplicationquerycurrentthreadisdebuggerthread"></a>IDebugApplication::QueryCurrentThreadIsDebuggerThread
Określa, czy bieżący wątek uruchomionego wątku debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się i bieżący wątek uruchomione jest debugera wątku.|  
|`S_FALSE`|Bieżący uruchomionego wątku nie jest wątek debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy bieżący wątek uruchomionego wątku debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)