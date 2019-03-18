---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
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
ms.openlocfilehash: aa46bc95087b3defaf739cc3473c58e29a93071c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155933"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Przerwanie wykonywania uruchomionemu wątkowi skryptu (obiekt sink zdarzenia, natychmiastowe wykonanie lub wywołanie makra). Ta metoda może służyć do zakończenia skryptu, który jest zablokowany (na przykład w pętli nieskończonej). Mogą być wywoływane z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) metody.  
  
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
 [in] Identyfikator wątku do przerwania lub jedną z następujących wartości identyfikatora wątku specjalne:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Wszystkie wątki. Przerwanie jest stosowany do wszystkich metod skryptu w toku. Należy pamiętać, że chyba że obiekt wywołujący ma o odłączony skryptu, następne zdarzenie inicjowane przez skrypty powoduje, że kod skryptu, aby ponownie uruchomić, wywołując [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metody z SCRIPTSTATE_DISCONNECTED lub Ustaw flagę SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Podstawowy wątek; oznacza to wątek, w którym skryptów aparatu została utworzona.|  
|SCRIPTTHREADID_CURRENT|Aktualnie wykonywany wątek.|  
  
 `pexcepinfo`  
 [in] Adres `EXCEPINFO` struktury zawierającej informacje o błędzie, które powinny być raportowane do skryptu zostało przerwane.  
  
 `dwFlags`  
 [in] Flagi opcji skojarzony czas przestoju. Może być jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Jeśli jest obsługiwany, wprowadź debuger aparatu skryptów w bieżącym punkcie Wykonywanie skryptu.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Jeśli jest obsługiwany przez język silnik wykonywania skryptów, niech skryptu obsłużyć wyjątek. W przeciwnym razie metoda skryptu zostało przerwane i kod błędu jest zwracany do obiektu wywołującego oznacza to, że zdarzenie źródła lub makro element wywołujący.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)