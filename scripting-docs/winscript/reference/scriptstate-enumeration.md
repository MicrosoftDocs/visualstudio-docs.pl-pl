---
title: Wyliczenie SCRIPTSTATE | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fe6a05c5e73d26a8daa9e46c317422d85d1c40be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840164"
---
# <a name="scriptstate-enumeration"></a>Wyliczenie SCRIPTSTATE
Określa stan silnika wykonywania skryptów. To wyliczenie jest używane przez [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , i [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.  
  
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
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Skrypt został utworzony, ale nie został jeszcze zainicjowany przy użyciu `IPersist*` interfejsu i [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skrypt został zainicjowany, ale nie uruchomioną (Nawiązywanie połączenia z innymi obiektami lub wychwytywania zdarzeń) lub jest wykonaniem jakiegokolwiek kodu. Kod może być odpytywany do wykonania przez wywołanie metody [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) metody.|  
|SCRIPTSTATE_STARTED|Skrypt można wykonać kod, ale nie jest jeszcze wychwytywania zdarzeń obiekty dodane przez [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) — metoda.|  
|SCRIPTSTATE_CONNECTED|Skrypt jest ładowany i podłączony do wychwytywania zdarzeń.|  
|SCRIPTSTATE_DISCONNECTED|Skrypt jest ładowany, ma stan wykonania, a jest tymczasowo odłączone od wychwytywania zdarzeń.|  
|SCRIPTSTATE_CLOSED|Skrypt został zamknięty. Aparat skryptów nie jest już działa i zwraca informacje o błędach dla większości metod.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)