---
title: 'Jak: Zapewnienie usługi Asynchronous Visual Studio | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710767"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Jak: Zapewnienie usługi asynchronii visual studio
Jeśli chcesz uzyskać usługę bez blokowania wątku interfejsu użytkownika, należy utworzyć usługę asynchroniiową i załadować pakiet w wątku w tle. W tym celu można <xref:Microsoft.VisualStudio.Shell.AsyncPackage> użyć <xref:Microsoft.VisualStudio.Shell.Package>zamiast , i dodać usługę ze specjalnymi metodami asynchronizajny pakietu asynchroniiowego pakietu asynchroniiowego.

 Aby uzyskać informacje dotyczące świadczenia synchronicznych usług programu Visual Studio, zobacz [Jak: Świadczenie usługi](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementowanie usługi asynchroniiowej

1. Tworzenie projektu VSIX (**Plik** > **nowy** > **projekt** > Visual**C#** > **Extensiblity** > **VSIX Project**). Nazwij projekt **TestAsync**.

2. Dodaj VSPackage do projektu. Wybierz węzeł projektu w **Eksploratorze rozwiązań** i kliknij pozycję **Dodaj** > **nowy element** > **Visual C# Element** > **Rozszerzalność** > **pakietu programu Visual Studio**. Nazwij ten plik *TestAsyncPackage.cs*.

3. W *TestAsyncPackage.cs*, zmień pakiet, `AsyncPackage` aby `Package`dziedziczyć, a nie:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Aby zaimplementować usługę, należy utworzyć trzy typy:

    - Interfejs, który identyfikuje usługę. Wiele z tych interfejsów są puste, oznacza to, że nie mają żadnych metod, ponieważ są one używane tylko do wykonywania zapytań usługi.

    - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody, które mają być zaimplementowane.

    - Klasa, która implementuje zarówno usługi i interfejsu usługi.

5. Poniższy przykład przedstawia bardzo podstawową implementację trzech typów. Konstruktor klasy usługi musi ustawić dostawcę usług. W tym przykładzie po prostu dodamy usługę do pliku kodu pakietu.

6. Dodaj następujące informacje za pomocą dyrektyw do pliku pakietu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Oto implementacja usługi asynchroniiowej. Należy zauważyć, że należy ustawić asynchroniczowego dostawcy usług, a nie synchroniczne dostawcy usług w konstruktorze:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Zarejestruj usługę
 Aby zarejestrować usługę, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> dodaj do pakietu, który udostępnia usługę. Różni się od rejestrowania usługi synchroniczowej, musisz upewnić się, że zarówno pakiet, jak i obsługa usługi obsługuje ładowanie asynchroniczne:

- Należy dodać **Pole AllowsBackgroundLoading =** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> true do, aby upewnić się, że pakiet może być inicjowany asynchronicznie Aby uzyskać więcej informacji na temat packageregistrationAttribute, zobacz [Zarejestruj i wyrejestruuj pakiet VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Należy dodać **IsAsyncQueryable = true** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> pole do, aby upewnić się, że wystąpienie usługi mogą być inicjowane asynchronicznie.

  Oto przykład `AsyncPackage` rejestracji usługi asynchroniiowej:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Dodawanie usługi

1. W *TestAsyncPackage.cs*, usunąć `Initialize()` metodę i zastąpić `InitializeAsync()` metodę. Dodaj usługę i dodaj metodę wywołania zwrotnego, aby utworzyć usługi. Oto przykład asynchroniiowego inicjatora dodawania usługi:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Aby ta usługa była widoczna poza tym pakietem, ustaw wartość flagi podwyższenia na *true* jako ostatni parametr:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Dodaj odwołanie do pliku *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Zaimplementuj metodę wywołania zwrotnego jako metodę asynchronizacjową, która tworzy i zwraca usługę.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Korzystanie z usługi
 Teraz możesz uzyskać usługę i korzystać z jej metod.

1. Pokażemy to w inicjatorze, ale możesz uzyskać usługę w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, w której chcesz korzystać z usługi.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Nie zapomnij zmienić `userpath` na nazwę pliku i ścieżkę, która ma sens na komputerze!

2. Skompiluj i uruchom kod. Po wyświetleniu eksperymentalnego wystąpienia programu Visual Studio otwórz rozwiązanie. Powoduje `AsyncPackage` to automatyczne ładowanie. Po uruchomieniu inicjatora należy znaleźć plik w określonej lokalizacji.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Używanie usługi asynchroniiowej w programie obsługi poleceń
 Oto przykład użycia usługi asynchroniiowej w poleceniu menu. Można użyć procedury pokazanej w tym miejscu, aby korzystać z usługi w innych metodach nieasynchronicznych.

1. Dodaj polecenie menu do projektu. (W **Eksploratorze rozwiązań**wybierz węzeł projektu, kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj** > nowe**polecenie niestandardowe****rozszerzalności** > **elementu).** >  Nazwij plik polecenia *TestAsyncCommand.cs*.

2. Niestandardowy szablon polecenia ponownie `Initialize()` dodaje metodę do pliku *TestAsyncPackage.cs* w celu zainicjowania polecenia. W `Initialize()` metodzie skopiuj wiersz, który inicjuje polecenie. Powinny wyglądać następująco:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Przenieś ten wiersz `InitializeAsync()` do metody w pliku *AsyncPackageForService.cs.* Ponieważ jest to inicjalizacja asynchroniza, należy przełączyć się do <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>wątku głównego przed zainicjowaniem polecenia za pomocą . Teraz powinno to wyglądać następująco:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Usuń `Initialize()` metodę.

4. W pliku *TestAsyncCommand.cs* znajdź `MenuItemCallback()` metodę. Usuń treść metody.

5. Dodaj za pomocą dyrektywy:

    ```csharp
    using System.IO;
    ```

6. Dodaj metodę asynchronizaj o nazwie `UseTextWriterAsync()`, która pobiera usługę i używa jej metod:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Wywołanie tej `MenuItemCallback()` metody z metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Skompiluj rozwiązanie i rozpocznij debugowanie. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, przejdź do menu **Narzędzia** i poszukaj elementu menu **Invoke TestAsyncCommand.** Po kliknięciu, TextWriterService zapisuje do określonego pliku. (Nie trzeba otwierać rozwiązania, ponieważ wywołanie polecenia powoduje również załadowanie pakietu).

## <a name="see-also"></a>Zobacz też
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
