---
title: 'Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d486aac8e990fef6b139bca989a51d74146ecb67
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826409"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio
Jeśli chcesz uzyskać usługi bez blokowania wątku interfejsu użytkownika, należy Tworzenie usługi asynchronicznego i załadować pakiet w wątku tła. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage>, a nie <xref:Microsoft.VisualStudio.Shell.Package>, i dodać usługę z zastosowaniem specjalnych metod asynchronicznych pakietu asynchronicznego.

 Aby uzyskać informacje o dostarczaniu synchronicznych usług programu Visual Studio, zobacz [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementowanie usługi asynchronicznej

1. Utwórz projekt VSIX (**plik** > **Nowy** > **Project** > **Visual C#**  > **Extensiblity** > **Project VSIX**). Nadaj projektowi nazwę **TestAsync**.

2. Dodanie pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań** a następnie kliknij pozycję **Dodaj** > **nowy element** > **elementy C# wizualne** > **rozszerzalność** > **pakiet programu Visual Studio**. Nazwij ten plik *TestAsyncPackage.cs*.

3. W *TestAsyncPackage.cs*Zmień pakiet, aby dziedziczyć po `AsyncPackage`, a nie `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Aby wdrożyć usługi, musisz utworzyć trzy typy:

    - Interfejs, który identyfikuje usługę. Wiele z tych interfejsów jest pustych, czyli nie ma metod, ponieważ są one używane tylko do wykonywania zapytań dotyczących usługi.

    - Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

    - Klasa, która implementuje interfejs usługi i usługi.

5. Poniższy przykład przedstawia bardzo podstawową implementację z trzech typów. Konstruktor klasy usługi należy ustawić dostawcę usług. W tym przykładzie dodamy usługę do pliku kodu pakietu.

6. Dodaj następujące dyrektywy using do pliku pakietu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Oto implementacja usługi asynchronicznej. Uwaga: należy ustawić asynchronicznego usługodawcy zamiast synchronicznych usługodawcy w Konstruktorze:

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

## <a name="register-a-service"></a>Rejestrowanie usługi
 Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, która dostarcza usługę. Aby zarejestrować usługę synchroniczną, należy się upewnić, że oba pakiety i usługi obsługują asynchroniczne ładowanie:

- Należy dodać pole **AllowsBackgroundLoading = true** do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, aby upewnić się, że pakiet może być zainicjowany asynchronicznie Aby uzyskać więcej informacji na temat PackageRegistrationAttribute, zobacz [register and Unregister pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Należy dodać pole **IsAsyncQueryable = true** do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>, aby umożliwić asynchroniczne inicjowanie wystąpienia usługi.

  Oto przykład `AsyncPackage` z rejestracją usługi asynchronicznej:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Dodaj usługę

1. W *TestAsyncPackage.cs*usuń metodę `Initialize()` i Zastąp metodę `InitializeAsync()`. Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego, trzeba utworzyć usługi. Oto przykład asynchronicznej inicjatora, dodanie usługi:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Aby ta usługa była widoczna poza tym pakietem, ustaw wartość flagi Podwyższ na *true* jako ostatni parametr: `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Dodaj odwołanie do *pliku Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime. dll*.

3. Jako metodę asynchroniczną, która tworzy i zwraca usługę, należy zaimplementować metodę wywołania zwrotnego.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Korzystanie z usługi
 Teraz możesz pobrać usługę i użycie jej metod.

1. Pokażemy to w inicjatorze, ale możesz skorzystać z usługi w dowolnym miejscu, w którym chcesz korzystać z usługi.

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

     Nie zapomnij zmienić `userpath` na nazwę pliku i ścieżkę, które są zrozumiałe dla Twojej maszyny.

2. Skompiluj i uruchom kod. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, otwórz rozwiązanie. Powoduje to automatyczne załadowanie `AsyncPackage`. Po uruchomieniu inicjatora powinien znajdować się plik w podanej lokalizacji.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Korzystanie z usługi asynchronicznej w programie obsługi poleceń
 Oto przykład sposobu korzystania z usługi asynchronicznej w menu polecenia. Można użyć procedury pokazano poniżej, korzystanie z usługi za pomocą innych metod asynchronicznego.

1. Dodaj polecenie menu do projektu. (W **Eksplorator rozwiązań**wybierz węzeł projektu, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj** > **nowy element** > **rozszerzanie** > **polecenie niestandardowe**). Nazwij plik poleceń *TestAsyncCommand.cs*.

2. Szablon polecenia niestandardowego ponownie dodaje metodę `Initialize()` do pliku *TestAsyncPackage.cs* , aby można było zainicjować polecenie. W metodzie `Initialize()` Skopiuj wiersz, który inicjuje polecenie. Jego powinien wyglądać następująco:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Przenieś ten wiersz do metody `InitializeAsync()` w pliku *AsyncPackageForService.cs* . Ponieważ jest to asynchronicznego inicjalizacji, musisz przełączyć się do wątku głównego przed zainicjowaniem, za pomocą polecenia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Powinna teraz wyglądać następująco:

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

3. Usuń `Initialize()` metody.

4. W pliku *TestAsyncCommand.cs* znajdź metodę `MenuItemCallback()`. Usunięcie treści metody.

5. Dodaj dyrektywę using:

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

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Wywołanie tej metody z `MenuItemCallback()` metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, przejdź do **narzędzia** menu i zwróć uwagę na **wywołania TestAsyncCommand** elementu menu. Po kliknięciu go TextWriterService zapisuje do podanego pliku. (Nie musisz otwierać rozwiązania, ponieważ wywołuje polecenie również powoduje załadowanie pakietu).

## <a name="see-also"></a>Zobacz także
- [Używanie i udostępnianie usług](../extensibility/using-and-providing-services.md)
