---
title: Zarządzanie ładowaniem projektu w rozwiązaniu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702729"
---
# <a name="manage-project-loading-in-a-solution"></a>Zarządzanie ładowaniem projektu w rozwiązaniu
Rozwiązania programu Visual Studio może zawierać dużą liczbę projektów. Domyślne zachowanie programu Visual Studio jest załadować wszystkie projekty w rozwiązaniu w momencie otwarcia rozwiązania i nie zezwalać użytkownikowi na dostęp do dowolnego z projektów, dopóki wszystkie z nich nie zostaną zakończone ładowanie. Gdy proces ładowania projektu będzie trwać dłużej niż dwie minuty, wyświetlany jest pasek postępu pokazujący liczbę załadowanych projektów i całkowitą liczbę projektów. Użytkownik może zwolnić projekty podczas pracy w rozwiązaniu z wieloma projektami, ale ta procedura ma pewne wady: niezaładowane projekty nie są tworzone jako część polecenia Odbuduj rozwiązanie, a opisy IntelliSense typów i członków zamkniętych projektów nie są wyświetlane.

 Deweloperzy mogą skrócić czas ładowania rozwiązania i zarządzać zachowaniem ładowania projektu, tworząc menedżera obciążenia rozwiązania. Menedżer ładowania rozwiązania może upewnić się, że projekty są ładowane przed rozpoczęciem kompilacji w tle, opóźniać ładowanie w tle, aż inne zadania w tle zostaną ukończone, i wykonywać inne zadania zarządzania obciążeniem projektu.

## <a name="create-a-solution-load-manager"></a>Tworzenie menedżera obciążenia rozwiązania
 Deweloperzy mogą utworzyć menedżera ładowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> rozwiązania, implementując i doradzając visual studio, że menedżer obciążenia rozwiązania jest aktywny.

### <a name="activate-a-solution-load-manager"></a>Aktywowanie menedżera ładowania rozwiązania
 Visual Studio zezwala tylko jeden menedżer ładowania rozwiązania w danym czasie, więc należy poinformować visual studio, gdy chcesz aktywować menedżera ładowania rozwiązania. Jeśli później zostanie aktywowany drugi menedżer ładowania rozwiązania, menedżer obciążenia rozwiązania zostanie odłączony.

 Musisz uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługę i ustawić [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) właściwość:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> jest wywoływana podczas zamykania programu Visual Studio lub gdy inny pakiet został przejęty jako menedżer ładowania aktywnego rozwiązania, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) nieruchomości.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dla różnych rodzajów menedżera obciążenia rozwiązania
 Menedżery obciążenia rozwiązań można implementować na różne sposoby, w zależności od typów rozwiązań, którymi mają zarządzać.

 Jeśli menedżer obciążenia rozwiązania jest przeznaczony do zarządzania ładowaniem rozwiązania w ogóle, może być zaimplementowana jako część VSPackage. Pakiet powinien być ustawiony na automatyczne <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ładowanie przez dodanie na <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>VSPackage z wartością . Menedżer obciążenia rozwiązania można następnie aktywować w metodzie. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>

