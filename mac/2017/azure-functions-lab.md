---
title: 'Samouczek: Azure Functions'
description: Korzystanie z usługi Azure Functions w Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 43720947d36fec1ee64c81a48f7bc3eb7466d034
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983366"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Samouczek: wprowadzenie do Azure Functions

W tym laboratorium dowiesz się, jak rozpocząć tworzenie Azure Functions przy użyciu Visual Studio dla komputerów Mac. Ponadto integrujesz się z tabelami usługi Azure Storage, które reprezentują jeden z wielu rodzajów powiązań i wyzwalaczy dostępnych dla deweloperów Azure Functions.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie i debugowanie Azure Functions lokalnych
> * Integracja z zasobami sieci Web i usługi Azure Storage
> * Organizowanie przepływu pracy obejmującego wiele Azure Functions

## <a name="requirements"></a>Wymagania

- Visual Studio dla komputerów Mac 7,5 lub wyższy.
- Subskrypcja platformy Azure (dostępna bezpłatnie z [https://azure.com/free](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Ćwiczenie 1: Tworzenie projektu Azure Functions

1. Uruchom **Visual Studio dla komputerów Mac**.

2. Wybierz pozycję **plik > nowe rozwiązanie**.

3. W kategorii **ogólne > w chmurze** wybierz szablon **Azure Functions** . Zostanie użyta C# do utworzenia biblioteki klas platformy .NET, która będzie hostować Azure Functions. Kliknij przycisk **Dalej**.

    ![Wybór szablonu usługi Azure Functions](media/azure-functions-lab-image1.png)

4. W polu **Nazwa projektu** ustaw wartość **"AzureFunctionsLab"** , a następnie kliknij pozycję **Utwórz**.

    ![Nazywanie i tworzenie projektu funkcji platformy Azure](media/azure-functions-lab-image2.png)

5. Rozwiń węzły w **okienko rozwiązania**. Domyślny szablon projektu zawiera odwołania NuGet do różnych pakietów Azure WebJobs, a także pakiet Newtonsoft. JSON.

     Istnieją również trzy pliki:- **host. JSON** opisujące opcje konfiguracji globalnej dla hosta- **Local. Settings. JSON** na potrzeby konfigurowania ustawień usługi.
        - Szablon projektu tworzy również domyślny HttpTrigger. Na potrzeby tego laboratorium należy usunąć plik **HttpTrigger.cs** z projektu.

    Otwórz plik **Local. Settings. JSON**. Domyślnie mają dwa puste ustawienia parametrów połączenia.

    ![Konsola rozwiązań wyświetlająca plik Local. Settings. JSON](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Ćwiczenie 2. Tworzenie konta usługi Azure Storage

1. Zaloguj się do konta platformy Azure w [https://portal.azure.com](https://portal.azure.com).

1. W sekcji **Ulubione** znajdującej się po lewej stronie ekranu wybierz pozycję **konta magazynu**:

    ![Sekcja Ulubione Azure Portal wyświetlania elementu kont magazynu](media/azure-functions-lab-image4.png)

1. Wybierz pozycję **Dodaj** , aby utworzyć nowe konto magazynu:

    ![Przycisk umożliwiający dodanie nowego konta magazynu](media/azure-functions-lab-image5.png)

1. Wprowadź globalnie unikatową nazwę dla **nazwy** i użyj jej ponownie dla **grupy zasobów**. Wszystkie pozostałe elementy można zachować jako domyślne.

    ![Szczegóły nowego konta magazynu](media/azure-functions-lab-image6.png)

1. Kliknij przycisk **Utwórz**. Utworzenie konta magazynu może potrwać kilka minut. Po pomyślnym utworzeniu zostanie wyświetlone powiadomienie.

    ![pomyślne powiadomienie dotyczące wdrożenia](media/azure-functions-lab-image7.png)

1. Wybierz przycisk **Przejdź do zasobu** na stronie powiadomienia.

1. Wybierz kartę **klucze dostępu** .

    ![ustawienie klucza dostępu](media/azure-functions-lab-image8.png)

1. Skopiuj pierwsze **Parametry połączenia**. Ten ciąg służy do integrowania usługi Azure Storage z Azure Functions później.

    ![Informacje o kluczu 1](media/azure-functions-lab-image9.png)

1. Wróć do **Visual Studio dla komputerów Mac** i wklej pełne parametry połączenia w programie jako ustawienie **AzureWebJobsStorage** w pliku **Local. Settings. JSON**. Teraz można odwołać się do nazwy ustawienia w atrybutach dla funkcji, które wymagają dostępu do zasobów.

    ![plik ustawień lokalnych z wprowadzonym kluczem połączenia](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Przykład 3: Tworzenie i debugowanie funkcji platformy Azure

1. Teraz możesz zacząć dodawać kod. Podczas pracy z biblioteką klas .NET Azure Functions są dodawane jako metody statyczne. W **okienko rozwiązania**kliknij prawym przyciskiem myszy węzeł projektu **AzureFunctions** i wybierz polecenie **Dodaj > Dodaj funkcję**:

    ![Dodawanie opcji funkcji](media/azure-functions-lab-image11.png)

1. W oknie dialogowym Nowy Azure Functions wybierz ogólny szablon elementu webhook. Ustaw **nazwę** do **dodania** , a następnie kliknij przycisk **OK** , aby utworzyć funkcję:

    ![Nowe okno dialogowe usługi Azure Functions](media/azure-functions-lab-image12.png)

1. W górnej części nowego pliku Dodaj dyrektywy **using** poniżej:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Usuń istniejącą metodę `Run` i Dodaj metodę poniżej do klasy jako funkcji platformy Azure:

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

1. Przechodźmy przez fragment definicji metody.

    Pierwsze, co zobaczysz, jest atrybut **FunctionName** , który oznacza tę metodę jako funkcję platformy Azure. Ten atrybut określa publiczną nazwę funkcji. Nazwa atrybutu nie musi być zgodna z rzeczywistą nazwą metody.

    ![Nowa metoda run z wyróżnionym atrybutem FunctionName](media/azure-functions-lab-image13.png)

1. Następnie metoda jest oznaczona jako **publiczna metoda statyczna** , która jest wymagana. Zauważ również, że wartość zwracana jest liczbą **całkowitą.** O ile nie określono inaczej przy użyciu atrybutów metody, każda wartość zwracana przez inną niż void funkcja platformy Azure jest zwracana do klienta jako tekst. Domyślnie jest on zwracany jako **XML**, ale można go zmienić na **Format JSON**, który można później wykonać w laboratorium.

    ![Nowa metoda run z wyróżnioną inicjalizacją metody](media/azure-functions-lab-image14.png)

1. Pierwszy parametr jest oznaczony atrybutem **HttpTrigger** , który wskazuje, że ta metoda jest wywoływana przez żądanie HTTP. Ten atrybut określa również poziom autoryzacji metody, a także obsługiwane przez niego zlecenia (w tym przypadku tylko **"Get"** ). Opcjonalnie można również zdefiniować **trasę** , która zastępuje ścieżkę do metody i oferuje sposób automatycznego wyodrębniania zmiennych ze ścieżki. Ponieważ **trasa** ma wartość null, ścieżka do tej metody będzie domyślnie **/API/Add**.

    ![Nowa metoda run z wyróżnionym parametrem](media/azure-functions-lab-image15.png)

1. Ostatnim parametrem metody jest **TraceWriter** , który może służyć do rejestrowania komunikatów na potrzeby diagnostyki i błędów.

    ![Nowa metoda run z wyróżnioną TraceWriter](media/azure-functions-lab-image16.png)

1. Ustaw punkt przerwania w wierszu **powrotu** metody, klikając na marginesie wiersza:

    ![Ustawiony punkt przerwania w wierszu powrotu](media/azure-functions-lab-image17.png)

1. Kompiluj i uruchamiaj projekt w sesji debugowania, naciskając klawisz **F5** lub wybierając pozycję **Uruchom > rozpocząć debugowanie**. Możesz również kliknąć przycisk **Uruchom** . Wszystkie te opcje wykonują to samo zadanie. Pozostała część tego laboratorium odwołuje się do **F5**, ale można użyć najwygodniejszej metody.

    ![Kompilowanie i uruchamianie projektu](media/azure-functions-lab-image18.png)

1. Uruchomienie projektu spowoduje automatyczne otwarcie aplikacji terminalowej.

1. Projekt przechodzi przez proces wykrywania Azure Functions na podstawie atrybutów metod i Konwencji plików, które zostały omówione w dalszej części tego artykułu. W tym przypadku wykrywa pojedynczą funkcję platformy Azure i "generuje" 1 funkcję zadania.

    ![Dane wyjściowe funkcji platformy Azure w terminalu](media/azure-functions-lab-image19.png)

1. Na dole komunikatów uruchamiania Azure Functions Host drukuje adresy URL dowolnego interfejsu API wyzwalacza HTTP. Powinien być tylko jeden. Skopiuj ten adres URL i wklej go na nowej karcie przeglądarki.

    ![Adres URL interfejsu API funkcji platformy Azure](media/azure-functions-lab-image20.png)

1. Punkt przerwania powinien być wyzwalany od razu. Żądanie sieci Web zostało przekazane do funkcji i teraz może być debugowane. Wskaźnik myszy nad zmienną **x** , aby zobaczyć jej wartość.

    ![Wyzwolono punkt przerwania](media/azure-functions-lab-image21.png)

1. Usuń punkt przerwania za pomocą tej samej metody, która została użyta do jej wcześniejszego dodania (kliknij margines lub wybierz wiersz i naciśnij klawisz **F9**).

1. Naciśnij klawisz **F5** , aby kontynuować działanie.

1. W przeglądarce zostanie renderowany wynik XML metody. Zgodnie z oczekiwaniami operacja dodawania stałe generuje sumę wartości. Uwaga Jeśli zobaczysz tylko "3" w przeglądarce Safari, przejdź do **przeglądarki safari > preferences > Advanced** i zaznacz pole wyboru**Pokaż menu Programowanie na pasku menu**, a następnie załaduj ponownie stronę.

1. W **Visual Studio dla komputerów Mac**kliknij przycisk **Zatrzymaj** , aby zakończyć sesję debugowania. Aby upewnić się, że nowe zmiany są pobierane, nie zapomnij uruchomić ponownie (zatrzymać, a następnie uruchomić) sesji debugowania.

    ![Opcja zatrzymania debugowania](media/azure-functions-lab-image22.png)

1. W metodzie **Run** Zastąp definicje **x** i **y** poniższym kodem. Ten kod wyodrębnia wartości z ciągu zapytania adresu URL, aby operacja dodawania mogła być wykonywana dynamicznie na podstawie podanych parametrów.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Uruchom aplikację.

1. Wróć do okna przeglądarki i dołącz ciąg `/?x=2&y=3` do adresu URL. Cały adres URL powinien być teraz `http://localhost:7071/api/Add?x=2&y=3`. Przejdź do nowego adresu URL.

1. Tym razem wynik powinien odzwierciedlać nowe parametry. Możesz uruchamiać projekt z różnymi wartościami. Należy zauważyć, że nie ma żadnego sprawdzenia błędów, więc nieprawidłowe lub brakujące parametry spowodują zgłoszenie błędu.

1. Zatrzymaj sesję debugowania.

## <a name="exercise-4-working-with-functionjson"></a>Ćwiczenie 4: Praca z funkcją Function. JSON

1. W poprzednim ćwiczeniu był on wymieniony Visual Studio dla komputerów Mac "Wygenerowano" funkcję zadania dla funkcji platformy Azure zdefiniowanej w bibliotece. Wynika to z faktu, że Azure Functions nie używa atrybutów metody w czasie wykonywania, ale zamiast tego używa konwencji systemu plików czasu kompilacji do skonfigurowania miejsca i sposobu, w jaki Azure Functions są udostępniane. W **okienko rozwiązania**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Odsłoń w programie Finder**.

     ![Opcja Odsłoń w menu wyszukiwania](media/azure-functions-lab-image23.png)

1. Przejdź w dół systemu plików, dopóki nie zostanie osiągnięty plik **bin/debug/Standard 2.0**. Powinien istnieć folder o nazwie **Add**. Ten folder został utworzony w celu odnoszący się do atrybutu nazwy C# funkcji w kodzie. Rozwiń folder Dodaj, aby wyświetlić plik Single **Function. JSON** . Ten plik jest używany przez środowisko uruchomieniowe do hostowania funkcji platformy Azure i zarządzania nią. W przypadku innych modeli języków bez obsługi czasu kompilacji (takich jak C# skrypt lub JavaScript) te foldery muszą być tworzone ręcznie i konserwowane. Dla C# deweloperów są one automatycznie generowane z metadanych atrybutów podczas kompilacji. Kliknij prawym przyciskiem myszy plik **Function. JSON** i wybierz polecenie, aby otworzyć go w programie Visual Studio.

    ![Function. JSON w katalogu plików](media/azure-functions-lab-image24.png)

1. Uwzględniając poprzednie kroki tego samouczka, należy uzyskać podstawową wiedzę na temat C# atrybutów. Biorąc pod uwagę, ten kod JSON powinien wyglądać znajomo. Istnieje jednak kilka elementów, które nie zostały omówione we wcześniejszych ćwiczeniach. Na przykład każde **powiązanie** musi mieć ustawiony **kierunek** . Jak można wywnioskować, **"w"** oznacza, że parametr jest wejściowy, natomiast **"out"** wskazuje, że parametr jest wartością zwracaną (za pośrednictwem **$Return**) lub parametrem **out** do metody. Należy również określić **scriptFile** (względem tej lokalizacji końcowej) i metodę **EntryPoint** (publiczną i statyczną) w ramach zestawu. W następnych kilku krokach dodasz niestandardową ścieżkę funkcji przy użyciu tego modelu, więc Skopiuj zawartość tego pliku do Schowka.

    ![plik Function. JSON jest otwierany w programie Visual Studio dla komputerów Mac](media/azure-functions-lab-image25.png)

1. W **okienko rozwiązania**kliknij prawym przyciskiem myszy węzeł projektu **AzureFunctionsLab** i wybierz polecenie **Dodaj > nowy folder**. Nazwij **Nowy folder.** Domyślnie nazwa tego folderu definiuje ścieżkę do interfejsu API, na przykład **API/** dodające.

    ![Opcja nowy folder](media/azure-functions-lab-image26.png)

1. Kliknij prawym przyciskiem myszy folder **dodawania** i wybierz polecenie **Dodaj > nowy plik**.

    ![Opcja nowego pliku](media/azure-functions-lab-image27.png)

1. Wybierz kategorię **sieci Web** i szablon **pustego pliku JSON** . Ustaw **nazwę** na **działanie** i kliknij pozycję **Nowy**.

    ![Pusta opcja pliku JSON](media/azure-functions-lab-image28.png)

1. Wklej zawartość pliku other **Function. JSON** (z kroku 3) w celu zamienienia domyślnej zawartości nowo utworzonego elementu.

1. Usuń następujące wiersze z góry pliku JSON:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na końcu pierwszego powiązania (po wierszu **"nazwa": "REQ** ") Dodaj poniższe właściwości. Nie zapomnij umieścić przecinki w poprzednim wierszu. Ta właściwość przesłania domyślny katalog główny, w taki sposób, że będzie teraz wyodrębniał parametry **int** ze ścieżki i umieścić je w parametrach metod o nazwach **x** i **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Dodaj kolejne powiązanie poniżej pierwszego. To powiązanie obsługuje zwracaną wartość funkcji. Nie zapomnij umieścić przecinka w poprzednim wierszu:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Zaktualizuj również właściwość **EntryPoint** w dolnej części pliku, aby użyć metody o nazwie **"ADD2"** , takiej jak pokazano poniżej. Ma to na celu zilustrowanie, że ścieżka **API/** obiekt dodający może być mapowany do odpowiedniej metody z dowolną nazwą (**ADD2** tutaj).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Końcowy plik **Function. JSON** powinien wyglądać podobnie do następującego kodu JSON:

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

1. Pierwszym krokiem wymaganym do przeprowadzenia tej operacji jest poinstruować Visual Studio dla komputerów Mac, aby skopiować ten plik do tej samej ścieżki względnej w katalogu wyjściowym za każdym razem, gdy zmieni się. Po wybraniu pliku wybierz kartę właściwości na pasku po prawej stronie, a w polu **Kopiuj do katalogu wyjściowego** wybierz opcję **Kopiuj, jeśli nowszy**:

    ![Opcje właściwości dla pliku JSON](media/azure-functions-lab-image30.png)

1. W **Add.cs**Zastąp metodę `Run` (łącznie z atrybutem) następującą metodą, aby spełnić oczekiwaną funkcję. Jest to bardzo podobne do `Run`, z tą różnicą, że nie używa żadnych atrybutów i ma jawne parametry dla **x** i **y**.

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

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

1. Gdy kompilacja zakończy się, a platforma zacznie się, będzie teraz wskazywać, że dla żądań, które są mapowane na nowo dodaną metodę, jest dostępna druga trasa:

    ![Adres URL funkcji http](media/azure-functions-lab-image31.png)

1. Zwróć okno przeglądarki i przejdź do **http://localhost:7071/api/Adder/3/5** .

1. Tym razem ta metoda działa ponownie, pobierając parametry ze ścieżki i generując sumę.

1. Wróć do **Visual Studio dla komputerów Mac** i Zakończ sesję debugowania.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Ćwiczenie 5: Praca z tabelami usługi Azure Storage

Często tworzona usługa może być dużo bardziej złożona, niż to, co zostało już zrobione i wymaga znacznej ilości czasu i/lub infrastruktury do wykonania. W takim przypadku może wystąpić potrzeba zaakceptowania żądań, które znajdują się w kolejce do przetworzenia, gdy zasoby staną się dostępne, co Azure Functions zapewnia pomoc techniczną dla programu. W innych przypadkach można przechowywać dane centralnie. Tabele usługi Azure Storage umożliwiają szybkie wykonywanie tych czynności.

1. Dodaj klasę poniżej do **Add.cs**. Powinien on się znaleźć w przestrzeni nazw, ale poza istniejącą klasą.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. W obszarze **Dodaj** Dodaj poniższy kod, aby wprowadzić inną funkcję. Należy zauważyć, że ta grupa jest unikatowa do momentu, w którym nie obejmuje odpowiedzi HTTP. Wiersz końcowy zwraca nowe **TableRow** wypełnione informacjami o kluczowym czasie, które ułatwią jego pobranie w dalszej części (**PartitionKey** i **RowKey**), a także jego parametry i sum. Kod w metodzie korzysta również z **TraceWriter** , aby łatwiej było wiedzieć, kiedy działa funkcja.

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

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

1. Na karcie Przeglądarka przejdź do **http://localhost:7071/api/Process/4/6** . Spowoduje to umieszczenie kolejnego komunikatu w kolejce, co powinno spowodować dodanie kolejnego wiersza do tabeli.

1. Wróć do **terminalu** i obejrzyj żądanie przychodzące dla **4 + 6**.

    ![Dane wyjściowe terminalu pokazujące żądanie dodania](media/azure-functions-lab-image32.png)

1. Wróć do przeglądarki, aby odświeżyć żądanie pod tym samym adresem URL. Tym razem zobaczysz błąd po metodzie **procesu** . Jest to spowodowane tym, że kod próbuje dodać wiersz do tabeli Table Storage platformy Azure przy użyciu kombinacji klucza i partycji, która już istnieje.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Zakończ sesję debugowania.

1. Aby wyeliminować błąd, Dodaj następujący parametr do definicji metody bezpośrednio przed parametrem **TraceWriter** . Ten parametr instruuje Azure Functions platformę, aby próbować pobrać **TableRow** z tabeli **wyników** w **PartitionKey** używanym do przechowywania wyników. Jednak niektóre z rzeczywistych magicznych Magic są odtwarzane, gdy zauważysz, że **RowKey** jest generowana dynamicznie na podstawie innych parametrów **x** i **y** dla tej samej metody. Jeśli ten wiersz już istnieje, **TableRow** będzie go używać, gdy metoda zacznie obowiązywać bez dodatkowej pracy wymaganej przez dewelopera. Jeśli wiersz nie istnieje, wówczas będzie miał po prostu wartość null. To sortowanie wydajności pozwala deweloperom skupić się na ważnych logice biznesowej, a nie na infrastrukturze.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Dodaj poniższy kod do początku metody. Jeśli **TableRow** nie ma wartości null, mamy już wyniki dla żądania operacji i można ją od razu zwrócić. W przeciwnym razie funkcja będzie kontynuowała działanie tak jak wcześniej. Chociaż może to nie być najbardziej niezawodny sposób zwrócenia danych, ilustruje to punkt, w którym można organizować Zaawansowane operacje niezwykle w wielu warstwach skalowalnych przy użyciu bardzo małego kodu.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

1. Na karcie Przeglądarka Odśwież adres URL w **http://localhost:7071/api/Process/4/6** . Ponieważ wiersz tabeli dla tego rekordu istnieje, powinien zostać zwrócony natychmiast i bez błędu. Ponieważ nie ma danych wyjściowych protokołu HTTP, można zobaczyć dane wyjściowe w terminalu.

    ![Dane wyjściowe terminalu pokazujące wiersz tabeli już istnieje](media/azure-functions-lab-image33.png)

1. Zaktualizuj adres URL, aby odzwierciedlić kombinację, która nie została jeszcze przetestowana, np. **http://localhost:7071/api/Process/5/7** . Zanotuj komunikat w terminalu, który wskazuje, że nie można odnaleźć wiersza tabeli (zgodnie z oczekiwaniami).

    ![Dane wyjściowe terminalu pokazujące nowy proces](media/azure-functions-lab-image34.png)

1. Wróć do **Visual Studio dla komputerów Mac** i Zakończ sesję debugowania.

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

W tym laboratorium dowiesz się, jak rozpocząć tworzenie Azure Functions z Visual Studio dla komputerów Mac.
