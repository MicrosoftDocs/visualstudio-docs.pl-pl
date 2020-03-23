---
title: 'Samouczek: Azure Functions'
description: Korzystanie z funkcji platformy Azure w programie Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 43720947d36fec1ee64c81a48f7bc3eb7466d034
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983366"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Samouczek: Wprowadzenie do usługi Azure Functions

W tym laboratorium dowiesz się, jak rozpocząć tworzenie usługi Azure Functions przy użyciu programu Visual Studio dla komputerów Mac. Można również zintegrować z tabelami magazynu platformy Azure, które reprezentują jeden z wielu rodzajów powiązań i wyzwalaczy dostępnych dla deweloperów usługi Azure Functions.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie i debugowanie lokalnych funkcji platformy Azure
> * Integracja z zasobami magazynu w sieci Web i platformy Azure
> * Organizowanie przepływu pracy obejmującego wiele funkcji platformy Azure

## <a name="requirements"></a>Wymagania

- Visual Studio dla komputerów Mac 7.5 lub nowszych.
- Subskrypcja platformy Azure [https://azure.com/free](https://azure.com/free)(dostępna bezpłatnie).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Ćwiczenie 1: Tworzenie projektu usługi Azure Functions

1. Uruchom **program Visual Studio dla komputerów Mac**.

2. Wybierz **opcję Plik > nowe rozwiązanie**.

3. W kategorii **Cloud > General** wybierz szablon Usługi **Azure.** Użyjesz języka C# do utworzenia biblioteki klas .NET, która obsługuje usługi Azure Functions. Kliknij przycisk **alej**.

    ![wybór szablonu funkcji azure](media/azure-functions-lab-image1.png)

4. Ustaw **nazwę projektu** na **"AzureFunctionsLab"** i kliknij przycisk **Utwórz**.

    ![nazewnictwo i tworzenie projektu funkcji platformy Azure](media/azure-functions-lab-image2.png)

5. Rozwiń węzły w **aplikacji Solution Pad**. Domyślny szablon projektu zawiera odwołania NuGet do różnych pakietów usługi Azure WebJobs, a także pakiet Newtonsoft.Json.

     Istnieją również trzy pliki: - **host.json** do opisywania globalnych opcji konfiguracji dla hosta - **local.settings.json** do konfigurowania ustawień usługi.
        - Szablon projektu tworzy również domyślny httptrigger. Dla dobra tego laboratorium należy usunąć plik **HttpTrigger.cs** z projektu.

    Otwórz **local.settings.json**. Domyślnie ma dwa puste ustawienia ciągu połączenia.

    ![podkładka rozrachująca wyświetlająca plik local.settings.json](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Ćwiczenie 2: Tworzenie konta magazynu platformy Azure

1. Zaloguj się do swojego [https://portal.azure.com](https://portal.azure.com)konta platformy Azure w programie .

1. W sekcji **Ulubione,** znajdującej się po lewej stronie ekranu, wybierz pozycję **Konta magazynu:**

    ![Sekcja ulubionych witryny Azure Portal z elementem kont magazynu](media/azure-functions-lab-image4.png)

1. Wybierz **pozycję Dodaj,** aby utworzyć nowe konto magazynu:

    ![Przycisk , aby dodać nowe konto magazynu](media/azure-functions-lab-image5.png)

1. Wprowadź globalnie unikatową nazwę **nazwy** i użyj jej ponownie dla **grupy Zasobów**. Wszystkie pozostałe elementy można zachować jako ich domyślne.

    ![nowe szczegóły konta magazynu](media/azure-functions-lab-image6.png)

1. Kliknij przycisk **Utwórz**. Utworzenie konta magazynu może potrwać kilka minut. Otrzymasz powiadomienie po pomyślnym utworzeniu.

    ![pomyślne powiadomienie o wdrożeniu](media/azure-functions-lab-image7.png)

1. Wybierz przycisk **Przejdź do zasobu** z powiadomienia.

1. Wybierz kartę **Klawisze dostępu.**

    ![ustawienie klawisza dostępu](media/azure-functions-lab-image8.png)

1. Skopiuj pierwszy **ciąg połączenia**. Ten ciąg jest używany do integracji usługi Azure Storage z usługą Azure Functions później.

    ![informacje dla klucza 1](media/azure-functions-lab-image9.png)

1. Wróć do **programu Visual Studio dla komputerów Mac** i wklej cały ciąg połączenia jako ustawienie **AzureWebJobsStorage** w **local.settings.json**. Teraz można odwoływać się do nazwy ustawienia w atrybutach dla funkcji, które wymagają dostępu do jego zasobów.

    ![plik ustawień lokalnych z wprowadzonym kluczem połączenia](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Przykład 3: Tworzenie i debugowanie funkcji platformy Azure

1. Teraz możesz zacząć dodawać kod. Podczas pracy z biblioteką klas .NET usługi Azure Functions są dodawane jako metody statyczne. Z **konsoli rozwiązania**kliknij prawym przyciskiem myszy węzeł projektu **AzureFunctions** i wybierz polecenie **Dodaj > Dodaj funkcję:**

    ![Opcja Dodaj funkcję](media/azure-functions-lab-image11.png)

1. W oknie dialogowym Nowe funkcje platformy Azure wybierz szablon ogólnego elementu webhook. Ustaw **nazwę,** aby **dodać** i kliknij przycisk **Ok,** aby utworzyć funkcję:

    ![Nowe okno dialogowe funkcji platformy Azure](media/azure-functions-lab-image12.png)

1. W górnej części nowego pliku dodaj poniższe dyrektywy **using:**

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Usuń istniejącą `Run` metodę i dodaj poniższą metodę do klasy jako funkcję platformy Azure:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. Przejdźmy przez definicję metody kawałek po kawałku.

    Pierwszą rzeczą, którą zobaczysz, jest atrybut **FunctionName,** który oznacza tę metodę jako funkcję platformy Azure. Atrybut wyznacza publiczną nazwę funkcji. Nazwa atrybutu nie musi być zgodna z rzeczywistą nazwą metody.

    ![Nowa metoda uruchamiania z wyróżnionym atrybutem FunctionName](media/azure-functions-lab-image13.png)

1. Następnie metoda jest oznaczona jako publiczna metoda **statyczna,** która jest wymagana. Można również zauważyć, że zwracana wartość jest **int**. O ile nie określono inaczej przy użyciu atrybutów metody, wszelkie non-void zwracana wartość funkcji platformy Azure jest zwracany do klienta jako tekst. Domyślnie jest zwracany jako **XML**, ale można zmienić na **JSON**, co zrobisz później w laboratorium.

    ![Nowa metoda uruchamiania z wyróżnioną inicjacją metody](media/azure-functions-lab-image14.png)

1. Pierwszy parametr jest oznaczony atrybutem **HttpTrigger,** który wskazuje, że ta metoda jest wywoływana przez żądanie HTTP. Atrybut określa również poziom autoryzacji metody, a także zlecenia, które obsługuje (tylko **"GET"** w tym przypadku). Można również opcjonalnie zdefiniować **Route,** który zastępuje ścieżkę do metody i oferuje sposób automatycznego wyodrębniania zmiennych ze ścieżki. Ponieważ **route** jest w tym miejscu zerowy, ścieżka do tej metody będzie domyślnie **/api/Add**.

    ![Nowa metoda uruchamiania z wyróżnionym parametrem](media/azure-functions-lab-image15.png)

1. Ostatnim parametrem metody jest **TraceWriter,** który może służyć do rejestrowania komunikatów dla diagnostyki i błędów.

    ![Nowa metoda uruchamiania z wyróżnioną pozycją TraceWriter](media/azure-functions-lab-image16.png)

1. Ustaw punkt przerwania w wierszu **powrotu** metody, klikając margines wiersza:

    ![Punkt przerwania ustawiony w wierszu powrotu](media/azure-functions-lab-image17.png)

1. Skompiluj i uruchom projekt w sesji debugowania, naciskając **klawisz F5** lub wybierając **polecenie Uruchom > Rozpocznij debugowanie**. Można też kliknąć przycisk **Uruchom.** Wszystkie te opcje wykonują to samo zadanie. Reszta tego laboratorium odwołuje się do **F5,** ale możesz użyć metody, którą uważasz za najbardziej komfortową.

    ![Tworzenie i uruchamianie projektu](media/azure-functions-lab-image18.png)

1. Uruchomienie projektu spowoduje automatyczne otwarcie aplikacji Terminal.

1. Projekt przechodzi przez proces wykrywania usług Azure Functions na podstawie atrybutów metody i konwencji plików, która jest omówiona w dalszej części tego artykułu. W takim przypadku wykrywa pojedynczą funkcję platformy Azure i "generuje" 1 funkcję zadania.

    ![Dane wyjściowe funkcji platformy Azure w terminalu](media/azure-functions-lab-image19.png)

1. U dołu komunikatów startowych host usług Azure Functions drukuje adresy URL dowolnych interfejsów API wyzwalacza HTTP. Powinien być tylko jeden. Skopiuj ten adres URL i wklej go na nowej karcie przeglądarki.

    ![Adres URL interfejsu API funkcji platformy Azure](media/azure-functions-lab-image20.png)

1. Punkt przerwania powinien wyzwolić natychmiast. Żądanie sieci web został przekierowany do funkcji i teraz można debugować. Najedź myszką na zmienną **x,** aby zobaczyć jej wartość.

    ![Punkt przerwania wyzwolony](media/azure-functions-lab-image21.png)

1. Usuń punkt przerwania przy użyciu tej samej metody, która została użyta do wcześniejszego dodania (kliknij na margines lub wybierz linię i naciśnij **klawisz F9).**

1. Naciśnij **klawisz F5,** aby kontynuować bieg.

1. W przeglądarce zostanie renderowany wynik XML metody. Zgodnie z oczekiwaniami operacja dodawania zakodowanego na stałe daje wiarygodną sumę. Uwaga: jeśli widzisz tylko "3" w przeglądarce Safari, przejdź do **przeglądarki Safari > preferencje > zaawansowane** i zaznacz pole wyboru " Pokaż menu**rozwijaj na pasku menu**" i przeładuj ponownie stronę.

1. W **programie Visual Studio dla komputerów Mac**kliknij przycisk **Zatrzymaj,** aby zakończyć sesję debugowania. Aby upewnić się, że nowe zmiany są pobierane, nie zapomnij ponownie uruchomić (zatrzymać, a następnie uruchomić) sesji debugowania.

    ![Opcja Zatrzymaj debugowanie](media/azure-functions-lab-image22.png)

1. W **Run** metody, zastąpić **x** i **y** definicje z kodem poniżej. Ten kod wyodrębnia wartości z ciągu zapytania adresu URL, dzięki czemu operacja dodawania może być wykonywana dynamicznie na podstawie podanych parametrów.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Uruchom aplikację.

1. Wróć do okna przeglądarki i `/?x=2&y=3` dołącz ciąg do adresu URL. Cały adres URL `http://localhost:7071/api/Add?x=2&y=3`powinien być teraz . Przejdź do nowego adresu URL.

1. Tym razem wynik powinien odzwierciedlać nowe parametry. Zapraszam do uruchomienia projektu z różnymi wartościami. Należy zauważyć, że nie ma żadnych sprawdzania błędów, więc nieprawidłowe lub brakujące parametry zrzucą błąd.

1. Zatrzymaj sesję debugowania.

## <a name="exercise-4-working-with-functionjson"></a>Ćwiczenie 4: Praca z function.json

1. We wcześniejszym ćwiczeniu wspomniano, że visual studio dla komputerów Mac "wygenerował" funkcję zadania dla funkcji platformy Azure zdefiniowaną w bibliotece. Dzieje się tak, ponieważ usługa Azure Functions faktycznie nie używa atrybutów metody w czasie wykonywania, ale raczej używa konwencji systemu plików w czasie kompilacji, aby skonfigurować, gdzie i jak usługi Azure Functions są udostępniane. Z **Solution Pad**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję Pokaż w **finderze**.

     ![Opcja menu Pokaż w finderze](media/azure-functions-lab-image23.png)

1. Przejdź w dół systemu plików, aż dojdziesz do **bin / Debug / netstandard2.0**. Powinien istnieć folder o nazwie **Add**. Ten folder został utworzony w celu korespondowania z atrybutem nazwa funkcji w kodzie C#. Rozwiń folder Dodaj, aby wyświetlić pojedynczy plik **function.json.** Ten plik jest używany przez środowisko wykonawcze do hostowania funkcji platformy Azure i zarządzania nią. W przypadku innych modeli języków bez obsługi w czasie kompilacji (takich jak skrypt C# lub JavaScript), te foldery muszą być ręcznie tworzone i obsługiwane. Dla deweloperów języka C# są one generowane automatycznie na podstawie metadanych atrybutów na kompilacji. Kliknij prawym przyciskiem myszy **na function.json** i wybierz, aby otworzyć go w programie Visual Studio.

    ![function.json w katalogu plików](media/azure-functions-lab-image24.png)

1. Biorąc pod uwagę poprzednie kroki tego samouczka, należy mieć podstawową wiedzę atrybutów języka C#. Biorąc to pod uwagę, ten JSON powinien wyglądać znajomo. Istnieje jednak kilka elementów, które nie zostały uwzględnione we wcześniejszych ćwiczeniach. Na przykład każde **powiązanie** musi mieć ustawiony **kierunek.** Jak można wywnioskować, **"w"** oznacza, że parametr jest wejściowy, natomiast **"out"** wskazuje, że parametr jest albo wartością zwracaną (za pośrednictwem **$return)** lub **out** parametr do metody. Należy również określić **scriptFile** (względem tej lokalizacji końcowej) i **entryPoint** metody (publicznych i statycznych) w zestawie. W następnych kilku krokach dodasz niestandardową ścieżkę funkcji przy użyciu tego modelu, więc skopiuj zawartość tego pliku do schowka.

    ![function.json plik otwarty w programie Visual Studio dla komputerów Mac](media/azure-functions-lab-image25.png)

1. W **programie Solution Pad**kliknij prawym przyciskiem myszy węzeł projektu **AzureFunctionsLab** i wybierz polecenie **Dodaj > nowy folder**. Nazwij nowy folder **Adder**. Domyślnie konwencja, nazwa tego folderu zdefiniuje ścieżkę do interfejsu API, takich jak **api/Adder**.

    ![Nowa opcja folderu](media/azure-functions-lab-image26.png)

1. Kliknij prawym przyciskiem myszy folder **Adder** i wybierz polecenie **Dodaj > nowy plik**.

    ![Nowa opcja pliku](media/azure-functions-lab-image27.png)

1. Wybierz kategorię **Sieci Web** i szablon Pusty **plik JSON.** Ustaw **nazwę,** aby **działać** i kliknij przycisk **Nowy**.

    ![Opcja Opróżnij plik json](media/azure-functions-lab-image28.png)

1. Wklej zawartość innego **pliku function.json** (od kroku 3), aby zastąpić domyślną zawartość nowo utworzonego pliku.

1. Usuń następujące wiersze z górnej części pliku json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na końcu pierwszego powiązania (po **wierszu "name": "req")** dodaj poniższe właściwości. Nie zapomnij dołączyć przecinka w poprzednim wierszu. Ta właściwość zastępuje domyślny katalog główny w taki sposób, że będzie teraz wyodrębniać parametry **int** ze ścieżki i umieszczać je w parametrach metody o nazwach **x** i **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Dodaj kolejne powiązanie pod pierwszym. To powiązanie obsługuje zwracaną wartość funkcji. Nie zapomnij dołączyć przecinka w poprzednim wierszu:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Zaktualizuj również właściwość **entryPoint** u dołu pliku, aby użyć metody o nazwie **"Add2",** takiej jak pokazano poniżej. Ma to na celu zilustrowanie, że **ścieżka api/Adder ...** może mapować do odpowiedniej metody o dowolnej nazwie **(Add2** tutaj).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Twój końcowy plik **function.json** powinien wyglądać następująco:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Ostatnim krokiem wymaganym do wykonania tej pracy jest poinstruowanie programu Visual Studio dla komputerów Mac, aby skopiował ten plik do tej samej ścieżki względnej w katalogu wyjściowym za każdym razem, gdy się zmienia. Po wybraniu pliku wybierz kartę właściwości z paska po prawej stronie, a w przypadku **katalogu Kopiuj do katalogu wyjściowego** wybierz **pozycję Kopiuj, jeśli nowsza:**

    ![Opcje właściwości pliku json](media/azure-functions-lab-image30.png)

1. W **Add.cs**, zastąp `Run` metodę (w tym atrybut) następującą metodą spełnienia oczekiwanej funkcji. Jest bardzo podobny `Run`do , z tą różnicą, że nie używa żadnych atrybutów i ma wyraźne parametry dla **x** i **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. Naciśnij **klawisz F5,** aby zbudować i uruchomić projekt.

1. Po zakończeniu kompilacji i rozkręceniu platformy, będzie teraz wskazywać, że istnieje druga trasa dostępna dla żądań, które mapuje do nowo dodanej metody:

    ![Adres URL funkcji Http](media/azure-functions-lab-image31.png)

1. Zwróć okno przeglądarki i **http://localhost:7071/api/Adder/3/5**przejdź do .

1. Tym razem metoda działa po raz kolejny, wyciągając parametry ze ścieżki i produkując sumę.

1. Wróć do **programu Visual Studio dla komputerów Mac** i zakończ sesję debugowania.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Ćwiczenie 5: Praca z tabelami magazynu platformy Azure

Często usługa, którą tworzysz, może być znacznie bardziej złożona niż to, które zbudowaliśmy do tej pory i wymaga znacznej ilości czasu i/lub infrastruktury do wykonania. W takim przypadku może okazać się skuteczne akceptowanie żądań, które są umieszczane w kolejce do przetwarzania, gdy zasoby stają się dostępne, które usługi Azure Functions zapewnia obsługę. W innych przypadkach należy przechowywać dane centralnie. Tabele usługi Azure Storage umożliwiają szybkie zrobicie to.

1. Dodaj poniższą klasę do **Add.cs**. Powinien przejść wewnątrz obszaru nazw, ale poza istniejącą klasą.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. W ramach **Add** klasy dodaj poniższy kod, aby wprowadzić inną funkcję. Należy zauważyć, że ten jest unikatowy do tej pory, ponieważ nie wymaga odpowiedzi HTTP. Wiersz końcowy zwraca nowy **TableRow** wypełnione niektóre kluczowe informacje, które ułatwią pobieranie później **(PartitionKey** i **RowKey),** a także jego parametry i suma. Kod w ramach metody używa również **TraceWriter,** aby ułatwić poznanie, kiedy funkcja jest uruchamiana.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. Naciśnij **klawisz F5,** aby zbudować i uruchomić projekt.

1. Na karcie przeglądarka **http://localhost:7071/api/Process/4/6**przejdź do pozycji . Spowoduje to umieszczenie innej wiadomości w kolejce, co ostatecznie powinno spowodować inny wiersz jest dodawany do tabeli.

1. Wróć do **terminalu** i obserwuj przychodzące żądanie **dla 4 + 6**.

    ![Wyjście zacisku z żądaniem dodania](media/azure-functions-lab-image32.png)

1. Wróć do przeglądarki, aby odświeżyć żądanie do tego samego adresu URL. Tym razem zostanie wyświetlony błąd po **Process** metody. Jest tak, ponieważ kod próbuje dodać wiersz do tabeli usługi Azure Table Storage przy użyciu kombinacji kluczy partycji i wiersza, która już istnieje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Zakończ sesję debugowania.

1. Aby ograniczyć błąd, należy dodać następujący parametr do definicji metody bezpośrednio przed **TraceWriter** parametru. Ten parametr instruuje platformę Usługi Azure Functions, aby podjąć próbę pobrania **TableRow** z **tabeli Wyniki** na **PartitionKey,** który używaliśmy do przechowywania wyników. Jednak niektóre z prawdziwej magii wchodzi w grę, gdy zauważysz, że **RowKey** jest generowany dynamicznie na podstawie innych parametrów **x** i **y** dla tej samej metody. Jeśli ten wiersz już istnieje, a następnie **tableRow** będzie go, gdy metoda zaczyna się bez dodatkowej pracy wymaganej przez dewelopera. Jeśli wiersz nie istnieje, to będzie po prostu null. Ten rodzaj wydajności umożliwia deweloperom skupić się na ważnej logiki biznesowej, a nie na infrastrukturze.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Dodaj poniższy kod na początku metody. Jeśli **tableRow** nie jest null, a następnie mamy już wyniki dla operacji żądane i można zwrócić go natychmiast. W przeciwnym razie funkcja jest kontynuowana tak jak poprzednio. Chociaż może to nie być najbardziej niezawodny sposób zwracania danych, ilustruje punkt, że można zorganizować niezwykle zaawansowane operacje w wielu skalowalnych warstwach z bardzo małym kodem.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Naciśnij **klawisz F5,** aby zbudować i uruchomić projekt.

1. Na karcie przeglądarka odśwież **http://localhost:7071/api/Process/4/6**adres URL w pliku . Ponieważ wiersz tabeli dla tego rekordu istnieje, powinien zwrócić natychmiast i bez błędu. Ponieważ nie ma wyjścia HTTP, można zobaczyć dane wyjściowe w terminalu.

    ![Wyjście terminalu pokazujące wiersz tabeli już istnieje](media/azure-functions-lab-image33.png)

1. Zaktualizuj adres URL, aby odzwierciedlić kombinację, która nie została jeszcze przetestowana, na przykład **http://localhost:7071/api/Process/5/7**. Zanotuj komunikat w terminalu, który wskazuje, że wiersz tabeli nie został znaleziony (zgodnie z oczekiwaniami).

    ![Wyjście zacisku pokazujące nowy proces](media/azure-functions-lab-image34.png)

1. Wróć do **programu Visual Studio dla komputerów Mac** i zakończ sesję debugowania.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Podsumowanie

W tym laboratorium dowiesz się, jak rozpocząć tworzenie usług Azure Functions w programie Visual Studio dla komputerów Mac.
