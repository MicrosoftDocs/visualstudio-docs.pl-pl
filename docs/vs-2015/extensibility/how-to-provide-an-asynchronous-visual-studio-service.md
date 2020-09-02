---
title: 'Instrukcje: dostarczanie usługi asynchronicznej | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204102"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz uzyskać usługę bez blokowania wątku interfejsu użytkownika, należy utworzyć usługę asynchroniczną i załadować pakiet w wątku w tle. W tym celu można użyć a <xref:Microsoft.VisualStudio.Shell.AsyncPackage> nie a <xref:Microsoft.VisualStudio.Shell.Package> i dodać usługę z zastosowaniem specjalnych metod asynchronicznych pakietu asynchronicznego

 Aby uzyskać informacje o dostarczaniu synchronicznych usług programu Visual Studio, zobacz [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementowanie usługi asynchronicznej

1. Utwórz projekt VSIX (**plik/nowy/projekt/Visual C#/Extensiblity/VSIX**). Nazwij projekt **TestAsync**.

2. Dodaj pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań** i kliknij pozycje **Dodaj/nowy element/Visual C# elementy/rozszerzalność/pakiet Visual Studio**. Nazwij ten plik **TestAsyncPackage.cs**.

3. W TestAsyncPackage.cs Zmień pakiet, aby dziedziczyć z AsyncPackage, a nie z pakietu:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Aby zaimplementować usługę, należy utworzyć trzy typy:

    - Interfejs, który opisuje usługę. Wiele z tych interfejsów jest pustych, czyli nie ma metod.

    - Interfejs opisujący interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

    - Klasa implementująca zarówno usługę, jak i interfejs usługi.

5. W poniższym przykładzie przedstawiono bardzo podstawową implementację trzech typów. Konstruktor klasy usługi musi ustawić dostawcę usług. W tym przykładzie dodamy usługę do pliku kodu pakietu.

6. Dodaj następujące instrukcje using do pliku pakietu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Oto implementacja usługi asynchronicznej. Należy pamiętać, że w Konstruktorze należy ustawić dostawcę usług asynchronicznych, a nie dostawcę usług synchronicznych:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Rejestrowanie usługi
 Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, który udostępnia usługę. Istnieją dwie różnice między rejestracją usługi synchronicznej:

- Jeśli ładujesz automatyczne pakiety, musisz dodać <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> wartość BackgroundLoad do atrybutu. Aby uzyskać więcej informacji na temat pakietów VSPackage ładowania, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

- Należy dodać pole **AllowsBackgroundLoading = true** do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Aby uzyskać więcej informacji na temat PackageRegistrationAttribute, zobacz [Rejestrowanie i Wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

  Oto przykład AsyncPackage z rejestracją usługi asynchronicznej:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Dodawanie usługi

1. W TestAsyncPackage.cs usuń `Initialize()` metodę i Zastąp `InitializeAsync()` metodę. Dodaj usługę i Dodaj metodę wywołania zwrotnego, aby utworzyć usługi. Oto przykład inicjatora asynchronicznego dodawanego do usługi:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Zaimplementuj metodę wywołania zwrotnego jako metodę asynchroniczną, która tworzy i zwraca usługę.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Korzystanie z usługi
 Teraz możesz uzyskać usługę i użyć jej metod.

1. Pokażemy to w inicjatorze, ale możesz skorzystać z usługi w dowolnym miejscu, w którym chcesz korzystać z usługi.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Nie zapomnij zmienić *\<userpath>* nazwy pliku i ścieżki, które są zrozumiałe dla Twojej maszyny.

2. Kompiluj i uruchamiaj kod. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, Otwórz rozwiązanie. Powoduje to automatyczne załadowanie AsyncPackage. Po uruchomieniu inicjatora należy znaleźć plik w określonej lokalizacji.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Korzystanie z usługi asynchronicznej w programie obsługi poleceń
 Oto przykład sposobu korzystania z usługi asynchronicznej w menu polecenia. Możesz użyć procedury pokazanej w tym miejscu, aby użyć usługi w innych metodach nieasynchronicznych.

1. Dodaj polecenie menu do projektu. (W **Eksplorator rozwiązań**wybierz węzeł projektu, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj/nowy element/rozszerzalność/polecenie niestandardowe**). Nazwij plik poleceń **TestAsyncCommand.cs.**

2. Szablon polecenia niestandardowego ponownie dodaje `Initialize()` metodę do pliku TestAsyncPackage.cs, aby można było zainicjować polecenie. W metodzie Initialize () Skopiuj wiersz, który inicjuje polecenie. Powinien on wyglądać następująco:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Przenieś ten wiersz do `InitializeAsync()` metody w pliku AsyncPackageForService.cs. Ponieważ jest to Inicjalizacja asynchroniczna, należy przełączyć się do głównego wątku przed zainicjowaniem polecenia za pomocą <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Powinien teraz wyglądać następująco:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Usuń `Initialize()` metodę.

4. W pliku TestAsyncCommand.cs Znajdź `MenuItemCallback()` metodę. Usuń treść metody.

5. Dodaj instrukcję using:

    ```
    using System.IO;
    ```

6. Dodaj metodę asynchroniczną o nazwie `GetAsyncService()` , która pobiera usługę i używa jej metod:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Wywołaj tę metodę z `MenuItemCallback()` metody:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Skompiluj rozwiązanie i Rozpocznij debugowanie. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, przejdź do menu **Narzędzia** i Wyszukaj element menu **Wywołaj TestAsyncCommand** . Po kliknięciu TextWriterService zapisuje w określonym pliku. (Nie musisz otwierać rozwiązania, ponieważ wywołuje polecenie również powoduje załadowanie pakietu).

## <a name="see-also"></a>Zobacz też
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)
