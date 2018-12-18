---
title: Zarządzanie ładowaniem projektu w rozwiązaniu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 041c5ab52a7a0e8be89ef1abe6db4d1aed51ecfc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781767"
---
# <a name="managing-project-loading-in-a-solution"></a>Zarządzanie ładowaniem projektu w rozwiązaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozwiązania programu Visual Studio mogą zawierać dużą liczbę projektów. Domyślne zachowanie programu Visual Studio jest można załadować wszystkich projektów w rozwiązaniu w czasie, które rozwiązanie jest otwierane, a nie Zezwalaj użytkownikowi dostępu do żadnego z projektów wszystkich z nich ma zakończenie ładowania. Podczas procesu ładowania projektu trwa więcej niż dwie minuty, jest wyświetlany pasek postępu, przedstawiający liczbę projektów i łącznej liczby projektów. Użytkownik może zwolnienia projektów podczas pracy w ramach rozwiązania z wieloma projektami, ale ta procedura ma pewne wady: zwolniono projekty są kompilowane jako część polecenia Kompiluj rozwiązanie i zamknięcie IntelliSense opisy typów i elementów członkowskich projekty nie są wyświetlane.  
  
 Deweloperzy mogą skrócić czas ładowania rozwiązania i zarządzać ładowanie zachowanie, tworząc ładowania rozwiązań menedżera projektu. Menedżera obciążenia rozwiązania można ustawić inny projekt ładowania priorytetów dla określonych projektów i typów projektów, upewnij się, że projekty zostały załadowane przed rozpoczęciem kompilacji tła, opóźnienie w tle podczas ładowania dopiero po zakończeniu innego zadania w tle i wykonania inne zadania zarządzania ładowania projektu.  
  
## <a name="project-loading-priorities"></a>Ładowanie priorytetów projektu  
 Program Visual Studio definiuje cztery priorytety podczas ładowania innego projektu:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (ustawienie domyślne): gdy rozwiązanie jest otwarte, projekty są ładowane asynchronicznie. Jeśli ten priorytet jest ustawiona na zwolnionego projektu, po rozwiązania jest już otwarty, projekt zostanie załadowany w następnym punkcie bezczynności.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: po otwarciu rozwiązania, projekty są ładowane w tle, co pozwala na dostęp do projektów, ponieważ są one załadowane bez konieczności poczekać, aż wszystkie projekty zostały załadowane.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty są ładowane, gdy są one używane. Projekt jest dostępny, gdy użytkownik rozwija węzeł projektu w Eksploratorze rozwiązań, po otwarciu pliku należących do projektu po otwarciu rozwiązania, ponieważ jest na liście otwartego dokumentu (utrwalane w plik opcji użytkownika rozwiązania) lub w przypadku, gdy inny projekt oznacza to ładowany zależny od projektu. Ten typ projektu nie jest automatycznie ładowany przed rozpoczęciem procesu kompilacji; Menedżer obciążenia rozwiązania jest odpowiedzialny za zapewnienie, że wszystkie niezbędne projekty są ładowane. Te projekty również powinny być załadowane przed rozpoczęciem Znajdź/Zamień w plikach dla całego rozwiązania.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projektów nie mają być załadowane, chyba że wyraźnie zażąda użytkownika. Dotyczy to sytuacji, gdy projekty są jawnie usuwane z pamięci.  
  
## <a name="creating-a-solution-load-manager"></a>Tworzenie Menedżera ładowania rozwiązań  
 Deweloperzy mogą tworzyć ładowania rozwiązań Menedżera implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> i wniosku programu Visual Studio, czy Menedżera obciążenia rozwiązania jest aktywny.  
  
