---
title: Aparaty skryptów systemu Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27a500f9df91738e2db563f7e37ee646925b674e
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835696"
---
# <a name="windows-script-engines"></a>Aparaty skryptów systemu Windows
Aby zaimplementować aparat skryptów systemu Microsoft Windows, Utwórz obiekt OLE COM, który obsługuje następujące interfejsy.  
  
|||  
|-|-|  
|Interfejs|Opis|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Zapewnia podstawową możliwość obsługi skryptów. Implementacja tego interfejsu jest wymagana.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Umożliwia dodawanie tekstu skryptu, obliczanie wyrażeń i tak dalej. Implementacja tego interfejsu jest opcjonalna; Jeśli jednak nie zostanie zaimplementowana, aparat skryptów musi zaimplementować jeden z interfejsów IPersist * w celu załadowania skryptu.|  
|IPersist*|Zapewnia obsługę trwałości. Jeśli [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest zaimplementowany, wymagana jest implementacja co najmniej jednego z następujących interfejsów.<br /><br /> IPersistStorage: zapewnia obsługę atrybutu DATA = {URL} w tagu OBJECT.<br /><br /> IPersistStreamInit: zapewnia obsługę tego samego, jak `IPersistStorage` również ATRYBUT Data = "strumień bajtów zakodowanych" w tagu Object.<br /><br /> IPersistPropertyBag: zapewnia obsługę atrybutu PARAM = w tagu OBJECT.|  
  
> [!NOTE]
> Jest możliwe, że aparat obsługi skryptów nigdy nie zostanie wywołany w celu zapisania lub przywrócenia stanu skryptu za pomocą programu `IPersist*` . Zamiast tego [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) jest używany przez wywołanie [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) w celu utworzenia pustego skryptu, a następnie skryptlety są dodawane i połączone ze zdarzeniami z [IActiveScriptParse:: AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) i kod ogólny jest dodawany z [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md). Niemniej jednak aparat obsługi skryptów powinien w pełni zaimplementować co najmniej jeden `IPersist*` interfejs (najlepiej `IPersistStreamInit` ), ponieważ inne aplikacje hosta mogą próbować korzystać z nich.  
  
 W poniższych sekcjach opisano implementację aparatu skryptów systemu Windows bardziej szczegółowo.  
  
 Aby uzyskać więcej informacji, zobacz informacje dotyczące [interfejsów skryptów systemu Windows](../winscript/reference/windows-script-interfaces-reference.md) .  
  
## <a name="registry-standard"></a>Standard rejestru  
 Aparat skryptów systemu Windows może identyfikować siebie przy użyciu identyfikatorów kategorii. Skrypt systemu Windows obecnie definiuje dwa identyfikatory kategorii.  
  
|||  
|-|-|  
|Kategoria|Opis|  
|CATID_ActiveScript|Wskazuje, że identyfikatory klas (CLSID) są aparatami skryptów systemu Windows, które obsługują, co najmniej Interfejs [IActiveScript](../winscript/reference/iactivescript.md) i mechanizm trwałości ( `IPersistStorage` `IPersistStreamInit` interfejs, lub IPersistPropertyBag).|  
|CATID_ActiveScriptParse|Wskazuje, że identyfikatory CLSID są aparatów skryptów systemu Windows, które obsługują co najmniej interfejsy [IActiveScript](../winscript/reference/iactivescript.md) i [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|  
  
 Chociaż [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest mechanizmem trwałości true, obsługuje metodę [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) , która jest funkcjonalnie równoważna z `IPersist*::InitNew` .  
  
## <a name="script-engine-states"></a>Stany aparatu skryptów  
 W dowolnym momencie aparat skryptów systemu Windows może znajdować się w jednym z kilku stanów.  
  
|||  
|-|-|  
|Stan|Opis|  
|niezainicjowanego|Skrypt nie został zainicjowany lub załadowany przy użyciu interfejsu IPersist * lub nie ma ustawionego interfejsu [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) . Aparat obsługi skryptów zwykle nie jest używany z tego stanu do momentu załadowania skryptu.|  
|Initialize|Skrypt został zainicjowany przy użyciu `IPersist*` interfejsu i ma ustawiony Interfejs [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) , ale nie jest połączony z obiektami hosta i zdarzeniami ujścia. Należy zauważyć, że ten stan po prostu oznacza, że `IPersist*::Load` `IPersist*::InitNew` Metoda,, lub [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) została zakończona i że metoda [IActiveScript:: SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) została wywołana. Aparat nie może uruchomić kodu w tym trybie. Aparat uruchamia kod, który host przekazuje do niego za pomocą metody [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) i wykonuje kod po przejściu do stanu uruchomienia.<br /><br /> Ponieważ języki mogą się różnić w semantyce, aparaty skryptów nie są wymagane do obsługi tego przejścia stanu. Aparaty obsługujące metodę [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) muszą jednak obsługiwać to przejście stanu. Hosty muszą przygotowywać się do tego przejścia i podejmować odpowiednie działania: Zwolnij bieżący aparat skryptów, Utwórz nowy aparat skryptów, a następnie Wywołaj metodę, `IPersist*::Load` `IPersist*::InitNew` lub [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) (a także wywołaj [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md)). Użycie tego przejścia powinno być traktowane jak optymalizacja powyższych kroków. Należy zauważyć, że wszystkie informacje o nazwach elementów i informacje o typie opisujące nazwane elementy są prawidłowe.<br /><br /> Ponieważ Języki różnią się znacznie, Definiowanie dokładnej semantyki tego przejścia jest trudne. Aparat obsługi skryptów musi być co najmniej rozłączony ze wszystkimi zdarzeniami i wydać wszystkie SCRIPTINFO_IUNKNOWN wskaźników uzyskanych przez wywołanie metody [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) . Aparat musi ponownie uzyskać te wskaźniki po ponownym uruchomieniu skryptu. Aparat skryptów powinien również zresetować skrypt z powrotem do stanu początkowego, który jest odpowiedni dla danego języka. Skrypt VBScript, na przykład resetuje wszystkie zmienne i zachowuje kod dodany dynamicznie przez wywołanie [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) z ustawioną flagą SCRIPTTEXT_ISPERSISTENT. Inne języki mogą wymagać zachowania bieżących wartości (takich jak Lisp, ponieważ nie ma kodu/separacji danych) lub resetowania do dobrze znanego stanu (obejmuje to języki ze statycznie zainicjowanymi zmiennymi).<br /><br /> Należy zauważyć, że przejście do stanu rozpoczęte powinno mieć tę samą semantykę (to oznacza, że aparat wykonywania skryptów jest w tym samym stanie) jako wywołujący `IPersist*::Save` , aby zapisać aparat wykonywania skryptów, a następnie wywołać `IPersist*::Load` nowy aparat obsługi skryptów; te działania powinny mieć taką samą semantykę jak [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md). Aparaty skryptów, które jeszcze nie obsługują `IActiveScript::Clone` lub `IPersist*` powinny starannie rozważyć sposób zachowania przejścia do stanu uruchomienia, tak że takie przeniesienie nie będzie naruszać powyższych warunków, jeśli `IActiveScript::Clone` `IPersist*` Pomoc techniczna została później dodana.<br /><br /> W trakcie tego przejścia do stanu uruchomiono aparat skryptów odłączy się od ujścia zdarzeń po odpowiednich destruktorach i tak dalej, są wykonywane w skrypcie. Aby uniknąć wykonywania tych destruktorów, host może najpierw przenieść skrypt do stanu rozłączenia przed przejściem do stanu uruchomienia.<br /><br /> Użyj [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) , aby anulować uruchomiony wątek skryptu bez oczekiwania na bieżące zdarzenia itd., aby zakończyć działanie.|  
|uruchomieniu|Przejście z stanu zainicjowania do stanu uruchomiono powoduje, że aparat wykona każdy kod, który został umieszczony w kolejce w stanie zainicjowany. Aparat może wykonać kod w stanie uruchomienia, ale nie jest podłączony do żadnych zdarzeń dodanych za pomocą metody [IActiveScript:: AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) . Aparat może wykonać kod, wywołując interfejs IDispatch uzyskany z metody [IActiveScript:: GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) lub wywołując [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md). Istnieje możliwość, że dalsze inicjowanie w tle (ładowanie progresywne) nadal trwa i wywołanie metody [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) z ustawioną flagą SCRIPTSTATE_CONNECTED może spowodować zablokowanie skryptu do momentu ukończenia inicjalizacji.|  
|połączono|Skrypt jest ładowany i połączony dla zdarzeń ujścia z obiektów hosta. Jeśli jest to przejście z stanu zainicjowania, aparat obsługi skryptów powinien przejść w stan uruchomienia, wykonać niezbędne akcje, przed wprowadzeniem stanu połączonego i nawiązaniem połączenia ze zdarzeniami.|  
|utrzymywani|Skrypt jest ładowany i ma stan czasu wykonywania, ale jest tymczasowo odłączony od obiektów hosta. Można to zrobić logicznie (ignorowanie zdarzeń odebranych) lub fizycznie (wywołując IConnectionPoint:: Unadvise w odpowiednich punktach połączenia). Jeśli jest to przejście z stanu zainicjowania, aparat skryptów powinien przejść w stan uruchomienia, wykonać niezbędne akcje przed wprowadzeniem stanu rozłączenia. Ujścia zdarzeń, które są w toku, są kończone przed zmianą stanu (Użyj [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) , aby anulować uruchomiony wątek skryptu). Ten stan jest oddzielony od stanu zainicjowania w przypadku, gdy przejście do tego stanu nie powoduje zresetowania skryptu, stanu czasu wykonywania skryptu nie jest resetowana, a procedura inicjowania skryptu nie jest wykonywana.|  
|zamknięte|Skrypt został zamknięty. Aparat skryptów nie działa już i zwraca błędy dla większości metod.|  
  
 Na poniższej ilustracji przedstawiono relacje między różnymi stanami aparatu skryptów i przedstawiono metody, które powodują przejście z jednego stanu do drugiego.  
  
 Na poniższej ilustracji przedstawiono akcje wykonywane przez aparat skryptów podczas różnych przejść między Stanami.  
  
## <a name="scripting-engine-threading"></a>Wątkowość aparatu skryptów  
 Ze względu na to, że aparat skryptów systemu Windows może być używany w wielu środowiskach, ważne jest, aby zachować model wykonywania, tak jak to możliwe. Na przykład hosta opartego na serwerze może być w stanie zachować wielowątkowy projekt, jednocześnie używając skryptu systemu Windows. W tym samym czasie host, który nie używa wątków, takich jak typowa aplikacja, nie powinien być niezależny od zarządzania wątkami. Skrypt systemu Windows osiąga to saldo, ograniczając sposoby wywołania przez aparat skryptów bezpłatnych wątków do hosta, zwalniając hosty z tego obciążenia.  
  
 Aparaty skryptów używane na serwerach są zwykle implementowane jako wolne wątki obiektów COM. Oznacza to, że metody interfejsu [IActiveScript](../winscript/reference/iactivescript.md) i skojarzone z nimi interfejsy mogą być wywoływane z dowolnego wątku w procesie, bez organizowania. (Niestety oznacza to również, że aparat skryptów musi być zaimplementowany jako serwer w procesie, ponieważ technologia OLE nie obsługuje obecnie międzyprocesowego organizowania obiektów wolnych wątków). Synchronizacja jest odpowiedzialna za aparat obsługi skryptów. W przypadku aparatów skryptów, które nie są wewnętrznie współużytkowane lub dla modeli języka, które nie są wielowątkowe, synchronizacja może być prosta jako Serializacja dostępu do aparatu skryptów z muteksem. Oczywiście niektóre metody, takie jak [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), nie powinny być serializowane w ten sposób, aby można było przerwać zablokowany skrypt z innego wątku.  
  
 Fakt, że [IActiveScript](../winscript/reference/iactivescript.md) jest zwykle bezpłatny, zwykle oznacza, że interfejs [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) i model obiektów hosta powinny być również bezwątkowe. Dzięki temu implementacja hosta jest dość trudna, szczególnie w typowym przypadku, gdy host jest jednowątkową aplikacją opartą na systemie Windows z kontrolkami ActiveX jednowątkowych lub typu Apartment w modelu obiektów. Z tego powodu następujące ograniczenia są umieszczane na [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)aparatu skryptów:  
  
 Lokacja skryptu jest zawsze wywoływana w kontekście wątku hosta. Oznacza to, że aparat obsługi skryptów nigdy nie wywołuje lokacji skryptu w kontekście wątku, w którym utworzono aparat skryptów, ale tylko z poziomu metody aparatu skryptów, która została wywołana z hosta za pośrednictwem [IActiveScript](../winscript/reference/iactivescript.md) i jego pochodnych, za pośrednictwem obiektu wysyłającego aparatu skryptów, za pośrednictwem komunikatu systemu Windows lub źródła zdarzeń w modelu obiektów hosta.  
  
 Lokacja skryptu nigdy nie jest wywoływana z poziomu kontekstu metody kontroli stanu prostego wątku (na przykład [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) ) lub z metody [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)
