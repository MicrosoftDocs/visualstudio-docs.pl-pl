---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575778"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Powoduje, że aparat skryptów porzuca każdy aktualnie załadowany skrypt, utraci swój stan i zwolni wszystkie wskaźniki interfejsu, które ma do innych obiektów, w tym samym momencie wprowadzając stan zamknięty. Ujścia zdarzeń, natychmiast wykonany tekst skryptu i wywołania makr, które są już w toku, są kończone przed zmianą stanu (Użyj [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) , aby anulować uruchomiony wątek skryptu). Ta metoda musi zostać wywołana przez tworzenie hosta przed zwolnieniem interfejsu, aby zapobiec problemom z odwołaniami cyklicznymi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`S_OK`|Prawnego.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów był już w stanie zamknięte).|  
|`OLESCRIPT_S_PENDING`|Metoda została pomyślnie umieszczona w kolejce, ale stan nie został jeszcze zmieniony. Po zmianie stanu lokacja jest wywoływana z powrotem w metodzie [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Metoda zakończyła się pomyślnie, ale skrypt został już zamknięty.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)