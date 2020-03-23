---
title: Narzędzia i techniki debugowania
description: Napisz lepszy kod z mniejszą ilością błędów, używając programu Visual Studio do naprawianie wyjątków, naprawianie błędów i ulepszanie kodu
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302029"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniki debugowania i narzędzia ułatwiające pisanie lepszego kodu

Naprawianie błędów i błędów w kodzie może być czasochłonne — a czasami frustrujące — zadanie. Potrzeba czasu, aby dowiedzieć się, jak skutecznie debugować, ale zaawansowane IDE jak Visual Studio może znacznie ułatwić pracę. IDE może pomóc naprawić błędy i debugować kod szybciej, a nie tylko, ale może również pomóc napisać lepszy kod z mniejszą liczbą błędów. Naszym celem w tym artykule jest zapewnienie całościowego widoku procesu "naprawiania błędów", dzięki czemu będziesz wiedzieć, kiedy używać analizatora kodu, kiedy używać debugera, jak naprawić wyjątki i jak kodować intencje. Jeśli już wiesz, że musisz użyć debugera, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

W tym artykule mówimy o wykorzystaniu IDE, aby twoje sesje kodowania bardziej wydajne. Dotykamy kilku zadań, takich jak:

* Przygotuj kod do debugowania, wykorzystując analizator kodu IDE

* Jak naprawić wyjątki (błędy w czasie wykonywania)

* Jak zminimalizować błędy przez kodowanie intencji (przy użyciu potwierdzenia)

* Kiedy używać debugera

Aby zademonstrować te zadania, pokazujemy kilka najczęstszych typów błędów i błędów, które można napotkać podczas próby debugowania aplikacji. Chociaż przykładowy kod jest C#, informacje koncepcyjne są ogólnie stosowane do języka C++, Visual Basic, JavaScript i innych języków obsługiwanych przez program Visual Studio (z wyjątkiem przypadków, gdy zaznaczono inaczej). Zrzuty ekranu są w języku C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Tworzenie przykładowej aplikacji z pewnymi błędami i błędami w niej

Poniższy kod zawiera kilka błędów, które można naprawić przy użyciu środowiska IDE programu Visual Studio. Aplikacja w tym miejscu jest prosta aplikacja, która symuluje uzyskanie danych JSON z niektórych operacji, deserializacji danych do obiektu i aktualizowanie prostej listy z nowymi danymi.

Aby utworzyć aplikację:

1. Program Visual Studio musi być zainstalowany i **program .NET Core — program rozwoju na wielu platformach** lub zainstalowane obciążenie **programistyczne dla komputerów .NET,** w zależności od typu aplikacji, który chcesz utworzyć.

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, kliknij pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia instalator programu Visual Studio. Wybierz program **.NET Core dla deweloperów międzyplatformowych** lub obciążenia **programistycznego .NET dla komputerów stacjonarnych,** a następnie wybierz pozycję **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie początkowym wybierz pozycję **Utwórz nowy projekt**. Wpisz **konsolę** w polu wyszukiwania, a następnie wybierz **aplikację konsoli (.NET Core)** lub aplikację konsoli **(.NET Framework).** Wybierz pozycję **Dalej**. Wpisz nazwę projektu, taką jak **Console_Parse_JSON,** a następnie kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Aplikacja konsoli**, a następnie w środkowym okienku wybierz aplikację **konsoli (.NET Core)** lub **aplikację konsoli (.NET Framework).** Wpisz nazwę, taką jak **Console_Parse_JSON** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **aplikacji konsoli (.NET Core)** lub **aplikacji konsoli (net framework),** przejdź do **pozycji Narzędzia** > **Pobierz narzędzia i funkcje**, który otwiera Instalator programu Visual Studio. Wybierz opcję **programowy platformy .NET Core dla różnych platform** lub obciążenia **programistycznego .NET dla komputerów stacjonarnych,** a następnie wybierz pozycję **Modyfikuj**.

    Visual Studio tworzy projekt konsoli, który pojawia się w Eksploratorze rozwiązań w prawym okienku.

