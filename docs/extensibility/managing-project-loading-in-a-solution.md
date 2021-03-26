---
title: Zarządzanie ładowaniem projektu w rozwiązaniu | Microsoft Docs
description: Dowiedz się, w jaki sposób deweloperzy mogą skrócić czasy ładowania rozwiązań i zarządzać zachowaniem ładowania projektu, tworząc Menedżera obciążenia rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 425f610e8a473460cb7d9170138521e2e7bee08a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073095"
---
# <a name="manage-project-loading-in-a-solution"></a>Zarządzanie ładowaniem projektu w rozwiązaniu
Rozwiązania programu Visual Studio mogą zawierać wiele projektów. Domyślne zachowanie programu Visual Studio polega na załadowaniu wszystkich projektów w rozwiązaniu w momencie otwarcia rozwiązania, a nie umożliwieniu użytkownikowi dostępu do żadnego z projektów do momentu zakończenia jego ładowania. Gdy proces ładowania projektu będzie trwać więcej niż dwie minuty, zostanie wyświetlony pasek postępu przedstawiający liczbę załadowanych projektów i łączną liczbę projektów. Użytkownik może zwolnić projekty podczas pracy w rozwiązaniu z wieloma projektami, ale ta procedura ma pewne wady: niezaładowane projekty nie są kompilowane jako część polecenia odbudowywania rozwiązania, a opisy typów i elementów członkowskich zamkniętych projektów nie są wyświetlane.

 Deweloperzy mogą skrócić czasy ładowania rozwiązań i zarządzać zachowaniem ładowania projektu, tworząc Menedżera ładowania rozwiązań. Menedżer obciążenia rozwiązań może upewnić się, że projekty są ładowane przed rozpoczęciem kompilacji w tle, opóźnić ładowanie w tle do momentu zakończenia innych zadań w tle i wykonać inne zadania związane z zarządzaniem obciążeniem projektu.

## <a name="create-a-solution-load-manager"></a>Tworzenie Menedżera ładowania rozwiązań
 Deweloperzy mogą utworzyć Menedżera obciążenia rozwiązań, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> i powiadamiając program Visual Studio, że Menedżer obciążenia rozwiązań jest aktywny.

### <a name="activate-a-solution-load-manager"></a>Aktywuj Menedżera ładowania rozwiązań
 Program Visual Studio umożliwia korzystanie z tylko jednego menedżera ładowania rozwiązań w danym momencie, dlatego musisz polecić programowi Visual Studio, gdy chcesz aktywować Menedżera obciążenia rozwiązania. Jeśli drugi Menedżer ładowania rozwiązań został aktywowany później w systemie, Menedżer obciążenia rozwiązań zostanie odłączony.

 Musisz pobrać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługę i ustawić [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) Właściwość:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Metoda jest wywoływana, gdy program Visual Studio jest zamykany lub gdy inny pakiet został przejęty jako aktywny Menedżer ładowania rozwiązań, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> przy użyciu [__VSPROPID4. Właściwość VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) .

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dotyczące różnych rodzajów Menedżera ładowania rozwiązań
 Można zaimplementować menedżerów obciążeń rozwiązań na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.

 Jeśli Menedżer obciążenia rozwiązań ma ogólnie zarządzać ładowaniem rozwiązań, można go zaimplementować jako część pakietu VSPackage. Pakiet powinien być ustawiony na automatyczne ładowanie przez dodanie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> elementu pakietu VSPackage z wartością <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Można następnie aktywować Menedżera ładowania rozwiązań w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie.

