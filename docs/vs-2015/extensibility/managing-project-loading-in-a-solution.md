---
title: Zarządzanie ładowaniem projektu w rozwiązaniu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64786152"
---
# <a name="managing-project-loading-in-a-solution"></a>Zarządzanie ładowaniem projektu w rozwiązaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozwiązania programu Visual Studio mogą zawierać wiele projektów. Domyślne zachowanie programu Visual Studio polega na załadowaniu wszystkich projektów w rozwiązaniu w momencie otwarcia rozwiązania, a nie umożliwieniu użytkownikowi dostępu do żadnego z projektów do momentu zakończenia jego ładowania. Gdy proces ładowania projektu będzie trwać więcej niż dwie minuty, zostanie wyświetlony pasek postępu przedstawiający liczbę załadowanych projektów i łączną liczbę projektów. Użytkownik może zwolnić projekty podczas pracy w rozwiązaniu z wieloma projektami, ale ta procedura ma pewne wady: niezaładowane projekty nie są kompilowane jako część polecenia odbudowywania rozwiązania, a opisy typów i elementów członkowskich zamkniętych projektów nie są wyświetlane.  
  
 Deweloperzy mogą skrócić czasy ładowania rozwiązań i zarządzać zachowaniem ładowania projektu, tworząc Menedżera ładowania rozwiązań. Menedżer obciążenia rozwiązań może ustawić różne priorytety ładowania projektu dla określonych projektów lub typów projektów, przed ukończeniem wykonywania innych zadań w tle, należy się upewnić, że projekty są załadowane przed rozpoczęciem kompilacji w tle.  
  
## <a name="project-loading-priorities"></a>Priorytety ładowania projektu  
 Program Visual Studio definiuje cztery różne priorytety ładowania projektu:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (wartość domyślna): po otwarciu rozwiązania projekty są ładowane asynchronicznie. Jeśli ten priorytet jest ustawiony w niezaładowanym projekcie po tym, jak rozwiązanie jest już otwarte, projekt zostanie załadowany w następnym punkcie bezczynności.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: po otwarciu rozwiązania projekty są ładowane w tle, co umożliwia użytkownikowi dostęp do projektów podczas ich ładowania bez konieczności oczekiwania na załadowanie wszystkich projektów.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty są ładowane podczas uzyskiwania do nich dostępu. Dostęp do projektu jest uzyskiwany, gdy użytkownik rozszerza węzeł projektu w Eksplorator rozwiązań, gdy plik należący do projektu zostanie otwarty, gdy zostanie otwarte, ponieważ znajduje się na liście Otwórz dokument (utrwalone w pliku opcji użytkownika rozwiązania) lub gdy inny ładowany projekt ma zależność od projektu. Ten typ projektu nie jest ładowany automatycznie przed rozpoczęciem procesu kompilacji; Menedżer obciążenia rozwiązań jest odpowiedzialny za zapewnienie, że wszystkie niezbędne projekty są załadowane. Te projekty należy również załadować przed rozpoczęciem wyszukiwania/zastępowania plików w całym rozwiązaniu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty nie są ładowane, chyba że użytkownik jawnie go zażąda. Dzieje się tak w przypadku, gdy projekty zostały jawnie zwolnione.  
  
## <a name="creating-a-solution-load-manager"></a>Tworzenie Menedżera ładowania rozwiązań  
 Deweloperzy mogą utworzyć Menedżera obciążenia rozwiązań, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> i powiadamiając program Visual Studio, że Menedżer obciążenia rozwiązań jest aktywny.  
  