1. Zastąp domyślny kod w pliku *Program.cs* projektu poniższym przykładowym kodem.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Znajdź czerwone i zielone faliszki!

Przed podjęciem próby uruchomienia przykładowej aplikacji i uruchomienia debugera, sprawdź kod w edytorze kodu dla czerwonego i zielonego squiggles. Reprezentują one błędy i ostrzeżenia, które są identyfikowane przez analizator kodu IDE. Czerwone squiggles są błędy w czasie kompilacji, które należy naprawić, zanim będzie można uruchomić kod. Zielone faliszki są ostrzeżenia. Chociaż często można uruchomić aplikację bez naprawiania ostrzeżeń, mogą one być źródłem błędów i często oszczędzasz czas i problemy, badając je. Te ostrzeżenia i błędy są również wyświetlane w oknie **Lista błędów,** jeśli wolisz widok listy.

W przykładowej aplikacji zobaczysz kilka czerwonych faliczek, które musisz naprawić, i jeden zielony, który będziesz patrzeć. Oto pierwszy błąd.

![Błąd wyświetlany jako czerwony squiggle](../debugger/media/write-better-code-red-squiggle.png)

Aby naprawić ten błąd, przyjrzysz się innej funkcji IDE, reprezentowanej przez ikonę żarówki.

## <a name="check-the-light-bulb"></a>Sprawdź żarówkę!

Pierwszy czerwony squiggle reprezentuje błąd w czasie kompilacji. Najedź nad nim ```The name `Encoding` does not exist in the current context```kursorem i zobaczysz komunikat .

