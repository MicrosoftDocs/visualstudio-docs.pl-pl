---
title: 'IActiveScriptSiteInterruptPoll:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572237"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Umożliwia hostowi określenie, że skrypt powinien zostać przerwany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wywołanie zakończyło się pomyślnie, a host zezwala na kontynuowanie działania skryptu.|  
|`S_FALSE`|Wywołanie zakończyło się pomyślnie, a host zażądał przerwania działania skryptu.|  
  
## <a name="remarks"></a>Uwagi  
 Skrypt hostowany powinien kończyć się, chyba że zwracana wartość metody `QueryContinue` jest `S_OK`. Wartość zwracana `S_FALSE` wskazuje, że host jawnie zażąda przerwania działania skryptu.  
  
 Host wielowątkowy może użyć metody `IActiveScript::InterruptScriptThread`, aby przerwać skrypt.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteInterruptPoll   interfejsu](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)