---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43211dca57a404d5625cfc2d7ede67a70a0a40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087987"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Umożliwia hosta określić, że skrypt powinien wygasają.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wywołanie zakończyło się pomyślnie, a host pozwala skryptu, aby kontynuować działanie.|  
|`S_FALSE`|Powodzenie wywołania metody i żądań hosta, które zakończyć skryptu.|  
  
## <a name="remarks"></a>Uwagi  
 Skrypt hostowanej powinien wygasają, chyba że wartość zwracana przez `QueryContinue` metodą jest `S_OK`. Zwracana wartość wynosząca `S_FALSE` wskazuje, że host wyraźnie zażąda, że skrypt zakończyć.  
  
 Wielowątkowe host może użyć `IActiveScript::InterruptScriptThread` metodę, aby zakończyć skryptu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)