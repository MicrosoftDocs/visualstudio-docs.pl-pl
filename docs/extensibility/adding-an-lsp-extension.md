---
title: Dodawanie rozszerzenia protokołu serwera języka | Microsoft Docs
description: Dowiedz się, jak utworzyć rozszerzenie programu Visual Studio, które integruje serwer języka w oparciu o protokół serwera języka (LSP).
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: accf054cbf0b58066568124a3f35e064ce3cba78
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094994"
---
# <a name="add-a-language-server-protocol-extension"></a>Dodawanie rozszerzenia Language Server Protocol

Protokół serwera języka (LSP) to wspólny protokół w formie JSON RPC 2.0, który służy do udostępniania funkcji usługi językowej różnym edytorom kodu. Korzystając z protokołu, deweloperzy mogą napisać jeden serwer języka, aby udostępnić funkcje usługi językowej, takie jak IntelliSense, diagnostyka błędów, znaleźć wszystkie odwołania itd., do różnych edytorów kodu, które obsługują dostawcę. Tradycyjnie można dodawać usługi językowe w programie Visual Studio przy użyciu plików gramatycznych deautomatyzuje w celu zapewnienia podstawowych funkcji, takich jak wyróżnianie składni lub zapisywanie niestandardowych usług językowych, które korzystają z pełnego zestawu interfejsów API rozszerzalności programu Visual Studio, aby zapewnić bardziej zaawansowane dane. Dzięki obsłudze programu Visual Studio dla dostawcy LSP istnieje trzecia opcja.