> [!NOTE]
> Aby uzyskać więcej informacji na temat pakietów ładowania automatyczne, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

 Ponieważ program Visual Studio rozpoznaje tylko ostatni Menedżer ładowania rozwiązań, który ma zostać aktywowany, menedżerowie ogólnego ładowania rozwiązań powinni zawsze wykrywać, czy istnieje istniejący Menedżer obciążenia przed uaktywnieniem siebie. W przypadku wywoływania `GetProperty()` usługi rozwiązania dla [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) zwraca `null` , nie istnieje aktywny Menedżer ładowania rozwiązań. Jeśli nie zwraca wartości null, sprawdź, czy obiekt jest taki sam jak w przypadku Menedżera obciążenia rozwiązań.

 Jeśli Menedżer obciążenia rozwiązań ma zarządzać tylko kilkoma typami rozwiązań, pakietu VSPackage może subskrybować zdarzenia ładowania rozwiązania (poprzez wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) i użyć programu obsługi zdarzeń dla programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> w celu aktywowania Menedżera ładowania rozwiązań.

 Jeśli Menedżer obciążenia rozwiązań ma zarządzać tylko określonymi rozwiązaniami, informacje o aktywacji mogą być utrwalane w ramach pliku rozwiązania, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> dla sekcji wstępnego rozwiązania.

 Określeni Menedżery ładowania rozwiązań powinni dezaktywować się w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> obsługi zdarzeń, aby nie powodowały konfliktów z innymi menedżerami ładowania rozwiązań.

 Jeśli potrzebujesz Menedżera ładowania rozwiązań tylko do utrwalania globalnych właściwości ładowania projektu (na przykład właściwości ustawionych na stronie Opcje), możesz aktywować Menedżera obciążenia rozwiązań w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> obsługi zdarzeń, zachować ustawienie we właściwościach rozwiązania, a następnie dezaktywować Menedżera ładowania rozwiązań.

## <a name="handle-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązania
 Aby subskrybować zdarzenia ładowania rozwiązania, Połącz się, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> gdy aktywujesz Menedżera ładowania rozwiązań. W przypadku zaimplementowania programu można <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> reagować na zdarzenia, które odnoszą się do różnych właściwości ładowania projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To zdarzenie jest wywoływane przed otwarciem rozwiązania.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To zdarzenie jest wywoływane po całkowitym załadowaniu rozwiązania, ale przed ponownym rozpoczęciem ładowania projektu w tle.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: To zdarzenie jest wywoływane po pierwszym całkowitym załadowaniu rozwiązania, niezależnie od tego, czy jest to Menedżer obciążenia rozwiązań. Jest również uruchamiany po załadowaniu w tle lub załadowaniu na żądanie, gdy rozwiązanie zostanie w pełni załadowane. W tym samym czasie program <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> zostanie ponownie aktywowany.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To zdarzenie jest wywoływane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle są kończone przed załadowaniem projektów, ustaw `pfShouldDelayLoadToNextIdle` na **wartość true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To zdarzenie jest wywoływane, gdy zostanie załadowana partia projektów. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty są ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość false, projekty są ładowane synchronicznie w wyniku żądania użytkownika, na przykład jeśli użytkownik rozwinie oczekujący projekt w Eksplorator rozwiązań. To zdarzenie można obsłużyć kosztowną służbę, która w przeciwnym razie trzeba będzie wykonać w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To zdarzenie jest wywoływane po załadowaniu partii projektów.

## <a name="detect-and-manage-solution-and-project-loading"></a>Wykrywaj rozwiązanie i ładowanie projektu i zarządzaj nimi
 W celu wykrycia stanu ładowania projektów i rozwiązań należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> następujące wartości:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` zwraca `true` czy rozwiązanie i wszystkie jego projekty są ładowane, w przeciwnym razie `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` zwraca `true` czy wsadowe projekty są aktualnie ładowane w tle, w przeciwnym razie `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` zwraca `true` czy wsadowe projekty są aktualnie ładowane synchronicznie w wyniku polecenia użytkownika lub innego, niejawnego obciążenia, w przeciwnym razie `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` zwraca `true` czy rozwiązanie jest aktualnie zamykane, w przeciwnym razie `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` zwraca `true` czy rozwiązanie jest aktualnie otwierane, w przeciwnym razie `false` .

Możesz również upewnić się, że projekty i rozwiązania są ładowane przez wywołanie jednej z następujących metod:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza załadowanie projektów w rozwiązaniu przed zwróceniem metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza `guidProject` załadowanie projektów przed zwróceniem metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza `guidProjectID` załadowanie projektu przed zwróceniem metody.