#### <a name="activating-a-solution-load-manager"></a>Aktywowanie Menedżera ładowania rozwiązań  
 Program Visual Studio umożliwia korzystanie z tylko jednego menedżera ładowania rozwiązań w danym momencie, dlatego musisz polecić programowi Visual Studio, gdy chcesz aktywować Menedżera obciążenia rozwiązania. Jeśli drugi Menedżer ładowania rozwiązań został aktywowany później w systemie, Menedżer obciążenia rozwiązań zostanie odłączony.  
  
 Musisz pobrać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługę i ustawić <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Właściwość:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementowanie IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>Metoda jest wywoływana podczas procesu otwierania rozwiązania. Aby zaimplementować tę metodę, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> usługi do ustawienia priorytetu obciążenia dla typu projektu, który ma być zarządzany. Na przykład poniższy kod ustawia typy projektów C# do załadowania w tle:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Metoda jest wywoływana, gdy program Visual Studio jest zamykany lub gdy inny pakiet został przejęty jako aktywny Menedżer ładowania rozwiązań przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwością.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dotyczące różnych rodzajów Menedżera ładowania rozwiązań  
 Można zaimplementować menedżerów obciążeń rozwiązań na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.  
  
 Jeśli Menedżer obciążenia rozwiązań ma ogólnie zarządzać ładowaniem rozwiązań, można go zaimplementować jako część pakietu VSPackage. Pakiet powinien być ustawiony na automatyczne ładowanie przez dodanie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> elementu pakietu VSPackage z wartością <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Można następnie aktywować Menedżera ładowania rozwiązań w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat pakietów ładowania automatyczne, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).  
  
 Ponieważ program Visual Studio rozpoznaje tylko ostatni Menedżer ładowania rozwiązań, który ma zostać aktywowany, menedżerowie ogólnego ładowania rozwiązań powinni zawsze wykrywać, czy istnieje istniejący Menedżer obciążenia przed uaktywnieniem siebie. W przypadku wywołania funkcji GetProperty () w usłudze rozwiązania dla funkcji <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Returns `null` nie istnieje aktywny Menedżer ładowania rozwiązań. Jeśli nie zwraca wartości null, sprawdź, czy obiekt jest taki sam jak w przypadku Menedżera obciążenia rozwiązań.  
  
 Jeśli Menedżer obciążenia rozwiązań ma zarządzać tylko kilkoma typami rozwiązań, pakietu VSPackage może subskrybować zdarzenia ładowania rozwiązania (poprzez wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) i użyć programu obsługi zdarzeń dla programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> w celu aktywowania Menedżera ładowania rozwiązań.  
  
 Jeśli Menedżer obciążenia rozwiązań ma zarządzać tylko określonymi rozwiązaniami, informacje o aktywacji mogą być utrwalane w ramach pliku rozwiązania. W tym celu Zadzwoń <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> do sekcji wstępnego rozwiązania.  
  
 Określeni Menedżery ładowania rozwiązań powinni dezaktywować się w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> obsługi zdarzeń, aby nie powodowały konfliktów z innymi menedżerami ładowania rozwiązań.  
  
 Jeśli potrzebujesz Menedżera ładowania rozwiązań tylko w celu utrwalenia priorytetów globalnego obciążenia projektu (na przykład właściwości ustawionych na stronie opcji), możesz aktywować Menedżera ładowania rozwiązań w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> obsługi zdarzeń, zachować ustawienie we właściwościach rozwiązania, a następnie dezaktywować Menedżera ładowania rozwiązań.  
  
## <a name="handling-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązania  
 Aby subskrybować zdarzenia ładowania rozwiązania, Połącz się, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> gdy aktywujesz Menedżera ładowania rozwiązań. W przypadku zaimplementowania programu można <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> reagować na zdarzenia, które odnoszą się do różnych priorytetów ładowania projektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Ten element jest uruchamiany przed otwarciem rozwiązania. Można jej użyć do zmiany priorytetu ładowania projektu dla projektów w rozwiązaniu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Jest uruchamiany po całkowitym załadowaniu rozwiązania, ale przed ponownym rozpoczęciem ładowania projektu w tle. Na przykład użytkownik może uzyskać dostęp do projektu, którego priorytet obciążenia to LoadIfNeeded, lub Menedżer obciążenia rozwiązania mógł zmienić priorytet obciążenia projektu na BackgroundLoad, co spowoduje rozpoczęcie ładowania w tle tego projektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Jest uruchamiany po pierwszym całkowitym załadowaniu rozwiązania, niezależnie od tego, czy jest to Menedżer obciążenia rozwiązań. Jest również uruchamiany po załadowaniu w tle lub załadowaniu na żądanie, gdy rozwiązanie zostanie w pełni załadowane. W tym samym czasie program <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> zostanie ponownie aktywowany.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Ten element jest uruchamiany przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle są kończone przed załadowaniem projektów, ustaw `pfShouldDelayLoadToNextIdle` na **wartość true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Ta wartość jest wyzwalana, gdy zostanie załadowana partia projektów. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty są ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość false, projekty są ładowane synchronicznie w wyniku żądania użytkownika, na przykład jeśli użytkownik rozwinie oczekujący projekt w Eksplorator rozwiązań. Można zaimplementować tę czynność, aby wykonać bardzo dużo pracy, które w przeciwnym razie byłyby konieczne <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Ta wartość jest wyzwalana po załadowaniu partii projektów.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Wykrywanie rozwiązań i ładowanie projektów oraz zarządzanie nimi  
 W celu wykrycia stanu ładowania projektów i rozwiązań należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> następujące wartości:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` czy rozwiązanie i wszystkie jego projekty są ładowane, w przeciwnym razie `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` czy wsadowe projekty są aktualnie ładowane w tle, w przeciwnym razie `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` czy wsadowe projekty są aktualnie ładowane synchronicznie w wyniku polecenia użytkownika lub innego, niejawnego obciążenia, w przeciwnym razie `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` zwraca `true` czy rozwiązanie jest aktualnie zamykane, w przeciwnym razie `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` zwraca `true` czy rozwiązanie jest aktualnie otwierane, w przeciwnym razie `false` .  
  
  Możesz również upewnić się, że projekty i rozwiązania są załadowane (niezależnie od tego, jakie są priorytety obciążenia projektu), wywołując jedną z następujących metod:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza załadowanie projektów w rozwiązaniu przed zwróceniem metody.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza `guidProject` załadowanie projektów przed zwróceniem metody.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza `guidProjectID` załadowanie projektu przed zwróceniem metody.  
  
> [!NOTE]
> . Domyślnie są ładowane tylko projekty, które mają priorytety obciążenia i obciążenia w tle, ale jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flaga jest przenoszona do metody, wszystkie projekty zostaną załadowane z wyjątkiem tych, które są oznaczone do załadowania jawnie.
