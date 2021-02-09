---
title: Narzędzia i techniki debugowania
description: Pisanie lepszego kodu z mniejszymi usterkami przy użyciu programu Visual Studio do rozwiązywania wyjątków, naprawiania błędów i ulepszania kodu
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c69fe13821f595a137c07d545a4ccfb10fc89b34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904954"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniki i narzędzia debugowania ułatwiające pisanie lepszego kodu

Naprawianie usterek i błędów w kodzie może być czasochłonne i czasami frustrujące — zadanie. Jest to czasochłonne, aby dowiedzieć się, jak skutecznie debugować, ale zaawansowane środowisko IDE, takie jak Visual Studio, może ułatwić wykonywanie zadań. Środowisko IDE może pomóc w rozwiązaniu błędów i szybszej debugowania kodu, a nie tylko, ale może też pomóc napisać lepszy kod z mniejszą liczbą błędów. Naszym celem tego artykułu jest udostępnienie całościowego widoku procesu "Usterka-naprawianie", dzięki czemu wiadomo, kiedy należy używać analizatora kodu, kiedy należy używać debugera, jak naprawić wyjątki i jak kod zamiaru. Jeśli już wiesz, że musisz użyć debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

W tym artykule omówiono sposób wykorzystania środowiska IDE, aby zwiększyć produktywność sesji kodowania. Pracujemy nad kilkoma zadaniami, takimi jak:

* Przygotuj kod do debugowania, wykorzystując analizator kodu IDE

* Jak naprawić wyjątki (błędy czasu wykonywania)

* Jak zminimalizować usterki przez kodowanie dla zamiaru (przy użyciu potwierdzenia)

* Kiedy używać debugera

Aby zademonstrować te zadania, pokazujemy kilka typowych typów błędów i usterek, które można napotkać podczas próby debugowania aplikacji. Mimo że przykładowy kod to C#, informacje o pojęciach są ogólnie stosowane do języka C++, Visual Basic, JavaScript i innych języków obsługiwanych przez program Visual Studio (chyba że zaznaczono inaczej). Zrzuty ekranu znajdują się w języku C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Tworzenie przykładowej aplikacji z niektórymi usterkami i błędami

Poniższy kod zawiera błędy, które można naprawić za pomocą programu Visual Studio IDE. Jest to prosta aplikacja, która symuluje pobieranie danych JSON z niektórych operacji, deserializacji danych do obiektu i aktualizowanie prostej listy przy użyciu nowych danych.

Aby utworzyć aplikację:

1. W zależności od typu aplikacji, który ma zostać utworzony, musi być zainstalowany program Visual Studio i **Programowanie na platformie .NET Core** lub środowisko **programistyczne programu .NET Desktop** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, kliknij przycisk **Narzędzia**  >  **Pobierz narzędzia i funkcje**. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie programu **.NET Core dla wielu platform** lub programowanie **aplikacji klasycznych platformy .NET** , a następnie wybierz **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**. Wpisz w polu wyszukiwania **konsolę** , a następnie wybierz pozycję **Aplikacja konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)**. Wybierz pozycję **Next** (Dalej). Wpisz nazwę projektu, taką jak **Console_Parse_JSON** , i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Aplikacja konsolowa**, a następnie w środkowym okienku wybierz pozycję **Aplikacja konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)**. Wpisz nazwę, taką jak **Console_Parse_JSON** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **aplikacja konsoli (.NET Core)** lub **aplikacja konsoli (.NET Framework)** , przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz opcję **Programowanie dla wielu platform w środowisku .NET Core** lub **środowisko programistyczne programu .NET Desktop** , a następnie wybierz polecenie **Modyfikuj**.

    Program Visual Studio tworzy projekt konsoli, który pojawia się w Eksplorator rozwiązań w okienku po prawej stronie.

1. Zastąp domyślny kod w pliku *program.cs* projektu następującym przykładowym kodem.

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

## <a name="find-the-red-and-green-squiggles"></a>Znajdź czerwoną i zieloną zygzaki!

