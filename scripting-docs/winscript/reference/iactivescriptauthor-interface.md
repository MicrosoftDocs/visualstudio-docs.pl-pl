---
title: Interfejs IActiveScriptAuthor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9d9c2a330ee72c6a843cd42586a09bb1d51e3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346374"
---
# <a name="iactivescriptauthor-interface"></a>Interfejs IActiveScriptAuthor
Reprezentuje tworzenia usług, w tym funkcji IntelliSense i sortowanie informacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IActiveScriptAuthor` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Dodaje nazwę elementu głównego poziomu do skryptu tworzenia przestrzeni nazw aparatu. A *elementu poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a, mogą również zawierać źródło zdarzeń.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Dodaje skryptletu kodu jako element podrzędny elementu poziomu głównego `IScriptNode` obiektu. Na hoście w pełni kwalifikowana nazwa scriptlet może mieć tylko dwa poziomy.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Dodaje bibliotekę typów, do przestrzeni nazw skryptu.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Zwraca zestaw znaków zakończenia dla kontekstu żądanego zakończenia.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Zwraca scriptlet, który ma określone atrybuty.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Zwraca typu informacji i pozycji zakotwiczenia dla danego znaku w bloku kodu. Zawiera informacje dla elementu członkowskiego, IntelliSense, wykazy globalne i porady dotyczące parametru.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Zwraca informacje o języku.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Zwraca `IScriptNode` drzewa skryptu autora.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Zwraca atrybuty tekstu scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Zwraca atrybuty tekst w bloku skryptu.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Zwraca wartość wskazującą, czy dany znak powinien zużywać uzupełniania instrukcji przez aplikację.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizuje tekst skryptu, dodaje tekst do tworzenia skryptu tworzenia aparatu i tworzy `IScriptEntry` obiekt, który odnosi się do bloku skryptu.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Usuwa `NamedItem` obiektu z przestrzeni nazw skryptu tworzenia aparatu.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Usuwa bibliotekę typów w skrypcie tworzenia przestrzeni nazw aparatu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)