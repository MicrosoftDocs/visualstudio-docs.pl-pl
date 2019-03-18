---
title: Przegląd debugowania skryptów aktywnych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 31fb3f5bf88b0caf179a43d02358bb6a9f1a2831
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149656"
---
# <a name="active-script-debugging-overview"></a>Przegląd debugowania aktywnego skryptu
Interfejsy funkcji aktywnego debugowania skryptu zezwolenia na debugowanie niezależny od języka, niezależny od hosta, a także obsługuje wiele różnych środowisk deweloperskich.  
  
 ![Script Host Process](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Rysunek 1.  
  
 Środowisko do debugowania niezależny od języka może obsługiwać dowolnego języka lub różnych języków programowania, bez określonych informacji o każdym z tych języków programowania. Środowisko debugowania obsługuje także przechodzenie między językami i punktów przerwania. (W tym omówieniu koncentruje się głównie dotyczących obsługi różnych języków, takich jak VBScript skryptów i [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Debuger niezależny od hosta można automatycznie z dowolnym hostem wykonywanie aktywnych skryptów, takich jak program Internet Explorer lub niestandardowego hosta. Host steruje, debuger wyświetla użytkownikowi, struktura drzewa dokumentu z zawartością i kolorowanie składni dokumentów debugowania. Dzięki temu kod źródłowy debugowanego, które mają być wyświetlane w kontekście dokumentu hosta. Na przykład program Internet Explorer można wyświetlić skryptu na stronie HTML.  
  
 W poniższych podsekcjach omówiono każdy kluczowym czynnikiem aktywnego debugowania i jego skojarzone interfejsy. Jednak przed kontynuowaniem, można zdefiniować kilka podstawowych pojęć aktywnego debugowania:  
  
 **Aplikacja hosta**  
 Aplikacji, który jest hostem skrypt silników i udostępnia zestaw za pomocą skryptów obiektów (lub "object model").  
  
 **aparat języka**  
 Składnik, który umożliwia analizowanie, wykonywania i debugowania abstrakcji dla określonego języka.  
  
 **Debuger środowiska IDE**  
 Aplikacja, która umożliwia debugowanie interfejsu użytkownika, komunikując się z aparatami aplikacji i języka hosta.  
  
 **Menedżer debugowania maszyny** składnik, który przechowuje rejestr procesów debugowania aplikacji.  
  
 **Menedżer debugowania procesów**  
 Składnik, który przechowuje drzewa debugowania dokumentów dla określonej aplikacji śledzi uruchomionych wątków i tak dalej.  
  
 **Kontekst dokumentu**  
 Kontekst dokumentu jest klasą abstrakcyjną reprezentującą określony zakres w kodzie źródłowym dokumentu hosta.  
  
 **Kontekst kodu**  
 Kontekst kodu reprezentuje określonego miejsca w uruchamianie kodu języka aparatu ("wskaźnik instrukcji wirtualne".)  
  
 **wyrażenie kontekstu**  
 Szczególnym kontekście (na przykład ramki stosu) w którym określeń może zostać ocenione przez aparat języka.  
  
 **Przeglądanie obiektów**  
 Ze strukturą, niezależny od języka reprezentacji nazwy, typu, wartości i obiektów podrzędnych, odpowiednie do wykonania "okno czujki" obiektu interfejsu użytkownika.  
  
 Poniżej przedstawiono omówienie każdego z kluczowych składników. ich aktywnego debugowania i odpowiednie skojarzone interfejsy, następuje szczegółowe informacje o tych interfejsów.  
  
## <a name="language-engine"></a>Aparat języka  
 Zapewnia aparat języka:  
  
- Język przeanalizowania i wykonania.  
  
- Obsługa debugowania (punkty przerwania i tak dalej).  
  
- Obliczanie wyrażenia.  
  
- Kolorowanie składni.  
  
- Obiekt, przeglądania.  
  
- Wyliczenie stosu i analizy.  
  
  Poniżej przedstawiono interfejsy, które aparat skryptu musi obsługiwać zapewnienie debugowania, Obliczanie wyrażenia i przeglądania obiektów. Te interfejsy są używane przez aplikację hosta do mapowania miedzy kontekst dokumentu i konteksty kodu aparatu, również przez debuger interfejsu użytkownika w celu oceny wyrażenia stosu wyliczenie oraz obiekt przeglądania.  
  
  [IActiveScriptDebug, interfejs](../winscript/reference/iactivescriptdebug-interface.md)  
  Zawiera wyliczenie kontekstu składni kolorowanie i kod.  
  
  [IActiveScriptErrorDebug, interfejs](../winscript/reference/iactivescripterrordebug-interface.md)  
  Zwraca dokumentu kontekstów oraz ramek stosu błędów.  
  
  [IActiveScriptSiteDebug, interfejs](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Hostowanie podany link z aparatu skryptów do debugera.  
  
  [IDebugCodeContext, interfejs](../winscript/reference/idebugcodecontext-interface.md)  
  Zawiera wirtualny "wskaźnik instrukcji" w wątku.  
  
  [IEnumDebugCodeContexts, interfejs](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Wylicza kontekstów kodu, które odnoszą się do kontekstu dokumentu.  
  
  [IDebugStackFrame, interfejs](../winscript/reference/idebugstackframe-interface.md)  
  Reprezentuje ramkę stosu logicznych na stosie wątku.  
  
  [IDebugExpressionContext, interfejs](../winscript/reference/idebugexpressioncontext-interface.md)  
  Udostępnia kontekst, w którym mogą być obliczane wyrażenia.  
  
  [IDebugStackFrameSniffer, interfejs](../winscript/reference/idebugstackframesniffer-interface.md)  
  Umożliwia wyliczenie ramek stosu logiczne.  
  
  [IDebugExpression, interfejs](../winscript/reference/idebugexpression-interface.md)  
  Reprezentuje asynchronicznie obliczane wyrażenie.  
  
  [IDebugSyncOperation, interfejs](../winscript/reference/idebugsyncoperation-interface.md)  
  Umożliwia aparat skryptów tworzących warstwę abstrakcji operacji, która musi zostać wykonana podczas zagnieżdżonego w określonym wątku zablokowane.  
  
  [IDebugAsyncOperation, interfejs](../winscript/reference/idebugasyncoperation-interface.md)  
  Udostępnia asynchronicznych operacji synchronicznych debugowania.  
  
  [IDebugAsyncOperationCallBack, interfejs](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Dostępne są zdarzenia stanu związane z postęp `IDebugAsyncOperation` interfejsu oceny.  
  
  [IEnumDebugExpressionContexts, interfejs](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Wylicza zbiór `IDebugExpressionContexts` obiektów.  
  
  [IProvideExpressionContexts, interfejs](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Zapewnia sposób wyliczyć kontekstów wyrażenie znane niektórych składników.  
  
  [IDebugFormatter, interfejs](../winscript/reference/idebugformatter-interface.md)  
  Umożliwia języka lub środowiska IDE, aby dostosować konwersji między wariant wartości lub typami VARTYPE i ciągów.  
  
  [IDebugStackFrameSnifferEx, interfejs](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Wylicza ramki stosu logicznych dla menedżerów PDM.  
  
## <a name="hosts"></a>Hosts  
 Host:  
  
- Obsługuje aparaty języka.  
  
- Udostępnia model obiektu (zestaw obiektów, które umożliwia pisanie skryptów).  
  
- Definiuje drzewa dokumentów, które mogą być debugowane i ich zawartość.  
  
- Organizuje skrypty w aplikacji wirtualnych.  
  
  Istnieją dwa rodzaje hostów:  
  
- Bez host obsługuje tylko podstawowe interfejsy usługi wykonywanie aktywnych skryptów. Go nie ma kontroli nad struktury dokumentu lub organizacji; jest to ustalane wyłącznie przez skrypty do silników języka.  
  
- Jest host inteligentny obsługuje większy zbiór interfejsów, który umożliwia definiowanie drzewa dokumentu, zawartość dokumentu i kolorowanie składni. Istnieje zestaw interfejsów pomocnika, opisane w podsekcji, które znacznie ułatwić hosta jako hosta inteligentnego.  
  
### <a name="smart-host-helper-interfaces"></a>Interfejsy pomocnika inteligentnych hosta  
 `IDebugDocumentHelper` Metod zapewnia znacznie uproszczonym zestawem interfejsów hosta może być korzyści w zakresie obsługi inteligentnej bez pełnej złożoność (i zasilania) interfejsów pełną hosta.  
  
 Host nie jest wymagany do użycia tych interfejsów, oczywiście. Jednak za pomocą tych interfejsów można uniknąć wdrażania lub za pomocą wielu interfejsach bardziej skomplikowane.  
  
 [IDebugDocumentHelper, interfejs](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementowany przez program PDM i zawiera implementacje dla wielu interfejsów wymaganych do hostowania inteligentnych.  
  
 [IDebugDocumentHost, interfejs](../winscript/reference/idebugdocumenthost-interface.md)  
 Zaimplementowane (opcjonalnie) przez hosta w celu udostępnienia funkcji specyficznych dla hosta, takich jak kolorowania do debugera.  
  
 Aby uzyskać więcej informacji, zobacz [implementacja interfejsów pomocnika hosta inteligentnego](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Interfejsy inteligentnych hosta  
 Poniżej jest pełną zbiór interfejsów, które hostem inteligentnych musi implementować lub, jeśli nie używa interfejsów pomocnika.  
  
 Interfejsy implementowane przez hosta:  
  
 [IDebugDocumentInfo, interfejs](../winscript/reference/idebugdocumentinfo-interface.md)  
 Zawiera informacje dotyczące dokumentów, które mogą lub nie można utworzyć wystąpienia.  
  
 [IDebugDocumentProvider, interfejs](../winscript/reference/idebugdocumentprovider-interface.md)  
 Zapewnia metodę dla wystąpienia dokumentu na żądanie.  
  
 [IDebugDocument, interfejs](../winscript/reference/idebugdocument-interface.md)  
 Podstawowy interfejs dla wszystkich dokumentów debugowania.  
  
 [IDebugDocumentText, interfejs](../winscript/reference/idebugdocumenttext-interface.md)  
 Zapewnia dostęp do wersji tylko do tekstu dokumentu debugowania.  
  
 [IDebugDocumentTextAuthor, interfejs](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Umożliwia edycję wersji tylko do tekstu dokumentu debugowania.  
  
 [IDebugDocumentContext, interfejs](../winscript/reference/idebugdocumentcontext-interface.md)  
 Udostępnia abstrakcyjną reprezentację w postaci części dokumentu debugowane.  
  
 Interfejsy implementowane przez program PDM w imieniu hosta:  
  
 [IDebugApplicationNode, interfejs](../winscript/reference/idebugapplicationnode-interface.md)  
 Rozszerza funkcjonalność `IDebugDocumentProvider` interfejs, dostarczając kontekstu w drzewie projektu.  
  
## <a name="debugger-ide"></a>Debuger środowiska IDE  
 Środowisko IDE jest niezależny od języka debugowania interfejsu użytkownika. Oferuje ono:  
  
- Osoby przeglądające dokumentu/edytorów.  
  
- Zarządzanie punktu przerwania.  
  
- Wyrażenie oceny i obejrzyj systemu windows.  
  
- Stosu, przeglądanie ramki.  
  
- / Klasę obiektu przeglądania.  
  
- Przeglądanie struktury aplikacji wirtualnej.  
  
  Interfejsy implementowane przez debugera:  
  
  [IApplicationDebugger, interfejs](../winscript/reference/iapplicationdebugger-interface.md)  
  Podstawowy interfejs narażona jest debugera sesji IDE.  
  
  [IApplicationDebuggerUI, interfejs](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Zawiera składnik zewnętrzny większą kontrolę nad interfejsu użytkownika (UI) debugera.  
  
  [IDebugExpressionCallBack, interfejs](../winscript/reference/idebugexpressioncallback-interface.md)  
  Dostępne są zdarzenia stanu dla `IDebugExpression` postępu oceny.  
  
  [IDebugDocumentTextEvents, interfejs](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Dostępne są zdarzenia wskazujące zmiany w dokumencie tekstu.  
  
  [IDebugApplicationNodeEvents, interfejs](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Udostępnia interfejs zdarzenia dla `IDebugApplicationNode` interfejsu.  
  
### <a name="machine-debug-manager"></a>Menedżer debugowania maszyny  
 Menedżer debugowania maszyny zapewnia punkt obsługi pomiędzy aplikacjami wirtualnymi i debugery za utrzymanie i wyliczania listę aktywnych aplikacji wirtualnej.  
  
 [IDebugSessionProvider, interfejs](../winscript/reference/idebugsessionprovider-interface.md)  
 Ustanawia sesję debugowania dla działającej aplikacji.  
  
 [IMachineDebugManager, interfejs](../winscript/reference/imachinedebugmanager-interface.md)  
 Podstawowy interfejs Menedżer debugowania maszyny.  
  
 [IMachineDebugManagerCookie, interfejs](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Podobnie jak `IMachineDebugManager` interfejs, ale ten interfejs obsługuje pliki cookie z debugowania.  
  
 [IMachineDebugManagerEvents, interfejs](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Sygnalizuje zmiany uruchomione listy aplikacji obsługiwane przez Menedżer debugowania maszyny.  
  
 [IEnumRemoteDebugApplications, interfejs](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Wylicza uruchomionych aplikacji na komputerze.  
  
### <a name="process-debug-manager"></a>Menedżer debugowania procesów  
 Program PDM wykonuje następujące czynności:  
  
- Synchronizuje debugowania wielu aparatów języka.  
  
- Przechowuje drzewa debugowania dokumentów.  
  
- Scala ramek stosu.  
  
- Współrzędne punktów przerwania i Krokowe przechodzenie między aparatami języka.  
  
- Śledzi wątków.  
  
- Przechowuje wątku debugera w celu asynchronicznego przetwarzania.  
  
- Komunikuje się z menedżerem debugowania maszyny i debuger środowiska IDE.  
  
  Poniżej przedstawiono interfejsów zapewnianych przez Menedżer debugowania procesów.  
  
  [IProcessDebugManager, interfejs](../winscript/reference/iprocessdebugmanager-interface.md)  
  Podstawowy interfejs Menedżer debugowania procesów. Ten interfejs może utworzyć, Dodaj lub Usuń aplikację wirtualną z procesu.  
  
  [IRemoteDebugApplication, interfejs](../winscript/reference/iremotedebugapplication-interface.md)  
  Reprezentuje uruchomionej aplikacji.  
  
  [IDebugApplication, interfejs](../winscript/reference/idebugapplication-interface.md)  
  Przedstawia bez możliwości obsługi zdalnej metody debugowania do użytku przez język aparatów i hosty.  
  
  [IRemoteDebugApplicationThread, interfejs](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Reprezentuje wątek wykonywania w obrębie określonej aplikacji.  
  
  [IDebugApplicationThread, interfejs](../winscript/reference/idebugapplicationthread-interface.md)  
  Umożliwia aparatów języka i hostów, aby zapewnić synchronizacji wątków i obsługiwać informacje właściwe dla wątków, stan debugowania.  
  
  [IEnumRemoteDebugApplicationThreads, interfejs](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Wylicza uruchomionych wątków w aplikacji.  
  
  [IDebugThreadCall, interfejs](../winscript/reference/idebugthreadcall-interface.md)  
  Międzyprocesowe wysyłki.  
  
  [IDebugApplicationNode, interfejs](../winscript/reference/idebugapplicationnode-interface.md)  
  Przechowuje pozycji do danego dokumentu w hierarchii.  
  
  [IEnumDebugApplicationNodes, interfejs](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Wylicza węzłów podrzędnych węzła skojarzone z aplikacją.  
  
  [IEnumDebugStackFrames, interfejs](../winscript/reference/ienumdebugstackframes-interface.md)  
  Wylicza ramki stosu, odpowiadający wątku scalone z silników.  
  
  [IDebugCookie, interfejs](../winscript/reference/idebugcookie-interface.md)  
  Umożliwia cookie debugowania w skrypcie debugery.  
  
  [IDebugHelper, interfejs](../winscript/reference/idebughelper-interface.md)  
  Służy jako fabrykę dla obiektu przeglądarek i punkty połączenia proste aparatów skryptu.  
  
  [ISimpleConnectionPoint, interfejs](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Zapewnia prostą metodę do opisu i wyliczania zdarzenia wywoływane punktu określonego połączenia dla aparatów skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugera aktywnego skryptu](../winscript/reference/active-script-debugger-interfaces.md)
