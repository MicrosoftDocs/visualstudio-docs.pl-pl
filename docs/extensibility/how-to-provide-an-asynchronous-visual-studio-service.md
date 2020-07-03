---
title: 'Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad178bf93e49c3d695c1ebd0a5d4f6b151175953
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905741"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio
Jeśli chcesz uzyskać usługę bez blokowania wątku interfejsu użytkownika, należy utworzyć usługę asynchroniczną i załadować pakiet w wątku w tle. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage> <xref:Microsoft.VisualStudio.Shell.Package> , a nie a, i dodać usługę z zastosowaniem specjalnych metod asynchronicznych pakietu asynchronicznego.

 Aby uzyskać informacje o dostarczaniu synchronicznych usług programu Visual Studio, zobacz [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementowanie usługi asynchronicznej

1. Utwórz projekt VSIX (**plik**  >  **Nowy**  >  **projekt**  >  **Visual C#**  >  **Extensiblity**  >  **VSIX**). Nazwij projekt **TestAsync**.

2. Dodaj pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań** a następnie kliknij pozycję **Dodaj**  >  **nowy element**  >  **Visual C# elementy**  >  **Rozszerzalny**  >  **pakiet Visual Studio**. Nazwij ten plik *TestAsyncPackage.cs*.

3. W *TestAsyncPackage.cs*Zmień pakiet, aby dziedziczyć `AsyncPackage` zamiast `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Aby zaimplementować usługę, należy utworzyć trzy typy:

    - Interfejs, który identyfikuje usługę. Wiele z tych interfejsów jest pustych, czyli nie ma metod, ponieważ są one używane tylko do wykonywania zapytań dotyczących usługi.

    - Interfejs opisujący interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

    - Klasa implementująca zarówno usługę, jak i interfejs usługi.

5. W poniższym przykładzie przedstawiono bardzo podstawową implementację trzech typów. Konstruktor klasy usługi musi ustawić dostawcę usług. W tym przykładzie dodamy usługę do pliku kodu pakietu.

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

7. Oto implementacja usługi asynchronicznej. Należy pamiętać, że w Konstruktorze należy ustawić dostawcę usług asynchronicznych, a nie dostawcę usług synchronicznych:

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
 Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, który udostępnia usługę. Aby zarejestrować usługę synchroniczną, należy się upewnić, że oba pakiety i usługi obsługują asynchroniczne ładowanie:

- Należy dodać pole **AllowsBackgroundLoading = true** do usługi, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Aby upewnić się, że można zainicjować pakiet asynchronicznie, aby uzyskać więcej informacji na temat PackageRegistrationAttribute, zobacz [register and Unregister pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Należy dodać pole **IsAsyncQueryable = true** do, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Aby upewnić się, że wystąpienie usługi można zainicjować asynchronicznie.

  Oto przykład z `AsyncPackage` rejestracją usługi asynchronicznej:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Dodawanie usługi

1. W *TestAsyncPackage.cs*Usuń `Initialize()` metodę i Zastąp `InitializeAsync()` metodę. Dodaj usługę i Dodaj metodę wywołania zwrotnego, aby utworzyć usługi. Oto przykład inicjatora asynchronicznego dodawanego do usługi:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Aby ta usługa była widoczna poza tym pakietem, ustaw wartość flagi Podwyższ na *true* jako ostatni parametr:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Dodaj odwołanie do *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Zaimplementuj metodę wywołania zwrotnego jako metodę asynchroniczną, która tworzy i zwraca usługę.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Korzystanie z usługi
 Teraz możesz uzyskać usługę i użyć jej metod.

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

     Nie zapomnij zmienić `userpath` nazwy pliku i ścieżki, które są zrozumiałe dla Twojej maszyny.

2. Kompiluj i uruchamiaj kod. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, Otwórz rozwiązanie. Powoduje to `AsyncPackage` automatyczne załadowanie. Po uruchomieniu inicjatora należy znaleźć plik w określonej lokalizacji.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Korzystanie z usługi asynchronicznej w programie obsługi poleceń
 Oto przykład sposobu korzystania z usługi asynchronicznej w menu polecenia. Możesz użyć procedury pokazanej w tym miejscu, aby użyć usługi w innych metodach nieasynchronicznych.

1. Dodaj polecenie menu do projektu. (W **Eksplorator rozwiązań**wybierz węzeł projektu, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj**  >  **Nowy element**  >  **Rozszerzalność**  >  **Polecenie niestandardowe**). Nazwij plik poleceń *TestAsyncCommand.cs*.

2. Szablon polecenia niestandardowego ponownie dodaje `Initialize()` metodę do pliku *TestAsyncPackage.cs* , aby można było zainicjować polecenie. W `Initialize()` metodzie Skopiuj wiersz, który inicjuje polecenie. Powinny wyglądać następująco:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Przenieś ten wiersz do `InitializeAsync()` metody w pliku *AsyncPackageForService.cs* . Ponieważ jest to Inicjalizacja asynchroniczna, należy przełączyć się do głównego wątku przed zainicjowaniem polecenia za pomocą <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Powinien teraz wyglądać następująco:

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

4. W pliku *TestAsyncCommand.cs* Znajdź `MenuItemCallback()` metodę. Usuń treść metody.

5. Dodaj dyrektywę using:

    ```csharp
    using System.IO;
    ```

6. Dodaj metodę asynchroniczną o nazwie `UseTextWriterAsync()` , która pobiera usługę i używa jej metod:

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

7. Wywołaj tę metodę z `MenuItemCallback()` metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Skompiluj rozwiązanie i Rozpocznij debugowanie. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, przejdź do menu **Narzędzia** i Wyszukaj element menu **Wywołaj TestAsyncCommand** . Po kliknięciu TextWriterService zapisuje w określonym pliku. (Nie musisz otwierać rozwiązania, ponieważ wywołuje polecenie również powoduje załadowanie pakietu).

## <a name="see-also"></a>Zobacz też
- [Używanie i udostępnianie usług](../extensibility/using-and-providing-services.md)
