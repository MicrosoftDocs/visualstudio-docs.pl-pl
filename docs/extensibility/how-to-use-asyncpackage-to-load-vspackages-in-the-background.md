---
title: 'Jak: Użyj AsyncPackage załadować VSPackages w tle | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710618"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Jak: Użyj AsyncPackage, aby załadować pakiety VSPackages w tle
Ładowanie i inicjowanie pakietu VS może spowodować we/wy dysku. Jeśli takie we/wy dzieje się w wątku interfejsu użytkownika, może to prowadzić do problemów z responsywnością. Aby rozwiązać ten problem, Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015 wprowadzono klasę, która umożliwia ładowanie pakietu w wątku w tle.

## <a name="create-an-asyncpackage"></a>Tworzenie pakietu AsyncPackage
 Można rozpocząć od utworzenia projektu VSIX **(File** > **New** > **Project** > Visual**C#** > **Extensibility** > **VSIX Project**) i dodania VSPackage do projektu (kliknij prawym przyciskiem myszy na projekt i **Dodaj** > nowy**element** > **C# pakiet** > **rozszerzalności** > programu Visual**Studio**). Następnie można utworzyć usługi i dodać te usługi do pakietu.

1. Wyprowadzić pakiet <xref:Microsoft.VisualStudio.Shell.AsyncPackage>z .

2. Jeśli świadczysz usługi, których wykonywanie zapytań może spowodować załadowanie pakietu:

    Aby wskazać visual studio, że pakiet jest bezpieczny dla ładowania <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w tle i zdecydować się na to zachowanie, należy ustawić **AllowsBackgroundLoading** właściwość true w konstruktorze atrybutów.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Aby wskazać visual studio, że jest bezpieczny do wystąpienia usługi w wątku w tle, należy ustawić <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> właściwość true w konstruktorze. <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Jeśli ładujesz za pośrednictwem kontekstów interfejsu użytkownika, należy określić **PackageAutoLoadFlags.BackgroundLoad** dla <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> LUB wartość (0x2) do flag zapisanych jako wartość wpisu automatycznego ładowania pakietu.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Jeśli masz do wykonania asynchroniię inicjalizacji, należy zastąpić <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Usuń `Initialize()` metodę dostarczoną przez szablon VSIX. (Metoda `Initialize()` w **AsyncPackage** jest zapieczętowana). Można użyć dowolnej <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> z metod, aby dodać usługi asynchroniczne do pakietu.

    UWAGA: Aby `base.InitializeAsync()`zadzwonić, możesz zmienić kod źródłowy na:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Należy zadbać, aby NIE tworzyć RPC (Remote Procedure Call) z kodu inicjowania asynchronicznego **(inicjujeAsync**). Mogą one wystąpić <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> podczas wywoływania bezpośrednio lub pośrednio.  Gdy wymagane są obciążenia synchronizacji, wątek <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>interfejsu użytkownika zablokuje użycie . Domyślny model blokowania wyłącza kontrolery RPC. Oznacza to, że jeśli spróbujesz użyć RPC z zadań asynchronii, będzie zakleszczenie, jeśli wątek interfejsu użytkownika jest sam czeka na pakiet do załadowania. Ogólną alternatywą jest organizowanie kodu do wątku interfejsu użytkownika, jeśli <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> jest to konieczne przy użyciu czegoś takiego jak **Joinable Task Factory**'s lub inny mechanizm, który nie używa RPC.  NIE należy używać **ThreadHelper.Generic.Invoke** lub zazwyczaj zablokować wątku wywołującego oczekiwania, aby uzyskać do wątku interfejsu użytkownika.

    UWAGA: Należy unikać korzystania **z GetService** lub **QueryService** w metodzie. `InitializeAsync` Jeśli trzeba użyć tych, należy najpierw przełączyć się do wątku interfejsu użytkownika. Alternatywą jest <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> użycie z **AsyncPackage** (przez <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>przerzucenie go do .)

   C#: Utwórz pakiet AsyncPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konwertowanie istniejącego pakietu VSPackage na pakiet AsyncPackage
 Większość pracy jest taka sama jak tworzenie nowego **AsyncPackage**. Wykonaj kroki od 1 do 5 powyżej. Należy również zachować szczególną ostrożność stosując następujące zalecenia:

1. Pamiętaj, aby `Initialize` usunąć zastąpienie, które miało w pakiecie.

2. Unikaj zakleszczenia: W kodzie mogą znajdować się ukryte kontrolery RPC. które teraz zdarzają się w wątku w tle. Upewnij się, że w przypadku tworzenia RPC (na przykład **GetService**), musisz przełączyć się na wątek główny lub (2) użyć asynchronicznej wersji interfejsu API, jeśli taka istnieje (na przykład **GetServiceAsync**).

3. Nie przełączaj się między wątkami zbyt często. Spróbuj zlokalizować pracę, która może się zdarzyć w wątku w tle, aby skrócić czas ładowania.

## <a name="querying-services-from-asyncpackage"></a>Wykonywanie zapytań z AsyncPackage
 **AsyncPackage** może lub nie może załadować asynchronicznie w zależności od wywołującego. Na przykład,

- Jeśli wywołujący o nazwie **GetService** lub **QueryService** (oba synchroniczne interfejsy API) lub

- Jeśli wywołujący o nazwie **IVsShell::LoadPackage** (lub **IVsShell5::LoadPackageWithContext**) lub

- Obciążenie jest wyzwalane przez kontekst interfejsu użytkownika, ale nie określono mechanizmu kontekstu interfejsu użytkownika można załadować asynchronicznie

  następnie pakiet zostanie załadowany synchronicznie.

  Pakiet nadal ma możliwość (w fazie inicjowania asynchronii) do pracy poza wątku interfejsu użytkownika, chociaż wątek interfejsu użytkownika zostanie zablokowany do zakończenia tej pracy. Jeśli obiekt wywołujący używa **IAsyncServiceProvider** do asynchronicznego kwerendy dla usługi, a następnie obciążenia i inicjowania zostaną wykonane asynchronicznie przy założeniu, że nie natychmiast zablokować wynikowy obiekt zadania.

  C#: Jak kwerendy usługi asynchronicznie:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
