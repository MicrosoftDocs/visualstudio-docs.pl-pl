---
title: Dodawanie rozszerzenia protokołu serwera języka | Dokumenty firmy Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740233"
---
# <a name="add-a-language-server-protocol-extension"></a>Dodawanie rozszerzenia Language Server Protocol

Language Server Protocol (LSP) jest typowym protokołem w postaci JSON RPC w wersji 2.0, używanym do dostarczania funkcji usługi językowej różnym edytorom kodu. Za pomocą protokołu deweloperzy mogą napisać serwer języka w celu zapewnienia funkcji usługi języka, takich jak IntelliSense, diagnostyka błędów, znaleźć wszystkie odwołania i tak dalej, do różnych edytorów kodu, które obsługują LSP. Tradycyjnie usługi języka w programie Visual Studio można dodać za pomocą plików gramatycznych TextMate, aby zapewnić podstawowe funkcje, takie jak wyróżnianie składni lub pisanie niestandardowych usług językowych, które używają pełnego zestawu interfejsów API rozszerzalności programu Visual Studio w celu zapewnienia bogatszych danych. Dzięki obsłudze programu Visual Studio dla LSP istnieje trzecia opcja.

![usługa protokołu serwera języka w programie Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Language Server Protocol

![Implementacja protokołu serwera języka](media/lsp-implementation.png)

W tym artykule opisano sposób tworzenia rozszerzenia programu Visual Studio, które używa serwera języka opartego na LSP. Przyjęto założenie, że masz już opracowany serwer języka oparty na LSP i po prostu chcesz zintegrować go z programem Visual Studio.

Aby uzyskać pomoc techniczną w programie Visual Studio, serwery języka mogą komunikować się z klientem (Visual Studio) za pośrednictwem dowolnego mechanizmu transmisji opartego na strumieniu, na przykład:

* Standardowe strumienie wejściowe/wyjściowe
* Nazwane potoki
* Gniazda (tylko TCP)

Intencją LSP i pomocy technicznej dla niego w programie Visual Studio jest wbudowane usługi języka, które nie są częścią produktu Visual Studio. Nie jest przeznaczony do rozszerzenia istniejących usług języka (takich jak C#) w programie Visual Studio. Aby rozszerzyć istniejące języki, zapoznaj się z przewodnikiem rozszerzalności usługi językowej (na przykład ["Roslyn" .NET Compiler Platform)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)lub zobacz [Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md).

Aby uzyskać więcej informacji na temat samego protokołu, zobacz dokumentację [tutaj](https://github.com/Microsoft/language-server-protocol).

Aby uzyskać więcej informacji na temat tworzenia przykładowego serwera języka lub integrowania istniejącego serwera języka z programem Visual Studio Code, zobacz dokumentację [tutaj](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funkcje obsługiwane przez protokół Language Server Protocol

W poniższych tabelach pokazano, które funkcje LSP są obsługiwane w programie Visual Studio:

Komunikat | Posiada pomoc techniczną w programie Visual Studio
--- | ---
Zainicjować | tak
Zainicjowany | tak
shutdown | tak
Zakończ | tak
$/cancelRequest | tak
okno/showMessage | tak
okno/showMessageRequest | tak
okno/logMessage | tak
telemetria/zdarzenie |
klient/rejestrMożność |
klient/wyrejestrowaniaMożliwość |
obszar roboczy/didZmiejeKonfiguracja | tak
obszar roboczy/didChangeWatchedFiles | tak
obszar roboczy/symbol | tak
obszar roboczy/wykonywanieZgod | tak
obszar roboczy/zastosowanieEdytuj | tak
textDocument/publishDiagnostics | tak
tekstDocument/didOtwarty | tak
tekstDocument/didZmieja | tak
tekstDocument/willZapis |
tekstDocument/willSaveWaitUntil |
tekstDocument/didZapis | tak
tekstDocument/didKrówka | tak
tekstDocument/uzupełnianie | tak
zakończenie/rozwiązanie | tak
textDocument/hover | tak
tekstDocument/podpisPomoc | tak
textDocument/odniesienia | tak
textDocument/documentSighlight | tak
tekstDokument/dokumentSymbol | tak
tekstDocument/formatowanie | tak
textDocument/zakresFormatting | tak
textDocument/onTypeFormatting |
tekstDocument/definicja | tak
tekstDocument/codeAkcja | tak
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/zmień nazwę | tak

## <a name="get-started"></a>Wprowadzenie

> [!NOTE]
> Począwszy od programu Visual Studio 2017 w wersji 15.8, obsługa wspólnego protokołu serwera języka jest wbudowana w program Visual Studio. Jeśli zostały utworzone rozszerzenia LSP przy użyciu wersji preview [Language Server Client VSIX,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) przestaną działać po uaktualnieniu do wersji 15.8 lub nowszej. Aby rozszerzenia LSP działały ponownie, należy wykonać następujące czynności:
>
> 1. Odinstaluj protokół VSIX protokołu Microsoft Visual Studio Language Server Protocol Preview.
>
>    Począwszy od wersji 15.8, za każdym razem, gdy wykonujesz uaktualnienie w programie Visual Studio, wersja zapoznawcza VSIX jest automatycznie wykrywana i usuwana.
>
> 2. Zaktualizuj odwołanie nuget do najnowszej wersji niesąbowej dla [pakietów LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Usuń zależność do programu Microsoft Visual Studio Language Server Protocol Preview VSIX w manifeście VSIX.
>
> 4. Upewnij się, że vsix określa Visual Studio 2017 wersja 15.8 Wersja zapoznawcza 3 jako dolna granica instalacji docelowej.
>
> 5. Ponownie skompiluj i wdróż.

### <a name="create-a-vsix-project"></a>Tworzenie projektu VSIX

Aby utworzyć rozszerzenie usługi języka przy użyciu serwera języka opartego na LSP, najpierw upewnij się, że masz zainstalowane obciążenie **deweloperskie rozszerzenia programu Visual Studio** dla wystąpienia programu VS.

Następnie utwórz nowy projekt VSIX, przechodząc do projektu Programu**Visual C#** >  **File** > **New Project** > **:** > **VSIX Project**

![tworzenie projektu vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalacja serwera języka i środowiska wykonawczego

Domyślnie rozszerzenia utworzone w celu obsługi serwerów języka opartych na LSP w programie Visual Studio nie zawierają samych serwerów języka ani środowiskach run y potrzebnych do ich wykonania. Deweloperzy rozszerzeń są odpowiedzialni za dystrybucję serwerów języka i wymaganych uruchomień. Istnieje kilka sposobów, aby to zrobić:

* Serwery językowe mogą być osadzone w VSIX jako pliki zawartości.
* Utwórz msi, aby zainstalować serwer języka i/lub potrzebne środowiska wykonawcze.
* W marketplace należy podać instrukcje informujące użytkowników o sposobie uzyskiwania środowiska wykonawczego i serwerów językowych.

### <a name="textmate-grammar-files"></a>Pliki gramatyczne TextMate

LSP nie zawiera specyfikacji dotyczące sposobu dostarczania kolorowania tekstu dla języków. Aby zapewnić niestandardowe kolorowanie dla języków w programie Visual Studio, deweloperzy rozszerzeń mogą używać pliku gramatycznego TextMate. Aby dodać niestandardowe pliki gramatyczne lub motywy TextMate, wykonaj następujące czynności:

1. Utwórz folder o nazwie "Gramatyka" wewnątrz rozszerzenia (lub może to być niezależnie od nazwy wybrać).

2. Wewnątrz folderu *Gramatyki* dołącz dowolne * \*pliki .tmlanguage*, * \*.plist*, * \*.tmtheme*lub * \*.json,* które umożliwiają niestandardowe kolorowanie.

   > [!TIP]
   > Plik *.tmtheme* definiuje sposób mapowania zakresów do klasyfikacji programu Visual Studio (nazwane klucze kolorów). Aby uzyskać wskazówki, można odwołać się do globalnego pliku *.tmtheme* w *katalogu\\\<%ProgramFiles(x86)%\Microsoft Visual Studio>\\ \<SKU>\Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg.*

3. Utwórz plik *pkgdef* i dodaj linię podobną do tej:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Kliknij prawym przyciskiem myszy pliki i wybierz polecenie **Właściwości**. Zmień akcję **Kompilacja** na **Zawartość** i zmień właściwość **Uwzględnij w vsix** na **true**.

Po wykonaniu poprzednich kroków folder *Gramatyki* jest dodawany do katalogu instalacyjnego pakietu jako źródło repozytorium o nazwie "MyLang" ("MyLang" jest tylko nazwą dla rozróżniania i może być dowolnym unikatowym ciągiem znaków). Wszystkie gramatyki *(.tmlanguage* plików) i plików tematycznych *(.tmtheme* plików) w tym katalogu są odbierane jako potencjał i zastępują wbudowane gramatyki dostarczone z TextMate. Jeśli zadeklarowane rozszerzenia pliku gramatycznego są zgodne z rozszerzeniem otwieranego pliku, textmate wkroczy.

## <a name="create-a-simple-language-client"></a>Tworzenie prostego klienta języka

### <a name="main-interface---ilanguageclient"></a>Główny interfejs - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Po utworzeniu projektu VSIX dodaj do projektu następujące pakiety NuGet:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Po wykonaniu zależności od pakietu NuGet po wykonaniu poprzednich kroków pakiety Newtonsoft.Json i StreamJsonRpc są również dodawane do projektu. **Nie należy aktualizować tych pakietów, chyba że masz pewność, że te nowe wersje zostaną zainstalowane w wersji programu Visual Studio przeznaczone dla rozszerzenia.** Zestawy nie zostaną uwzględnione w vsix; zamiast tego zostaną one pobrane z katalogu instalacji programu Visual Studio. Jeśli odwołujesz się do nowszej wersji zestawów niż to, co jest zainstalowane na komputerze użytkownika, rozszerzenie nie będzie działać.

Następnie można utworzyć nową klasę, która implementuje interfejs [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) który jest głównym interfejsem potrzebnym dla klientów języka łączących się z serwerem języka opartym na LSP.

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

Główne metody, które muszą być zaimplementowane są [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) i [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) jest wywoływana, gdy visual studio załadował rozszerzenie i serwer języka jest gotowy do rozpoczęcia. W tej metodzie można wywołać [Delegat StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) natychmiast zasygnalizując, że serwer języka powinien zostać uruchomiony, lub można wykonać dodatkową logikę i wywołać [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) później. **Aby aktywować serwer języka, należy w pewnym momencie wywołać startAsync.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) jest metoda ostatecznie wywoływane przez wywołanie [Delegat StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Zawiera logikę, aby uruchomić serwer języka i ustanowić połączenie z nim. Obiekt połączenia, który zawiera strumienie do zapisywania na serwerze i odczytu z serwera muszą być zwracane. Wszelkie wyjątki zgłaszane w tym miejscu są przechwytywały i wyświetlane użytkownikowi za pośrednictwem komunikatu InfoBar w programie Visual Studio.

### <a name="activation"></a>Aktywacja

Po zaimplementowanie klasy klienta języka należy zdefiniować dwa atrybuty dla niego, aby zdefiniować, jak zostanie załadowany do programu Visual Studio i aktywowany:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio używa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) do zarządzania jego punktów rozszerzalności. Atrybut [Export](/dotnet/api/system.componentmodel.composition.exportattribute) wskazuje visual studio, że ta klasa powinna zostać pobrana jako punkt rozszerzenia i załadowana w odpowiednim czasie.

Aby użyć MEF, należy również zdefiniować MEF jako zasób w manifeście VSIX.

Otwórz projektanta manifestu VSIX i przejdź do karty **Zasoby:**

![dodawanie aktywów MEF](media/lsp-add-asset.png)

Kliknij **przycisk Nowy,** aby utworzyć nowy zasób:

![definiowanie aktywów MEF](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **Źródło**: Projekt w bieżącym rozwiązaniu
* **Projekt**: [Twój projekt]

### <a name="content-type-definition"></a>Definicja typu zawartości

Obecnie jedynym sposobem załadowania rozszerzenia serwera języka opartego na LSP jest typ zawartości pliku. Oznacza to, że podczas definiowania klasy klienta języka (który implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), należy zdefiniować typy plików, które po otwarciu spowoduje rozszerzenie do załadowania. Jeśli nie zostaną otwarte żadne pliki pasujące do zdefiniowanego typu zawartości, rozszerzenie nie zostanie załadowane.

Odbywa się to poprzez zdefiniowanie jednej lub więcej `ContentTypeDefinition` klas:

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

W poprzednim przykładzie definicja typu zawartości jest tworzona dla plików, które kończą się rozszerzeniem pliku *.bar.* Definicja typu zawartości otrzymuje nazwę "bar" i musi pochodzić od [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Po dodaniu definicji typu zawartości można następnie określić, kiedy należy załadować rozszerzenie klienta języka w klasie klienta języka:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Dodawanie obsługi serwerów języka LSP nie wymaga zaimplementowania własnego systemu projektu w programie Visual Studio. Klienci mogą otworzyć pojedynczy plik lub folder w programie Visual Studio, aby rozpocząć korzystanie z usługi języka. W rzeczywistości obsługa serwerów języka LSP jest przeznaczona do pracy tylko w otwartych scenariuszach folderów/plików. Jeśli niestandardowy system projektu zostanie zaimplementowany, niektóre funkcje (takie jak ustawienia) nie będą działać.

## <a name="advanced-features"></a>Funkcje zaawansowane

### <a name="settings"></a>Ustawienia

Obsługa niestandardowych ustawień specyficznych dla języka serwera jest dostępna, ale nadal jest w trakcie ulepszania. Ustawienia są specyficzne dla tego, co obsługuje serwer języka i zazwyczaj określają sposób, w jaki serwer języka emituje dane. Na przykład serwer języka może mieć ustawienie maksymalnej liczby zgłoszonych błędów. Autorzy rozszerzeń zdefiniowaliby wartość domyślną, która może być zmieniona przez użytkowników dla określonych projektów.

Wykonaj następujące kroki poniżej, aby dodać obsługę ustawień do rozszerzenia usługi języka LSP:

1. Dodaj plik JSON (na przykład *MockLanguageExtensionSettings.json)* do projektu, który zawiera ustawienia i ich wartości domyślne. Przykład:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Kliknij prawym przyciskiem myszy plik JSON i wybierz polecenie **Właściwości**. Zmień akcję **Kompilacja** na "Zawartość" i właściwość "Uwzględnij w vsixie" na **true**.

3. Implementuj configurationsections i zwraca listę prefiksów dla ustawień zdefiniowanych w pliku JSON (W programie Visual Studio Code spowoduje to mapowanie nazwy sekcji konfiguracji w pliku package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Dodaj plik pkgdef do projektu (dodaj nowy plik tekstowy i zmień rozszerzenie pliku na pkgdef). Plik pkgdef powinien zawierać te informacje:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Przykład:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Kliknij prawym przyciskiem myszy plik pkgdef i wybierz **polecenie Właściwości**. Zmień akcję **Kompilacja** na **Zawartość** i **właściwość Dołącz w vsix** na **true**.

6. Otwórz plik *source.extension.vsixmanifest* i dodaj zasób na karcie **Zasoby:**

   ![edytowanie zasobu vspackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **Źródło**: Plik w systemie plików
   * **Ścieżka:**[Ścieżka do pliku *pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Edycja ustawień dla obszaru roboczego przez użytkownika

1. Użytkownik otwiera obszar roboczy zawierający pliki, których jest właścicielem serwera.
2. Użytkownik dodaje plik w folderze *.vs* o nazwie *VSWorkspaceSettings.json*.
3. Użytkownik dodaje wiersz do pliku *VSWorkspaceSettings.json* dla ustawienia, które zapewnia serwer. Przykład:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Włączanie śledzenia diagnostyki

Śledzenie diagnostyki można włączyć do wyprowadzania wszystkich komunikatów między klientem a serwerem, co może być przydatne podczas debugowania problemów. Aby włączyć śledzenie diagnostyczne, wykonaj następujące czynności:

1. Otwórz lub utwórz plik ustawień obszaru *roboczego VSWorkspaceSettings.json* (zobacz "Edycja ustawień dla obszaru roboczego przez użytkownika").
2. Dodaj następujący wiersz w pliku json ustawienia:

```json
{
    "foo.trace.server": "Off"
}
```

Istnieją trzy możliwe wartości szczegółowości śledzenia:

* "Off": śledzenie całkowicie wyłączone
* "Wiadomości": śledzenie włączone, ale śledzone są tylko nazwy metody i identyfikator odpowiedzi.
* "Pełne": śledzenie włączone; cała wiadomość rpc jest śledzona.

Gdy śledzenie jest włączone, zawartość jest zapisywana w pliku w katalogu *%temp%\VisualStudio\LSP.* Dziennik jest zgodny z formatem nazewnictwa *[LanguageClientName]-[Datetime Stamp].log*]. Obecnie śledzenie można włączyć tylko w przypadku scenariuszy otwartych folderów. Otwarcie pojedynczego pliku w celu aktywowania serwera języka nie obsługuje śledzenia diagnostyki.

### <a name="custom-messages"></a>Wiadomości niestandardowe

Istnieją interfejsy API w celu ułatwienia przekazywania wiadomości do i odbierania wiadomości z serwera języka, które nie są częścią standardowego protokołu serwera języka. Aby obsłużyć wiadomości niestandardowe, należy zaimplementować interfejs [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) w klasie klienta języka. [Biblioteka VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) służy do przesyłania wiadomości niestandardowych między klientem języka a serwerem języka. Ponieważ rozszerzenie klienta języka LSP jest tak samo jak każde inne rozszerzenie programu Visual Studio, można zdecydować się na dodanie dodatkowych funkcji (które nie są obsługiwane przez LSP) do programu Visual Studio (przy użyciu innych interfejsów API programu Visual Studio) w rozszerzeniu za pośrednictwem wiadomości niestandardowych.

#### <a name="receive-custom-messages"></a>Odbieranie wiadomości niestandardowych

Aby odbierać wiadomości niestandardowe z serwera języka, należy zaimplementować [Właściwość CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) w [uprzeglądarce ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) i zwrócić obiekt, który wie, jak obsługiwać wiadomości niestandardowe. Przykład poniżej:

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

Aby wysłać niestandardowe wiadomości do serwera języka, należy zaimplementować metodę [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) w [aplikacji ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Ta metoda jest wywoływana, gdy serwer języka jest uruchomiony i gotowy do odbierania wiadomości. Obiekt [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) jest przekazywany jako parametr, który można następnie zachować, aby wysyłać wiadomości do serwera języka przy użyciu interfejsów API [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Przykład poniżej:

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

Czasami deweloper rozszerzenia może chcieć przechwycić wiadomości LSP wysyłane do i odebrane z serwera języka. Na przykład deweloper rozszerzenia może chcieć zmienić parametr wiadomości wysłany dla określonej wiadomości LSP lub zmodyfikować wyniki zwrócone z serwera języka dla funkcji LSP (na przykład uzupełnień). Gdy jest to konieczne, deweloperzy rozszerzenia można użyć interfejsu API MiddleLayer do przechwytywania komunikatów LSP.

Każdy komunikat LSP ma swój własny interfejs warstwy środkowej do przechwytywania. Aby przechwycić określony komunikat, należy utworzyć klasę, która implementuje interfejs warstwy środkowej dla tej wiadomości. Następnie zaimplementuj interfejs [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) w klasie klienta języka i zwróć wystąpienie obiektu we właściwości [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Przykład poniżej:

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

Funkcja warstwy środkowej jest nadal w fazie rozwoju i nie jest jeszcze wszechstronna.

## <a name="sample-lsp-language-server-extension"></a>Przykładowe rozszerzenie serwera języka LSP

Aby wyświetlić kod źródłowy przykładowego rozszerzenia przy użyciu interfejsu API klienta LSP w programie Visual Studio, zobacz [przykład LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)ZSDK-Extensibility-Samples .

## <a name="faq"></a>Często zadawane pytania

**Chciałbym zbudować niestandardowy system projektu w celu uzupełnienia serwera języka LSP, aby zapewnić bogatszą obsługę funkcji w programie Visual Studio, jak to zrobić?**

Obsługa serwerów językowych opartych na LSP w programie Visual Studio opiera się na [funkcji otwartego folderu](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) i nie jest przeznaczona do nie wymaga niestandardowego systemu projektu. W tym miejscu można utworzyć własny [niestandardowy](https://github.com/Microsoft/VSProjectSystem)system projektu, postępując zgodnie z instrukcjami, ale niektóre funkcje, takie jak ustawienia, mogą nie działać. Domyślną logiką inicjowania serwerów języka LSP jest przekazywanie w lokalizacji folderu głównego aktualnie otwieranego folderu, więc w przypadku korzystania z niestandardowego systemu projektów może być konieczne podanie niestandardowej logiki podczas inicjowania, aby upewnić się, że serwer językowy może zostać uruchomiony poprawnie.

**Jak dodać obsługę debugera?**

Będziemy zapewniać obsługę [wspólnego protokołu debugowania](https://code.visualstudio.com/docs/extensionAPI/api-debugging) w przyszłej wersji.

**Jeśli zainstalowano już obsługiwaną usługę języka VS (na przykład JavaScript), czy nadal mogę zainstalować rozszerzenie serwera języka LSP, które oferuje dodatkowe funkcje (takie jak linting)?**

Tak, ale nie wszystkie funkcje będą działać poprawnie. Ostatecznym celem dla rozszerzeń serwera języka LSP jest włączenie usług językowych, które nie są natywnie obsługiwane przez program Visual Studio. Można tworzyć rozszerzenia, które oferują dodatkową obsługę przy użyciu serwerów języka LSP, ale niektóre funkcje (takie jak IntelliSense) nie będą płynne. Ogólnie rzecz biorąc zaleca się, że rozszerzenia serwera języka LSP mogą być używane do dostarczania nowych środowisk językowych, a nie rozszerzania istniejących.

**Gdzie mogę opublikować ukończony serwer języka LSP VSIX?**

Zapoznaj się z instrukcjami Marketplace [tutaj](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Zobacz też

- [Dodawanie obsługi edytora programu Visual Studio dla innych języków](../ide/adding-visual-studio-editor-support-for-other-languages.md)
