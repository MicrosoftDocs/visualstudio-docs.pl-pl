---
title: Interfejsy podstawowe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737579"
---
# <a name="core-interfaces"></a>Interfejsy podstawowe
Następujące interfejsy są podstawowymi interfejsami do rozszerzania debugera za pomocą [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Dyskusja
 Te interfejsy są używane głównie do tworzenia aparatu debugowania (DE). Są one zorganizowane w tym miejscu według kategorii:

- [Punkty przerwania](#Breakpoints)

- [Konteksty](#Contexts)

- [Serwer podstawowy](#CoreServer)

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

- [Wizualizatory typów](#TypeVisualizers)

  Jednostki, które mogą implementować interfejsy są:

- Aparat debugowania (Niemcy)

- Dostawca portu (PS)

- Ewaluatora wyrażeń (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Punkty przerwania
 Te interfejsy są powiązane z implementacją i śledzeniem punktów przerwania.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Reprezentuje punkt przerwania powiązany z lokalizacją w pamięci.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wysyłany przez DE, gdy punkt przerwania jest powiązany z lokalizacją w pamięci.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Przedstawia sumę kontrolną dokumentu dla żądania punktu przerwania.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wysyłany przez DE, gdy punkt przerwania nie może zostać powiązany z lokalizacją w pamięci.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Wysyłany przez chwilę po osiągnięciu punktu przerwania.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Reprezentuje żądanie dla punktu przerwania; używane podczas tworzenia oczekującego punktu przerwania.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Reprezentuje żądanie dla punktu przerwania; używane podczas tworzenia oczekującego punktu przerwania.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Reprezentuje informacje używane do powiązania punktu przerwania.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Wysyłany przez DE, gdy punkt przerwania jest niepowiązany z lokalizacji pamięci.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Reprezentuje nieprawidłowy punkt przerwania (zwracany przez `IDebugBreakpointErrorEvent2` ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Reprezentuje informacje o rozdzielczości dotyczące nieprawidłowego punktu przerwania.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Reprezentuje pozycję w funkcji, w której jest ustawiony punkt przerwania.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Reprezentuje punkt przerwania, który ma zostać powiązany; używane podczas tworzenia powiązanego punktu przerwania.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Reprezentuje Wyliczenie w zestawie powiązanych punktów przerwania.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Reprezentuje Wyliczenie na zestawie punktów przerwania, które nie mogły być powiązane z lokalizacją w pamięci.|

## <a name="contexts"></a><a name="Contexts"></a> Sytuacjach
 Te interfejsy reprezentują różne rodzaje kontekstów w debugowanym programie.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Reprezentuje pozycję początkową instrukcji kodu.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozszerza interfejs [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , aby umożliwić pobieranie interfejsów modułu i procesów.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|A, DE|Reprezentuje pozycję w dokumencie.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst, w którym ma zostać obliczone wyrażenie.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje lokalizację początkową w pamięci kolekcji bajtów.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Reprezentuje Wyliczenie na zestawie kontekstów kodu.|

## <a name="core-server"></a><a name="CoreServer"></a> Serwer podstawowy
 Te interfejsy reprezentują maszynę, na której jest debugowany program. Są one implementowane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] program, ale mogą być wywoływane przez aparaty debugowania.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Zapewnia dostęp do portów i dostawców portów oraz informacje o komputerze.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Reprezentuje element [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , który obsługuje debugowanie zdalne.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Aparaty debugowania
 Te interfejsy reprezentują aparaty debugowania i powiązane z nimi zdarzenia.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Reprezentuje niestandardowy aparat debugowania.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Reprezentuje niestandardowy aparat debugowania obsługujący ładowanie symboli, JustMyCode i wyjątków.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wysyłany przez każde nowe wystąpienie elementu DE, aby wskazać, że jest gotowy do obsługi zadań debugowania.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Reprezentuje niestandardowy aparat debugowania, który obsługuje uruchamianie programów.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje węzeł programu obsługujący wiele aparatów debugowania.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Umożliwia modelowi SDM uzyskanie interfejsu do aparatu debugowania z wątku, programu lub ramki stosu.|

## <a name="documents"></a><a name="Documents"></a> Secret
 Te interfejsy reprezentują dokumenty (pliki źródłowe) i ich skojarzone elementy.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wysyłany przez Anuluj do żądania otwarcia dokumentu.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Reprezentuje strumień rozmieszczonych instrukcji z dokumentu.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|A, DE|Reprezentuje dokument dostarczony przez DE, określając nazwę i identyfikator klasy (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Reprezentuje sumę kontrolną dla dokumentu debugowania i umożliwia przekazywanie sum kontrolnych między składnikami.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|A, DE|Reprezentuje kontekst dokumentu, położenie w obrębie dokumentu odpowiadającego określonej instrukcji i kontekstowi kodu.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|A, DE|Reprezentuje pozycję ogólną w dokumencie.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Reprezentuje pozycję w pliku źródłowym jako przesunięcie znaku.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|A, DE|Reprezentuje dokument tekstowy dostarczony przez DE (pochodna from [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), dostarczając rzeczywisty tekst.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wysyłany przez DE, aby określić zmiany w pliku źródłowym, który znajduje się w pamięci.|

## <a name="events"></a><a name="Events"></a> Wydarzeniach
 Te interfejsy reprezentują wszystkie zdarzenia, które są wysyłane między programem a i menedżerem debugowania sesji (SDM).

| Interfejs | Zaimplementowane przez | Opis |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Wysyłany przez Anuluj do żądania otwarcia dokumentu. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Aparat debugowania (DE) wysyła ten interfejs do Menedżera debugowania sesji (SDM), aby ustawić komunikat paska stanu podczas ładowania symboli. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Wysyłany przez DE, gdy przerwa w programie został ukończony. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Wysyłany przez DE, gdy punkt przerwania jest powiązany. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Wysyłany przez DE, gdy punkt przerwania nie może być powiązany. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Wysyłany przez chwilę po osiągnięciu punktu przerwania. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Wysyłany przez DE, gdy punkt przerwania jest niepowiązany. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Wysyłany przez DE do ustalenia, czy powinien zostać zatrzymany w określonej lokalizacji. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Wysyłany przez DE, aby określić zmiany w pliku źródłowym, który znajduje się w pamięci. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Wysyłany przez każde nowe wystąpienie elementu DE, aby wskazać, że jest gotowy do obsługi zadań debugowania. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Wysyłany przez DE do wskazuje, że debugowany program jest gotowy do wykonania pierwszej instrukcji. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interfejs, który jest używany przez inne interfejsy zdarzeń, które może zwrócić błąd, aby zapewnić wiadomości o błędach, które można odczytać przez człowieka. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interfejs podstawowy, z którego pochodzą wszystkie inne interfejsy zdarzeń. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Reprezentuje interfejs zaimplementowany przez model SDM, do którego są wysyłane zdarzenia (wyrażone jako obiekty implementujące określony interfejs zdarzenia). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Wysyłany przez DE, gdy wystąpił wyjątek w debugowanym programie. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Wysyłany przez DE, gdy szacowanie wyrażeń asynchronicznych zostało zakończone. |
| IDebugFindSymbolEvent2 | | Zbędn. NIE NALEŻY UŻYWAĆ. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Wysyłany przez DE, gdy przetwarzanie dla nieprzechwyconego wyjątku zostało zakończone. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Wysyłany przez DE, gdy program zakończył ładowanie. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Wysyłany przez element DE do, aby IDE wyświetlał komunikat informacyjny dla użytkownika. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Wysyłany przez DE, gdy moduł jest ładowany lub zwolniony. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Informuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika debugera, aby ostrzec użytkownika o tym, że nie można zlokalizować symboli dla uruchomionego pliku wykonywalnego. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Wysyłany przez DE do, aby IDE wyświetlał dowolny ciąg. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | A, DE | Wysyłany przez port do przekazywania zdarzeń portów do dowolnego odbiornika. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Wysyłany przez DE lub port, gdy proces został utworzony. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Wysyłany przez DE lub port, gdy proces został zniszczony. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Wysyłany przez DE lub port, gdy program został utworzony. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Wysyłany przez DE lub port, gdy program został zniszczony. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Umożliwia aparatowi debugowania przesłonięcie domyślnego zachowania [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika po zakończeniu sesji debugowania. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Wysyłany z aparatu debugowania (poza) do Menedżera debugowania sesji (SDM), gdy zmienia się nazwa programu. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Wysyłany przez DE po utworzeniu nowej właściwości (reprezentowanej przez `IDebugProperty2` interfejs). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Wysyłany przez DE, gdy właściwość została zniszczona. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Wysyłany przez DE podczas wykonywania kroku lub nad funkcją, aby można było poprawnie wyświetlić wartość zwracaną. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Umożliwia aparatom debugowania zdalne odczytywanie ustawień metryki. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Wysyłany przez DE, gdy krok do, przekroczenia lub z instrukcji został ukończony. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Wysyłany przez DE do wskazywania sukcesu lub niepowodzenia ładowania symboli dla modułu. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Wysyłany przez DE po utworzeniu wątku. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Wysyłany przez DE, gdy wątek został zniszczony. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Wysyłany przez DE, gdy wątek zmienił swoją nazwę. |

## <a name="expressions"></a><a name="Expressions"></a> Wyrażeń
 Te interfejsy reprezentują wyrażenia, które mają być oceniane w określonym kontekście.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Reprezentuje wyrażenie, które ma zostać obliczone. Uzyskany z interfejsu [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst, w którym jest oceniane wyrażenie. Uzyskany z interfejsu [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wysyłany przez DE, gdy szacowanie wyrażeń asynchronicznych zostało zakończone.|

## <a name="memory"></a><a name="Memory"></a> Rozmiar
 Te interfejsy reprezentują sekwencje bajtów w pamięci.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Reprezentuje sekwencję bajtów w pamięci, która może być odczytywana lub zapisywana.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje lokalizację w pamięci sekwencji bajtów.|

## <a name="modules"></a><a name="Modules"></a> Moduły
 Te interfejsy reprezentują moduł, który odnosi się do pliku wykonywalnego lub. Plik DLL.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Reprezentuje pojedynczy plik wykonywalny lub DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Reprezentuje element [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , który obsługuje symbole.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wysyłany przez DE, gdy moduł jest ładowany lub zwolniony.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Reprezentuje informacje o serwerze źródłowym, które znajdują się w pliku PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Reprezentuje Wyliczenie na zestawie modułów, które są znane przez [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a> Np
 Te interfejsy reprezentują portów i dostawców portów.

| Interfejs | Zaimplementowane przez | Opis |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | A, PS | Reprezentuje domyślny port na komputerze lokalnym. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Umożliwia aparatowi debugowania korzystającemu z modelu DCOM zaproszenie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika, aby upewnić się, że Zapora nie blokuje zdalnego debugowania. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | A, PS | Reprezentuje port. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Wysyłany przez port do przekazywania zdarzeń portów do dowolnego odbiornika. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Reprezentuje port, który może uruchamiać i kończyć procesy. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Służy do rejestrowania i wyrejestrowywania programów przy użyciu portu; umożliwia portowi śledzenie aktualnie debugowanych programów. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Reprezentuje dostosowany interfejs użytkownika do wybierania portu. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Reprezentuje żądanie dotyczące portu, z którego zostanie utworzony lub zlokalizowany nowy port. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Reprezentuje dostawcę portów. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Reprezentuje dostawcę portów, które mogą być utrwalane (Zapisz na dysku) informacje o utworzonych przez siebie portach. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Włącza [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika do wyświetlania tekstu w sekcji **Informacje o transporcie** okna dialogowego **Dołącz do procesu** . |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Umożliwia wykonywanie zapytań dotyczących informacji o komputerze docelowym. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | A, PS | Reprezentuje Wyliczenie na zestawie portów. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Reprezentuje Wyliczenie na zestawie dostawców portów. |

## <a name="processes"></a><a name="Processes"></a> Przetwarzające
 Te interfejsy reprezentują procesy, jeden plik wykonywalny, który zawiera jeden lub więcej programów.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Reprezentuje proces, który jest uruchomiony na komputerze.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Reprezentuje proces, który aktywnie obsługuje debugowanie (używany do zastępowania metod krok, Kontynuuj i Execute w interfejsie [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wysyłany przez DE lub port, gdy proces został utworzony.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Wysyłany przez DE lub port, gdy proces został zniszczony.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Reprezentuje proces, który musi śledzić dołączoną do niej sesję.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Reprezentuje Wyliczenie zestawu procesów na porcie.|

## <a name="programs"></a><a name="Programs"></a> Programu
 Te interfejsy reprezentują programy, jednostki logiczne wykonywania, które nie muszą być zgodne z fizycznym plikiem wykonywalnym lub modułem.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Reprezentuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który musi współpracować z innymi programami, które są debugowane w tym samym czasie.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Reprezentuje jednostkę logiczną wykonania.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wysyłany przez DE lub port, gdy program został utworzony.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Wysyłany przez DE lub port, gdy program został zniszczony.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje element [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , który może być obsługiwany przez wiele aparatów debugowania.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Reprezentuje element [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który musi być w stanie śledzić, do której sesji jest dołączona.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Reprezentuje element [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który może zwracać informacje o procesie, w którym jest uruchomiony.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Reprezentuje program, który może być debugowany.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Zezwala na powiadamianie węzła programu o próbie dołączenia do skojarzonego programu.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Umożliwia modelowi SDM wykonywanie zapytania o wszystkie programy kontrolowane przez to DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Używany przez DEs do rejestrowania programów z modelem SDM, aby pokazać, że są debugowane.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Reprezentuje element [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , który może organizować interfejsy między granicami wątków lub procesów.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Reprezentuje Wyliczenie zestawu programów.|

## <a name="properties"></a><a name="Properties"></a> Aœciwoœci
 Te interfejsy reprezentują właściwości, wartość skojarzoną z określonym kontekstem, zazwyczaj wynik oceny wyrażenia.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Reprezentuje element [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który może wyświetlać jego wartość w niestandardowy sposób.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Reprezentuje wartość ramki stosu, dokumentu lub wyniku oceny wyrażenia.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Reprezentuje element [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który obsługuje arbitralnie długie ciągi.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wysyłany przez DE po utworzeniu nowej właściwości (reprezentowanej przez interfejs [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ).|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Wysyłany przez DE, gdy właściwość została zniszczona.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Reprezentuje odwołanie do właściwości, która może istnieć poza określoną ramką stosu.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Reprezentuje Wyliczenie na zestawie struktur [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , które opisują zmienne, rejestry, parametry i wyrażenia.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Reprezentuje Wyliczenie na zestawie struktur [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .|

## <a name="stack-frames"></a><a name="StackFrames"></a> Ramki stosu
 Te interfejsy reprezentują ramkę stosu, kontekst, w którym wystąpiło punkt przerwania lub wyjątek.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst, w którym wystąpił punkt przerwania lub wyjątek.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje element [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , który może obsługiwać przechwycone wyjątki.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Reprezentuje Wyliczenie na zestawie struktur [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) , które określają sekwencję wywołań funkcji używaną do osiągnięcia określonej ramki stosu.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Reprezentuje Wyliczenie na zestawie struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , które opisują ramki stosu.|

## <a name="threads"></a><a name="Threads"></a> Wątk
 Te interfejsy reprezentują wątki i powiązane z nimi zdarzenia.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Reprezentuje wątek wykonania.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wysyłany przez DE po utworzeniu wątku.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wysyłany przez DE, gdy wątek został zniszczony.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wysyłany przez DE, gdy wątek zmienił swoją nazwę.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Reprezentuje Wyliczenie w zestawie wątków.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Wizualizatory typów
 Te interfejsy zapewniają obsługę wizualizatorów typów. Te interfejsy są zwykle implementowane przez ewaluatora wyrażeń.

|Interfejs|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Reprezentuje tablicę bajtów, która ma zostać przedstawiona dla wizualizatora typu.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Zapewnia metody uzyskiwania dostępu do danych, które mają być przekazywane do wizualizatora typu.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Reprezentuje właściwość, która zapewnia dostęp do implementacji [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .|

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Tworzenie niestandardowego aparatu debugowania](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
