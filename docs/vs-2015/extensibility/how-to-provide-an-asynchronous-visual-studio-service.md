---
title: 'Instrukcje: asynchroniczne obsługi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e57de7ca683678441b4e0908110e8e651930b64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061619"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Porady: obsługi asynchronicznego programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz uzyskać usługi bez blokowania wątku interfejsu użytkownika, należy Tworzenie usługi asynchronicznego i załadować pakiet w wątku tła. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage> zamiast <xref:Microsoft.VisualStudio.Shell.Package>i Dodaj usługę za pomocą specjalnych metod asynchronicznych asynchronicznego pakietu

 Aby dowiedzieć się, jak dostarczanie synchroniczne usługi Visual Studio, zobacz [jak: świadczenia usług](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Wdrażanie usługi asynchroniczne

1.  Utwórz projekt VSIX (**plik / nowy / Project / Visual C# / Extensiblity / projekt VSIX**). Nadaj projektowi nazwę **TestAsync**.

2.  Dodanie pakietu VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Add / nowy element / elementy Visual C# / rozszerzalność / pakiet rozszerzeń Visual Studio**. Nazwij ten plik **TestAsyncPackage.cs**.

3.  W TestAsyncPackage.cs Zmień pakietu odziedziczone AsyncPackage, a nie pakiet:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4.  Aby wdrożyć usługi, musisz utworzyć trzy typy:

    -   Interfejs, który zawiera opis usługi. Wiele z tych interfejsów są puste, oznacza to, ponieważ mają one żadnych metod.

    -   Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody do zaimplementowania.

    -   Klasa, która implementuje interfejs usługi i usługi.

5.  Poniższy przykład przedstawia bardzo podstawową implementację z trzech typów. Konstruktor klasy usługi należy ustawić dostawcę usług. W tym przykładzie po prostu dodamy usługę do pliku z kodem pakietu.

6.  Dodaj następujące instrukcje using do pliku pakietu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7.  Oto implementacja usługi asynchronicznego. Uwaga: należy ustawić asynchronicznego usługodawcy zamiast synchronicznych usługodawcy w Konstruktorze:

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
 Aby zarejestrować usługę, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, która dostarcza usługę. Istnieją dwie różnice zarejestrowanie synchroniczne usługi:

- Jeśli jesteś autoloading pakietu, należy dodać <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad wartość atrybutu. Aby uzyskać więcej informacji na temat pakietów VSPackage autoloading zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md).

- Należy dodać **AllowsBackgroundLoading = true** pole <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Aby uzyskać więcej informacji na temat PackageRegistrationAttribute zobacz [rejestrowanie i wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

  Poniżej przedstawiono przykład AsyncPackage za pomocą rejestracji usługi asynchronicznego::

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Dodawanie usług telefonii

1.  W TestAsyncPackage.cs, Usuń `Initialize()` metodę i Zastąp `InitializeAsync()` metody. Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego, trzeba utworzyć usługi. Oto przykład asynchronicznej inicjatora, dodanie usługi:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3.  Jako metodę asynchroniczną, która tworzy i zwraca usługę, należy zaimplementować metodę wywołania zwrotnego.

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

## <a name="using-a-service"></a>Korzystając z usługi
 Teraz możesz pobrać usługę i użycie jej metod.

1.  Pokazano to w inicjatorze, ale możesz uzyskać odpowiednią usługę dowolne miejsce do korzystania z usługi.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Nie zapomnij zmienić  *\<userpath >* do nazwy pliku i ścieżkę, która ma sens na swojej maszynie!

2.  Skompiluj i uruchom kod. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, otwórz rozwiązanie. Powoduje to AsyncPackage do automatyczne ładowanie. Po uruchomieniu inicjatora powinien znajdować się plik w podanej lokalizacji.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Za pomocą asynchronicznej usługi programu obsługi poleceń
 Oto przykład sposobu użycia usługi asynchroniczne za pomocą polecenia menu. Można użyć procedury pokazano poniżej, korzystanie z usługi za pomocą innych metod asynchronicznego.

1.  Dodaj polecenie menu do projektu. (W **Eksploratora rozwiązań**, wybierz węzeł projektu, kliknij prawym przyciskiem myszy i wybierz **Add / nowy element / rozszerzalności / polecenia niestandardowe**.) Nazwa pliku polecenia **TestAsyncCommand.cs.**

2.  Szablon polecenie niestandardowe ponownie dodaje `Initialize()` metody do pliku TestAsyncPackage.cs w celu zainicjowania polecenia. W przypadku metody Initialize() skopiuj wiersz, który inicjuje polecenia. Jego powinien wyglądać następująco:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Ten wiersz, aby przenieść `InitializeAsync()` metody w pliku AsyncPackageForService.cs. Ponieważ jest to asynchronicznego inicjalizacji, musisz przełączyć się do wątku głównego przed zainicjowaniem, za pomocą polecenia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Powinna teraz wyglądać następująco:

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

3.  Usuń `Initialize()` metody.

4.  W pliku TestAsyncCommand.cs Znajdź `MenuItemCallback()` metody. Usunięcie treści metody.

5.  Dodaj instrukcję using instrukcji:

    ```
    using System.IO;
    ```

6.  Dodaj metodę asynchroniczną o nazwie `GetAsyncService()`, która pobiera usługi i korzysta z jego metody:

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

7.  Wywołanie tej metody z `MenuItemCallback()` metody:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8.  Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Gdy pojawi się doświadczalnym wystąpieniu programu Visual Studio, przejdź do **narzędzia** menu i zwróć uwagę na **wywołania TestAsyncCommand** elementu menu. Po kliknięciu go TextWriterService zapisuje do podanego pliku. (Nie trzeba otworzyć rozwiązanie, ponieważ wywoływanie polecenia również powoduje, że pakiet do załadowania.)

## <a name="see-also"></a>Zobacz też
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)
