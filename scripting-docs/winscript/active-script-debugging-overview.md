---
title: Omówienie debugowania aktywnego skryptu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c06477b7cd9d069e416cfd7d86a8cd0cb7bfd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572270"
---
# <a name="active-script-debugging-overview"></a>Przegląd debugowania aktywnego skryptu
Interfejsy debugowania aktywnego skryptu zezwalają na niezależną od języka, debugowaniem neutralnym dla hosta i obsługują szeroką gamę środowisk programistycznych.  
  
 ![Proces hosta skryptu](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Rysunek 1  
  
 Środowisko debugowania niezależne od języka może obsługiwać dowolny język programowania lub kombinację języków programowania bez konkretnej znajomości któregokolwiek z tych języków. Środowisko debugowania obsługuje również przechodzenie między językami i punkty przerwania. (To omówienie dotyczy głównie języków obsługi skryptów, takich jak VBScript i [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]).  
  
 Debuger neutralny od hosta może być automatycznie używany z dowolnym aktywnym hostem skryptów, takim jak Internet Explorer lub hostem niestandardowym. Host kontroluje, jakie elementy Debugger prezentuje użytkownikowi, od struktury drzewa dokumentu do zawartości i kolorowania składni dokumentów debugowania. Umożliwia to wyświetlanie debugowanego kodu źródłowego w kontekście dokumentu hosta. Na przykład program Internet Explorer może wyświetlić skrypt na stronie HTML.  
  
 W poniższych podsekcjach omówiono każdy składnik klucza w aktywnym debugowaniu i powiązane z nim interfejsy. Jednak przed kontynuowaniem należy zdefiniować kilka aktywnych koncepcji debugowania:  
  
 **aplikacja hosta**  
 Aplikacja obsługująca aparaty skryptów i udostępniająca skryptowy zestaw obiektów (lub "model obiektów").  
  
 **Aparat języka**  
 Składnik, który zapewnia analizę, wykonywanie i debugowanie abstrakcji dla określonego języka.  
  
 **Debuger IDE**  
 Aplikacja, która zapewnia interfejs użytkownika debugowania, komunikując się z aplikacjami hosta i aparatami językowymi.  
  
 **Menedżer debugowania maszyn** Składnik, który utrzymuje rejestr procesów aplikacji możliwością debugowania.  
  
 **Menedżer debugowania procesów**  
 Składnik, który przechowuje drzewo dokumentów możliwością debugowania dla określonej aplikacji, śledzi uruchomione wątki i tak dalej.  
  
 **kontekst dokumentu**  
 Kontekst dokumentu jest abstrakcją reprezentującą konkretny zakres w kodzie źródłowym dokumentu hosta.  
  
 **kontekst kodu**  
 Kontekst kodu reprezentuje konkretną lokalizację w uruchomionym kodzie aparatu języka ("wskaźnik instrukcji wirtualnej").  
  
 **kontekst wyrażenia**  
 Określony kontekst (na przykład Ramka stosu), w którym wyrażenia mogą być oceniane przez Aparat języka.  
  
 **Przeglądanie obiektów**  
 Strukturalna, niezależna od języka reprezentacja nazwy, typu, wartości i obiektów podrzędnych obiektu, odpowiednie do wdrożenia interfejsu użytkownika "okno czujka".  
  
 Poniżej przedstawiono omówienie każdego z kluczowych składników debugowania i odpowiadających im interfejsów, a następnie Szczegóły tych interfejsów.  
  
## <a name="language-engine"></a>Aparat języka  
 Aparat języka udostępnia następujące informacje:  
  
- Analizowanie i wykonywanie języka.  
  
- Obsługa debugowania (punkty przerwania itp.).  
  
- Obliczanie wyrażenia.  
  
- Kolorowanie składni.  
  
- Przeglądanie obiektów.  
  
- Wyliczanie i analizowanie stosu.  
  
  Poniżej przedstawiono interfejsy, które aparat skryptów musi obsługiwać, aby zapewnić debugowanie, obliczanie wyrażeń i przeglądanie obiektów. Te interfejsy są używane przez aplikację hosta do mapowania między kontekstem dokumentu a kontekstami kodu aparatu, a także przez interfejs użytkownika debugera do wykonywania obliczeń wyrażeń, wyliczania stosu i przeglądania obiektów.  
  
  [IActiveScriptDebug, interfejs](../winscript/reference/iactivescriptdebug-interface.md)  
  Oferuje kolorowanie składni i Wyliczenie kontekstu kodu.  
  
  [IActiveScriptErrorDebug, interfejs](../winscript/reference/iactivescripterrordebug-interface.md)  
  Zwraca konteksty dokumentu i ramki stosu dla błędów.  
  
  [IActiveScriptSiteDebug, interfejs](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Udostępniony link hosta z aparatu skryptu do debugera.  
  
  [IDebugCodeContext, interfejs](../winscript/reference/idebugcodecontext-interface.md)  
  Zawiera wirtualny "wskaźnik instrukcji" w wątku.  
  
  [IEnumDebugCodeContexts, interfejs](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Wylicza konteksty kodu, które odnoszą się do kontekstu dokumentu.  
  
  [IDebugStackFrame, interfejs](../winscript/reference/idebugstackframe-interface.md)  
  Reprezentuje logiczną ramkę stosu na stosie wątków.  
  
  [IDebugExpressionContext, interfejs](../winscript/reference/idebugexpressioncontext-interface.md)  
  Zawiera kontekst, w którym można obliczyć wyrażenia.  
  
  [IDebugStackFrameSniffer, interfejs](../winscript/reference/idebugstackframesniffer-interface.md)  
  Umożliwia Wyliczenie logicznych ramek stosu.  
  
  [IDebugExpression, interfejs](../winscript/reference/idebugexpression-interface.md)  
  Reprezentuje wyrażenie asynchronicznie oceniane.  
  
  [IDebugSyncOperation, interfejs](../winscript/reference/idebugsyncoperation-interface.md)  
  Umożliwia aparatowi skryptu abstrakcyjną operację, która musi zostać wykonana, podczas gdy jest zagnieżdżona w określonym zablokowanym wątku.  
  
  [IDebugAsyncOperation, interfejs](../winscript/reference/idebugasyncoperation-interface.md)  
  Zapewnia asynchroniczny dostęp do synchronicznej operacji debugowania.  
  
  [IDebugAsyncOperationCallBack, interfejs](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Udostępnia zdarzenia stanu dotyczące postępu oceny interfejsu `IDebugAsyncOperation`.  
  
  [IEnumDebugExpressionContexts, interfejs](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Wylicza kolekcję obiektów `IDebugExpressionContexts`.  
  
  [IProvideExpressionContexts, interfejs](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Umożliwia Wyliczenie kontekstów wyrażeń znanych przez określony składnik.  
  
  [IDebugFormatter, interfejs](../winscript/reference/idebugformatter-interface.md)  
  Umożliwia językowi lub środowisko IDE dostosowanie konwersji między wartościami VARIANT lub typami VARTYPE i ciągami.  
  
  [IDebugStackFrameSnifferEx, interfejs](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Wylicza logiczne ramki stosu dla PDM.  
  
## <a name="hosts"></a>Pracując  
 Host:  
  
- Hostuje aparaty języka.  
  
- Udostępnia model obiektów (zestaw obiektów, które mogą być skryptowe).  
  
- Definiuje drzewo dokumentów, które mogą być debugowane i ich zawartość.  
  
- Organizuje skrypty w aplikacjach wirtualnych.  
  
  Istnieją dwa rodzaje hostów:  
  
- Host Dumb obsługuje tylko podstawowe interfejsy skryptów aktywnych. Nie ma kontroli nad strukturą dokumentu ani organizacjami; jest to określane całkowicie przez skrypty udostępniane aparatom językowym.  
  
- Inteligentny host obsługuje większy zestaw interfejsów, który umożliwia działowi IT Definiowanie drzewa dokumentów, zawartości dokumentu i kolorowanie składni. Istnieje zestaw interfejsów pomocnika opisany w następnej podsekcji, które znacznie ułatwiają hostowi inteligentnego hosta.  
  
### <a name="smart-host-helper-interfaces"></a>Interfejsy pomocnika inteligentnego hosta  
 Metody `IDebugDocumentHelper` zapewniają znacznie uproszczony zestaw interfejsów, które mogą być używane przez hosta w celu uzyskania korzyści z inteligentnego hostingu bez obsługi pełnej złożoności (i mocy) pełnych interfejsów hosta.  
  
 Host nie jest wymagany do korzystania z tych interfejsów. Jednak użycie tych interfejsów może uniknąć implementacji lub użycia wielu bardziej skomplikowanych interfejsów.  
  
 [IDebugDocumentHelper, interfejs](../winscript/reference/idebugdocumenthelper-interface.md)  
 Zaimplementowane przez PDM i zawiera implementacje dla wielu interfejsów, które są niezbędne do hostingu inteligentnego.  
  
 [IDebugDocumentHost, interfejs](../winscript/reference/idebugdocumenthost-interface.md)  
 Zaimplementowane (opcjonalnie) przez hosta, aby uwidocznić funkcje specyficzne dla hosta, takie jak kolorowanie składni w debugerze.  
  
 Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsów pomocnika inteligentnego hosta](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Pełne interfejsy inteligentnego hosta  
 Poniżej znajduje się pełen zestaw interfejsów, które są implementowane lub używane przez inteligentnego hosta, jeśli nie używa interfejsów pomocnika.  
  
 Interfejsy zaimplementowane przez hosta:  
  
 [IDebugDocumentInfo, interfejs](../winscript/reference/idebugdocumentinfo-interface.md)  
 Zawiera informacje o dokumencie, który może lub nie można utworzyć wystąpienia.  
  
 [IDebugDocumentProvider, interfejs](../winscript/reference/idebugdocumentprovider-interface.md)  
 Zapewnia sposób tworzenia wystąpienia dokumentu na żądanie.  
  
 [IDebugDocument, interfejs](../winscript/reference/idebugdocument-interface.md)  
 Interfejs podstawowy dla wszystkich dokumentów debugowania.  
  
 [IDebugDocumentText, interfejs](../winscript/reference/idebugdocumenttext-interface.md)  
 Zapewnia dostęp do wersji tekstowej dokumentu debugowania.  
  
 [IDebugDocumentTextAuthor, interfejs](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Umożliwia edytowanie wersji tekstowej dokumentu debugowania.  
  
 [IDebugDocumentContext, interfejs](../winscript/reference/idebugdocumentcontext-interface.md)  
 Zapewnia abstrakcyjną reprezentację części debugowanego dokumentu.  
  
 Interfejsy zaimplementowane przez PDM w imieniu hosta:  
  
 [IDebugApplicationNode, interfejs](../winscript/reference/idebugapplicationnode-interface.md)  
 Rozszerza funkcjonalność interfejsu `IDebugDocumentProvider` przez udostępnienie kontekstu w drzewie projektu.  
  
## <a name="debugger-ide"></a>Debuger IDE  
 IDE jest niezależnym od języka interfejsem użytkownika debugowania. Zapewnia:  
  
- Przeglądający dokumenty/redaktorzy.  
  
- Zarządzanie punktem przerwania.  
  
- Ocenianie wyrażeń i okna czujki.  
  
- Przeglądanie ramek stosu.  
  
- Przeglądanie obiektów/klas.  
  
- Przeglądanie struktury aplikacji wirtualnej.  
  
  Interfejsy implementowane przez debuger:  
  
  [IApplicationDebugger, interfejs](../winscript/reference/iapplicationdebugger-interface.md)  
  Podstawowy interfejs udostępniany przez sesję debugera IDE.  
  
  [IApplicationDebuggerUI, interfejs](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Zapewnia, że składnik zewnętrzny ma większą kontrolę nad interfejsem użytkownika (UI) debugera.  
  
  [IDebugExpressionCallBack, interfejs](../winscript/reference/idebugexpressioncallback-interface.md)  
  Udostępnia zdarzenia stanu dla `IDebugExpression` oceny postępu.  
  
  [IDebugDocumentTextEvents, interfejs](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Zapewnia zdarzenia wskazujące zmiany w skojarzonym dokumencie tekstowym.  
  
  [IDebugApplicationNodeEvents, interfejs](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Udostępnia interfejs zdarzenia dla interfejsu `IDebugApplicationNode`.  
  
### <a name="machine-debug-manager"></a>Menedżer debugowania maszyn  
 Menedżer debugowania maszynowego udostępnia punkt podłączenie między aplikacjami wirtualnymi i debugerami przez utrzymywanie i wyliczanie listy aktywnych aplikacji wirtualnych.  
  
 [IDebugSessionProvider, interfejs](../winscript/reference/idebugsessionprovider-interface.md)  
 Ustanawia sesję debugowania dla działającej aplikacji.  
  
 [IMachineDebugManager, interfejs](../winscript/reference/imachinedebugmanager-interface.md)  
 Podstawowy interfejs Menedżera debugowania maszynowego.  
  
 [IMachineDebugManagerCookie, interfejs](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Podobnie jak w przypadku interfejsu `IMachineDebugManager`, ale ten interfejs obsługuje debugowanie plików cookie.  
  
 [IMachineDebugManagerEvents, interfejs](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Sygnalizuje zmiany na działającej liście aplikacji obsługiwane przez Menedżera debugowania maszyny.  
  
 [IEnumRemoteDebugApplications, interfejs](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Wylicza uruchomione aplikacje na komputerze.  
  
### <a name="process-debug-manager"></a>Menedżer debugowania procesów  
 PDM wykonuje następujące czynności:  
  
- Synchronizuje debugowanie wielu aparatów językowych.  
  
- Utrzymuje drzewo dokumentów możliwością debugowania.  
  
- Scala ramki stosu.  
  
- Koordynuje punkty przerwania i taktowanie między aparatami języka.  
  
- Śledzi wątki.  
  
- Utrzymuje wątek debugera do przetwarzania asynchronicznego.  
  
- Komunikuje się z menedżerem debugowania maszyn i IDE.  
  
  Poniżej przedstawiono interfejsy udostępniane przez Menedżera debugowania procesów.  
  
  [IProcessDebugManager, interfejs](../winscript/reference/iprocessdebugmanager-interface.md)  
  Interfejs podstawowy do Menedżera debugowania procesów. Ten interfejs może tworzyć, dodawać lub usuwać aplikacje wirtualne z procesu.  
  
  [IRemoteDebugApplication, interfejs](../winscript/reference/iremotedebugapplication-interface.md)  
  Reprezentuje uruchomioną aplikację.  
  
  [IDebugApplication, interfejs](../winscript/reference/idebugapplication-interface.md)  
  Uwidacznia metody debugowania inne niż zdalne do użycia przez aparaty i hosty języka.  
  
  [IRemoteDebugApplicationThread, interfejs](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Reprezentuje wątek wykonania w ramach określonej aplikacji.  
  
  [IDebugApplicationThread, interfejs](../winscript/reference/idebugapplicationthread-interface.md)  
  Umożliwia aparatom i hostom języka zapewnienie synchronizacji wątku oraz zachowanie informacji o stanie debugowania specyficznych dla wątków.  
  
  [IEnumRemoteDebugApplicationThreads, interfejs](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Wylicza uruchomione wątki w aplikacji.  
  
  [IDebugThreadCall, interfejs](../winscript/reference/idebugthreadcall-interface.md)  
  Wysyła wywołania organizowane.  
  
  [IDebugApplicationNode, interfejs](../winscript/reference/idebugapplicationnode-interface.md)  
  Zachowuje położenie dokumentu w hierarchii.  
  
  [IEnumDebugApplicationNodes, interfejs](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Wylicza węzły podrzędne węzła skojarzonego z aplikacją.  
  
  [IEnumDebugStackFrames, interfejs](../winscript/reference/ienumdebugstackframes-interface.md)  
  Wylicza ramki stosu odpowiadające wątkowi, scalone z aparatu.  
  
  [IDebugCookie, interfejs](../winscript/reference/idebugcookie-interface.md)  
  Umożliwia ustawienie pliku cookie debugowania w debugerach skryptów.  
  
  [IDebugHelper, interfejs](../winscript/reference/idebughelper-interface.md)  
  Służy jako fabryka dla przeglądarek obiektów i prostych punktów połączenia dla aparatów skryptów.  
  
  [ISimpleConnectionPoint, interfejs](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Zapewnia prosty sposób opisywania i wyliczania zdarzeń wyzwalanych w określonym punkcie połączenia dla aparatów skryptów.  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy debugera aktywnego skryptu](../winscript/reference/active-script-debugger-interfaces.md)
