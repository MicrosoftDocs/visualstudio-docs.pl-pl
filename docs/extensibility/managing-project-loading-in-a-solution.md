---
title: Zarządzanie ładowaniem projektu w rozwiązaniu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 90a97097eed7b97ad96bfda1f5520d1a9b4f0203
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335405"
---
# <a name="manage-project-loading-in-a-solution"></a>Zarządzanie ładowaniem projektu w rozwiązaniu
Rozwiązania programu Visual Studio mogą zawierać dużą liczbę projektów. Domyślne zachowanie programu Visual Studio jest można załadować wszystkich projektów w rozwiązaniu w czasie, które rozwiązanie jest otwierane, a nie Zezwalaj użytkownikowi dostępu do żadnego z projektów wszystkich z nich ma zakończenie ładowania. Podczas procesu ładowania projektu trwa więcej niż dwie minuty, jest wyświetlany pasek postępu, przedstawiający liczbę projektów i łącznej liczby projektów. Użytkownik może zwolnienia projektów podczas pracy w ramach rozwiązania z wieloma projektami, ale ta procedura ma pewne wady: zwolniono projekty są kompilowane jako część polecenia Kompiluj rozwiązanie i zamknięcie IntelliSense opisy typów i elementów członkowskich projekty nie są wyświetlane.

 Deweloperzy mogą skrócić czas ładowania rozwiązania i zarządzać ładowanie zachowanie, tworząc ładowania rozwiązań menedżera projektu. Menedżera obciążenia rozwiązania można upewnij się, że projekty zostały załadowane przed rozpoczęciem kompilacji tła, opóźnienie w tle podczas ładowania dopiero po zakończeniu innego zadania w tle i wykonywać inne zadania zarządzania ładowania projektu.

## <a name="create-a-solution-load-manager"></a>Tworzenie Menedżera ładowania rozwiązań
 Deweloperzy mogą tworzyć ładowania rozwiązań Menedżera implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> i wniosku programu Visual Studio, czy Menedżera obciążenia rozwiązania jest aktywny.

### <a name="activate-a-solution-load-manager"></a>Aktywowanie Menedżera obciążenia rozwiązania
 Program Visual Studio umożliwia rozwiązanie tylko jednego z kierowników obciążenia w danym momencie, dlatego konieczne jest poinformowanie programu Visual Studio aktywować obciążenia rozwiązania menedżera. Jeśli drugi Menedżera obciążenia rozwiązania została aktywowana później, rozwiązanie Menedżera obciążenia zostaną rozłączone.

 Należy uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługi i ustaw [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) właściwości:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Metoda jest wywoływana, gdy trwa zamykanie programu Visual Studio lub inny pakiet przejmuje jako Menedżer ds. rozwiązania aktywnego obciążenia przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) właściwości.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dotyczące różnych rodzajów Menedżera obciążenia rozwiązania
 Menedżerowie obciążenia rozwiązania można zaimplementować na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.

 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania ogólnie rzecz biorąc ładowania rozwiązania, można zaimplementować jako część pakietu VSPackage. Pakiet powinna być ustawiona na automatyczne ładowanie, dodając <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na VSPackage o wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Następnie można aktywować Menedżera obciążenia rozwiązania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

> [!NOTE]
>  Aby uzyskać więcej informacji na temat pakietów autoloading zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

 Ponieważ program Visual Studio rozpoznaje tylko ostatni rozwiązania obciążenia Menedżera aktywacji, menedżerów obciążenia ogólne rozwiązanie powinien zawsze wykrywa, czy przed aktywowaniem samodzielnie jest istniejącego menedżera obciążenia. Jeśli wywołanie `GetProperty()` usłudze rozwiązania dla [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) zwraca `null`, istnieje nie aktywne rozwiązanie Menedżera obciążenia. Jeśli nie zwróci wartość null, sprawdź, czy obiekt jest taki sam jak Menedżer ładowania rozwiązania.

 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko kilka typów rozwiązania, pakietu VSPackage mogą subskrybować zdarzeń ładowania rozwiązania (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) i użyj programu obsługi zdarzeń <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktywować Menedżera obciążenia rozwiązania.

 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko określone rozwiązania, informacje o aktywacji, może być utrwalony jako część pliku rozwiązania przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> dla sekcji rozwiązania wstępnego.

 Menedżerowie ładowania konkretnego rozwiązania dezaktywować w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> procedura obsługi zdarzeń, aby nie powodują konflikt z innych menedżerów ładowania rozwiązania.

 Jeśli potrzebujesz Menedżera obciążenia rozwiązanie tylko do utrwalenia właściwości obciążenia projektu globalnego (na przykład zbioru właściwości na stronie Opcje), możesz aktywować Menedżera obciążenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> programu obsługi zdarzeń utrwalić ustawienie we właściwościach rozwiązania, a następnie Dezaktywuj Menedżera obciążenia rozwiązania.

## <a name="handle-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązań
 Aby subskrybować zdarzeń ładowania rozwiązania, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> po aktywacji usługi Menedżera obciążenia rozwiązania. W przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, pozwalające reagować na zdarzenia, które odnoszą się do innego projektu ładowania właściwości.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To zdarzenie jest wywoływane przed otwarciem rozwiązania.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To zdarzenie jest wywoływane po całkowitym załadowaniu rozwiązania, ale przed tła ładowanie projektu rozpoczyna się od nowa.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: To zdarzenie jest wywoływane po początkowym pełni załadowaniu rozwiązania, czy istnieje Menedżera obciążenia rozwiązania. Również wyzwoleniu po obciążenia tło lub żądanie załadowania zawsze wtedy, gdy rozwiązanie staje się w pełni załadowane. W tym samym czasie <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> zostanie ponownie aktywowany.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To zdarzenie jest wywoływane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle odbywa się przed projekty są ładowane, należy ustawić `pfShouldDelayLoadToNextIdle` do **true**.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To zdarzenie jest wywoływane, gdy partii projektów ma być załadowany. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty mają być ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość FAŁSZ, projekty są mają zostać załadowane synchronicznie w wyniku żądania użytkownika, na przykład jeśli użytkownik rozwija oczekujące projekt w Eksploratorze rozwiązań. Może obsługiwać to zdarzenie, aby spełniała kosztowne, które w przeciwnym razie musi odbywać się w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To zdarzenie jest wywoływane po załadowaniu partii projektów.

## <a name="detect-and-manage-solution-and-project-loading"></a>Wykrywanie i zarządzanie nimi rozwiązania i ładowanie projektu
 W celu wykrycia stan ładowania projektów i rozwiązań, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> z następującymi wartościami:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` zwraca `true` Jeśli rozwiązanie i jego projekty są załadowane, w przeciwnym razie `false`.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` zwraca `true` Jeśli partii projekty są obecnie ładowane w tle, w przeciwnym razie `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` zwraca `true` Jeśli partii projektów aktualnie Trwa ładowanie synchronicznie wyniku polecenia user lub inne obciążenia jawne, w przeciwnym razie `false`.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` zwraca `true` Jeśli rozwiązanie jest obecnie zamykane, w przeciwnym razie `false`.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` zwraca `true` Jeśli rozwiązanie jest obecnie są otwarte, w przeciwnym razie `false`.

Może również zagwarantować, że projekty i rozwiązania są ładowane, wywołując jedną z następujących metod:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza projektów w rozwiązaniu do załadowania przed powrotem z metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza projektów w `guidProject` załadować przed powrotem z metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza projektu w `guidProjectID` załadować przed powrotem z metody.
