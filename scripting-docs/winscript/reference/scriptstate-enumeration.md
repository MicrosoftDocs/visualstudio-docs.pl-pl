---
title: SCRIPTSTATE, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575683"
---
# <a name="scriptstate-enumeration"></a>Wyliczenie SCRIPTSTATE
Określa stan aparatu obsługi skryptów. To wyliczenie jest używane przez metody [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) i [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczeniowe  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Skrypt został właśnie utworzony, ale nie został jeszcze zainicjowany przy użyciu interfejsu `IPersist*` i [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skrypt został zainicjowany, ale nie jest uruchomiony (połączenie z innymi obiektami lub zdarzeniami ujścia) lub wykonywanie dowolnego kodu. Aby można było wykonać zapytanie o kod, należy wywołać metodę [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|Skrypt może wykonać kod, ale nie jest jeszcze ujścia zdarzeń obiektów dodanych przez metodę [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|Skrypt jest ładowany i połączony dla zdarzeń ujścia.|  
|SCRIPTSTATE_DISCONNECTED|Skrypt jest ładowany i ma stan wykonywania w czasie wykonywania, ale jest tymczasowo odłączony od zdarzeń ujścia.|  
|SCRIPTSTATE_CLOSED|Skrypt został zamknięty. Aparat skryptów nie działa już i zwraca błędy dla większości metod.|  
  
## <a name="see-also"></a>Zobacz także  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)