Przed podjęciem próby uruchomienia aplikacji przykładowej i uruchomienia debugera Sprawdź kod w edytorze kodu dla czerwonych i zielonych zygzaków. Reprezentują one błędy i ostrzeżenia, które są identyfikowane przez analizator kodu IDE. Czerwona zygzakowata są błędy czasu kompilacji, które należy naprawić przed uruchomieniem kodu. Zielonki są ostrzeżeniami. Mimo że aplikacja jest często uruchamiana bez rozwiązywania ostrzeżeń, może być źródłem błędów i często zaoszczędzić czas i problemy, badając je. Te ostrzeżenia i błędy są również wyświetlane w oknie **Lista błędów** , jeśli wolisz wyświetlić widok listy.

W przykładowej aplikacji zobaczysz kilka czerwonych zygzaków, które należy naprawić, i jeden zielony, który będzie wyglądał. Oto pierwszy błąd.

![Błąd pokazywany jako czerwona zygzakowata](../debugger/media/write-better-code-red-squiggle.png)

Aby naprawić ten błąd, należy zapoznać się z inną funkcją środowiska IDE, reprezentowanej przez ikonę żarówki.

## <a name="check-the-light-bulb"></a>Sprawdź żarówkę.

Pierwsza czerwona zygzakowata reprezentuje błąd czasu kompilacji. Umieść kursor nad nim i zobaczysz komunikat ```The name `Encoding` does not exist in the current context``` .

Zauważ, że ten błąd pokazuje ikonę żarówki w lewym dolnym rogu. Wraz z ikoną śrubokręter ikona żarówki ikona świecącej ikony żarówki ![ ](../ide/media/screwdriver-icon.png) ![ ](../ide/media/light-bulb-icon.png) reprezentuje szybkie akcje, które mogą pomóc w rozwiązaniu lub refaktoryzacji kodu w tekście. Żarówka reprezentuje problemy, które *należy* naprawić. Śrubokręt dotyczy problemów, które mogą zostać naprawione. Użyj pierwszej sugerowanej poprawki, aby rozwiązać ten problem, klikając pozycję **System. Text** po lewej stronie.

![Aby naprawić kod, użyj żarówki](../debugger/media/write-better-code-missing-include.png)

Po kliknięciu tego elementu program Visual Studio dodaje `using System.Text` instrukcję w górnej części pliku *program.cs* , a czerwona zygzakowata znika. (Jeśli nie masz pewności, jaka będzie Sugerowana poprawka, wybierz link **Podgląd zmian** po prawej stronie przed zastosowaniem poprawki).

