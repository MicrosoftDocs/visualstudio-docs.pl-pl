---
title: 'Instrukcje: używanie AsyncPackage do ładowania pakietów VSPackage w tle | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 7727d53c84ab876fe6616c8ec5d438033216481e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905593"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Instrukcje: używanie AsyncPackage do ładowania pakietów VSPackage w tle
Załadowanie i zainicjowanie pakietu programu VS może spowodować powstanie we/wy dysku. Jeśli takie operacje we/wy wystąpią w wątku interfejsu użytkownika, może to prowadzić do problemów z czasem odpowiedzi. W programie Visual Studio 2015 wprowadzono  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> klasę, która umożliwia ładowanie pakietów w wątku w tle.

## <a name="create-an-asyncpackage"></a>Utwórz AsyncPackage
 Możesz rozpocząć od utworzenia projektu VSIX (**plik**  >  **Nowy**  >  **projekt**  >  **Visual C#**  >  **rozszerzalności**Visual C#  >  ,**Projekt VSIX**) i dodanie pakietu VSPackage do projektu (kliknij prawym przyciskiem myszy projekt i **Dodaj**  >  **nowy element**  >  **C# item**  >  **Rozszerzalny**element kodu w języku C#  >  **Visual Studio Package**). Następnie możesz utworzyć usługi i dodać te usługi do pakietu.

1. Utwórz pakiet z programu <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .

2. Jeśli dostarczasz usługi, których wykonywanie zapytania może spowodować załadowanie pakietu:

    Aby wskazać programowi Visual Studio, że pakiet jest bezpieczny do załadowania w tle i aby to zrobić, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> należy ustawić właściwość **AllowsBackgroundLoading** na true w konstruktorze atrybutu.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Aby wskazać programowi Visual Studio bezpieczne wystąpienie usługi w wątku w tle, należy ustawić <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Właściwość na wartość true w <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> konstruktorze.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. W przypadku ładowania za pomocą kontekstów interfejsu użytkownika należy określić **PackageAutoLoadFlags. BackgroundLoad** dla <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> lub wartość (0x2) do flag zapisanych jako wartość wpisu ładowania automatyczne pakietu.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Jeśli asynchroniczna Inicjalizacja została zainicjowana, należy przesłonić <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Usuń `Initialize()` metodę dostarczoną przez szablon VSIX. ( `Initialize()` Metoda w **AsyncPackage** jest zapieczętowana). <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>Aby dodać usługi asynchroniczne do pakietu, można użyć dowolnej z tych metod.

    Uwaga: aby wywołać `base.InitializeAsync()` , możesz zmienić kod źródłowy na:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Należy zachować ostrożność, aby nie wykonywać zdalnych wywołań procedur (zdalne wywołanie procedury) z kodu inicjacji asynchronicznej (w **InitializeAsync**). Mogą wystąpić w przypadku wywołania <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> bezpośrednio lub pośrednio.  Gdy wymagane są obciążenia synchronizacji, wątek interfejsu użytkownika blokuje użycie <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Domyślny model blokowania wyłącza zdalne wywołania procedury. Oznacza to, że jeśli spróbujesz użyć wywołania RPC z zadań asynchronicznych, wystąpi zakleszczenie, jeśli wątek interfejsu użytkownika zaczeka na załadowanie pakietu. Ogólna alternatywa polega na kierowaniu kodu do wątku interfejsu użytkownika, jeśli jest to konieczne przy użyciu **dołączanej fabryki zadań** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> lub innego mechanizmu, który nie korzysta z wywołania RPC.  NIE należy używać **ThreadHelper. Generic. Invoke** ani ogólnie blokować wątek wywołujący oczekujący na przejście do wątku interfejsu użytkownika.

    Uwaga: należy unikać używania metody **GetService** lub **QueryService** w `InitializeAsync` metodzie. Jeśli musisz korzystać z tych funkcji, musisz najpierw przełączyć się do wątku interfejsu użytkownika. Alternatywą jest użycie <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> z **AsyncPackage** (przez rzutowanie na <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .)

   C#: Tworzenie elementu AsyncPackage:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konwertuj istniejący pakietu VSPackage na AsyncPackage
 Większość pracy jest taka sama jak w przypadku tworzenia nowego **AsyncPackage**. Wykonaj kroki od 1 do 5 powyżej. Należy również zachować wyjątkową ostrożność, wykonując następujące zalecenia:

1. Pamiętaj, aby usunąć `Initialize` zastąpienie w pakiecie.

2. Unikaj zakleszczenii: w kodzie mogą znajdować się ukryte zdalne wywołania procedury. który teraz występuje w wątku w tle. Upewnij się, że jeśli korzystasz z usługi RPC (na przykład **GetService**), musisz albo (1) przełączyć do głównego wątku lub (2) użyć asynchronicznej wersji interfejsu API, jeśli taka istnieje (na przykład **GetServiceAsync**).

3. Nie przełączaj między wątkami zbyt często. Spróbuj zlokalizować działanie, które może wystąpić w wątku w tle, aby skrócić czas ładowania.

## <a name="querying-services-from-asyncpackage"></a>Wykonywanie zapytań względem usług z AsyncPackage
 **AsyncPackage** może lub nie może ładować się asynchronicznie w zależności od obiektu wywołującego. Na przykład

- Jeśli obiekt wywołujący o nazwie **GetService** lub **QueryService** (synchroniczne interfejsy API) lub

- Jeśli obiekt wywołujący o nazwie **IVsShell:: LoadPackage** (lub **IVsShell5:: LoadPackageWithContext**) lub

- Obciążenie jest wyzwalane przez kontekst interfejsu użytkownika, ale nie określono mechanizmu kontekstu interfejsu użytkownika, który może ładować Cię asynchronicznie

  następnie pakiet zostanie załadowany synchronicznie.

  Pakiet nadal ma szansę (w swojej asynchronicznej fazie inicjowania) do pracy z wątkiem interfejsu użytkownika, chociaż wątek interfejsu użytkownika zostanie zablokowany dla ukończenia tego działania. Jeśli obiekt wywołujący używa **IAsyncServiceProvider** do asynchronicznego zapytania dla usługi, to obciążenie i Inicjalizacja zostaną wykonane asynchronicznie, przy założeniu, że nie będą natychmiast blokowane w obiekcie zadania.

  C#: jak wysyłać zapytania do usługi asynchronicznej:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