#### <a name="activating-a-solution-load-manager"></a>Aktywowanie Menedżera obciążenia rozwiązania  
 Program Visual Studio umożliwia rozwiązanie tylko jednego z kierowników obciążenia w danym momencie, dlatego konieczne jest poinformowanie programu Visual Studio aktywować obciążenia rozwiązania menedżera. Jeśli drugi Menedżera obciążenia rozwiązania została aktywowana później, rozwiązanie Menedżera obciążenia zostaną rozłączone.  
  
 Należy uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługi i ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwości:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementowanie IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Metoda jest wywoływana podczas otwierania rozwiązania. Aby zaimplementować tę metodę, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> usługi, aby ustawić priorytet obciążenia dla typu projektu, którą chcesz zarządzać. Na przykład poniższy kod ustawia typy projektów C# do załadowania w tle:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Metoda jest wywoływana, gdy trwa zamykanie programu Visual Studio lub inny pakiet przejmuje jako Menedżer ds. rozwiązania aktywnego obciążenia przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwości.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dotyczące różnych rodzajów Menedżera obciążenia rozwiązania  
 Menedżerowie obciążenia rozwiązania można zaimplementować na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania ogólnie rzecz biorąc ładowania rozwiązania, można zaimplementować jako część pakietu VSPackage. Pakiet powinna być ustawiona na automatyczne ładowanie, dodając <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na VSPackage o wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Następnie można aktywować Menedżera obciążenia rozwiązania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pakietów autoloading zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).  
  
 Ponieważ program Visual Studio rozpoznaje tylko ostatni rozwiązania obciążenia Menedżera aktywacji, menedżerów obciążenia ogólne rozwiązanie powinien zawsze wykrywa, czy przed aktywowaniem samodzielnie jest istniejącego menedżera obciążenia. Jeśli wywołanie GetProperty() usłudze rozwiązania dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> zwraca `null`, istnieje nie aktywne rozwiązanie Menedżera obciążenia. Jeśli nie zwróci wartość null, sprawdź, czy obiekt jest taki sam jak Menedżer ładowania rozwiązania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko kilka typów rozwiązania, pakietu VSPackage mogą subskrybować zdarzeń ładowania rozwiązania (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) i użyj programu obsługi zdarzeń <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktywować Menedżera obciążenia rozwiązania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko określone rozwiązania, informacje o aktywacji, może być utrwalony jako część pliku rozwiązania. Aby to zrobić, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> dla sekcji rozwiązania wstępnego.  
  
 Menedżerowie ładowania konkretnego rozwiązania dezaktywować w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> procedura obsługi zdarzeń, aby nie powodują konflikt z innych menedżerów ładowania rozwiązania.  
  
 Jeśli potrzebujesz Menedżera obciążenia rozwiązanie tylko do utrwalenia priorytetów ładowania projektu globalnego (na przykład zbioru właściwości na stronie Opcje), możesz aktywować Menedżera obciążenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> programu obsługi zdarzeń utrwalić ustawienie we właściwościach rozwiązania, a następnie Dezaktywuj Menedżera obciążenia rozwiązania.  
  
## <a name="handling-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązań  
 Aby subskrybować zdarzeń ładowania rozwiązania, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> po aktywacji usługi Menedżera obciążenia rozwiązania. W przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, pozwalające reagować na zdarzenia, które odnoszą się do innego projektu podczas ładowania priorytetów.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To jest uruchamiane przed otwarciem rozwiązania. Służy on do zmiany projektu podczas ładowania priorytet dla projektów w rozwiązaniu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To jest uruchamiane po całkowitym załadowaniu rozwiązania, ale przed tła ładowanie projektu rozpoczyna się od nowa. Na przykład użytkownik może uzyskać dostęp do projektu, w których priorytet obciążenia jest LoadIfNeeded lub rozwiązania Menedżera obciążenia mogły ulec zmianie priorytet ładowania projektu do BackgroundLoad, który chce się uruchomić obciążenia tła tego projektu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Czy istnieje Menedżera obciążenia rozwiązania w tym uruchamiane po początkowym pełni załadowaniu rozwiązania. Również wyzwoleniu po obciążenia tło lub żądanie załadowania zawsze wtedy, gdy rozwiązanie staje się w pełni załadowane. W tym samym czasie <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> zostanie ponownie aktywowany.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To jest uruchamiane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle odbywa się przed projekty są ładowane, należy ustawić `pfShouldDelayLoadToNextIdle` do **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To jest uruchamiane, gdy partii projektów ma być załadowany. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty mają być ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość FAŁSZ, projekty są mają zostać załadowane synchronicznie w wyniku żądania użytkownika, na przykład jeśli użytkownik rozwija oczekujące projekt w Eksploratorze rozwiązań. Można zaimplementować ten element, aby spełniała kosztowne, które w przeciwnym razie musi odbywać się w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To jest wyzwalane po załadowaniu partii projektów.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Wykrywanie i zarządzania nimi rozwiązania i ładowanie projektu  
 W celu wykrycia stan ładowania projektów i rozwiązań, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> z następującymi wartościami:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli rozwiązanie i jego projekty są załadowane, w przeciwnym razie `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projekty są obecnie ładowane w tle, w przeciwnym razie `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projekty są obecnie ładowane synchronicznie wyniku polecenia user lub inne obciążenia jawne, w przeciwnym razie `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie zamykane, w przeciwnym razie `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie są otwarte, w przeciwnym razie `false`.  
  
  Można także zapewnić, że projekty i rozwiązania są ładowane (niezależnie od tego, jakie są priorytetów ładowania projektu), wywołując jedną z następujących metod:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza projektów w rozwiązaniu do załadowania przed powrotem z metody.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza projektów w `guidProject` załadować przed powrotem z metody.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza projektu w `guidProjectID` załadować przed powrotem z metody.  
  
> [!NOTE]
>  . Domyślnie tylko projekty, które mają zapotrzebowanie obciążenia i priorytety obciążenia w tle są załadowane, ale jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flaga jest przekazywany do metody, zostaną załadowane wszystkie projekty z wyjątkiem tych, które zostaną oznaczone, aby jawnie załadować.

