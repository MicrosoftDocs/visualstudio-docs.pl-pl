---
title: 'Samouczek: Azure Functions'
description: Użycie usługi Azure functions w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: d728de52a159d058ecae48d48620547b6d8fcf4f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652972"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Samouczek: Wprowadzenie do usługi Azure Functions

W tym laboratorium dowiesz się, jak rozpocząć tworzenie usługi Azure Functions przy użyciu programu Visual Studio dla komputerów Mac. Będzie można również zintegrować z tabele magazynu platformy Azure, które reprezentują jedną z wielu różnych powiązania i wyzwalacze dostępnych dla deweloperów usługi Azure Functions.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie i debugowanie lokalne usługi Azure Functions
> * Integracja z usługą sieci web i zasobami usługi Azure storage
> * Możesz odpowiednio organizować w przepływie pracy obejmujące wiele funkcji platformy Azure

## <a name="requirements"></a>Wymagania

- Program Visual Studio dla komputerów Mac w wersji 7.5 lub nowszej.
- Subskrypcja platformy Azure (dostępne wolne od [ https://azure.com/free ](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Ćwiczenie 1: Tworzenie projektu usługi Azure Functions

1. Uruchom **programu Visual Studio dla komputerów Mac**.

2. Wybierz **Plik > nowe rozwiązanie**.

3. Z **chmura > Ogólne** kategorii, wybierz opcję **usługi Azure Functions** szablonu. Użyjesz C# do tworzenia biblioteki klas .NET obsługujący usługi Azure Functions. Kliknij przycisk **Dalej**.

    ![Wybieranie szablonu usługi Azure functions](media/azure-functions-lab-image1.png)

4. Ustaw **Nazwa projektu** do **"AzureFunctionsLab"** i kliknij przycisk **Utwórz**.

    ![Nazewnictwo i tworzenie projektu funkcji platformy azure](media/azure-functions-lab-image2.png)

5. Rozwiń węzły w **konsoli rozwiązania**. Domyślny szablon projektu zawiera odwołania do NuGet z szeroką gamą pakietów usługi Azure WebJobs, a także pakiet Newtonsoft.Json.

     Dostępne są także trzy pliki:- **host.json** do opisywania globalną opcje konfiguracji dla hosta — **local.settings.json** do konfigurowania ustawień usługi.
        - Szablon projektu tworzy również domyślny HttpTrigger. Dla tego laboratorium, należy usunąć **HttpTrigger.cs** pliku z projektem.

    Open **local.settings.json**. Domyślnie po dwa połączenia pusty ciąg ustawienia.

    ![solution pad displaying local.settings.json file](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Ćwiczenie 2: Tworzenie konta usługi Azure storage

1. Zaloguj się do konta platformy Azure na poziomie [ https://portal.azure.com ](https://portal.azure.com).

1. W obszarze **ulubione** sekcji znajduje się w lewej części ekranu wybierz **kont magazynu**:

    ![sekcja ulubionych elementu witryny Azure portal przedstawiający kont magazynu](media/azure-functions-lab-image4.png)

1. Wybierz **Dodaj** do utworzenia nowego konta magazynu:

    ![Przycisk, aby dodać nowe konto magazynu](media/azure-functions-lab-image5.png)

1. Wprowadź unikatową w skali globalnej nazwę **nazwa** i ponowne użycie go do **grupy zasobów**. Domyślnie, można zachować wszystkie pozostałe elementy.

    ![szczegóły nowego konta magazynu](media/azure-functions-lab-image6.png)

1. Kliknij przycisk **Utwórz**. Może upłynąć kilka minut, aby utworzyć konto magazynu. Otrzymasz powiadomienie po pomyślnym utworzeniu.

    ![powiadomienie pomyślnego wdrożenia](media/azure-functions-lab-image7.png)

1. Wybierz **przejdź do zasobu** przycisk powiadomienia.

1. Wybierz **klucze dostępu** kartę.

    ![Ustawienie klucza dostępu](media/azure-functions-lab-image8.png)

1. Skopiuj pierwszy **parametry połączenia**. Ten ciąg jest używany w dalszej integracji usługi Azure storage z usługi Azure Functions.

    ![informacje dotyczące klucza 1](media/azure-functions-lab-image9.png)

1. Wróć do **programu Visual Studio dla komputerów Mac** i Wklej w ciągu połączenia pełne, jak **AzureWebJobsStorage** w **local.settings.json**. Teraz możesz odwoływać się nazwa ustawienia w atrybutach dla funkcji, które muszą mieć dostęp do swoich zasobów.

    ![Plik ustawień lokalnych z wprowadzony klucz połączenia](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Przykład 3: Tworzenie i debugowanie funkcji platformy Azure

1. Teraz możesz rozpocząć dodawanie kodu. Podczas pracy z biblioteki klas platformy .NET, usługi Azure Functions są dodawane jako metody statyczne. Z **konsoli rozwiązania**, kliknij prawym przyciskiem myszy **AzureFunctions** węzeł projektu i wybierz pozycję **Dodaj > Dodaj funkcję**:

    ![Dodaj opcję — funkcja](media/azure-functions-lab-image11.png)

1. W oknie dialogowym nowej usługi Azure Functions wybierz szablon ogólny element webhook. Ustaw **nazwa** do **Dodaj** i kliknij przycisk **Ok** Tworzenie funkcji:

    ![Okno dialogowe nowej usługi azure functions](media/azure-functions-lab-image12.png)

1. U góry nowego pliku, należy dodać **przy użyciu** dyrektywy poniżej:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Usuń istniejące `Run` metody i Dodaj metodę poniżej do klasy jako funkcji platformy Azure:

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
1. Przejdźmy teraz przez definicję metody eliminujemy.

    Pierwszą rzeczą, zostanie wyświetlony jest **FunctionName** atrybut, który oznacza tę metodę jako funkcję platformy Azure. Ten atrybut Określa publiczny nazwę funkcji. Nazwa atrybutu nie musi być zgodna z nazwą rzeczywistego — metoda.

    ![Nowa metoda uruchamiania atrybutem FunctionName wyróżniony](media/azure-functions-lab-image13.png)

1. Następnie metoda jest oznaczona jako **publiczne statyczne** metody, która jest wymagana. Można także zauważyć, że wartość zwracana jest **int**. Chyba że określono inaczej, przy użyciu metody atrybutów, wszelkie niż void wartość zwracaną funkcji platformy Azure jest zwracany do klienta jako tekst. Domyślnie jest zwracana jako **XML**, ale można ją zmienić na **JSON**, którego należy to zrobić później w środowisku laboratoryjnym.

    ![Nowa metoda uruchamiania przy użyciu metody inicjowania wyróżniony](media/azure-functions-lab-image14.png)

1. Pierwszy parametr jest oznaczony za pomocą **HttpTrigger** atrybut, który wskazuje, że ta metoda jest wywoływana przez żądanie HTTP. Ten atrybut określa również poziom autoryzacji, metody, a także zleceń obsługuje (tylko **"GET"** w tym przypadku). Mogą również opcjonalnie określić **trasy** , zastępuje ścieżki do metody i możliwość podzielenia próbę automatycznego wyodrębniania zmienne przy użyciu ścieżki. Ponieważ **trasy** ma wartość null w tym miejscu będą domyślnie ścieżkę do tej metody **/api/Dodaj**.

    ![Nowa metoda uruchamiania za pomocą parametru wyróżniony](media/azure-functions-lab-image15.png)

1. Ostatni parametr metody jest **TraceWriter** który może służyć do rejestrowania komunikatów błędów i diagnostyki.

    ![Nowa metoda uruchamiania z wyróżnioną pozycją TraceWriter](media/azure-functions-lab-image16.png)

1. Ustaw punkt przerwania na **zwracają** wiersz metody, klikając na marginesie wiersza:

    ![Punkt przerwania w wierszu zwrotu](media/azure-functions-lab-image17.png)

1. Kompilowanie i uruchamianie projektu w trakcie sesji debugowania, naciskając klawisz **F5** lub wybierając **Uruchom > Rozpocznij debugowanie**. Można również kliknąć **Uruchom** przycisku. Opcje te wykonują to samo zadanie. Odwołuje się do pozostałej części tego laboratorium **F5**, ale można użyć metody, można znaleźć najbardziej Ci.

    ![Kompilowanie i uruchamianie projektu](media/azure-functions-lab-image18.png)

1. Uruchamianie projektu zostanie automatycznie uruchomiona terminalu aplikacji.

1. Projekt przechodzi przez proces wykrywania usługi Azure Functions, w oparciu o atrybuty metody i Konwencji plików, które zostało omówione w dalszej części tego artykułu. W tym przypadku wykrywa pojedynczej funkcji platformy Azure i 1 stanowisko "generuje".

    ![Dane wyjściowe funkcji platformy Azure w terminalu](media/azure-functions-lab-image19.png)

1. W dolnej części wiadomości uruchamiania hosta usługi Azure Functions drukuje adresy URL dowolnego wyzwalacza HTTP interfejsów API. Powinien istnieć tylko jeden. Skopiuj ten adres URL i wklej go w nowej karcie przeglądarki.

    ![Adres URL interfejsu API funkcji platformy Azure](media/azure-functions-lab-image20.png)

1. Punkt przerwania powinny wywoływać bezpośrednio. Żądania sieci web został przesłany do funkcji i można teraz debugować. Wskaźnik myszy nad **x** zmiennej, aby zobaczyć jej wartość.

    ![Punkt przerwania wyzwolone](media/azure-functions-lab-image21.png)

1. Usuń punkt przerwania przy użyciu tej samej metody, które są używane do dodawania go wcześniej (kliknij na marginesie, lub zaznacz wiersz, a następnie naciśnij klawisz **F9**).

1. Naciśnij klawisz **F5** kontynuować działanie.

1. XML wynikiem metody będą renderowane w przeglądarce. Zgodnie z oczekiwaniami, operacja dodawania zapisane na stałe tworzy wiarygodne sum. Uwaga: Jeśli wyświetlane są tylko "3" w przeglądarce Safari, go, aby **Safari > Preferencje > Zaawansowane** i "**pokazują tworzenie menu na pasku menu**" checkbox i ponownie załaduj stronę.

1. W **programu Visual Studio dla komputerów Mac**, kliknij przycisk **zatrzymać** przycisk, aby zakończyć sesję debugowania. Aby upewnić się, że nowe zmiany są pobierane, nie zapomnij Uruchom ponownie (Zatrzymaj i uruchom) sesji debugowania.

    ![Zatrzymaj debugowanie opcji](media/azure-functions-lab-image22.png)

1. W **Uruchom** metody, Zastąp **x** i **y** definicje z poniższym kodem. Ten kod wyodrębnia wartości z ciągu zapytania adresu URL, tak aby operacja dodawania może zostać wykonana dynamicznie w oparciu podane parametry.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Uruchom aplikację.

1. Wróć do okna przeglądarki i Dołącz ciąg `/?x=2&y=3` do adresu URL. Cały adres URL powinien być teraz `http://localhost:7071/api/Add?x=2&y=3`. Przejdź do nowego adresu URL.

1. Tym razem wynik powinien odzwierciedlać nowych parametrów. Możesz uruchomić projekt z różnymi wartościami. Należy pamiętać, że nie ma wszelkie błędy sprawdzania, dzięki czemu będzie sygnalizować błąd, nieprawidłowe lub brakujące parametry.

1. Zatrzymaj sesję debugowania.

## <a name="exercise-4-working-with-functionjson"></a>Ćwiczenie 4: Praca z function.json

1.  W ćwiczeniu wcześniej wspomniano, Visual Studio for Mac "wygenerowania" funkcję zadania dla funkcji platformy Azure zdefiniowany w bibliotece. Jest to, ponieważ usługi Azure Functions faktycznie nie używa atrybuty metody w czasie wykonywania, ale raczej używa konwencji systemu plików w czasie kompilacji do konfigurowania miejsca i w jaki sposób usługa Azure Functions są udostępniane. Z **konsoli rozwiązania**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Odsłoń w programie Finder**.

     ![Odsłoń w opcji menu wyszukiwania](media/azure-functions-lab-image23.png)

1. Nawigować w systemie plików, aż dojdziesz **bin/Debug/netstandard2.0**. Powinna to być folder o nazwie **Dodaj**. Ten folder został utworzony z atrybutu nazwy funkcji w kodzie języka C#. Rozwiń folder Dodaj, aby wyświetlić jeden **function.json** pliku. Ten plik jest używany przez środowisko uruchomieniowe do zarządzania funkcją platformy Azure. W przypadku innych modeli języka nie obsługują kompilacji (na przykład skrypt języka C# lub JavaScript) te foldery musi być ręcznie tworzone i konserwowane. Dla deweloperów języka C# są one generowane automatycznie z metadanych atrybutu podczas kompilacji. Kliknij prawym przyciskiem myszy **function.json** a następnie wybierz pozycję Tak, aby go otworzyć w programie Visual Studio.

    ![Function.JSON w katalogu pliku](media/azure-functions-lab-image24.png)

1. Biorąc pod uwagę poprzednie kroki tego samouczka, należy mieć podstawową wiedzę na temat atrybutów języka C#. Uwzględniając, ten kod JSON powinien wyglądać znajomo. Istnieją jednak kilka elementów, które nie zostały pokryte w starszych ćwiczeniach. Na przykład, każda **powiązania** musi mieć jej **kierunek** zestawu. Jak może samodzielnie określać **"in"** oznacza, że parametr jest dane wejściowe, natomiast **"out"** wskazuje, że parametr jest zwracana wartość (za pośrednictwem **$return**) lub **się** parametrem metody. Należy także określić **plik_skryptu** (względna do tej lokalizacji końcowej) i **punktu wejścia** — metoda (publiczne ale statyczne) w zestawie. W ciągu następnych kilku krokach, należy dodać ścieżkę niestandardową funkcję przy użyciu tego modelu, więc skopiuj zawartość tego pliku do Schowka.

    ![Plik Function.JSON Otwórz w programie visual studio dla komputerów mac](media/azure-functions-lab-image25.png)

1. W **konsoli rozwiązania**, kliknij prawym przyciskiem myszy **AzureFunctionsLab** węzeł projektu i wybierz pozycję **Dodaj > Nowy Folder**. Nadaj nazwę nowego folderu **Moduł dodający**. Zgodnie z Konwencją domyślna nazwa tego folderu będą definiować ścieżki do interfejsu API, takich jak **interfejsu api/Moduł dodający**.

    ![Opcja nowy folder](media/azure-functions-lab-image26.png)

1. Kliknij prawym przyciskiem myszy **Moduł dodający** i wybierz polecenie **Dodaj > Nowy plik**.

    ![Nowa opcja pliku](media/azure-functions-lab-image27.png)

1. Wybierz **Web** kategorii i **pusty plik JSON** szablonu. Ustaw **nazwa** do **funkcja** i kliknij przycisk **New**.

    ![Opcja pliku pusty kod json](media/azure-functions-lab-image28.png)

1. Wklej zawartość innych **function.json** (z kroku 3) w celu zastąpienia domyślnej zawartości nowo utworzony plik.

1. Usuń następujące wiersze z na górze pliku json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na końcu pierwszego powiązania (po **"name": "wymagane"** wiersza), Dodaj poniższe właściwości. Nie zapomnij dołączyć przecinkami w poprzednim wierszu. Ta właściwość zastępuje domyślny katalog główny w taki sposób, że teraz wyodrębni **int** parametrów ze ścieżki i umieszczenie ich w parametrach metody, które są nazywane **x** i **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Dodaj inny powiązanie poniżej pierwszej. To powiązanie obsługuje wartość zwracaną przez funkcję. Nie zapomnij dołączyć przecinkami w poprzednim wierszu:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Również zaktualizować **punktu wejścia** właściwości w dolnej części pliku przy użyciu metody o nazwie **"Add2"**, takie jak pokazano poniżej. To jest, aby zilustrować, że ścieżka **interfejsu api/Moduł dodający...**  może mapować do odpowiedniej metody o dowolnej nazwie (**Add2** poniżej).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Ostateczna **function.json** plik powinien wyglądać podobnie jak następujący kod json:

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

1. Ostatnim krokiem jeden, trzeba wprowadzić to cała praca jest poinstruować Visual Studio dla komputerów Mac skopiować ten plik do tej samej ścieżki względnej w katalogu wyjściowym, za każdym razem, gdy zmienia się. Przy użyciu pliku wybrana, wybierz kartę właściwości z po prawej stronie paska, a także **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj Jeśli nowszy**:

    ![Opcje właściwości dla pliku json](media/azure-functions-lab-image30.png)

1. W **Add.cs**, Zastąp `Run` — metoda (w tym atrybucie) przy użyciu następującej metody, aby zrealizować Oczekiwano funkcji. Jest bardzo podobne do `Run`, z tą różnicą, że korzysta z żadnych atrybutów, a ma jawnych parametrów dla **x** i **y**.

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
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Zakończeniu kompilacji i uruchamia platformę, teraz poinformuje, jest druga trasa żądania, które mapuje do nowo dodanego metody:

    ![Adres URL dla protokołu Http, funkcje](media/azure-functions-lab-image31.png)

1. Wróć do okna przeglądarki i przejdź do **http://localhost:7071/api/Adder/3/5**.

1. Tym razem działania metody ponownie, ściągając parametrów ze ścieżki i produkcji to suma.

1. Wróć do **programu Visual Studio dla komputerów Mac** i zakończenie sesji debugowania.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Ćwiczenie 5: Praca z tabelami usługi Azure storage

Często usługi, które tworzysz może być znacznie bardziej złożone niż co możemy utworzone do tej pory wymagać znacznej ilości czasu i/lub infrastrukturę do wykonania. W tym przypadku może okazać się obowiązujące w celu umożliwienia akceptowania żądań, które oczekują w kolejce do przetwarzania, gdy zasoby będą dostępne, które usługi Azure Functions zapewnia obsługę. W innych przypadkach należy do centralnego przechowywania danych. Tabele magazynu platformy Azure pozwolą Ci to zrobić szybko.

1. Dodaj klasę poniżej, aby **Add.cs**. Powinien być kierowany wewnątrz przestrzeni nazw, ale poza programem istniejącej klasy.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. W ramach **Dodaj** klasy, Dodaj poniższy kod, aby wprowadzić inną funkcję. Należy pamiętać, że ta unikatowa do tej pory w tym, że nie obejmują, odpowiedź HTTP. Ostatni wiersz zwraca nowy **wymagają elementu** wypełniony niektóre informacje o kluczu, która ułatwi późniejszą do pobrania w późniejszym czasie na (**PartitionKey** i **RowKey**), a także jej Parametry i sum. Używa również kod w metodzie **TraceWriter** ułatwiają wiedzieć podczas wykonywania funkcji.

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
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Na karcie przeglądarki przejdź do **http://localhost:7071/api/Process/4/6**. Spowoduje to umieszczenie kolejną wiadomość do kolejki po pewnym czasie powinno spowodować kolejnego wiersza, które są dodawane do tabeli.

1. Wróć do **terminalu** , zwracając uwagę na żądanie przychodzące dla **4 + 6**.

    ![Żądanie dodania przedstawiający końcowych danych wyjściowych](media/azure-functions-lab-image32.png)

1. Wróć do przeglądarki, aby odświeżyć żądania do tego samego adresu URL. Tym razem zostanie wyświetlony komunikat o błędzie **procesu** metody. Jest to spowodowane kod próbuje dodać wiersz do tabeli usługi Azure Table Storage, za pomocą partycji i wiersza kombinacji klawiszy, który już istnieje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Zakończenie sesji debugowania.

1. Aby rozwiązać ten błąd, Dodaj następujący parametr do definicji metody bezpośrednio przed **TraceWriter** parametru. Tego parametru powoduje, że platformy usługi Azure Functions w celu podejmowane próby pobierania **wymagają elementu** z **wyniki** tabeli na **PartitionKey** używamy do przechowywania wyniki. Jednak niektóre prawdziwa Magia trafia do odtwarzania po można zauważyć, że **RowKey** dynamicznie generowanych zależy od innych **x** i **y** parametry dla tej samej Metoda. Jeśli ten wiersz już istnieje, następnie **wymagają elementu** będzie mieć je, gdy metoda zaczyna się od nie dodatkowej pracy wymagane przez projektanta. Jeśli wiersz nie istnieje, a następnie po prostu będziesz mieć wartości null. Tego rodzaju wydajności umożliwia deweloperom skoncentrowanie się na logice biznesowej ważna, a nie na infrastrukturze.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Dodaj poniższy kod do początku metody. Jeśli **wymagają elementu** nie jest null, a firma Microsoft już ma wyników dla Żądana operacja może zwrócić go bezpośrednio. W przeciwnym razie funkcja jest kontynuowane tak jak poprzednio. Chociaż może to nie być najlepszy sposób zwrócenia danych, przedstawia punkt, czy można organizować bardzo zaawansowane operacje w wielu warstwach skalowalne z bardzo niewielkiej ilości kodu.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Na karcie przeglądarki, Odśwież adres URL w **http://localhost:7071/api/Process/4/6**. Ponieważ istnieje wiersz tabeli dla tego rekordu, powinien zostać zwrócony natychmiast i bez błędów. Ponieważ nie ma żadnych danych wyjściowych HTTP, zostaną wyświetlone dane wyjściowe w terminalu.

    ![Końcowych danych wyjściowych przedstawiający wiersz tabeli już istnieje](media/azure-functions-lab-image33.png)

1. Aktualizacja adresu URL, aby odzwierciedlić kombinację nie testowano, takich jak **http://localhost:7071/api/Process/5/7**. Należy zauważyć komunikat w terminalu, co oznacza, że wiersz tabeli nie znaleziono (zgodnie z oczekiwaniami).

    ![Nowy proces przedstawiający końcowych danych wyjściowych](media/azure-functions-lab-image34.png)

1. Wróć do **programu Visual Studio dla komputerów Mac** i zakończenie sesji debugowania.

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

W tym środowisku laboratoryjnym już wiesz, jak zacząć tworzenie aplikacji usługi Azure Functions za pomocą programu Visual Studio dla komputerów Mac.
