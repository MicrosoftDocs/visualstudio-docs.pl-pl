---
title: Interfejsy podstawowe | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737579"
---
# <a name="core-interfaces"></a>Interfejsy podstawowe
Następujące interfejsy są podstawowe interfejsy do rozszerzania debugera za pomocą . [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]

## <a name="discussion"></a>Dyskusji
 Interfejsy te są używane głównie do tworzenia aparatu debugowania (DE). Są one organizowane tutaj według kategorii:

- [Punkty przerwania](#Breakpoints)

- [Konteksty](#Contexts)

- [Serwer podstawowy](#CoreServer)

- [Aparaty debugowania](#DebugEngines)

- [Dokumenty](#Documents)

- [Zdarzenia](#Events)

- [Wyrażenia](#Expressions)

- [Pamięci](#Memory)

- [Moduły](#Modules)

- [Porty](#Ports)

- [Procesów](#Processes)

- [Programy](#Programs)

- [Właściwości](#Properties)

- [Ramki stosu](#StackFrames)

- [Wątki](#Threads)

- [Wizualizatory typu](#TypeVisualizers)

  Jednostki, które można zaimplementować interfejsy są:

- Aparat debugowania (DE)

- Dostawca portu (PS)

- Ewaluator ekspresji (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Punkty przerwania
 Interfejsy te są związane z implementacją i śledzeniem punktów przerwania.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Reprezentuje punkt przerwania powiązany z lokalizacją pamięci.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania jest powiązany z lokalizacją pamięci.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Reprezentuje sumę kontrolną dokumentu dla żądania punktu przerwania.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania nie może być powiązany z lokalizacją pamięci.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Wysyłane przez DE po osiągnięciu punktu przerwania.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Reprezentuje żądanie punktu przerwania; używane w tworzeniu oczekującego punktu przerwania.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Reprezentuje żądanie punktu przerwania; używane w tworzeniu oczekującego punktu przerwania.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Reprezentuje informacje używane do powiązania punktu przerwania.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Wysyłane przez DE, gdy punkt przerwania jest niezwiązany z lokalizacji pamięci.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Reprezentuje nieprawidłowy punkt przerwania (zwrócony przez `IDebugBreakpointErrorEvent2`).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Reprezentuje informacje o rozdzielczości o nieprawidłowym punkcie przerwania.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Reprezentuje pozycję w funkcji, w której jest ustawiony punkt przerwania.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Reprezentuje punkt przerwania, który ma być powiązany; używane w tworzeniu powiązanego punktu przerwania.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Reprezentuje wyliczenie nad zestawem powiązanych punktów przerwania.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Reprezentuje wyliczenie nad zestawem punktów przerwania, które nie mogą być powiązane z lokalizacją pamięci.|

## <a name="contexts"></a><a name="Contexts"></a>Kontekstów
 Interfejsy te reprezentują różnego rodzaju kontekstów w programie są debugowane.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Reprezentuje pozycję początkową instrukcji kodu.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozszerza interfejs [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) aby umożliwić pobieranie interfejsów modułu i procesu.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Reprezentuje pozycję w dokumencie.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst, w którym do oceny wyrażenia.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje lokalizację początkową w pamięci kolekcji bajtów.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje kontekst ramki stosu w punkcie przerwania lub wyjątku.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Reprezentuje wyliczenie nad zestawem kontekstów kodu.|

## <a name="core-server"></a><a name="CoreServer"></a>Serwer podstawowy
 Interfejsy te reprezentują komputer, na którym program jest debugowany. Są one implementowane przez, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ale mogą być wywoływane przez aparaty debugowania.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Zapewnia dostęp do portów i dostawców portów, a także informacji o komputerze.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Reprezentuje [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) który obsługuje zdalne debugowanie.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Aparaty debugowania
 Te interfejsy reprezentują aparaty debugowania i skojarzone z nimi zdarzenia.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Reprezentuje aparat debugowania niestandardowe.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Reprezentuje aparat debugowania niestandardowe, który obsługuje ładowanie symboli, JustMyCode i wyjątków.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wysyłane przez każde nowe wystąpienie DE, aby wskazać, że jest gotowy do obsługi zadań debugowania.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Reprezentuje niestandardowy aparat debugowania, który obsługuje uruchamianie programów.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje węzeł programu, który obsługuje wiele aparatów debugowania.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Umożliwia SDM, aby uzyskać interfejs do aparatu debugowania z wątku, programu lub ramki stosu.|

## <a name="documents"></a><a name="Documents"></a>Dokumentów
 Interfejsy te reprezentują dokumenty (pliki źródłowe) i skojarzone z nimi elementy.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wysłana przez DE w celu zażądania otwarcia dokumentu.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Reprezentuje strumień zdemontowanych instrukcji z dokumentu.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Reprezentuje dokument dostarczony przez DE, określając nazwę i identyfikator klasy (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Reprezentuje sumę kontrolną dla dokumentu debugowania i umożliwia przekazywanie sumy kontrolnej między składnikami.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Reprezentuje kontekst dokumentu, pozycja w dokumencie odpowiadająca określonej instrukcji i kontekstu kodu.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Reprezentuje ogólne stanowisko w dokumencie.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Reprezentuje pozycję w pliku źródłowym jako przesunięcie znaku.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Reprezentuje dokument tekstowy dostarczony przez DE (pochodzący z [IDebugDocument2),](../../../extensibility/debugger/reference/idebugdocument2.md)dostarczający rzeczywisty tekst.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wysłane przez DE, aby określić zmiany w pliku źródłowym, który znajduje się w pamięci.|

## <a name="events"></a><a name="Events"></a>Zdarzenia
 Interfejsy te reprezentują wszystkie zdarzenia, które są wysyłane między DE i menedżera debugowania sesji (SDM).

| Interface | Zaimplementowane przez | Opis |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Wysłana przez DE w celu zażądania otwarcia dokumentu. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Aparat debugowania (DE) wysyła ten interfejs do menedżera debugowania sesji (SDM), aby ustawić komunikat paska stanu podczas ładowania symbolu. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Wysyłane przez DE po zakończeniu przerwy w programie. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Wysyłane przez DE, gdy punkt przerwania jest powiązany. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Wysyłane przez DE, gdy punkt przerwania nie powiedzie się powiększe. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Wysyłane przez DE po osiągnięciu punktu przerwania. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Wysyłane przez DE, gdy punkt przerwania jest niezwiązany. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Wysłane przez DE w celu ustalenia, czy należy zatrzymać się w określonym miejscu. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Wysłane przez DE, aby określić zmiany w pliku źródłowym, który znajduje się w pamięci. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Wysyłane przez każde nowe wystąpienie DE, aby wskazać, że jest gotowy do obsługi zadań debugowania. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Wysłany przez DE, aby wskazać, że program jest debugowany jest gotowy do wykonania pierwszej instrukcji. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interfejs, który jest używany przez inne interfejsy zdarzeń, które mogą zwracać błąd, aby zapewnić komunikaty o błędach czytelne dla człowieka. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interfejs podstawowy, z którego pochodzą wszystkie inne interfejsy zdarzeń. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Reprezentuje interfejs zaimplementowany przez SDM, do którego są wysyłane zdarzenia (wyrażone jako obiekty implementujące interfejs określonego zdarzenia). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Wysyłane przez DE, gdy wystąpił wyjątek w programie debugowanym. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Wysyłane przez DE po zakończeniu oceny wyrażenia asynchronicznej. |
| IDebugFindSymbolEvent2 | | Przestarzałe. NIE UŻYWAĆ. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Wysłane przez DE podczas przetwarzania przechwyconego wyjątku zostało zakończone. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Wysyłane przez DE po zakończeniu ładowania programu. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Wysyłane przez DE, aby IDE wyświetlić komunikat informacyjny do użytkownika. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Wysyłane przez DE, gdy moduł jest ładowany lub wyładowywany. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Sygnalizuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika debugera, aby ostrzec użytkownika, że symbole nie mogą być zlokalizowane dla uruchomionego pliku wykonywalnego. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Wysyłane przez DE, aby IDE wyświetlić dowolny ciąg. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Wysyłane przez port do komunikowania zdarzeń portu do dowolnego odbiornika. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Wysyłane przez DE lub port po utworzeniu procesu. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Wysyłane przez DE lub port, gdy proces został zniszczony. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Wysyłane przez DE lub port po utworzeniu programu. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Wysyłane przez DE lub port, gdy program został zniszczony. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Włącza aparat debugowania, aby zastąpić domyślne zachowanie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika po zakończeniu sesji debugowania. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Wysyłane z aparatu debugowania (DE) do menedżera debugowania sesji (SDM), gdy zmienia się nazwa programu. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Wysyłane przez DE po utworzeniu nowej `IDebugProperty2` właściwości (reprezentowane przez interfejs). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Wysyłane przez DE, gdy nieruchomość została zniszczona. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Wysyłane przez DE podczas przechodzenia z lub za pomocą funkcji, dzięki czemu wartość zwracana może być poprawnie wyświetlana. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Umożliwia aparatom debugowania zdalne odczytywanie ustawień metryki. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Wysyłane przez DE po zakończeniu kroku do, nad lub poza instrukcją. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Wysyłane przez DE, aby wskazać sukces lub niepowodzenie ładowania symboli dla modułu. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Wysyłane przez DE po utworzeniu wątku. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Wysyłane przez DE, gdy wątek został zniszczony. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Wysyłane przez DE, gdy wątek zmienił nazwę. |

## <a name="expressions"></a><a name="Expressions"></a>Wyrażenia
 Interfejsy te reprezentują wyrażenia, które mają być oceniane w określonym kontekście.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Reprezentuje wyrażenie, które ma zostać ocenione. Uzyskane z interfejsu [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Reprezentuje kontekst, w którym wyrażenie jest oceniane. Uzyskane z interfejsu [IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wysyłane przez DE po zakończeniu oceny wyrażenia asynchronicznej.|

## <a name="memory"></a><a name="Memory"></a>Pamięci
 Interfejsy te reprezentują sekwencje bajtów w pamięci.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Reprezentuje sekwencję bajtów w pamięci, które mogą być odczytywane z lub zapisywane do.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Reprezentuje lokalizację w pamięci sekwencji bajtów.|

## <a name="modules"></a><a name="Modules"></a>Moduły
 Interfejsy te reprezentują moduł, który odpowiada wykonywalnej lub . DLL.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Reprezentuje pojedynczy plik wykonywalny lub biblioteka DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Reprezentuje [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) który obsługuje symbole.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wysyłane przez DE, gdy moduł jest ładowany lub wyładowywany.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Reprezentuje informacje o serwerze źródłowym zawarte w pliku PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Reprezentuje wyliczenie nad zestawem modułów, które są znane przez [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a>Porty
 Interfejsy te reprezentują porty i dostawców portów.

| Interface | Zaimplementowane przez | Opis |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Reprezentuje domyślny port na komputerze lokalnym. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Włącza aparat debugowania, który używa [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] DCOM, aby poprosić interfejsu użytkownika, aby upewnić się, że zapora nie będzie blokować zdalnego debugowania. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Reprezentuje port. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Wysyłane przez port do komunikowania zdarzeń portu do dowolnego odbiornika. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Reprezentuje port, który może uruchamiać i kończyć procesy. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Służy do rejestrowania i wyrejestrowywać programy z portem; umożliwia portowi śledzenie programów, które są obecnie debugowane. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Reprezentuje dostosowany interfejs użytkownika do wybierania portu. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Reprezentuje żądanie dla portu, z którego zostanie utworzony lub zlokalizowany nowy port. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Reprezentuje dostawcę portów. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Reprezentuje dostawcę portów, które mogą utrwalać (zapisywać na dysku) informacje o utworzonych portach. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Umożliwia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejsowi użytkownika wyświetlanie tekstu w sekcji **Informacje o transporcie** w oknie dialogowym **Dołączanie do procesu.** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Umożliwia wykonywanie zapytań o informacje o komputerze docelowym. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Reprezentuje wyliczenie nad zestawem portów. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Reprezentuje wyliczenie nad zestawem dostawców portów. |

## <a name="processes"></a><a name="Processes"></a>Procesów
 Te interfejsy reprezentują procesy, pojedynczy plik wykonywalny, który zawiera jeden lub więcej programów.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Reprezentuje proces, który jest uruchomiony na komputerze.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Reprezentuje proces, który aktywnie obsługuje debugowanie (używane do zastąpienia krok, Kontynuuj i Wykonaj metody na [interfejsie IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wysyłane przez DE lub port po utworzeniu procesu.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Wysyłane przez DE lub port, gdy proces został zniszczony.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Reprezentuje proces, który musi śledzić, która sesja jest do niego dołączona.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Reprezentuje wyliczenie zestawu procesów na porcie.|

## <a name="programs"></a><a name="Programs"></a>Programy
 Interfejsy te reprezentują programy, logiczne jednostki wykonania, które niekoniecznie odpowiadają fizycznemu wykonywalowi lub modułowi.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Reprezentuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) który musi pracować w porozumieniu z innymi programami są debugowane w tym samym czasie.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Reprezentuje logiczną jednostkę wykonania.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wysyłane przez DE lub port po utworzeniu programu.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Wysyłane przez DE lub port, gdy program został zniszczony.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Reprezentuje [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) które mogą być obsługiwane przez wiele aparatów debugowania.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Reprezentuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) który musi być w stanie śledzić, która sesja jest do niego dołączona.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Reprezentuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) który może zwracać informacje o procesie, w którym jest uruchomiony.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Reprezentuje program, który może być debugowany.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Umożliwia powiadamianie węzła programu o próbie dołączenia do skojarzonego programu.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Umożliwia SDM do kwerendy DE o programach kontrolowanych przez tego DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Używane przez DEs do rejestrowania programów z SDM, aby pokazać, że są debugowane.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Reprezentuje [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) który może marshal interfejsów w granicach wątku lub procesu.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Reprezentuje wyliczenie zestawu programów.|

## <a name="properties"></a><a name="Properties"></a>Właściwości
 Interfejsy te reprezentują właściwości, wartość skojarzoną z określonym kontekstem, zwykle wynikiem oceny wyrażenia.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Reprezentuje [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który może wyświetlać jego wartość w sposób niestandardowy.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Reprezentuje wartość ramki stosu, dokumentu lub wyniku oceny wyrażenia.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Reprezentuje [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który obsługuje dowolnie długie ciągi.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wysłane przez DE po utworzeniu nowej właściwości (reprezentowanej przez interfejs [IDebugProperty2).](../../../extensibility/debugger/reference/idebugproperty2.md)|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Wysyłane przez DE, gdy nieruchomość została zniszczona.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Reprezentuje odwołanie do właściwości, która może istnieć poza dowolną ramką stosu określonego.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Reprezentuje wyliczenie nad zestawem [struktur DEBUG_PROPERTY_INFO,](../../../extensibility/debugger/reference/debug-property-info.md) które opisują zmienne, rejestry, parametry i wyrażenia.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Reprezentuje wyliczenie nad zestawem [struktur DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)|

## <a name="stack-frames"></a><a name="StackFrames"></a>Ramki stosu
 Interfejsy te reprezentują ramki stosu, kontekst, w którym wystąpił punkt przerwania lub wyjątek.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Reprezentuje kontekst, w którym wystąpił punkt przerwania lub wyjątek.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Reprezentuje [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) który może obsługiwać przechwycone wyjątki.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Reprezentuje wyliczenie nad zestawem [struktur CODE_PATH,](../../../extensibility/debugger/reference/code-path.md) które określają sekwencję wywołań funkcji używanej do dotarcie do określonej ramki stosu.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Reprezentuje wyliczenie nad zestawem struktur [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) które opisują ramki stosu.|

## <a name="threads"></a><a name="Threads"></a>Wątków
 Te interfejsy reprezentują wątki i ich skojarzone zdarzenia.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Reprezentuje wątek wykonywania.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wysyłane przez DE po utworzeniu wątku.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wysyłane przez DE, gdy wątek został zniszczony.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wysyłane przez DE, gdy wątek zmienił nazwę.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Reprezentuje wyliczenie nad zestawem wątków.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Wizualizatory typu
 Interfejsy te zapewniają obsługę wizualizatorów typów. Interfejsy te są zazwyczaj implementowane przez oceniającego wyrażenie.

|Interface|Zaimplementowane przez|Opis|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Reprezentuje tablicę bajtów, które mają być prezentowane do wizualizatora typu.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Udostępnia metody uzyskiwania dostępu do danych, które mają być przekazywane do wizualizatora typu.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Reprezentuje właściwość, która zapewnia dostęp do implementacji [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Zobacz też
- [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Tworzenie niestandardowego aparatu debugowania](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
