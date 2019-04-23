---
title: 'Instrukcje: Zapewniają usługi asynchronicznego programu Visual Studio | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a03c4282fb7c2719f0f408759be972ead0f866
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110300"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Instrukcje: Dostarcza asynchroniczne usługi Visual Studio
Jeśli chcesz uzyskać usługi bez blokowania wątku interfejsu użytkownika, należy Tworzenie usługi asynchronicznego i załadować pakiet w wątku tła. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage> zamiast <xref:Microsoft.VisualStudio.Shell.Package>i Dodaj usługę za pomocą specjalnych metod asynchronicznych asynchronicznego pakietu.

 Aby dowiedzieć się, jak dostarczanie synchroniczne usługi Visual Studio, zobacz [jak: Oferuje usługi](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Wdrożenie usługi asynchroniczne

1. Utwórz projekt VSIX (**pliku** > **New** > **projektu** > **Visual C#**  >  **Extensiblity** > **projekt VSIX**). Nadaj projektowi nazwę **TestAsync**.

2. Dodanie pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj** > **nowy element** > **elementy Visual C#**  >  **Rozszerzalności** > **pakietu Visual Studio**. Nazwij ten plik *TestAsyncPackage.cs*.

3. W *TestAsyncPackage.cs*, zmień pakietu można dziedziczyć `AsyncPackage` zamiast `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Aby wdrożyć usługi, musisz utworzyć trzy typy:

    - Interfejs, który identyfikuje usługę. Wiele z tych interfejsów są puste, oznacza to, ponieważ mają one żadnych metod jak są używane tylko podczas wykonywania zapytań usługi.

    - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

    - Klasa, która implementuje interfejs usługi i usługi.

5. Poniższy przykład przedstawia bardzo podstawową implementację z trzech typów. Konstruktor klasy usługi należy ustawić dostawcę usług. W tym przykładzie po prostu dodamy usługę do pliku z kodem pakietu.

6. Dodaj następujące instrukcje using do pliku pakietu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Oto implementacja usługi asynchronicznego. Uwaga: należy ustawić asynchronicznego usługodawcy zamiast synchronicznych usługodawcy w Konstruktorze:

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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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
 Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, która dostarcza usługę. Rejestrowanie synchroniczne usługi jest inny, należy upewnić się, czy zarówno pakiet, jak i usługa obsługuje asynchroniczne ładowanie:

- Należy dodać **AllowsBackgroundLoading = true** pole <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> zapewnienie pakietu mogą być inicjowane asynchronicznie, aby uzyskać więcej informacji na temat PackageRegistrationAttribute zobacz [zarejestrować i Wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Należy dodać **IsAsyncQueryable = true** pole <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> aby upewnić się, wystąpienie usługi, które mogą być inicjowane asynchronicznie.

  Oto przykład `AsyncPackage` przy użyciu asynchronicznej usługi rejestracji:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Dodaj usługę

1. W *TestAsyncPackage.cs*, Usuń `Initialize()` metodę i Zastąp `InitializeAsync()` metody. Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego, trzeba utworzyć usługi. Oto przykład asynchronicznej inicjatora, dodanie usługi:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. Dodaj odwołanie do *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Jako metodę asynchroniczną, która tworzy i zwraca usługę, należy zaimplementować metodę wywołania zwrotnego.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Użyj usługi
 Teraz możesz pobrać usługę i użycie jej metod.

1. Pokazano to w inicjatorze, ale możesz uzyskać odpowiednią usługę dowolne miejsce do korzystania z usługi.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync(<userpath>), "this is a test");
    }

    ```

     Nie zapomnij zmienić  *\<userpath >* do nazwy pliku i ścieżkę, która ma sens na swojej maszynie!

2. Skompiluj i uruchom kod. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, otwórz rozwiązanie. Powoduje to, że `AsyncPackage` na automatyczne ładowanie. Po uruchomieniu inicjatora powinien znajdować się plik w podanej lokalizacji.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Przy użyciu usługi asynchronicznego programu obsługi poleceń
 Oto przykład sposobu użycia usługi asynchroniczne za pomocą polecenia menu. Można użyć procedury pokazano poniżej, korzystanie z usługi za pomocą innych metod asynchronicznego.

1. Dodaj polecenie menu do projektu. (W **Eksploratora rozwiązań**, wybierz węzeł projektu, kliknij prawym przyciskiem myszy i wybierz **Dodaj** > **nowy element**  >   **Rozszerzalność** > **polecenie niestandardowe**.) Nazwa pliku polecenia *TestAsyncCommand.cs*.

2. Ponownie dodaje szablon polecenie niestandardowe `Initialize()` metody *TestAsyncPackage.cs* plik w celu zainicjowania polecenia. W `Initialize()` metody Kopiuj linię, która inicjuje polecenia. Powinny wyglądać następująco:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Ten wiersz, aby przenieść `InitializeAsync()` method in Class metoda *AsyncPackageForService.cs* pliku. Ponieważ jest to asynchronicznego inicjalizacji, musisz przełączyć się do wątku głównego przed zainicjowaniem, za pomocą polecenia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Powinna teraz wyglądać następująco:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync((<userpath>, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Usuń `Initialize()` metody.

4. W *TestAsyncCommand.cs* plików, Znajdź `MenuItemCallback()` metody. Usunięcie treści metody.

5. Dodaj instrukcję using instrukcji:

    ```csharp
    using System.IO;
    ```

6. Dodaj metodę asynchroniczną o nazwie `UseTextWriterAsync()`, która pobiera usługi i korzysta z jego metody:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        // don't forget to change <userpath> to a local path
        await textService.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Wywołanie tej metody z `MenuItemCallback()` metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, przejdź do **narzędzia** menu i zwróć uwagę na **wywołania TestAsyncCommand** elementu menu. Po kliknięciu go TextWriterService zapisuje do podanego pliku. (Nie trzeba otworzyć rozwiązanie, ponieważ wywoływanie polecenia również powoduje, że pakiet do załadowania.)

## <a name="see-also"></a>Zobacz także
- [Użyj i świadczenia usług](../extensibility/using-and-providing-services.md)
