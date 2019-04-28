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
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436080"
---
# <a name="iactivescript"></a>IActiveScript
Udostępnia metody, które są niezbędne do zainicjowania silnik wykonywania skryptów. Aparat skryptów musi implementować `IActiveScript` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informuje silnik wykonywania skryptów z [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) lokacji udostępniane przez hosta.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Pobiera obiekt lokacji skojarzone z aparatu skryptów Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Umieszcza silnik wykonywania skryptów w określonym stanie.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Pobiera bieżący stan silnika wykonywania skryptów.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Powoduje, że aparat skryptów zrezygnowania z dowolnego aktualnie załadowanych skryptu, utraty stanu i zwolnij wszystkie wskaźniki interfejsu, które inne obiekty, w związku z tym wprowadzenie stanu zamkniętego.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Dodaje nazwę elementu głównego poziomu do przestrzeni nazw aparatu skryptów.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Dodaje bibliotekę typów, do przestrzeni nazw skryptu.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Pobiera `IDispatch` interfejs uruchamianie skryptu.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Pobiera identyfikator aktualnie wykonywany wątek skryptów aparatu zdefiniowane.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Pobiera skryptów aparatu-zdefiniowany przez identyfikator wątku skojarzone z danym wątek Win32 firmy Microsoft.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Pobiera bieżący stan wątku skryptu.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Przerwanie wykonywania uruchomionemu wątkowi skryptu.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klony bieżącym silnikiem skryptującym (bez żadnych bieżący stan wykonania), zwracając załadować aparat skryptów, który ma żadna lokacja w bieżącym wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)