---
title: Windows aparatami skryptów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3434e9baaeb483e60087aec1b8536108c8af4471
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157766"
---
# <a name="windows-script-engines"></a>Aparaty skryptów systemu Windows
Aby zaimplementować aparatu programu Microsoft Windows Script, należy utworzyć obiekt OLE COM, który obsługuje następujące interfejsy.  
  
|||  
|-|-|  
|Interface|Opis|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Zapewnia podstawowe możliwości obsługi skryptów. Wymagana jest implementacja tego interfejsu.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Oferuje możliwość dodawania tekst skryptu, obliczać wyrażeń i tak dalej. Implementację tego interfejsu jest opcjonalna. Jednak jeśli nie jest zaimplementowana, aparat skryptu musi implementować jeden z interfejsów IPersist * w celu załadowania skryptu.|  
|IPersist *|Zapewnia obsługę trwałości. Wymagana jest implementacja co najmniej jeden z następujących interfejsów, jeśli [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest zaimplementowana.<br /><br /> IPersistStorage: Zapewnia obsługę danych = {url} atrybut w tagu obiektu.<br /><br /> IPersistStreamInit: Dodano obsługę taka sama jak `IPersistStorage` oraz danych = "strumień zakodowany w formacie ciągu bajtów" atrybut w tagu obiektu.<br /><br /> IPersistPropertyBag: Zapewnia obsługę PARAMETR = atrybut w tagu obiektu.|  
  
> [!NOTE]
>  Istnieje możliwość, że aparat skryptów będą nigdy nie zobowiązane do zapisania lub przywrócenia stanu skrypt, za pośrednictwem `IPersist*`. Zamiast tego [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) jest używany przez wywołanie metody [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) Aby utworzyć skrypt pusta, następnie skryptlety są dodawane i podłączone do zdarzenia przy użyciu [IActiveScriptParse:: AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) i ogólne kod dodaje się [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Niemniej jednak silnik wykonywania skryptów w pełni zaimplementować co najmniej jeden `IPersist*` interfejsu (najlepiej `IPersistStreamInit`), ponieważ inne aplikacje hosta mogą próbować wprowadzić je wykorzystać.  
  
 W poniższych sekcjach opisano Implementowanie to aparat obsługi skryptów Windows bardziej szczegółowo.  
  
 Zobacz [dokumentacja interfejsów skryptów Windows](../winscript/reference/windows-script-interfaces-reference.md) Aby uzyskać więcej informacji.  
  
## <a name="registry-standard"></a>Standardowa rejestru  
 Aparat skryptów Windows może identyfikować się przy użyciu identyfikatorów kategorii. Skrypt Windows obecnie definiuje dwa identyfikatory kategorii.  
  
|||  
|-|-|  
|Kategoria|Opis|  
|CATID_ActiveScript|Wskazuje, że identyfikatorów klasy (CLSID) aparatów skryptów Windows, które obsługują co najmniej [IActiveScript](../winscript/reference/iactivescript.md) interfejsu i mechanizmu stanu trwałego ( `IPersistStorage`, `IPersistStreamInit`, lub IPersistPropertyBag Interfejs).|  
|CATID_ActiveScriptParse|Wskazuje, że CLSID aparatów skryptów Windows, które obsługują co najmniej [IActiveScript](../winscript/reference/iactivescript.md) i [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsów.|  
  
 Mimo że [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest mechanizm trwałości wartość true, obsługuje on [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodę, która jest funkcjonalnym odpowiednikiem `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Stany aparatu obsługi skryptów  
 W dowolnym momencie aparat skryptów Windows może być w jednym z kilku stanów.  
  
|||  
|-|-|  
|Stan|Opis|  
|Niezainicjowane|Skrypt nie został zainicjowany lub ładowane przy użyciu interfejsu IPersist * lub nie ma [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu zestawu. Aparat skryptów ogólnie nie jest używany w tym stanie do momentu załadowania skryptu.|  
|zainicjowany|Skrypt został zainicjowany przy użyciu `IPersist*` interfejs i ma [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu zestawu, ale nie jest podłączony do obiektów hosta i wychwytywania zdarzeń. Należy pamiętać, że ten stan po prostu oznacza, że `IPersist*::Load`, `IPersist*::InitNew`, lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metoda została zakończona i że [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) metoda ma została wywołana. Aparat nie może uruchomić kod, w tym trybie. Aparat kolejki kod, który host przekazuje do niego za pośrednictwem [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) metodę i wykonuje kod po przejście do stanu uruchomienia.<br /><br /> Ponieważ języków mogą się znacznie zmieniać w semantyce, aparatów obsługi skryptów nie są wymagane do obsługi tego przejścia stanu. Aparaty obsługujące [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) metoda jednak musi obsługiwać tego przejścia stanu. Hosty muszą przygotować się do tego przejścia i podejmij odpowiednie działanie: wersji bieżącym silnikiem skryptującym, Utwórz nowy aparat skryptów i wywołania `IPersist*::Load`, `IPersist*::InitNew`, lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (i prawdopodobnie również wywołać [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). Użyj tego przejścia należy rozważyć optymalizacji powyższych kroków. Należy pamiętać, że wszystkie informacje o nazwach elementów o nazwie uzyskał silnik wykonywania skryptów i informacje o typie o nazwie elementy opisujące pozostaje ważny.<br /><br /> Ponieważ języki są bardzo zróżnicowane, definiowanie dokładnie semantykę ten proces przejścia jest trudne. Co najmniej silnik wykonywania skryptów należy odłączyć od wszystkich zdarzeń i zwolnij wszystkie wskaźniki SCRIPTINFO_IUNKNOWN można uzyskać przez wywołanie [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metody. Aparat musi ponownie uzyskać te wskaźniki, po ponownym uruchomieniu skryptu. Aparat skryptów należy również przywrócić skrypt początkowy stan, który jest odpowiedni dla języka. Skrypt VBScript, na przykład resetuje wszystkie zmienne i zachowuje jakiegokolwiek kodu dodawane dynamicznie przez wywołanie metody [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) z SCRIPTTEXT_ISPERSISTENT flagą zestawu. Inne języki może być konieczne zachowanie bieżących wartości (takie jak Lisp, ponieważ nie istnieje bez separacji danych/kodu), lub zresetuj dobrze znanego stanu (w tym języków za pomocą zmiennych statycznie zainicjowane).<br /><br /> Należy pamiętać, że przejście do stanu uruchomienia powinny mieć tą samą semantyką (czyli go należy pozostawić silnik wykonywania skryptów w tym samym stanie) co wywołanie metody `IPersist*::Save` można zapisać silnik wykonywania skryptów, a następnie wywoływania `IPersist*::Load` załadować nowy aparat skryptów; te akcje powinny mieć tą samą semantyką jako [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Skryptów, które nie obsługują jeszcze `IActiveScript::Clone` lub `IPersist*` należy rozważyć, jak przejście do stanu uruchomienia powinny zachowywać się, dzięki czemu takie przejście może naruszają powyższe warunki, jeśli `IActiveScript::Clone` lub `IPersist*` później dodano obsługę.<br /><br /> Podczas to przejście do stanu uruchomienia aparatu skryptów spowoduje rozłączenie ujścia zdarzeń po odpowiednich destruktory i tak dalej, są wykonywane w skrypcie. Aby uniknąć tych destruktory wykonywane, hosta można najpierw przenieść skrypt rozłączona przed przeniesieniem do stanu uruchomienia.<br /><br /> Użyj [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) zakończą działanie, aby anulować uruchomionemu wątkowi skryptu bez oczekiwania na bieżące wydarzenia i tak dalej.|  
|Pracę|Przejście ze stanu zainicjowania do stanu uruchomienia powoduje, że aparat wykonywania żadnych kodu, które zostało umieszczone w kolejce jest w stanie inicjowania. Silnik może wykonać kod znajduje się w stanie uruchomienia, ale nie jest podłączony do żadnych zdarzeń dodane za pomocą [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metody. Silnik może wykonać kod, wywołując interfejs IDispatch uzyskany z [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) metody lub przez wywołanie [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Istnieje możliwość, że dodatkowe inicjowanie tła (progresywny załadunku) nadal trwa i że wywołanie [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metody z ustawioną flagą SCRIPTSTATE_CONNECTED może spowodować, że skrypt blokowania przed zakończeniem inicjowania.|  
|Połączone|Skrypt jest ładowany i podłączony do wychwytywania zdarzeń z obiektów hosta. Jeśli przejście ze stanu zainicjowania silnik wykonywania skryptów powinny przejście do stanu uruchomienia, wykonując niezbędne działania, zanim wprowadzania stan połączenia i połączenie na zdarzenia.|  
|Odłączony|Skrypt jest ładowany, ma stan czasu wykonywania, a jest tymczasowo odłączone od wychwytywania zdarzeń z obiektów hosta. Można to zrobić albo logicznie (bez uwzględnienia zdarzeń otrzymanych) lub fizycznie (wywołanie IConnectionPoint::Unadvise punktach odpowiednie połączenie). Jeśli przejście ze stanu zainicjowania silnik wykonywania skryptów powinny przejście do stanu uruchomienia, wykonując niezbędne działania przed wejściem w stanie odłączonym. Obiekty sink zdarzenia, które są w toku są wykonywane przed zmianami stanu (Użyj [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) anulowania uruchomionego wątku skryptu). Ten stan jest różnią się od stanie zainicjowania, że przejście do tego stanu nie powoduje, że skrypt zresetować, stan czasu wykonywania skryptu nie jest resetowany i nie jest wykonywany skrypt procedury inicjowania.|  
|Zamknięte|Skrypt został zamknięty. Aparat skryptów nie jest już działa i zwraca informacje o błędach dla większości metod.|  
  
 Na poniższej ilustracji przedstawiono relacje między różne stany aparatu obsługi skryptów i zawiera metody, które powodują przejścia z jednego stanu do drugiego.  
  
 Na poniższej ilustracji przedstawiono akcje, że aparat skryptów jest wykonywane podczas różnych stanów przejść.  
  
## <a name="scripting-engine-threading"></a>Wątkowość aparatu obsługi skryptów  
 Ponieważ aparat skryptów Windows mogą być używane w wielu środowiskach, należy zachować jak najbardziej elastyczny model jego wykonywania. Na przykład na serwerze hosta może być konieczne zachowanie wielowątkowe projektu podczas za pomocą skryptu Windows w sposób efektywny. W tym samym czasie hosta, która nie korzysta z wątków, takie jak typowa aplikacja powinna nie można obciążać wątkowości zarządzania. Skrypt Windows realizuje tej równowagi przez ograniczenie sposobów bezwątkowy silnik wykonywania skryptów wywołania zwrotnego do hosta, zwalniając hosty z poziomu tego obciążenia.  
  
 Używany na serwerach aparatów obsługi skryptów są zwykle implementowane jako wolny wątków obiektów COM. Oznacza to, że metody [IActiveScript](../winscript/reference/iactivescript.md) interfejsu i jego skojarzone interfejsy mogą być wywoływane z żadnym z wątków w procesie bez kierowania. (Niestety, oznacza to, że aparat skryptów musi zostać wdrożony jako serwer w trakcie ponieważ OLE nie obsługuje obecnie międzyprocesowej szeregowanie obiektów bezwątkowy.) Synchronizacja jest odpowiedzialny za aparatu obsługi skryptów. Dla skryptów, które nie są współużytkowane wewnętrznie lub modele językowe, które nie są wielowątkowe synchronizacji można tak proste, jak serializacji dostęp do aparatu skryptów za pomocą elementu mutex. Oczywiście w niektórych metod, takich jak [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), nie powinien podlegać serializacji w ten sposób, dzięki czemu można przerywać działanie skryptu zablokowane z innego wątku.  
  
 Fakt, [IActiveScript](../winscript/reference/iactivescript.md) jest zazwyczaj bezwątkowy zazwyczaj oznacza, że [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu i model obiektu hosta powinien być bezwątkowy także. Dzięki temu upewnisz się implementacji hosta bardzo trudne, szczególnie w przypadku typowe, gdy host jest oparte na Windows aplikacja jednowątkowa z kontrolkami ActiveX w jednowątkowym lub modelu typu apartment w jego modelu obiektów. Z tego powodu następujące ograniczenia są umieszczane na używanie aparatu skryptów [IActiveScriptSite](../winscript/reference/iactivescriptsite.md):  
  
 W witrynie skryptu zawsze jest wywoływany w kontekście wątku hosta. Oznacza to, skryptów aparatu nigdy nie wywołania lokacji skryptu w kontekście wątku utworzonego przez silnik wykonywania skryptów, ale tylko z poziomu skryptów aparatu metodę, która została wywołana z hosta za pośrednictwem [IActiveScript](../winscript/reference/iactivescript.md) i jego pochodne za pośrednictwem obiektu wysyłania narażonych silnik wykonywania skryptów, za pośrednictwem wiadomości Windows lub z źródła zdarzeń w modelu obiektu hosta.  
  
 W kontekście wątku proste metody kontroli stanu lokacji skrypt nigdy nie jest wywoływana z (na przykład [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) metoda) lub z [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) Metoda.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)