> [!NOTE]
> Aby uzyskać więcej informacji na temat automatycznego ładowania pakietów, zobacz [Ładowanie pakietów VSPackages](../extensibility/loading-vspackages.md).

 Ponieważ visual studio rozpoznaje tylko ostatni menedżer obciążenia rozwiązania do aktywacji, menedżerów ogólnego obciążenia rozwiązania należy zawsze wykryć, czy istnieje istniejący menedżer obciążenia przed aktywacją siebie. Jeśli `GetProperty()` wywołanie usługi rozwiązania dla [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) zwraca `null`, nie ma aktywnego menedżera ładowania rozwiązania. Jeśli nie zwraca wartości null, sprawdź, czy obiekt jest taki sam jak menedżer ładowania rozwiązania.

 Jeśli menedżer ładowania rozwiązania jest przeznaczony do zarządzania tylko kilka typów rozwiązania, VSPackage można <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>subskrybować zdarzenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> ładowania rozwiązania (przez wywołanie), a następnie użyć programu obsługi zdarzeń, aby aktywować menedżera ładowania rozwiązania.

 Jeśli menedżer ładowania rozwiązania jest przeznaczony do zarządzania tylko określonymi rozwiązaniami, informacje o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> aktywacji mogą być utrwalane jako część pliku rozwiązania, wywołując sekcję pre-solution.

 Menedżerowie obciążenia określonego rozwiązania należy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> dezaktywować się w programie obsługi zdarzeń, aby nie kolidować z innymi menedżerami ładowania rozwiązania.

 Jeśli potrzebujesz menedżera ładowania rozwiązania tylko do utrwalania właściwości globalnego obciążenia projektu (na przykład właściwości ustawione na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> stronie Opcje), można aktywować menedżera ładowania rozwiązania w programie obsługi zdarzeń, utrwalić ustawienie we właściwościach rozwiązania, a następnie dezaktywować menedżera obciążenia rozwiązania.

## <a name="handle-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązania
 Aby zasubskrybować zdarzenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ładowania rozwiązania, wywołanie po aktywowaniu menedżera ładowania rozwiązania. Jeśli zaimplementujesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, można odpowiedzieć na zdarzenia, które odnoszą się do różnych właściwości ładowania projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To zdarzenie jest uruchamiane przed otwarciem rozwiązania.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To zdarzenie jest uruchamiane po całkowitym załadowaniu rozwiązania, ale przed ponownym rozpoczęciem ładowania projektu w tle.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: To zdarzenie jest uruchamiane po rozwiązaniu jest początkowo w pełni załadowany, niezależnie od tego, czy istnieje menedżer obciążenia rozwiązania. Jest również uruchamiany po obciążeniu tła lub obciążeniu popytu, gdy rozwiązanie zostanie w pełni załadowane. W tym samym <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> czasie jest reaktywowany.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To zdarzenie jest uruchamiane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy `pfShouldDelayLoadToNextIdle` w tle są wykonywane przed załadowaniem projektów, ustaw wartość **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To zdarzenie jest uruchamiane, gdy partia projektów ma zostać załadowana. Jeśli `fIsBackgroundIdleBatch` jest to prawda, projekty mają być ładowane w tle; jeśli `fIsBackgroundIdleBatch` jest false, projekty mają być ładowane synchronicznie w wyniku żądania użytkownika, na przykład jeśli użytkownik rozszerza oczekujące projektu w Eksploratorze rozwiązań. Możesz obsłużyć to zdarzenie, aby wykonać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>kosztowną pracę, która w przeciwnym razie musiałaby zostać wykonana w .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To zdarzenie jest uruchamiane po załadowaniu partii projektów.

## <a name="detect-and-manage-solution-and-project-loading"></a>Wykrywanie i zarządzanie ładowaniem rozwiązań i projektów
 Aby wykryć stan obciążenia projektów i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> rozwiązań, wywołaj następujące wartości:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` zwraca, `true` jeśli rozwiązanie i wszystkie jego `false`projekty są ładowane, w przeciwnym razie .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` zwraca, `true` jeśli partia projektów jest aktualnie ładowana `false`w tle, w przeciwnym razie .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` zwraca, `true` jeśli partia projektów jest obecnie ładowana synchronicznie w wyniku polecenia użytkownika `false`lub innego jawnego obciążenia, w przeciwnym razie .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` zwraca, `true` jeśli rozwiązanie jest obecnie `false`zamknięte, w przeciwnym razie .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` zwraca, `true` jeśli rozwiązanie jest obecnie otwierane, w przeciwnym razie `false`.

Można również upewnić się, że projekty i rozwiązania są ładowane przez wywołanie jednej z następujących metod:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza projekty w rozwiązaniu, aby załadować przed powrocie metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody `guidProject` wymusza projekty do załadowania przed powrocie metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody `guidProjectID` wymusza załadowanie projektu przed powrotem metody.