Poprzedni błąd jest typowym, który jest zwykle naprawiany przez dodanie nowej `using` instrukcji do kodu. Istnieje kilka typowych, podobnych błędów, takich jak ```The type or namespace `Name` cannot be found.``` te rodzaje błędów mogą wskazywać brak odwołania do zestawu (kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Dodaj**  >  **odwołanie**), nazwę błędnej pisowni lub brakującą bibliotekę, którą trzeba dodać (dla języka C#, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Usuń pozostałe błędy i ostrzeżenia

Istnieje kilka nieco więcej informacji na temat tego kodu. Tutaj zobaczysz typowy błąd konwersji typu. Po umieszczeniu wskaźnika myszy na zygzaku, zobaczysz, że kod próbuje skonwertować ciąg na int, co nie jest obsługiwane, chyba że dodasz jawny kod w celu wykonania konwersji.

![Błąd konwersji typu](../debugger/media/write-better-code-conversion-error.png)

Ponieważ analizator kodu nie może odgadnąć zamiaru, nie ma lamp jasnych, aby pomóc Ci w tym czasie. Aby naprawić ten błąd, musisz znać zamiar kodu. W tym przykładzie nie jest zbyt trudne, aby zobaczyć, że `points` powinna być wartością liczbową (Integer), ponieważ próbujesz dodać `points` do `totalpoints` .

Aby naprawić ten błąd, Zmień `points` element członkowski `User` klasy z:

```csharp
[DataMember]
internal string points;
```

wprowadź następujące zmiany:

```csharp
[DataMember]
internal int points;
```

Czerwone linie falistej w edytorze kodu.

Następnie umieść wskaźnik myszy na zielonym zygzaku w deklaracji `points` elementu członkowskiego danych. Analizator kodu informuje, że zmienna nie ma nigdy przypisanej wartości.

![Komunikat ostrzegawczy dla nieprzypisanej zmiennej](../debugger/media/write-better-code-warning-message.png)

Zazwyczaj oznacza to problem, który należy naprawić. Jednak w przykładowej aplikacji, w której znajdują się dane w `points` zmiennej, podczas procesu deserializacji, a następnie dodając tę wartość do `totalpoints` elementu członkowskiego danych. W tym przykładzie wiadomo, że zamierzenia kodu i można bezpiecznie zignorować ostrzeżenie. Jeśli jednak chcesz wyeliminować ostrzeżenie, możesz zastąpić następujący kod:

```csharp
item.totalpoints = users[i].points;
```

na kod:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zostanie wysunięty zielony zygzak.

## <a name="fix-an-exception"></a>Naprawianie wyjątku

Po naprawieniu wszystkich czerwonych zygzaków i rozwiązanych — lub co najmniej zbadane — wszystkie zielone zygzaki są gotowe do uruchomienia debugera i uruchomienia aplikacji.

Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

W tym momencie Przykładowa aplikacja zgłasza `SerializationException` wyjątek (błąd czasu wykonywania). Oznacza to, że aplikacja jest podlewka na danych, które próbuje serializować. Ponieważ uruchomiono aplikację w trybie debugowania (dołączony debuger), pomocnik wyjątków debugera przenosi Cię bezpośrednio do kodu, który zgłosił wyjątek, i daje przydatny komunikat o błędzie.

![Wystąpił SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Komunikat o błędzie informuje o tym, że `4o` nie można przeanalizować wartości jako liczby całkowitej. Dlatego w tym przykładzie wiadomo, że dane są nieprawidłowe: `4o` powinny być `40` . Jeśli jednak nie masz kontroli nad danymi w rzeczywistym scenariuszu (Załóżmy, że otrzymujesz ją z usługi sieci Web), co chcesz zrobić? Jak rozwiązać ten problem?

Po osiągnięciu wyjątku należy zadać pytanie (i odpowiedzieć) na kilka pytań:

* Czy ten wyjątek jest tylko usterką, którą można naprawić? Lub:

* Czy ten wyjątek występuje, gdy użytkownicy mogą napotkać problemy?

Jeśli jest to pierwsze, napraw usterkę. (W przykładowej aplikacji oznacza to poprawienie nieprawidłowych danych). Jeśli jest to ostatnie, może być konieczne obsłużenie wyjątku w kodzie przy użyciu `try/catch` bloku (patrzmy inne możliwe strategie w następnej sekcji). W przykładowej aplikacji Zastąp następujący kod:

```csharp
users = ser.ReadObject(ms) as User[];
```

następującym:

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

`try/catch`Blok ma koszt wydajności, więc będzie można używać go tylko wtedy, gdy ich naprawdę potrzebujesz, czyli gdzie (a) mogą wystąpić w wydanej wersji aplikacji i gdzie (b) Dokumentacja metody wskazuje, że należy sprawdzić wyjątek (przy założeniu, że dokumentacja jest kompletna). W wielu przypadkach można odpowiednio obsłużyć wyjątek, a użytkownik nigdy nie będzie musiał znać go.

Poniżej przedstawiono kilka ważnych porad dotyczących obsługi wyjątków:

* Unikaj używania pustego bloku catch, takiego jak `catch (Exception) {}` , który nie podejmuje odpowiedniej akcji, aby uwidocznić lub obsłużyć błąd. Pusty lub nieinformacyjny blok catch może ukryć wyjątki i może utrudnić Debugowanie kodu, a nie łatwiejszy.

* Użyj `try/catch` bloku otaczającej konkretną funkcję, która zgłasza wyjątek ( `ReadObject` w przykładowej aplikacji). Jeśli używasz tego elementu na większym fragmencie kodu, możesz zakończyć ukrywanie lokalizacji błędu. Na przykład nie należy używać `try/catch` bloku wokół wywołania funkcji nadrzędnej `ReadToObject` , pokazanej tutaj lub nie wiadomo, gdzie wystąpił wyjątek.

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

* W przypadku nieznanych funkcji, które są dołączane do aplikacji, szczególnie tych, które współdziałają z danymi zewnętrznymi (takimi jak żądanie sieci Web), zapoznaj się z dokumentacją, aby zobaczyć, jakie wyjątki może zgłosić funkcja. Mogą to być krytyczne informacje dotyczące prawidłowej obsługi błędów i debugowania aplikacji.

W przypadku przykładowej aplikacji napraw `SerializationException` `GetJsonData` metodę, zmieniając polecenie `4o` na `40` .

## <a name="clarify-your-code-intent-by-using-assert"></a>Wyjaśnij zamiar kodu przy użyciu metody Assert

Kliknij przycisk **Uruchom** ponownie ![Uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl**  +  **SHIFT**  +  **F5**). Spowoduje to ponowne uruchomienie aplikacji w mniejszej liczbie kroków. W oknie konsoli są widoczne następujące dane wyjściowe.

![Wartość zerowa w danych wyjściowych](../debugger/media/write-better-code-using-assert-null-output.png)

Zobaczysz coś w tych danych wyjściowych, które nie są całkiem odpowiednie. **Nazwa** i **nazwisko** dla trzeciego rekordu są puste!

Jest to dobry moment, aby poznać przydatną technikę kodowania, często nieużywaną, która polega na użyciu `assert` instrukcji w funkcjach. Dodając następujący kod, należy dołączyć sprawdzanie środowiska uruchomieniowego, aby upewnić się, że `firstname` i `lastname` nie są `null` . Zastąp następujący kod w `UpdateRecords` metodzie:

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

Dodając `assert` instrukcje, takie jak to, do funkcji w trakcie procesu tworzenia, możesz pomóc określić intencję kodu. W poprzednim przykładzie określono następujące elementy:

* Dla pierwszej nazwy wymagany jest prawidłowy ciąg
* Dla ostatniej nazwy wymagany jest prawidłowy ciąg

Określając zamiar w ten sposób, wymuszasz Twoje wymagania. Jest to prosta i przydatna Metoda, której można użyć do wypróbowania błędów podczas opracowywania. ( `assert` instrukcje są również używane jako element główny w testach jednostkowych).

Kliknij przycisk **Uruchom** ponownie ![Uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl**  +  **SHIFT**  +  **F5**).

> [!NOTE]
> `assert`Kod jest aktywny tylko w kompilacji debugowania.

Po ponownym uruchomieniu debuger zatrzymuje się w `assert` instrukcji, ponieważ wyrażenie `users[i].firstname != null` daje `false` zamiast `true` .

![Potwierdzenie jest rozpoznawane jako FAŁSZ](../debugger/media/write-better-code-using-assert.png)

`assert`Błąd informuje o wystąpieniu problemu, który należy zbadać. `assert` może obejmować wiele scenariuszy, w których niekoniecznie widzisz wyjątek. W tym przykładzie użytkownik nie zobaczy wyjątku, a `null` wartość zostanie dodana jako `firstname` na liście rekordów. Może to powodować problemy później (na przykład w danych wyjściowych w konsoli) i może być trudniejsze do debugowania.

> [!NOTE]
> W scenariuszach, w których wywoływana jest metoda dla `null` wartości, `NullReferenceException` wyniki. Zwykle chcesz uniknąć używania `try/catch` bloku dla ogólnego wyjątku, czyli wyjątku, który nie jest powiązany z określoną funkcją biblioteki. Każdy obiekt może zgłosić `NullReferenceException` . Jeśli nie masz pewności, zapoznaj się z dokumentacją funkcji biblioteki.

Podczas procesu debugowania warto zachować określoną `assert` instrukcję do momentu, w którym należy zamienić ją na rzeczywistą poprawkę kodu. Załóżmy, że użytkownik zdecyduje, że może napotkać wyjątek w kompilacji wydania aplikacji. W takim przypadku należy ponownie wykonać kod, aby upewnić się, że aplikacja nie zgłasza wyjątku krytycznego lub spowoduje powstanie innego błędu. Aby naprawić ten kod, Zastąp następujący kod:

```csharp
if (existingUser == false)
{
    User user = new User();
```

następującym:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Korzystając z tego kodu, spełniasz wymagania dotyczące kodu i upewnij się, że rekord o `firstname` wartości lub `lastname` `null` nie został dodany do danych.

W tym przykładzie dodaliśmy dwie `assert` instrukcje wewnątrz pętli. Zwykle, gdy `assert` jest używany, najlepiej dodać `assert` instrukcje w punkcie wejścia (początek) funkcji lub metody. Przeglądasz teraz `UpdateRecords` metodę w przykładowej aplikacji. W tej metodzie wiadomo, że masz problemy, jeśli jeden z argumentów metody jest `null` , więc sprawdź je w `assert` instrukcji w punkcie wejścia funkcji.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

W przypadku powyższych instrukcji zamiarem jest załadowanie istniejących danych ( `db` ) i pobranie nowych danych ( `users` ) przed aktualizacją.

Można użyć `assert` z dowolnym rodzajem wyrażenia, które jest rozpoznawane jako `true` lub `false` . Można na przykład dodać do `assert` niej instrukcję.

```csharp
Debug.Assert(users[0].points > 0);
```

Poprzedni kod jest przydatny, jeśli chcesz określić następujący cel: w celu zaktualizowania rekordu użytkownika wymagana jest nowa wartość punktu większa od zera (0).

## <a name="inspect-your-code-in-the-debugger"></a>Sprawdzanie kodu w debugerze

Teraz, po usunięciu wszystkiego krytycznego dla aplikacji przykładowej, możesz przejść do innych ważnych rzeczy.

Wykryliśmy pomocnika wyjątków debugera, ale debuger jest znacznie bardziej zaawansowanym narzędziem, które umożliwia również wykonywanie innych czynności, takich jak krok przez kod i sprawdzanie jego zmiennych. Te bardziej zaawansowane możliwości są przydatne w wielu scenariuszach, w szczególności następujących:

* Podjęto próbę odizolowania usterki środowiska uruchomieniowego w kodzie, ale nie można tego zrobić za pomocą metod i narzędzi omówionych wcześniej.

* Chcesz sprawdzić poprawność kodu, czyli obejrzeć go w trakcie działania, aby upewnić się, że działa w oczekiwany sposób, i wykonaj to, aby to zrobić.

    W trakcie jego działania warto obejrzeć swój kod. Możesz dowiedzieć się więcej o kodzie w ten sposób i często identyfikować usterki przed zapoznawaniem jakichkolwiek oczywistych objawów.

Aby dowiedzieć się, jak korzystać z najważniejszych funkcji debugera, zobacz [debugowanie dla bezwzględnych początkujących](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Usterki innego rodzaju zawierają nieefektywny kod, który powoduje spowolnienie działania aplikacji lub użycie zbyt dużej ilości pamięci. Na ogół Optymalizacja wydajności jest czymś w dalszej części opracowywania aplikacji. Można jednak szybko uruchamiać problemy z wydajnością (na przykład, że część aplikacji działa wolno) i może być konieczne przetestowanie aplikacji przy użyciu narzędzi profilowania na początku. Aby uzyskać więcej informacji na temat narzędzi profilowania, takich jak narzędzie użycie procesora CPU i Analizator pamięci, zobacz [najpierw przejrzyj narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

W tym artykule przedstawiono sposób unikania i naprawiania wielu typowych usterek w kodzie oraz kiedy używać debugera. Następnie Dowiedz się więcej na temat rozwiązywania usterek przy użyciu debugera programu Visual Studio.

> [!div class="nextstepaction"]
> [Debugowanie dla całkowicie początkujących](../debugger/debugging-absolute-beginners.md)
