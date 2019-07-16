---
title: Podstawowe interfejsy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94703f13eba0c58aad24597bc65beeea862e79e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179215"
---
# <a name="core-interfaces"></a>Interfejsy podstawowe
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Następujące interfejsy są interfejsy podstawowe rozszerzania debugera za pomocą [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Dyskusja  
 Te interfejsy są głównie używane do tworzenia aparatu debugowania (DE). Są tu zorganizowane według kategorii:  
  
- [Punkty przerwania](#Breakpoints)  
  
- [Konteksty](#Contexts)  
  
- [W trybie Server Core](#CoreServer)  
  
- [Aparaty debugowania](#DebugEngines)  
  
- [Dokumenty](#Documents)  
  
- [Zdarzenia](#Events)  
  
- [Wyrażenia](#Expressions)  
  
- [Pamięć](#Memory)  
  
- [Moduły](#Modules)  
  
- [Porty](#Ports)  
  
- [Procesy](#Processes)  
  
- [Programy](#Programs)  
  
- [Właściwości](#Properties)  
  
- [Ramki stosu](#StackFrames)  
  
- [Wątki](#Threads)  
  
- [Wizualizatorów typu](#TypeVisualizers)  
  
  Jednostki, które mogą implementować interfejsy są:  
  
- Debugowanie aparatu (DE)  
  
- Dostawcy portu (PS)  
  
- Ewaluator wyrażeń (EE)  
  
- Visual Studio (VS)  
  
## <a name="Breakpoints"></a> Punkty przerwania  
 Te interfejsy są ze sobą powiązane do implementacji i śledzenie punktów przerwania.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Przedstawia punkt przerwania, powiązane z lokalizacją pamięci.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania jest powiązana z lokalizacji w pamięci.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Reprezentuje dokument sumy kontrolnej dla żądania punktu przerwania.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wysyłany przez DE, gdy punkt przerwania nie może być powiązane z lokalizacji w pamięci.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Wysyłane przez DE, po osiągnięciu punktu przerwania.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Reprezentuje żądanie dla punktu przerwania; używany podczas tworzenia oczekujący punkt przerwania.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Reprezentuje żądanie dla punktu przerwania; używany podczas tworzenia oczekujący punkt przerwania.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Reprezentuje informacje używane do powiązania punktu przerwania.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Wysyłany przez DE, gdy punkt przerwania jest niezwiązany z lokalizacji w pamięci.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Reprezentuje nieprawidłowy punkt przerwania (zwrócone przez `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Reprezentuje informacje rozwiązania dotyczące nieprawidłowy punkt przerwania.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Reprezentuje pozycji w funkcji, w którym ustawiono punkt przerwania.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Reprezentuje punkt przerwania, który ma zostać powiązany; używany podczas tworzenia powiązany punkt przerwania.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Reprezentuje wyliczenie dla zestawu powiązanych punktów przerwania.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Reprezentuje wyliczenia w zestawie punktów przerwania, których nie można powiązać lokalizacji w pamięci.|  
  
## <a name="Contexts"></a> Konteksty  
 Te interfejsy reprezentują różne rodzaje kontekstów w ramach debugowanego programu.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Reprezentuje pozycję początkową instrukcji kodu.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozszerza [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu, aby umożliwić pobieranie interfejsy modułu i procesu.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, NIEMCY|Reprezentuje pozycji w dokumencie.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst w którym można obliczyć wartości wyrażenia.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje początkową lokalizację w pamięci w procentach kolekcja bajtów.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst ramki stosu w punkt przerwania lub wyjątku.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje kontekst ramki stosu w punkt przerwania lub wyjątku.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Reprezentuje wyliczenia w zestawie kontekstów kodu.|  
  
## <a name="CoreServer"></a> W trybie Server Core  
 Te interfejsy reprezentują maszyny, na którym jest debugowany program. Są one zaimplementowane przez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , ale może być wywoływany do przez aparaty debugowania.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Zapewnia dostęp do portów i dostawcy portów, a także informacje o komputerze.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Reprezentuje [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , która obsługuje zdalne debugowanie.|  
  
## <a name="DebugEngines"></a> Aparaty debugowania  
 Te interfejsy reprezentują silniki debugowania i ich skojarzone zdarzenia.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Reprezentuje niestandardowego aparatu debugowania.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Reprezentuje niestandardowego aparatu debugowania obsługujący ładowania symboli, JustMyCode i wyjątki.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wysyłane przez każde nowe wystąpienie DE, aby wskazać, że jest gotowy do obsługi zadań debugowania.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Reprezentuje niestandardowego aparatu debugowania obsługującego uruchamiania programów.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje węzeł program, który obsługuje wielu aparatów debugowania.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Zapewnia sposób SDM można uzyskać interfejsu do aparatu debugowania z wątku, programu lub ramki stosu.|  
  
## <a name="Documents"></a> Dokumenty  
 Te interfejsy reprezentują dokumenty (pliki źródłowe) i skojarzonych z nimi elementów.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wysyłane przez DE, żądanie dokumentu do otwarcia.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Przedstawia strumień dezasemblowany instrukcje z dokumentu.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, NIEMCY|Reprezentuje dokument, dostarczone przez DE, określając nazwę i identyfikator klasy (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Reprezentuje sumy kontrolnej dla dokumentu debugowania i umożliwia przekazanie sumę kontrolną między składnikami.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, NIEMCY|Reprezentuje kontekst dokumentu, położenie w obrębie dokumentu odpowiadający szczególnym kontekście instrukcji i kod.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, NIEMCY|Reprezentuje pozycję Ogólne w dokumencie.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Reprezentuje pozycji w pliku źródłowym jako przesunięcie znaku.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, NIEMCY|Reprezentuje dokument tekstowy, dostarczone przez DE (pochodną [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), podając faktycznego tekstu.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wysyłane przez DE, aby określić zmiany w pliku źródłowego, który znajduje się w pamięci.|  
  
## <a name="Events"></a> Zdarzenia  
 Te interfejsy reprezentują wszystkie zdarzenia, które są przesyłane między DE i Menedżer debugowania sesji (SDM).  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wysyłane przez DE, żądanie dokumentu do otwarcia.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Aparat debugowania (DE) wysyła ten interfejs Menedżer debugowania sesji (SDM), aby ustawić stan paska komunikatów podczas ładowania symboli.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Wysyłane przez DE podziału w programie zostało ukończone.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania jest powiązana.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania nie powiodło się z oświadczeniem.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Wysyłane przez DE, po osiągnięciu punktu przerwania.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Punkt przerwania jest niepowiązanych wysyłane przez DE.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Wysyłane przez DE, aby określić, czy ma zostać zatrzymana w danej lokalizacji.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wysyłane przez DE, aby określić zmiany w pliku źródłowego, który znajduje się w pamięci.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wysyłane przez każde nowe wystąpienie DE, aby wskazać, że jest gotowy do obsługi zadań debugowania.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Wysyłane przez DE, aby wskazać, że program debugowany jest gotowy do wykonania pierwszej instrukcji.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Interfejs, który jest używany przez inne interfejsy zdarzeń, które mogą zwracać błąd, aby zapewnić komunikaty o błędach czytelny dla człowieka.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Interfejs podstawowy, w której wszystkie inne zdarzenie interfejsy są pochodną.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Reprezentuje interfejs implementowany przez SDM, do którego są wysyłane zdarzenia (wyrażone jako obiekty implementującej interfejs określonego zdarzenia).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Wystąpił wyjątek w aktualnie debugowanego wysyłane przez DE.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wysyłane przez DE, po zakończeniu Obliczanie wyrażenia asynchroniczne.|  
|IDebugFindSymbolEvent2||OBSOLETE. NIE NALEŻY UŻYWAĆ.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Wysyłane przez DE przetwarzanie, dla wyjątku przechwycone zostało ukończone.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Wysyłane przez DE, gdy program zakończy ładowanie.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Wysyłane przez DE wyświetlone IDE komunikat informacyjny dla użytkownika.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wysyłany, DE, gdy moduł jest załadowany lub zwolnione.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Sygnały [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugera interfejsu użytkownika, aby ostrzec użytkownika, że symbole nie można zlokalizować dla uruchomionego pliku wykonywalnego.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Wysyłany przez DE wyświetlone IDE dowolny ciąg.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, NIEMCY|Wysyłane przez port do komunikowania się zdarzenia portu dla dowolnego odbiornika.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wysyłane przez port lub DE, po utworzeniu procesu.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Proces został zniszczony wysyłane przez port lub Niemcy.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wysyłane przez DE lub port, gdy program został utworzony.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Program został zniszczony wysyłane przez port lub Niemcy.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Umożliwia to aparat debugowania zastąpić domyślne zachowanie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfejsu użytkownika podczas kończenia sesji debugowania.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Wysyłane z aparatu debugowania (DE) do Menedżer debugowania sesji (SDM) po zmianie nazwy programu.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wysyłany przez DE, gdy nowa właściwość (reprezentowane przez `IDebugProperty2` interfejsu) został utworzony.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Wysyłane przez DE właściwość została zniszczona.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Wysyłane przez DE przy przechodzeniu z lub funkcji, więc zwracana wartość może być poprawnie wyświetlane.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Włącza debugowanie aparatów odczytać ustawienia metryki zdalnie.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Wysyłane przez DE, po ukończeniu kroku do, nad lub poza instrukcję.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Wysyłany przez DE do wskazania powodzenia lub niepowodzenia ładowania symboli dla modułu.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wysyłane przez DE, po utworzeniu wątku.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wysyłane przez DE wątku została zniszczona.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wysyłane przez DE, gdy wątek zmieniono jego nazwę.|  
  
## <a name="Expressions"></a> Wyrażenia  
 Te interfejsy reprezentują wyrażenia, które mogło zostać ocenione w szczególnym kontekście.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Reprezentuje wyrażenie do obliczenia. Uzyskany z [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst, w którym wyrażenie jest obliczane. Uzyskany z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wysyłane przez DE, po zakończeniu Obliczanie wyrażenia asynchroniczne.|  
  
## <a name="Memory"></a> Pamięć  
 Te interfejsy reprezentują sekwencje bajtów w pamięci.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Reprezentuje sekwencję bajtów w pamięci, który może odczytać lub zapisywane.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje lokalizację w pamięci sekwencji bajtów.|  
  
## <a name="Modules"></a> Moduły  
 Te interfejsy reprezentują moduł, który odnosi się do pliku wykonywalnego lub. Plik DLL.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Reprezentuje pojedynczy plik wykonywalny lub bibliotekę DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Reprezentuje [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , która obsługuje symboli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wysyłany, DE, gdy moduł jest załadowany lub zwolnione.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Reprezentuje informacji o serwerze źródłowym, który jest zawarty w pliku PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Reprezentuje wyliczenia w zestawie modułów, które są znane przez [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
## <a name="Ports"></a> Porty  
 Te interfejsy reprezentują portów i dostawcy portów.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Reprezentuje domyślny port na komputerze lokalnym.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Umożliwia to aparat debugowania, który używa modelu DCOM poprosić [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfejsu użytkownika, aby upewnić się, że Zapora nie blokuje debugowanie zdalne.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Reprezentuje port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Wysyłane przez port do komunikowania się zdarzenia portu dla dowolnego odbiornika.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Reprezentuje port, który można uruchomić, a następnie Zakończ działanie procesów.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Umożliwia rejestrowanie i wyrejestrowywanie programy z portem; zezwala na użycie portu do śledzenia aktualnie debugowanych programów.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Reprezentuje dostosowanego interfejsu użytkownika dotyczące wybierania portu.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Reprezentuje żądanie dla portu, z którego zostanie utworzony lub znajduje się nowy port.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Reprezentuje dostawcę portów.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Reprezentuje dostawcę portów, które można utrwalić (Zapisz na dysku) informacji na temat portów on utworzony.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Włącza [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfejsu użytkownika, aby wyświetlić tekst wewnątrz **transportowania informacji** części **dołączyć do procesu** okno dialogowe.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Zezwala na wykonanie zapytania dotyczącego informacji o komputerze docelowym.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Reprezentuje wyliczenie za pośrednictwem zestawu portów.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Reprezentuje wyliczenie zestawu dostawcy portów.|  
  
## <a name="Processes"></a> Procesy  
 Te interfejsy reprezentują procesów, pojedynczy plik wykonywalny, który zawiera jeden lub więcej programów.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Reprezentuje proces, który jest uruchomiony na komputerze.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Reprezentuje proces, który obsługuje aktywnego debugowania (użyć w celu zastąpienia krok, kontynuować i wykonywanie metod na [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wysyłane przez port lub DE, po utworzeniu procesu.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Proces został zniszczony wysyłane przez port lub Niemcy.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Reprezentuje proces, który musi śledzić sesji, który jest dołączony do niego.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Reprezentuje wyliczenie zestaw procesów na porcie.|  
  
## <a name="Programs"></a> Programy  
 Te interfejsy reprezentują programów, jednostki logiczne wykonywania, które nie muszą odpowiadać fizycznego pliku wykonywalnego lub modułu.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , które musi działać w połączeniu z innymi programami debugowany w tym samym czasie.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Reprezentuje jednostkę logiczną wykonywania.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wysyłane przez DE lub port, gdy program został utworzony.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Program został zniszczony wysyłane przez port lub Niemcy.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) mogą być obsługiwane przez wiele aparaty debugowania.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , musi mieć możliwość śledzenia sesji, który jest dołączony do niego.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , może zwrócić informacje na temat procesu, w którym jest uruchomiony.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Reprezentuje program, który może być debugowany.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Umożliwia węzła program otrzymywać powiadomienia o próba dołączenia do skojarzonego programu.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Zapewnia sposób SDM DE dotyczące jej programów w wartości clientauthtrustmode DE tej kwerendy.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Używane przez DEs, aby zarejestrować programy za pomocą SDM, aby pokazać, że są debugowane.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Reprezentuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) może kierować element interfejsów granice wątku lub procesu.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Reprezentuje wyliczenie zestawu programów.|  
  
## <a name="Properties"></a> Właściwości  
 Te interfejsy reprezentuje właściwości i wartość skojarzoną z określonym kontekstem, zazwyczaj wynikiem oceny wyrażenia.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Reprezentuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , można wyświetlić jego wartość w niestandardowy sposób.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Reprezentuje wartość ramkę stosu, dokumentu lub wynik obliczania wyrażenia.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Reprezentuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , która obsługuje arbitralnie długie ciągi.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wysyłany przez DE, gdy nowa właściwość (reprezentowane przez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu) został utworzony.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Wysyłane przez DE właściwość została zniszczona.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Reprezentuje odwołanie do właściwości, która może znajdować się poza wszystkie ramki określonego stosu.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Reprezentuje wyliczenie za pośrednictwem zestawu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur, które opisują zmiennych, rejestry, parametry i wyrażenia.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Reprezentuje wyliczenie za pośrednictwem zestawu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.|  
  
## <a name="StackFrames"></a> Ramki stosu  
 Te interfejsy reprezentuje ramkę stosu, kontekst, w której punkt przerwania lub wyjątek wystąpił.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst, w której punkt przerwania lub wyjątek wystąpił.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) który może obsługiwać przechwycone wyjątki.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Reprezentuje wyliczenie zestawu [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) struktur, które określają funkcja wywołania sekwencja używana do osiągnięcia ramki określonego stosu.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Reprezentuje wyliczenie za pośrednictwem zestawu [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktur, które opisują ramki stosu.|  
  
## <a name="Threads"></a> Wątki  
 Te interfejsy reprezentują wątków i ich skojarzone zdarzenia.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Reprezentuje wykonanie wątku.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wysyłane przez DE, po utworzeniu wątku.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wysyłane przez DE wątku została zniszczona.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wysyłane przez DE, gdy wątek zmieniono jego nazwę.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Reprezentuje wyliczenia w zestawie wątków.|  
  
## <a name="TypeVisualizers"></a> Wizualizatorów typu  
 Interfejsy te zapewniają obsługę wizualizatorów typu. Te interfejsy są zazwyczaj implementowane przez ewaluatora wyrażeń.  
  
|Interface|Zaimplementowane przez|Opis|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Reprezentuje tablicę bajtów, które mają zostać wyświetlone Wizualizator typów.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Udostępnia metody w celu uzyskania dostępu do danych, które zostaną przekazane do Wizualizator typów.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Reprezentuje właściwość, która zapewnia dostęp do [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Tworzenie niestandardowego aparatu debugowania](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