Należy zauważyć, że ten błąd pokazuje ikonę żarówki w lewym dolnym dolnym. Wraz z ikoną ![śrubokręta, ikona](../ide/media/screwdriver-icon.png)](../ide/media/light-bulb-icon.png) ![żarówki ikona żarówki reprezentuje szybkie akcje, które mogą pomóc naprawić lub refaktoryzuje kod wbudowany. Żarówka reprezentuje problemy, które *należy* rozwiązać. Śrubokręt jest przeznaczony do rozwiązywania problemów, które można rozwiązać. Użyj pierwszej sugerowanej poprawki, aby rozwiązać ten błąd, klikając **pozycję System.Text** po lewej stronie.

![Użyj żarówki, aby naprawić kod](../debugger/media/write-better-code-missing-include.png)

Po kliknięciu tego elementu visual `using System.Text` studio dodaje instrukcję w górnej części pliku *Program.cs,* a czerwony squiggle zniknie. (Jeśli nie masz pewności, co zrobi sugerowana poprawka, wybierz łącze **Zmiany podglądu** po prawej stronie przed zastosowaniem poprawki).

Poprzedni błąd jest typowy, który zwykle naprawić, `using` dodając nową instrukcję do kodu. Istnieje kilka typowych, podobnych błędów ```The type or namespace `Name` cannot be found.``` do tego, takich jak Te rodzaje błędów może wskazywać na brakujące odwołanie do zestawu (kliknij prawym przyciskiem myszy projekt, wybierz **polecenie Dodaj** > **odwołanie), błędnie**wpozwędną nazwę lub brakującą bibliotekę, którą należy dodać (dla języka C#, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet).**

## <a name="fix-the-remaining-errors-and-warnings"></a>Napraw pozostałe błędy i ostrzeżenia

Istnieje kilka więcej squiggles spojrzeć na w tym kodzie. W tym miejscu jest widoczny typowy błąd konwersji typu. Po umieszczeniu wskaźnika myszy nad faliskiem zobaczysz, że kod próbuje przekonwertować ciąg na int, który nie jest obsługiwany, chyba że dodasz jawny kod, aby dokonać konwersji.

![Błąd konwersji typu](../debugger/media/write-better-code-conversion-error.png)

Ponieważ analizator kodu nie można odgadnąć intencji, nie ma żarówek, które pomogą Ci tym razem. Aby naprawić ten błąd, musisz znać intencji kodu. W tym przykładzie nie jest zbyt `points` trudne, aby zobaczyć, że powinna być wartością liczbową (liczba całkowita), ponieważ próbujesz dodać `points` do `totalpoints`.

Aby naprawić ten błąd, `points` zmień `User` element członkowski klasy z tego:

```csharp
[DataMember]
internal string points;
```

wprowadź następujące zmiany:

```csharp
[DataMember]
internal int points;
```

Czerwone faliste linie w edytorze kodu odejdą.

Następnie umieść wskaźnik myszy na zielonym falista `points` w deklaracji elementu członkowskiego danych. Analizator kodu informuje, że zmienna nigdy nie jest przypisana wartość.

![Komunikat ostrzegawczy dla nieprzypisaną zmienną](../debugger/media/write-better-code-warning-message.png)

Zazwyczaj reprezentuje to problem, który należy rozwiązać. Jednak w przykładowej aplikacji są w rzeczywistości `points` przechowywania danych w zmiennej podczas procesu deserializacji, a następnie dodanie tej wartości do elementu członkowskiego `totalpoints` danych. W tym przykładzie znasz intencji kodu i można bezpiecznie zignorować ostrzeżenie. Jeśli jednak chcesz wyeliminować ostrzeżenie, możesz zastąpić następujący kod:

```csharp
item.totalpoints = users[i].points;
```

na kod:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zielony squiggle odchodzi.

## <a name="fix-an-exception"></a>Naprawianie wyjątku

Po naprawieniu wszystkich czerwonych falizw i rozwiązany - lub przynajmniej zbadane - wszystkie zielone squiggles, można przystąpić do uruchomienia debugera i uruchomić aplikację.

Naciśnij **klawisz F5** **(Debugowanie > rozpocznij debugowanie)** lub przycisk **Start Debugowania** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi Debugowania.

W tym momencie przykładowa `SerializationException` aplikacja zgłasza wyjątek (błąd środowiska uruchomieniowego). Oznacza to, że aplikacja dławi się danymi, które próbuje serializować. Ponieważ aplikacja została uruchomiona w trybie debugowania (debuger dołączony), Debuger's Exception Helper przeniesie Cię bezpośrednio do kodu, który zgłosił wyjątek i daje pomocny komunikat o błędzie.

![Występuje a SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Komunikat o błędzie informuje, `4o` że wartość nie może być analizowana jako liczba całkowita. Tak więc, w tym przykładzie, `4o` wiesz, `40`że dane są złe: powinny być . Jeśli jednak nie masz kontroli nad danymi w rzeczywistym scenariuszu (powiedzmy, że otrzymujesz go z usługi sieci web), co z tym robisz? Jak to naprawić?

Po naciśnięciu wyjątku musisz zadać (i odpowiedzieć) na kilka pytań:

* Czy ten wyjątek jest tylko błędem, który można naprawić? Lub:

* Czy ten wyjątek jest czymś, co użytkownicy mogą napotkać?

Jeśli jest to pierwszy, naprawić błąd. (W przykładowej aplikacji oznacza to naprawienie złych danych). Jeśli jest to ten ostatni, może być konieczne obsłużenie wyjątku w kodzie przy użyciu `try/catch` bloku (przyjrzymy się innym możliwym strategiom w następnej sekcji). W przykładowej aplikacji zastąp następujący kod:

```csharp
users = ser.ReadObject(ms) as User[];
```

z tym kodem:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Blok `try/catch` ma pewien koszt wydajności, więc będziesz chciał ich używać tylko wtedy, gdy naprawdę ich potrzebujesz, czyli gdzie (a) mogą wystąpić w wersji aplikacji i gdzie (b) dokumentacja metody wskazuje, że należy sprawdzić wyjątek (przy założeniu, że dokumentacja jest kompletna!). W wielu przypadkach można obsługiwać wyjątek odpowiednio i użytkownik nigdy nie będzie musiał wiedzieć o tym.

Oto kilka ważnych wskazówek dotyczących obsługi wyjątków:

* Należy unikać używania pustego bloku catch, takiego jak `catch (Exception) {}`, który nie podejmuje odpowiednich działań w celu udostępnienia lub obsługi błędu. Pusty lub niepoinformacyjny blok catch może ukryć wyjątki i może utrudnić debugowanie kodu zamiast łatwiejsze.

* Użyj `try/catch` bloku wokół określonej funkcji, która`ReadObject`zgłasza wyjątek ( , w przykładowej aplikacji). Jeśli używasz go wokół większego fragmentu kodu, kończy się ukrywanie lokalizacji błędu. Na przykład nie należy `try/catch` używać bloku wokół wywołania `ReadToObject`funkcji nadrzędnej, wyświetlane w tym miejscu, lub nie wiadomo dokładnie, gdzie wystąpił wyjątek.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* W przypadku nieznanych funkcji, które można uwzględnić w aplikacji, zwłaszcza tych, które wchodzą w interakcję z danymi zewnętrznymi (takich jak żądanie sieci web), sprawdź dokumentację, aby zobaczyć, jakie wyjątki funkcja może zgłosić. Może to być informacje krytyczne dla prawidłowej obsługi błędów i debugowania aplikacji.

W przypadku przykładowej `SerializationException` aplikacji `GetJsonData` napraw metodę, zmieniając `4o` na `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Wyjaśnij zamiar kodu za pomocą potwierdzenia

Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5**). Spowoduje to ponowne uruchomienie aplikacji w mniejszej liczbie kroków. W oknie konsoli są widoczne następujące dane wyjściowe.

![Wartość null w danych wyjściowych](../debugger/media/write-better-code-using-assert-null-output.png)

Widać w tym wyjściu coś, co nie jest w porządku. **nazwa i** **nazwisko** dla trzeciego rekordu są puste!

Jest to dobry moment, aby porozmawiać o pomocnej praktyce kodowania, często niedostatecznie stosowanej, czyli używania `assert` instrukcji w funkcjach. Dodając następujący kod, należy dołączyć sprawdzanie środowiska uruchomieniowego, aby upewnić się, że `firstname` nie `lastname` `null`są . Zastąp następujący `UpdateRecords` kod w metodzie:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

na kod:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Dodając `assert` instrukcje takie jak ten do funkcji podczas procesu tworzenia, można określić intencji kodu. W poprzednim przykładzie określamy następujące elementy:

* Prawidłowy ciąg jest wymagany dla imienia
* Prawidłowy ciąg jest wymagany dla nazwiska

Określając intencji w ten sposób, można wymusić wymagania. Jest to prosta i przydatna metoda, której można użyć do tworzenia błędów podczas tworzenia. (Instrukcje`assert` są również używane jako główny element w testach jednostkowych.)

Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5**).

> [!NOTE]
> Kod `assert` jest aktywny tylko w kompilacji debugowania.

Po `assert` ponownym uruchomieniu debuger wstrzymuje instrukcję, ponieważ wyrażenie `true` `users[i].firstname != null` ocenia zamiast `false` .

![Assert rozpoznaje fałsz](../debugger/media/write-better-code-using-assert.png)

Błąd `assert` informuje, że istnieje problem, który należy zbadać. `assert`może obejmować wiele scenariuszy, w których nie zawsze widzisz wyjątek. W tym przykładzie użytkownik nie zobaczy wyjątku, `null` a `firstname` wartość zostanie dodana, jak na liście rekordów. Może to spowodować problemy później (takie jak widać w danych wyjściowych konsoli) i może być trudniejsze do debugowania.

> [!NOTE]
> W scenariuszach, w których `null` można wywołać metodę na wartość, `NullReferenceException` wyniki. Zwykle chcesz uniknąć używania `try/catch` bloku dla wyjątku ogólnego, czyli wyjątku, który nie jest związany z określoną funkcją biblioteki. Każdy obiekt może `NullReferenceException`rzucić . Sprawdź dokumentację funkcji biblioteki, jeśli nie masz pewności.

Podczas procesu debugowania dobrze jest zachować `assert` określoną instrukcję, dopóki nie wiesz, że musisz zastąpić ją rzeczywistą poprawką kodu. Załóżmy, że zdecydujesz, że użytkownik może napotkać wyjątek w kompilacji wersji aplikacji. W takim przypadku należy refaktoryzuje kod, aby upewnić się, że aplikacja nie zgłasza wyjątek krytyczny lub spowodować inny błąd. Tak więc, aby naprawić ten kod, zastąp następujący kod:

```csharp
if (existingUser == false)
{
    User user = new User();
```

z tym kodem:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Korzystając z tego kodu, należy spełnić wymagania dotyczące kodu `firstname` i `lastname` upewnij `null` się, że rekord o wartości lub wartości nie jest dodawany do danych.

W tym przykładzie dodaliśmy dwie `assert` instrukcje wewnątrz pętli. Zazwyczaj podczas korzystania `assert`z programu najlepiej `assert` jest dodać instrukcje w punkcie wejścia (początek) funkcji lub metody. Aktualnie przeglądasz metodę `UpdateRecords` w przykładowej aplikacji. W tej metodzie wiesz, że masz kłopoty, `null`jeśli jeden z argumentów metody jest , więc sprawdź je zarówno z instrukcją `assert` w punkcie wejścia funkcji.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

W przypadku poprzednich instrukcji intencją jest załadowanie`db`istniejących danych (`users`) i pobranie nowych danych ( ) przed zaktualizowaniem czegokolwiek.

Można użyć `assert` z dowolnego rodzaju wyrażenie, `true` `false`które rozwiązuje lub . Na przykład można dodać takie `assert` stwierdzenie.

```csharp
Debug.Assert(users[0].points > 0);
```

Poprzedni kod jest przydatne, jeśli chcesz określić następujące intencji: nowa wartość punktu większa niż zero (0) jest wymagana do aktualizacji rekordu użytkownika.

## <a name="inspect-your-code-in-the-debugger"></a>Sprawdzanie kodu w debugerze

OK, teraz, gdy naprawiłeś wszystko, co jest krytyczne, co jest nie tak z przykładową aplikacją, możesz przejść do innych ważnych rzeczy!

Pokazaliśmy Ci debugera wyjątek Pomocnika, ale debuger jest znacznie bardziej zaawansowane narzędzie, które pozwala również zrobić inne rzeczy, takie jak krok po kroku przez kod i sprawdzić jego zmienne. Te bardziej zaawansowane funkcje są przydatne w wielu scenariuszach, szczególnie w następujących przypadkach:

* Próbujesz wyizolować błąd środowiska uruchomieniowego w kodzie, ale nie można tego zrobić przy użyciu metod i narzędzi wcześniej omówione.

* Chcesz sprawdzić poprawność kodu, czyli oglądać go podczas pracy, aby upewnić się, że zachowuje się w sposób oczekiwany i robi to, co chcesz.

    Jest pouczające, aby obejrzeć kod, gdy działa. Możesz dowiedzieć się więcej o kodzie w ten sposób i często można zidentyfikować błędy, zanim zamanifestują one żadnych oczywistych objawów.

Aby dowiedzieć się, jak korzystać z podstawowych funkcji debugera, zobacz [Debugowanie dla początkujących .](../debugger/debugging-absolute-beginners.md)

## <a name="fix-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Błędy innego rodzaju obejmują nieefektywny kod, który powoduje, że aplikacja działa wolno lub używać zbyt dużo pamięci. Ogólnie rzecz biorąc, optymalizacja wydajności jest coś zrobić w dalszej części tworzenia aplikacji. Jednak można uruchomić na problemy z wydajnością wcześnie (na przykład widać, że niektóre części aplikacji działa wolno) i może być konieczne przetestowanie aplikacji z narzędzi profilowania na początku. Aby uzyskać więcej informacji na temat narzędzi profilowania, takich jak narzędzie Użycie procesora i analizator pamięci, zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

W tym artykule dowiesz się, jak uniknąć i naprawić wiele typowych błędów w kodzie i kiedy używać debugera. Następnie dowiedz się więcej na temat używania debugera programu Visual Studio do rozwiązywania błędów.

> [!div class="nextstepaction"]
> [Debugowanie dla całkowicie początkujących](../debugger/debugging-absolute-beginners.md)
