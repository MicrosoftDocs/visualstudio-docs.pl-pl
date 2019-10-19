---
title: Interfejs IActiveScriptAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576158"
---
# <a name="iactivescriptauthor-interface"></a>Interfejs IActiveScriptAuthor
Reprezentuje usługi autorstwa, w tym IntelliSense i sortowanie informacji.  
  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `IActiveScriptAuthor` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Dodaje nazwę elementu poziomu głównego do przestrzeni nazw aparatu tworzenia skryptów. *Element poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a także może zawierać Źródło zdarzenia.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Dodaje kod Scriptlet jako element podrzędny obiektu głównego poziomu `IScriptNode`. W pełni kwalifikowana nazwa Scriptlet może mieć tylko dwa poziomy na hoście.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Dodaje bibliotekę typów do przestrzeni nazw dla skryptu.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Zwraca zestaw znaków zakończenia dla żądanego kontekstu uzupełniania.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Zwraca Scriptlet, który ma określone atrybuty.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Zwraca informacje o typie i położenia zakotwiczenia dla danego znaku w bloku kodu. Zawiera informacje na temat elementów członkowskich IntelliSense, list globalnych i porad dotyczących parametrów.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Zwraca informacje o języku.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Zwraca katalog główny `IScriptNode` drzewa skryptu autora.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Zwraca atrybuty tekstu Scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Zwraca atrybuty tekstu bloku skryptu.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Zwraca wartość wskazującą, czy dany znak powinien zatwierdzić ukończenie instrukcji przez aplikację.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizuje tekst skryptu, dodaje tekst do aparatu tworzenia skryptów tworzenia i tworzy obiekt `IScriptEntry`, który odpowiada blokowi skryptu.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Usuwa obiekt `NamedItem` z przestrzeni nazw aparatu tworzenia skryptów.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Usuwa bibliotekę typów z przestrzeni nazw aparatu tworzenia skryptów.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)