![Usługa protokołu serwera języka w programie Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Language Server Protocol

![Implementacja protokołu serwera języka](media/lsp-implementation.png)

W tym artykule opisano sposób tworzenia rozszerzenia programu Visual Studio, które korzysta z serwera języka opartego na dostawcy LSP. Przyjęto założenie, że opracowano już serwer językowy oparty na dostawcy LSP i chcę zintegrować go z Visual Studio.

Aby uzyskać pomoc techniczną w programie Visual Studio, serwery języka mogą komunikować się z klientem (Visual Studio) za pośrednictwem dowolnego mechanizmu przesyłania strumieniowego, na przykład:

* Standardowe strumienie danych wejściowych/wyjściowych
* Nazwane potoki
* Gniazda (tylko protokół TCP)

Zamiarem dostawcy LSP i pomocy technicznej dla IT w programie Visual Studio jest dołączenie usług językowych, które nie są częścią produktu Visual Studio. Nie ma potrzeby poszerzania istniejących usług językowych (takich jak C#) w programie Visual Studio. Aby rozszerzać istniejące Języki, zapoznaj się z przewodnikiem rozszerzania usługi językowej (na przykład ["Roslyn" .NET compiler platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) lub zobacz [rozszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md).

Aby uzyskać więcej informacji na temat samego protokołu, zapoznaj się z dokumentacją w [tym miejscu](https://github.com/Microsoft/language-server-protocol).

Aby uzyskać więcej informacji na temat tworzenia przykładowego serwera języka lub sposobu integrowania istniejącego serwera języka z Visual Studio Code, zobacz dokumentację w [tym miejscu](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funkcje obsługiwane przez protokół serwera języka

W poniższych tabelach przedstawiono, które funkcje programu LSP są obsługiwane w programie Visual Studio:

Komunikat | Ma pomoc techniczną w programie Visual Studio
--- | ---
inicjacj | tak
Initialize | tak
shutdown | tak
Zakończ | tak
$/cancelRequest | tak
okno/showMessage | tak
okno/showMessageRequest | tak
okno/logMessage | tak
Telemetria/wydarzenie |
Klient/registerCapability |
Klient/unregisterCapability |
obszar roboczy/didChangeConfiguration | tak
obszar roboczy/didChangeWatchedFiles | tak
obszar roboczy/symbol | tak
obszar roboczy/executeCommand | tak
obszar roboczy/applyEdit | tak
TextDocument/publishDiagnostics | tak
TextDocument/didOpen | tak
TextDocument/didChange | tak
TextDocument/willSave |
TextDocument/willSaveWaitUntil |
TextDocument/didSave | tak
TextDocument/didClose | tak
Dokumentowanie/uzupełnianie | tak
zakończenie/rozwiązanie | tak
TextDocument/Aktywuj | tak
TextDocument/signatureHelp | tak
TextDocument/References | tak
TextDocument/documentHighlight | tak
TextDocument/documentSymbol | tak
TextDocument/formatowanie | tak
TextDocument/rangeFormatting | tak
TextDocument/onTypeFormatting |
TextDocument/Definition | tak
TextDocument/codeAction | tak
TextDocument/codeLens |
codeLens/Rozwiąż |
TextDocument/documentLink |
documentLink/Rozwiąż |
TextDocument/Zmień nazwę | tak

## <a name="get-started"></a>Rozpoczęcie pracy

> [!NOTE]
> Począwszy od programu Visual Studio 2017 w wersji 15,8, obsługa protokołu Common Language Server jest wbudowana w program Visual Studio. Jeśli skompilowano rozszerzenia LSP przy użyciu wersji zapoznawczej [klienta serwera językowego](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) , program przestanie działać po uaktualnieniu do wersji 15,8 lub nowszej. Aby Twoje rozszerzenia dostawcy LSP działały ponownie, należy wykonać następujące czynności:
>
> 1. Odinstaluj plik programu Microsoft Visual Studio Language Protocol w wersji zapoznawczej.
>
>    Począwszy od wersji 15,8, za każdym razem, gdy przeprowadzasz uaktualnienie w programie Visual Studio, zostanie automatycznie wykryta i usunięta wersja zapoznawcza.
>
> 2. Zaktualizuj odwołanie do programu NuGet do najnowszej wersji bez podglądu dla [pakietów LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Usuń zależność do programu Microsoft Visual Studio Language Server Protocol w wersji zapoznawczej w manifeście VSIX.
>
> 4. Upewnij się, że Twój VSIX określa program Visual Studio 2017 w wersji 15,8 Preview 3 jako dolną granicę dla celu instalacji.
>
> 5. Ponownie skompiluj i wdróż.

### <a name="create-a-vsix-project"></a>Tworzenie projektu VSIX

Aby utworzyć rozszerzenie usługi językowej przy użyciu serwera języka opartego na dostawcy LSP, najpierw upewnij się, że zainstalowano obciążenie **programowanie rozszerzenia programu Visual Studio** dla wystąpienia programu vs.

Następnie utwórz nowy projekt VSIX, przechodząc do pozycji **plik**  >  **Nowy** projekt  >    >  **rozszerzalność** Visual C#,  >  **Projekt VSIX**:

![Utwórz projekt VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalacja serwera języka i środowiska uruchomieniowego

Domyślnie rozszerzenia utworzone w celu obsługi serwerów języka opartych na dostawcy LSP w programie Visual Studio nie zawierają samych serwerów języków lub środowiska uruchomieniowego potrzebne do ich wykonania. Deweloperzy rozszerzeń są odpowiedzialni za dystrybucję serwerów języków oraz wymaganych środowisk uruchomieniowych. Istnieje kilka sposobów, aby to zrobić:

* Serwery języka można osadzić w plikach VSIX jako pliki zawartości.
* Utwórz plik MSI, aby zainstalować serwer języka i/lub potrzebne środowiska uruchomieniowe.
* Podaj instrukcje dla użytkowników z informacją o tym, jak uzyskać środowiska uruchomieniowe i serwery języków.

### <a name="textmate-grammar-files"></a>Pliki gramatyki deautomatyzuje

LSP nie zawiera specyfikacji dotyczącej sposobu tworzenia kolorowania tekstu dla języków. Aby zapewnić niestandardowe kolorowanie języków w programie Visual Studio, deweloperzy rozszerzeń mogą korzystać z pliku gramatyki deautomatyzuj. Aby dodać niestandardową gramatykę lub pliki motywów, wykonaj następujące kroki:

1. Utwórz folder o nazwie "gramatyki" wewnątrz rozszerzenia (może to być dowolnie wybrana nazwa).

2. W folderze *gramatyki* Uwzględnij dowolne pliki *\* . tmlanguage*, *\* . plist*, *\* . tmtheme* lub *\* . JSON* , które mają zapewniać niestandardowe kolorowanie.

   > [!TIP]
   > Plik *. tmtheme* definiuje, jak zakresy są mapowane na klasyfikacje programu Visual Studio (klucze kolorów). Aby uzyskać wskazówki, można odwołać się do pliku Global *. tmtheme* w katalogu *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* .

3. Utwórz plik *. pkgdef* i Dodaj wiersz podobny do tego:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Kliknij prawym przyciskiem myszy pliki i wybierz polecenie **Właściwości**. Zmień akcję **kompilacji** na **zawartość** i zmień właściwość **include w VSIX** na **true**.

Po wykonaniu poprzednich kroków folder *gramatyki* zostanie dodany do katalogu instalacyjnego pakietu jako źródło repozytorium o nazwie "mój lang" ("mój lang" jest tylko nazwą dla uściślania i może być dowolnym unikatowym ciągiem). Wszystkie gramatyki (pliki *. tmlanguage* ) i pliki motywów (pliki *. tmtheme* ) w tym katalogu są wybierane jako potencjalne i zastępują wbudowane gramatyki dostarczone z programem. Jeśli zadeklarowane rozszerzenia pliku gramatyki pasują do rozszerzenia otwieranego pliku, element textoficer zostanie przedłużony.

## <a name="create-a-simple-language-client"></a>Tworzenie klienta języka prostego

### <a name="main-interface---ilanguageclient"></a>Interfejs główny — [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Po utworzeniu projektu VSIX Dodaj następujące pakiety NuGet do projektu:

* [Microsoft. VisualStudio. LanguageServer. Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Jeśli po wykonaniu poprzednich kroków zostanie wdrożona zależność od pakietu NuGet, Newtonsoft.Jsi pakiety StreamJsonRpc są również dodawane do projektu. **Nie Aktualizuj tych pakietów, jeśli nie masz pewności, że te nowe wersje zostaną zainstalowane w wersji programu Visual Studio, która jest przeznaczona dla rozszerzenia**. Zestawy nie zostaną uwzględnione w Twoim VSIX; Zamiast tego zostaną one pobrane z katalogu instalacyjnego programu Visual Studio. Jeśli odwołujesz się do nowszej wersji zestawów niż zainstalowana na komputerze użytkownika, rozszerzenie nie będzie działało.

Następnie można utworzyć nową klasę, która implementuje interfejs [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) , który jest głównym interfejsem, który jest wymagany dla klientów języka nawiązujących połączenie z serwerem języka opartym na dostawcy LSP.

Oto przykład:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Główne metody, które należy zaimplementować, to [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) i [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) jest wywoływana, gdy program Visual Studio załadował Twoje rozszerzenie, a serwer języka jest gotowy do uruchomienia. W tej metodzie można natychmiast wywołać delegata [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) , aby sygnalizować, że serwer języka powinien być uruchomiony lub można wykonać dodatkową logikę i wywołać [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) później. **Aby aktywować serwer języka, należy wywołać StartAsync w pewnym momencie.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) to metoda ostatecznie wywołana przez wywołanie delegata [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) . Zawiera logikę umożliwiającą uruchomienie serwera języka i nawiązanie z nim połączenia. Należy zwrócić obiekt połączenia, który zawiera strumienie do zapisu na serwerze i odczytywania z serwera. Wszystkie wyjątki zgłoszone w tym miejscu są przechwytywane i wyświetlane dla użytkownika za pośrednictwem komunikatu paska informacji w programie Visual Studio.

### <a name="activation"></a>Uaktywnienie

Po zaimplementowaniu klasy klienta języka należy zdefiniować dwa atrybuty, aby określić, jak zostanie ona załadowana do programu Visual Studio i aktywowana:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Program Visual Studio używa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) do zarządzania punktami rozszerzalności. Atrybut [Export](/dotnet/api/system.componentmodel.composition.exportattribute) wskazuje programowi Visual Studio, że ta klasa powinna zostać pobrana jako punkt rozszerzenia i załadowana w odpowiednim czasie.

Aby użyć MEF, należy również zdefiniować MEF jako element zawartości w manifeście VSIX.

Otwórz projektanta manifestu VSIX i przejdź do karty **składniki** :

![Dodaj element zawartości MEF](media/lsp-add-asset.png)

Kliknij pozycję **Nowy** , aby utworzyć nowy element zawartości:

![Zdefiniuj element zawartości MEF](media/lsp-define-asset.png)

* **Typ**: Microsoft. VisualStudio. MefComponent
* **Źródło**: projekt w bieżącym rozwiązaniu
* **Projekt**: [Twój projekt]

### <a name="content-type-definition"></a>Definicja typu zawartości

Obecnie jedynym sposobem ładowania rozszerzenia serwera języka opartego na dostawcy LSP jest typ zawartości pliku. Oznacza to, że podczas definiowania klasy klienta języka (która implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)), należy zdefiniować typy plików, które po otwarciu nie spowodują załadowania rozszerzenia. Jeśli nie zostaną otwarte żadne pliki zgodne z określonym typem zawartości, to rozszerzenie nie zostanie załadowane.

W tym celu należy zdefiniować co najmniej jedną `ContentTypeDefinition` klasę:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

W poprzednim przykładzie definicja typu zawartości jest tworzona dla plików kończących się rozszerzeniem *. bar* . Definicja typu zawartości otrzymuje nazwę "bar" i musi pochodzić od [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

Po dodaniu definicji typu zawartości można określić, kiedy załadować rozszerzenie klienta języka w klasie klienta języka:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Dodanie obsługi dla serwerów języka LSP nie wymaga implementacji własnego systemu projektu w programie Visual Studio. Klienci mogą otworzyć pojedynczy plik lub folder w programie Visual Studio, aby rozpocząć korzystanie z usługi językowej. W rzeczywistości pomoc techniczna dla serwerów języka LSP została zaprojektowana tak, aby działała tylko w scenariuszach otwartych folderów/plików. W przypadku zaimplementowania niestandardowego systemu projektu niektóre funkcje (takie jak ustawienia) nie będą działały.

## <a name="advanced-features"></a>Funkcje zaawansowane

### <a name="settings"></a>Ustawienia

Dostępna jest obsługa niestandardowych ustawień specyficznych dla serwera, ale nadal trwa proces ich ulepszania. Ustawienia są specyficzne dla elementów obsługiwanych przez serwer języka i zwykle kontrolują sposób, w jaki serwer języka emituje dane. Na przykład serwer języka może mieć ustawienie maksymalnej liczby raportowanych błędów. Autorzy rozszerzeń definiują wartość domyślną, która może zostać zmieniona przez użytkowników dla określonych projektów.

Wykonaj następujące kroki, aby dodać obsługę ustawień do rozszerzenia usługi języka LSP:

1. Dodaj plik JSON (na przykład *MockLanguageExtensionSettings.json*) do projektu, który zawiera ustawienia i ich wartości domyślne. Na przykład:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Kliknij prawym przyciskiem myszy plik JSON i wybierz polecenie **Właściwości**. Zmień akcję **kompilacji** na "Content" i właściwość "include in VSIX" na **wartość true**.

3. Wdrożenie elementów ConfigurationSection i zwrócenie listy prefiksów dla ustawień zdefiniowanych w pliku JSON (w Visual Studio Code może to spowodować zamapowanie na nazwę sekcji konfiguracji w package.jsna):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Dodaj plik. pkgdef do projektu (Dodaj nowy plik tekstowy i Zmień rozszerzenie pliku na. pkgdef). Plik pkgdef powinien zawierać następujące informacje:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Przykład:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Kliknij prawym przyciskiem myszy plik. pkgdef i wybierz polecenie **Właściwości**. Zmień akcję **kompilacji** na **zawartość** i Właściwość **include w VSIX** na **wartość true**.

6. Otwórz plik *source. Extension. vsixmanifest* i Dodaj element zawartości na karcie element **zawartości** :

   ![Edytuj zasób pakietu VSPackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft. VisualStudio. pakietu VSPackage
   * **Źródło**: plik w systemie plików
   * **Ścieżka**: [ścieżka do pliku *. pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edytowanie ustawień obszaru roboczego przez użytkownika

1. Użytkownik otwiera obszar roboczy zawierający pliki, do których należy serwer.
2. Użytkownik dodaje plik w folderze *. vs* o nazwie *VSWorkspaceSettings.json*.
3. Użytkownik dodaje wiersz do *VSWorkspaceSettings.jsw* pliku dla ustawienia, które zapewnia serwer. Na przykład:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Włącz śledzenie diagnostyki

Śledzenie diagnostyki można włączyć w celu wyprowadzania wszystkich komunikatów między klientem a serwerem, co może być przydatne w przypadku problemów z debugowaniem. Aby włączyć śledzenie diagnostyczne, wykonaj następujące czynności:

1. Otwórz lub Utwórz plik ustawień obszaru roboczego *VSWorkspaceSettings.jsna stronie* (zobacz "Edytowanie ustawień obszaru roboczego przez użytkownika").
2. Dodaj następujący wiersz w pliku JSON ustawień:

```json
{
    "foo.trace.server": "Off"
}
```

Istnieją trzy możliwe wartości dla szczegółowości śledzenia:

* "Wyłączone": śledzenie jest wyłączone całkowicie
* "Messages": śledzenie włączone, ale tylko nazwa metody i Identyfikator odpowiedzi są śledzone.
* "Verbose": śledzenie włączone; cały komunikat RPC jest śledzony.

Po włączeniu śledzenia zawartość jest zapisywana w pliku w katalogu *%temp%\VisualStudio\LSP* . Dziennik jest zgodny z formatem nazewnictwa *[LanguageClientName]-[Sygnatura daty i godziny]. log*. Obecnie śledzenie można włączyć tylko dla scenariuszy z otwartym folderem. Otwarcie pojedynczego pliku w celu aktywowania serwera języka nie ma obsługi śledzenia diagnostycznego.

### <a name="custom-messages"></a>Komunikaty niestandardowe

Istnieją interfejsy API, które ułatwiają przekazywanie komunikatów do i otrzymywanie komunikatów z serwera języka, który nie jest częścią protokołu standardowego serwera języka. Aby obsłużyć niestandardowe komunikaty, zaimplementuj Interfejs [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) w klasie klienta języka. Biblioteka [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) służy do przesyłania komunikatów niestandardowych między klientem języka a serwerem języka. Ponieważ rozszerzenie klienta języka LSP jest takie samo jak inne rozszerzenie programu Visual Studio, możesz zdecydować się na dodanie dodatkowych funkcji (które nie są obsługiwane przez dostawcę LSP) do programu Visual Studio (przy użyciu innych interfejsów API programu Visual Studio) w rozszerzeniu za pośrednictwem komunikatów niestandardowych.

#### <a name="receive-custom-messages"></a>Odbieraj komunikaty niestandardowe

Aby odbierać niestandardowe komunikaty z serwera języka, należy zaimplementować Właściwość [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) w [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) i zwrócić obiekt, który wie, jak obsługiwać niestandardowe komunikaty. Na przykład:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>Wysyłanie wiadomości niestandardowych

Aby wysłać niestandardowe komunikaty do serwera języka, Zaimplementuj metodę [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) na [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Ta metoda jest wywoływana, gdy serwer języka jest uruchomiony i gotowy do odbierania komunikatów. Obiekt [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) jest przekazujący jako parametr, który następnie można kontynuować wysyłanie komunikatów do serwera języka za pomocą interfejsów API [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . Na przykład:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Warstwa środkowa

Czasami deweloper rozszerzenia może chcieć przechwycić komunikaty dostawcy LSP wysyłane do i odbierane z serwera języka. Na przykład deweloper rozszerzenia może chcieć zmienić parametr komunikatu wysyłanego dla konkretnego komunikatu LSP lub zmodyfikować wyniki zwrócone z serwera języka dla funkcji LSP (na przykład uzupełniania). Gdy jest to konieczne, deweloperzy rozszerzeń mogą przechwycić komunikaty LSP przy użyciu interfejsu API MiddleLayer.

Każdy komunikat dostawcy LSP ma własny interfejs warstwy środkowej do przechwycenia. Aby przechwycić określony komunikat, należy utworzyć klasę, która implementuje interfejs warstwy środkowej dla tego komunikatu. Następnie należy zaimplementować interfejs [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) w klasie klienta języka i zwrócić wystąpienie obiektu we właściwości [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) . Na przykład:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Funkcja warstwy środkowej nadal jest opracowywana i nie jest jeszcze kompletna.

## <a name="sample-lsp-language-server-extension"></a>Przykładowe rozszerzenie serwera języka LSP

Aby wyświetlić kod źródłowy przykładowego rozszerzenia przy użyciu interfejsu API klienta LSP w programie Visual Studio, zobacz przykład VSSDK-rozszerzalności-przykłady dla dostawcy [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Często zadawane pytania

**Chcę utworzyć niestandardowy system projektu, aby uzupełnić mój serwer języka LSP, aby zapewnić bardziej rozbudowaną obsługę funkcji w programie Visual Studio, jak to zrobić?**

Obsługa serwerów języka opartych na dostawcy LSP w programie Visual Studio opiera się na [funkcji Otwórz folder](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) i została zaprojektowana tak, aby nie wymagała niestandardowego systemu projektu. W [tym miejscu](https://github.com/Microsoft/VSProjectSystem)możesz utworzyć własny niestandardowy system projektu, ale niektóre funkcje, takie jak ustawienia, mogą nie funkcjonować. Domyślna logika inicjalizacji dla serwerów języka LSP jest zapisywana w folderze głównym folderu, który jest aktualnie otwierany, dlatego jeśli używasz niestandardowego systemu projektu, może być konieczne dostarczenie logiki niestandardowej podczas inicjowania, aby upewnić się, że serwer języka może być prawidłowo uruchamiany.

**Jak mogę dodać obsługę debugera?**

Firma Microsoft zapewnia pomoc techniczną dla [wspólnego protokołu debugowania](https://code.visualstudio.com/docs/extensionAPI/api-debugging) w przyszłej wersji.

**Jeśli jest już zainstalowana usługa języka VS obsługiwana (na przykład JavaScript), można nadal zainstalować rozszerzenie serwera języka LSP, które oferuje dodatkowe funkcje (takie jak zaznaczanie błędów)?**

Tak, ale nie wszystkie funkcje będą działały prawidłowo. Ostatecznym celem rozszerzeń serwera języka LSP jest umożliwienie usług językowych, które nie są natywnie obsługiwane przez program Visual Studio. Można tworzyć rozszerzenia, które oferują dodatkową pomoc techniczną, korzystając z serwerów języka LSP, ale niektóre funkcje (na przykład IntelliSense) nie będą działać w sposób płynny. Ogólnie rzecz biorąc, zaleca się, aby aplikacje serwera języka LSP były używane do udostępniania nowych środowisk językowych, nie rozszerzając istniejących.

**Gdzie mogę opublikować zakończono pracę VSIX serwera języka LSP?**

Zobacz [tutaj](walkthrough-publishing-a-visual-studio-extension.md)instrukcje dotyczące witryny Marketplace.

## <a name="see-also"></a>Zobacz też

- [Dodaj obsługę edytora programu Visual Studio dla innych języków](../ide/adding-visual-studio-editor-support-for-other-languages.md)
