---
title: IDebugApplication::StartDebugSession | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StartDebugSession
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a42fe61d67eedbe6f69350c7b5ec17726f43486e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990692"
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Uruchamia domyślny debuger zintegrowanego środowiska programistycznego (IDE) i dołącza sesji debugowania do tej aplikacji, jeśli nie jest już dołączony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana do zaimplementowania debugowania just in time.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)