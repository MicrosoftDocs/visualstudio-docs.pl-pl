---
title: Dodawanie rozszerzenia protokołu Language Server Protocol | Dokumentacja firmy Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b8e31fea497bff928ce19e5cb165c7809883cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104567"
---
# <a name="add-a-language-server-protocol-extension"></a>Dodawanie rozszerzenia protokołu Language Server Protocol

Protokół serwera języka (LSP) jest wspólny protokół w formie wywołania JSON RPC w wersji 2.0, użycie go do udostępnienia funkcji usługi różne edytory kodu języka. Przy użyciu protokołu, programiści mogą pisać serwera jednego języka do zapewniają funkcje usługi, takie jak IntelliSense, Diagnostyka błędów języka, Znajdź wszystkie odwołania, itp., aby różne edytory kodu, które obsługują LSP. Tradycyjnie, można dodać usług językowych w programie Visual Studio, albo za pomocą plików gramatyki TextMate, aby zapewnić podstawowe funkcje, takie jak wyróżnianie składni lub pisząc usług języka niestandardowego przy użyciu pełnego zestawu interfejsów API rozszerzania programu Visual Studio do zapewnia dokładniejsze dane. Teraz Pomoc techniczna dla LSP zapewnia trzecią opcję.

![język serwera protokołu usługi w programie Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Language Server Protocol

![Implementacja protokołu serwera języka](media/lsp-implementation.png)

W tym artykule opisano sposób tworzenia rozszerzenia programu Visual Studio, gdy używany serwer opartych na LSP języka. Zakłada się, został już utworzony serwer opartych na LSP języka, a następnie po prostu chcesz zintegrować go z programu Visual Studio.

Obsługi w programie Visual Studio język serwerów może komunikować się z klienta (Visual Studio) za pośrednictwem dowolnego mechanizmu przekazywania strumień, na przykład:

* Standardowych strumieni wejścia/wyjścia
* Nazwane potoki
* Gniazda (TCP tylko)

Celem LSP i pomoc techniczna dla niej w programie Visual Studio jest usług dołączanie języka, które nie są częścią produktu Visual Studio. Nie ma rozszerzenie istniejących usług języka (np. C#) w programie Visual Studio. Aby rozszerzyć istniejące języków, można znaleźć w podręczniku rozszerzeń usługi językowej (na przykład [platformie kompilatora .NET "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Aby uzyskać więcej informacji na temat z samym protokołem, zobacz dokumentację [tutaj](https://github.com/Microsoft/language-server-protocol).

Aby uzyskać więcej informacji na temat tworzenia przykładowego serwera języka lub jak zintegrować istniejącego serwera języka programu Visual Studio Code, zobacz dokumentację [tutaj](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Obsługiwane funkcje protokołu serwera języka

Następujące funkcje LSP są obsługiwane w programie Visual Studio do tej pory:

Komunikat | Obsługuje w programie Visual Studio
--- | ---
Inicjowanie | tak
zainicjowany | tak
shutdown | tak
Zakończ | tak
$/cancelRequest | tak
window/showMessage | tak
window/showMessageRequest | tak
window/logMessage | tak
zdarzenia/telemetrii |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | tak
workspace/didChangeWatchedFiles | tak
obszar roboczy/symbol | tak
workspace/executeCommand | tak
obszar roboczy/applyEdit | tak
textDocument/publishDiagnostics | tak
textDocument/didOpen | tak
textDocument/didChange | tak
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | tak
textDocument/didClose | tak
textDocument/zakończenia | tak
ukończenie/rozwiązania. | tak
textDocument/po wskazaniu wskaźnikiem | tak
textDocument/signatureHelp | tak
textDocument/odwołania | tak
textDocument/documentHighlight | tak
textDocument/documentSymbol | tak
textDocument/formatowania | tak
textDocument/rangeFormatting | tak
textDocument/onTypeFormatting |
textDocument/definicji | tak
textDocument/codeAction | tak
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/zmiany nazwy | tak

## <a name="getting-started"></a>Wprowadzenie

> [!NOTE]
> Począwszy od programu Visual Studio 15.8 wersję zapoznawczą 3, obsługa common Language Server Protocol jest wbudowana w program Visual Studio. Jeśli został zbudowany rozszerzeń LSP przy użyciu naszym podglądzie [języka serwera klienta VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) wersji, ich przestanie działać po do przeprowadzono uaktualnienie do wersji Preview należy zachować 15,8 3 lub nowszej. Należy wykonać następujące czynności, które można pobrać rozszerzeń LSP spowodowana:
>
> 1. Odinstaluj program Microsoft Visual Studio Language Server protokołu Preview VSIX. Począwszy od należy zachować 15,8 w wersji zapoznawczej 4, każdym razem, gdy należy wykonać uaktualnienie w programie Visual Studio, firma Microsoft umożliwia automatyczne wykrywanie i Usuń Podgląd VSIX dla Ciebie podczas procesu uaktualniania.
>
> 2. Aktualizuj odwołania programu Nuget do najnowszej wersji — wersja zapoznawcza dla [pakietów LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Usuń zależności do firmy Microsoft Visual Studio Language Server Protocol (wersja zapoznawcza) VSIX w manifeście VSIX.
>
> 4. Upewnij się, że w VSIX użytkownika określa 3 (wersja zapoznawcza) 15.8 w usłudze Visual Studio jako dolną granicę dla elementu docelowego instalacji.
>
> 5. Ponownie skompiluj i Wdróż ponownie.

### <a name="create-a-vsix-project"></a>Create a VSIX project

Aby utworzyć rozszerzenie usługi języka używany jest serwer oparty na LSP język, najpierw upewnij się, że masz **programowanie rozszerzeń programu Visual Studio** obciążenia zainstalowane wystąpienia programu VS.

Następnie utwórz nowe, puste VSIXProject, przechodząc do **pliku** > **nowy projekt** > **Visual C#**  >   **Rozszerzalność** > **projekt VSIX**:

![Utwórz projekt vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalacja serwera i środowiska uruchomieniowego języka

Domyślnie rozszerzenia tworzone do obsługi języka opartego na LSP serwerów w programie Visual Studio nie będzie zawierać samych serwerów języka lub środowiska uruchomieniowe wymaganej do ich wykonania. Deweloperzy rozszerzenia jest odpowiedzialna za dystrybucję serwerów języka i środowiska uruchomieniowe potrzebne. Istnieje kilka sposobów, aby to zrobić:

* Język serwerów można osadzić w pliku VSIX jako pliki zawartości.
* Utwórz plik MSI, aby zainstalować serwer języka i/lub potrzebne środowisk uruchomieniowych.
* Zawierają instrukcje dotyczące witryny Marketplace informowania użytkowników uzyskiwania serwerów środowisk uruchomieniowych i języka.

### <a name="textmate-grammar-files"></a>Pliki gramatyki TextMate

LSP nie zawiera specyfikacji dostarczania tekstu kolorowania dla języków. Aby podać niestandardowy kolorowania dla języków w programie Visual Studio, rozszerzenia deweloperzy mogą używać pliku gramatyki TextMate. Aby dodać niestandardowe pliki motywu lub gramatyki TextMate, wykonaj następujące kroki:

1. Utwórz folder o nazwie "Gramatyki" wewnątrz rozszerzenia (lub może być dowolną nazwę, możesz wybrać).

2. Wewnątrz *gramatyki* folderze zawierać  *\*.tmlanguage*,  *\*.plist*,  *\*.tmtheme*, lub  *\*.json* plików chcesz udostępniających kolorowanie niestandardowych.

3. Kliknij prawym przyciskiem myszy na pliki i wybierz **właściwości**. Zmiana **kompilacji** akcji **zawartości** i **Include w VSIX** właściwości na wartość true.

4. Tworzenie *.pkgdef* pliku i Dodaj wiersz podobny do poniższego:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

5. Kliknij prawym przyciskiem myszy na pliki i wybierz **właściwości**. Zmiana **kompilacji** akcji **zawartości** i **Include w VSIX** właściwości na wartość true.

Po wykonaniu poprzednich kroków *gramatyki* folder zostanie dodany do pakietu instalacji katalogu jako źródło repozytorium o nazwie "MyLang" ("MyLang" jest po prostu nazwą uściślania i może być dowolnym ciągiem unikatowy). Wszystkie gramatyki (*.tmlanguage* plików) i pliki motywów (*.tmtheme* pliki) w tym katalogu są pobierane jako rynkowych i zastępują wbudowane gramatyki dołączonym TextMate. Jeśli plik gramatyki zadeklarowane rozszerzenia są zgodne z rozszerzeniem otwierany plik, TextMate przechodzi.

## <a name="create-a-simple-language-client"></a>Tworzenie prostego języka klienta

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Główny interfejs - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Po utworzeniu projektu VSIX, należy dodać następujące pakiety NuGet do projektu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Jeśli przełączysz zależność od pakietu NuGet, po wykonaniu poprzednich kroków, Newtonsoft.Json i StreamJsonRpc pakietów są dodawane do projektu w także. **Nie są uaktualniane te pakiety, chyba że masz pewność, że te nowe wersje zostanie zainstalowana w wersji programu Visual Studio, elementy docelowe rozszerzenie**. Zestawy nie będzie uwzględniane w VSIX użytkownika — zamiast tego są zostaną pobrane z katalogu instalacyjnego programu Visual Studio. Jeśli odwołujesz się do nowszej wersji zestawów, niż zainstalowana na komputerze użytkownika, rozszerzenia *nie będzie działać*.

Następnie możesz utworzyć nową klasę, która implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfejsu, główny interfejs wymagane w przypadku języka klientów nawiązujących połączenie z serwerem na podstawie LSP języka.

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

Główne metody, które powinny być wdrożone są [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) i [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) jest wywoływana, gdy program Visual Studio został załadowany rozszerzenia, a serwer języka jest gotowa do uruchomienia. W przypadku tej metody można wywołać [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegata natychmiast w celu sygnalizowania, że że server języka, które mają być uruchamiane lub wykonaj dodatkową logikę i wywołać [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) później. **Aby uaktywnić serwer języka, należy wywołać StartAsync w pewnym momencie.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) jest metodą ostatecznie wywołana przez wywołanie metody [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegować; zawiera logikę w celu uruchomienia serwera języka i nawiązania połączenia z nią. Należy zwrócić obiekt połączenia, który zawiera strumieni na potrzeby zapisywania do serwera i odczytywania danych z serwera. Wyjątki zgłaszane w tym miejscu są przechwytywane i widoczne dla użytkownika za pośrednictwem komunikat informacyjny w programie Visual Studio.

### <a name="activation"></a>Aktywacja

Po zaimplementowaniu Klasa klienta języka należy zdefiniować dwa atrybuty na jego definiują sposób zostaną załadowane do programu Visual Studio i aktywacji:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Program Visual Studio używa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) do zarządzania jej punkty rozszerzalności. [Wyeksportować](/dotnet/api/system.componentmodel.composition.exportattribute) atrybut wskazuje do programu Visual Studio, że ta klasa powinien być pobierane jako punkt rozszerzenia i załadowany w odpowiednim czasie.

Aby użyć MEF, należy zdefiniować MEF jako zasób w manifestu VSIX.

Otwórz projektanta manifestu VSIX i przejdź do **zasoby** karty:

![Dodaj element zawartości MEF](media/lsp-add-asset.png)

Kliknij pozycję Nowy, aby utworzyć nowy element zawartości:

![Definiowanie zasobów MEF](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **źródło**: Projekt w bieżącym rozwiązaniu
* **Projekt**: [project]

### <a name="content-type-definition"></a>Definicja typu zawartości

Obecnie jedynym sposobem, aby załadować rozszerzenia serwera języka opartego na LSP jest typ zawartości pliku. Oznacza to, że podczas definiowania klasy klienta języka (który implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), należy zdefiniować typy plików, gdy otwierane, spowoduje, że rozszerzenie do załadowania. Jeśli nie pliki, które spełniają Twoje zdefiniowanego typu zawartości są otwierane, rozszerzenie nie można załadować.

Jest to realizowane poprzez definiowanie co najmniej jedną klasę ContentTypeDefinition:

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

W poprzednim przykładzie, definicja typu zawartości jest tworzony dla plików, które kończą się na *.bar* rozszerzenie pliku. Definicja typu zawartości znajduje się nazwa "bar" i **musi** dziedziczyć [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Po dodaniu definicja typu zawartości, można zdefiniować, kiedy można załadować rozszerzenia klienta języka w klasie klienta języka:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Dodano obsługę serwerów języka LSP nie wymaga wdrożenia systemu projektu w programie Visual Studio. Klienci mogą otworzyć pojedynczy plik lub folder, w programie Visual Studio, aby rozpocząć korzystanie z usługi języka. W rzeczywistości pomoc techniczna dotycząca serwerów języka LSP jest przeznaczona do pracy tylko w scenariuszach otwartego folderu/pliku. Jeśli system niestandardowego projektu jest zaimplementowany, niektóre funkcje (takie jak ustawienia) nie będzie działać.

## <a name="advanced-features"></a>Funkcje zaawansowane

### <a name="settings"></a>Ustawienia

Obsługa niestandardowe ustawienia językowe serwera jest dostępna, ale jest nadal w trakcie ulepszana. Ustawienia są właściwe co serwer języka obsługuje i zazwyczaj kontrolować, jak serwer języka emituje dane. Na przykład serwer język może być ustawienie maksymalnej liczby błędów. Twórcy rozszerzeń zdefiniować wartości domyślnej, które mogą zostać zmienione przez użytkowników do określonych projektów.

Wykonaj następujące kroki poniżej, aby dodać obsługę ustawień do rozszerzenia LSP usługi języka:

1. Dodaj plik w formacie JSON (na przykład *MockLanguageExtensionSettings.json*) w projekcie, który zawiera ustawienia i wartości domyślnych. Na przykład:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Kliknij prawym przyciskiem myszy plik JSON, a następnie wybierz pozycję **właściwości**. Zmiana **kompilacji** akcji "Treści" i "Dołącz VSIX" właściwości na wartość true.

3. Implementowanie elementów ConfigurationSections i zwrócić listę prefiksów dla ustawień zdefiniowanych w pliku JSON (w programie Visual Studio Code to mapującej nazwę sekcji konfiguracji w pliku package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Dodaj plik .pkgdef do projektu (Dodaj nowy plik tekstowy i zmień rozszerzenie pliku .pkgdef). Plik pkgdef powinien zawierać te informacje:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Przykład:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Kliknij prawym przyciskiem myszy plik .pkgdef i wybierz **właściwości**. Zmiana **kompilacji** akcji **zawartości** i **Include w VSIX** właściwości na wartość true.

6. Otwórz *source.extension.vsixmanifest* pliku i Dodaj zasób w **zasobów** karty:

   ![Edytowanie zasobów pakietu vspackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **źródło**: Plików w systemie plików
   * **Ścieżka**: [ścieżka do Twojej *.pkgdef* plików]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edytowanie ustawień dla obszaru roboczego użytkownika

1. Użytkownik otwiera zawierający pliki, których właścicielem jest serwer obszaru roboczego.
2. Użytkownik doda plik w *.vs* folder o nazwie *VSWorkspaceSettings.json*.
3. Użytkownik dodaje wiersz do *VSWorkspaceSettings.json* pliku ustawienia zawiera serwer. Na przykład:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enabling-diagnostics-tracing"></a>Włączanie śledzenia diagnostyki

Śledzenie diagnostyczne można włączyć w taki sposób, aby dane wyjściowe wszystkich wiadomości między klientem i serwerem, które mogą być przydatne podczas debugowania problemów. Aby włączyć śledzenie diagnostyczne, wykonaj następujące czynności:

4. Otwórz lub Utwórz plik ustawień obszaru roboczego *VSWorkspaceSettings.json* (patrz "Użytkownika edytowania ustawień dla obszaru roboczego").
5. Dodaj następujący wiersz w pliku ustawień json:

```json
{
    "foo.trace.server": "Off"
}
```

Istnieją trzy możliwe wartości szczegółowości śledzenia:
* "Wyłączone": całkowicie wyłączyć śledzenie
* "Komunikaty o": śledzenie włączone, ale jedyną metodą identyfikator nazwy i odpowiedzi są śledzone.
* "Pełne": śledzenie włączone; komunikat całego rpc jest śledzone.

Jeśli śledzenie jest włączone zawartości są zapisywane do pliku w *%temp%\VisualStudio\LSP* katalogu. Dziennik w formacie nazewnictwa *[LanguageClientName]-log [sygnatury Datetime]*. Obecnie śledzenie można włączyć tylko w scenariuszach Otwórz folder. Otwieranie pojedynczy plik, aby aktywować aplikację serwer języka nie ma diagnostyki śledzenie pomocy technicznej.

### <a name="custom-messages"></a>Niestandardowe komunikaty

Brak interfejsów API w miejscu, w celu ułatwienia przekazywanie komunikatów i odbieranie wiadomości z serwera języka, które nie są częścią standardowych Language Server Protocol. Aby obsługiwać komunikaty niestandardowe, należy zaimplementować [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfejsu w klasie klienta języka. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) biblioteki jest używany do przesyłania komunikatów niestandardowych między języka klienta i serwera języka. Ponieważ rozszerzenia klienta języka LSP odbywa się podobnie jak każde inne rozszerzenie programu Visual Studio, możesz dodać dodatkowe funkcje, (które nie są obsługiwane przez LSP) do programu Visual Studio (przy użyciu innych Visual Studio interfejsów API) w rozszerzeniu za pomocą niestandardowych komunikatów o.

#### <a name="receiving-custom-messages"></a>Odbieranie komunikatów niestandardowych

Aby odbierać komunikaty niestandardowe z serwera języka, należy zaimplementować [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) właściwość [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) i zwraca obiekt, który wie, jak obsługiwać niestandardowe wiadomości . Poniższy przykład:

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

#### <a name="sending-custom-messages"></a>Wysyłanie komunikatów niestandardowych

Do wysyłania niestandardowych wiadomości do serwera języka, należy zaimplementować [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metody [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Ta metoda jest wywoływana, gdy serwer języka jest uruchomiona i gotowa do odbierania komunikatów. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) obiekt jest przekazywany jako parametr, który można następnie zachować do wysyłania komunikatów do języka serwera przy użyciu [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) interfejsów API. Poniższy przykład:

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

Czasami Deweloper rozszerzenia może wystąpić potrzeba przechwycenia LSP wiadomości wysyłane do i odbierane z serwera języka. Deweloper rozszerzenia mogą na przykład chcesz zmienić parametr wiadomości wysłane dla danego komunikatu LSP lub zmienić wyniki zwrócone z serwera języka dla funkcji LSP (na przykład uzupełnianie). Jeśli jest to niezbędne, deweloperzy rozszerzenia MiddleLayer interfejs API umożliwia przechwytywanie LSP wiadomości.

Każdy komunikat LSP ma własny interfejs warstwy środkowej do przechwycenia. Do przechwycenia określonego komunikatu, należy utworzyć klasę, która implementuje interfejs warstwy środkowej dla tego komunikatu. Następnie należy zaimplementować [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfejsu w klasie klienta języka i zwrócenia wystąpienia obiektu w [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) właściwości. Poniższy przykład:

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

Funkcja Środkowa warstwa jest nadal w fazie projektowania ale nie są jeszcze pełne.

## <a name="sample-lsp-language-server-extension"></a>Rozszerzenie serwera języka LSP próbki

Aby wyświetlić kod źródłowy Przykładowe rozszerzenie przy użyciu interfejsu API klienta LSP w programie Visual Studio, zobacz przykłady w przypadku rozszerzania VSSDK [przykładowe LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Najczęściej zadawane pytania

**Chcę stworzyć system niestandardowego projektu, aby uzupełnić Mój serwer języka LSP umożliwia bogatszych obsługi różnych funkcji w programie Visual Studio, jak przejść o tych czynności?**

Obsługa języka opartego na LSP serwerów w programie Visual Studio, który opiera się na [funkcja otwierania folderu](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) i jest specjalnie z myślą o nie wymagają systemu niestandardowego projektu. Można utworzyć własny system niestandardowego projektu, postępując zgodnie z instrukcjami [tutaj](https://github.com/Microsoft/VSProjectSystem), ale niektóre funkcje, takie jak ustawienia, może nie działać. Domyślnej logiki inicjowania dla serwerów języka LSP służy do przekazywania w lokalizacji folderu głównego folderu jest otwarty, dlatego jeśli używasz systemu niestandardowego projektu, może być konieczne zapewnić logikę niestandardową podczas inicjowania, aby upewnić się, możesz serwera języka prawidłowe uruchomienie.

**Jak dodać obsługę debugera?**

Firma Microsoft będzie udostępniać obsługę [typowych debugowania protokołu](https://code.visualstudio.com/docs/extensionAPI/api-debugging) w przyszłej wersji.

**Jeśli istnieje już w PORÓWNANIU z obsługiwanych języków zainstalowana usługa (na przykład JavaScript), można nadal zainstalować rozszerzenie serwera języka LSP, która oferuje dodatkowe funkcje (na przykład zaznaczanie błędów)?**

Tak, ale nie wszystkie funkcje będzie działać prawidłowo. Jest ostatecznym celem dla rozszerzeń serwera języka LSP włączania usług języka nieobsługiwane natywnie przez program Visual Studio. Można utworzyć rozszerzenia, które oferują dodatkową pomoc przy użyciu serwerów języka LSP, ale niektóre funkcje (takie jak IntelliSense) nie będzie bezproblemowe środowisko. Ogólnie rzecz biorąc zaleca się, że rozszerzenia serwera języka LSP służyć za dostarczanie nowych środowisk języka, nie rozszerzania istniejących.

**Gdy publikowanie Moje ukończone server języka LSP VSIX?**

Zapoznaj się z instrukcjami w portalu Marketplace [tutaj](walkthrough-publishing-a-visual-studio-extension.md).
