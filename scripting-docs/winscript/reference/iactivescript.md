---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577233"
---
# <a name="iactivescript"></a>IActiveScript
Zapewnia metody niezbędne do zainicjowania aparatu skryptów. Aparat skryptów musi implementować interfejs `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informuje aparat obsługi skryptów w witrynie [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) dostarczonej przez hosta.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Pobiera obiekt lokacji skojarzony z aparatem skryptów systemu Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Umieszcza aparat obsługi skryptów w określonym stanie.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Pobiera bieżący stan aparatu obsługi skryptów.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Powoduje, że aparat skryptów porzuca każdy aktualnie załadowany skrypt, utraci swój stan i zwolni wszystkie wskaźniki interfejsu, które ma do innych obiektów, w tym samym momencie wprowadzając stan zamknięty.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Dodaje nazwę elementu poziomu głównego do przestrzeni nazw aparatu skryptów.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Dodaje bibliotekę typów do przestrzeni nazw dla skryptu.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Pobiera interfejs `IDispatch` dla uruchomionego skryptu.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Pobiera identyfikator zdefiniowany przez aparat skryptów dla aktualnie wykonywanego wątku.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Pobiera identyfikator zdefiniowany przez aparat skryptu dla wątku skojarzonego z danym wątkiem Win32 firmy Microsoft.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Pobiera bieżący stan wątku skryptu.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Przerywa wykonywanie działającego wątku skryptu.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klonuje bieżący aparat skryptów (minus dowolny bieżący stan wykonania), zwracając załadowany aparat skryptów, który nie ma lokacji w bieżącym wątku.|  
  
## <a name="see-also"></a>Zobacz także  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)