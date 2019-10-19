---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577264"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Przerywa wykonywanie działającego wątku skryptu (ujścia zdarzeń, natychmiastowe wykonywanie lub wywołanie makra). Ta metoda może służyć do kończenia działania skryptu, który jest zablokowany (na przykład w pętli nieskończonej). Może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania do obiektów hosta lub metody [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 podczas Identyfikator wątku do przerwania lub jedna z następujących wartości specjalnych identyfikatora wątku:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Wszystkie wątki. Przerwanie jest stosowane do wszystkich metod skryptów, które są obecnie w toku. Należy pamiętać, że jeśli obiekt wywołujący nie zażądał odłączenia skryptu, następne zdarzenie skryptowe powoduje ponowne uruchomienie kodu skryptu przez wywołanie metody [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) z flagą SCRIPTSTATE_DISCONNECTED lub SCRIPTSTATE_INITIALIZED zbiór.|  
|SCRIPTTHREADID_BASE|Wątek podstawowy; oznacza to, że wątek, w którym utworzono wystąpienie aparatu skryptów.|  
|SCRIPTTHREADID_CURRENT|Aktualnie wykonywany wątek.|  
  
 `pexcepinfo`  
 podczas Adres struktury `EXCEPINFO` zawierającej informacje o błędzie, które powinny zostać zgłoszone do przerwanego skryptu.  
  
 `dwFlags`  
 podczas Flagi opcji skojarzone z przerwaniem. Może być jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Jeśli jest obsługiwana, wprowadź debuger aparatu skryptów w bieżącym punkcie wykonywania skryptu.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Jeśli jest obsługiwana przez język aparatu skryptów, pozwól, aby skrypt obsłużył wyjątek. W przeciwnym razie Metoda skryptu jest przerywana i kod błędu jest zwracany do obiektu wywołującego; oznacza to, że źródło zdarzenia lub źródło makro.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)