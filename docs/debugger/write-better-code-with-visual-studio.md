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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416415"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniki i narzędzia debugowania ułatwiające pisanie lepszego kodu

Naprawianie usterek i błędów w kodzie może być czasochłonne i czasami frustrujące — zadanie. Zajmuje trochę czasu, aby dowiedzieć się, jak można debugować skutecznie, ale rozbudowane środowisko IDE, takie jak Visual Studio ułatwia zadania o wiele prostsze. Środowisko IDE może pomóc w rozwiązaniu błędów i szybszej debugowania kodu, a nie tylko, ale może też pomóc napisać lepszy kod z mniejszą liczbą błędów. Naszym celem tego artykułu jest udostępnienie całościowego widoku procesu "Usterka-naprawianie", dzięki czemu wiadomo, kiedy należy używać analizatora kodu, kiedy należy używać debugera, jak naprawić wyjątki i jak kod zamiaru. Jeśli już wiesz, że musisz użyć debugera, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

W tym artykule omówiono sposób wykorzystania środowiska IDE, aby zwiększyć produktywność sesji kodowania. Firma Microsoft dotyku kilku zadań, takich jak:

* Przygotowanie kodu do debugowania przy użyciu analizatora kodu środowiska IDE

* Jak naprawić wyjątków (błędy środowiska wykonawczego)

* Jak zminimalizować usterki przez kodowanie dla zamiaru (przy użyciu potwierdzenia)

* Kiedy należy używać debugera

Aby zademonstrować te zadania, pokazujemy kilka najbardziej typowych błędów i usterek, które będzie występować podczas próby przeprowadzenia debugowania aplikacji. Mimo że kod przykładowy C#, informacje koncepcyjne poniżej ogólnie stosuje się do języka C++, Visual Basic, JavaScript i inne języki obsługiwane przez program Visual Studio (z wyjątkiem sytuacji, gdy podane). Zrzuty ekranu są w języku C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Tworzenie przykładowej aplikacji z niektórymi usterkami i błędami

Poniższy kod zawiera pewne błędy, które można rozwiązać, przy użyciu programu Visual Studio IDE. W tym miejscu aplikacja jest prosta aplikacja, która symuluje pobieranie danych JSON z niektórych operacji, podczas deserializacji danych do obiektu i aktualizowanie prostą listę nowych danych.

Aby utworzyć aplikację:

1. W zależności od typu aplikacji, który ma zostać utworzony, musi być zainstalowany program Visual Studio i **Programowanie na platformie .NET Core** lub środowisko **programistyczne programu .NET Desktop** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, kliknij pozycję **narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie programu **.NET Core dla wielu platform** lub programowanie **aplikacji klasycznych platformy .NET** , a następnie wybierz **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**. Wpisz w polu wyszukiwania **konsolę** , a następnie wybierz pozycję **Aplikacja konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)** . Wybierz pozycję **Dalej**. Wpisz nazwę projektu, taką jak **Console_Parse_JSON** , i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Wizualizacja C#** wybierz pozycję **Aplikacja konsolowa**, a następnie w środkowym okienku wybierz pozycję Aplikacja **konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)** . Wpisz nazwę, taką jak **Console_Parse_JSON** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **Aplikacja konsolowa (.NET Core)** lub **aplikacja konsoli (.NET Framework)** , przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz opcję **Programowanie dla wielu platform w środowisku .NET Core** lub **środowisko programistyczne programu .NET Desktop** , a następnie wybierz polecenie **Modyfikuj**.

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

## <a name="find-the-red-and-green-squiggles"></a>Znajdź zygzaki czerwonego i zielonego!

Przed podjęciem próby Uruchom przykładową aplikację i uruchom debuger, sprawdź kod w edytorze kodu dla czerwonego i zielonego faliste linie. Reprezentują te błędy i ostrzeżenia, które są identyfikowane przez analizator kodu środowiska IDE. Czerwone faliste linie błędów kompilacji, które należy naprawić przed uruchomić kod. Zielone symbole są ostrzeżenia. Chociaż często można uruchomić aplikację bez ustalenia ostrzeżenia, mogą być źródłem błędów i możesz często zaoszczędzić czas i problemy, badając ich. Te ostrzeżenia i błędy są również wyświetlane w oknie **Lista błędów** , jeśli wolisz wyświetlić widok listy.

W przykładowej aplikacji Zobacz kilka czerwone symbole, które trzeba naprawić, a jeden, zielony, który możesz przyjrzymy się. Oto pierwszy błąd.

![Błąd podczas pokazywania jako czerwona fala](../debugger/media/write-better-code-red-squiggle.png)

Aby naprawić ten błąd, zostanie przyjrzymy się inna funkcja IDE, reprezentowany przez ikonę żarówki.

## <a name="check-the-light-bulb"></a>Sprawdź żarówki.

Pierwszy czerwona fala reprezentuje błąd kompilacji. Umieść kursor nad nim i zobaczysz komunikat ```The name `Encoding` does not exist in the current context```.

Należy zauważyć, że ten błąd wskazuje ikonę żarówki, aby lewym dolnym rogu. Wraz ze ikoną śrubokrętu ![ikonę śrubokrętu](../ide/media/screwdriver-icon.png)ikona żarówki ![ikona żarówki](../ide/media/light-bulb-icon.png) reprezentuje szybkie akcje, które mogą pomóc w rozwiązaniu lub ponownym uruchomieniu kodu. Żarówka reprezentuje problemy, które *należy* naprawić. Śrubokręt jest w przypadku problemów, które można wybrać, aby rozwiązać problem. Użyj pierwszej sugerowanej poprawki, aby rozwiązać ten problem, klikając pozycję **System. Text** po lewej stronie.

![Użyj żarówki, aby naprawić kod](../debugger/media/write-better-code-missing-include.png)

Po kliknięciu tego elementu program Visual Studio dodaje instrukcję `using System.Text` w górnej części pliku *program.cs* i czerwona zygzakowata znika. (Jeśli nie masz pewności, jaka będzie Sugerowana poprawka, wybierz link **Podgląd zmian** po prawej stronie przed zastosowaniem poprawki).

Poprzedni błąd jest typowym, który jest zwykle naprawiany przez dodanie nowej instrukcji `using` do kodu. Istnieje kilka typowych, podobnych błędów do tego, takich jak ```The type or namespace `Name` cannot be found.``` tego rodzaju błędy mogą wskazywać brak odwołania do zestawu (kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Dodaj** **odwołanie** > ), nazwę błędnej pisowni lub brakującą bibliotekę, którą trzeba dodać (dla C#, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Usuń pozostałe błędy i ostrzeżenia

Istnieje kilka więcej zygzaki przyjrzenie się w tym kodzie. W tym miejscu zobaczysz typowy błąd konwersji typu. Po umieszczeniu wężyk zobaczysz, że kod próbuje przekonwertować ciąg na liczbę całkowitą, która nie jest obsługiwana, chyba że dodasz kod jawne, aby konwersji.

![Błąd konwersji typu](../debugger/media/write-better-code-conversion-error.png)

Analizator kodu nie można odgadnąć zgodne z zamiarami użytkownika, dlatego są nie żarówki, aby Ci pomóc tym razem. Aby naprawić ten błąd, musisz wiedzieć celem kodu. W tym przykładzie nie jest zbyt trudne, aby zobaczyć, że `points` powinna być wartością liczbową (Integer), ponieważ próbujesz dodać `points` do `totalpoints`.

Aby naprawić ten błąd, Zmień `points` składową klasy `User` z:

```csharp
[DataMember]
internal string points;
```

na taki:

```csharp
[DataMember]
internal int points;
```

Pozbycie czerwoną linią falistą w edytorze kodu.

Następnie umieść wskaźnik myszy na zielonym zygzaku w deklaracji elementu członkowskiego danych `points`. Analizator kodu informujący o tym, że zmienna nigdy nie jest przypisywana wartość.

![Komunikat ostrzegawczy dotyczący nieprzypisanej zmiennej](../debugger/media/write-better-code-warning-message.png)

Zazwyczaj jest to problem, który musi mieć stałą. Jednak w przykładowej aplikacji, w której znajdują się dane w zmiennej `points` podczas procesu deserializacji, a następnie dodając tę wartość do `totalpoints` elementu członkowskiego danych. W tym przykładzie znana celem kod i można bezpiecznie zignorować to ostrzeżenie. Jednakże jeśli chcesz wyeliminować ostrzeżenia, możesz zastąpić następujący kod:

```csharp
item.totalpoints = users[i].points;
```

na kod:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Zielony wężyk stanie się niepotrzebna.

## <a name="fix-an-exception"></a>Usuń wyjątek

Po stałej czerwone symbole i rozwiązany — lub co najmniej zbadać — wszystkie zielone symbole, jesteś gotowy do uruchomienia debugera i uruchomić aplikację.

Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania.

W tym momencie Przykładowa aplikacja zgłasza wyjątek `SerializationException` (błąd czasu wykonywania). Oznacza to, że aplikacja zastosowana podlewka na dane, które podejmuje próbę serializacji. Ponieważ aplikacja jest uruchomiona w trybie debugowania (debuger dołączony), pomocnika wyjątków debugera spowoduje przejście bezpośrednio do kodu, który wygenerował wyjątek i zapewnia komunikat o błędzie przydatne.

![Występuje SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Komunikat o błędzie informuje o tym, że wartość `4o` nie może być analizowana jako liczba całkowita. Dlatego w tym przykładzie wiadomo, że dane są nieprawidłowe: `4o` powinna być `40`. Jednakże jeśli nie masz kontrolę nad danymi w scenariuszu rzeczywistego (np. otrzymujesz z usługi sieci web), co można zrobić na jego temat? Jak można to naprawić?

Po osiągnięciu wyjątek, należy poprosić (i odpowiedzi) na kilka pytań:

* Jest to wyjątek po prostu usterkę, która będzie można naprawić? Lub:

* Ten wyjątek jest coś, co użytkownicy mogą występować?

Jeśli jest to pierwsza, naprawić błąd. (W przykładowej aplikacji oznacza to poprawienie nieprawidłowych danych). Jeśli jest to ostatnie, może być konieczne obsłużenie wyjątku w kodzie przy użyciu bloku `try/catch` (w następnej sekcji znajdziesz inne możliwe strategie). W przykładowej aplikacji Zastąp następujący kod:

```csharp
users = ser.ReadObject(ms) as User[];
```

przy użyciu tego kodu:

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

Blok `try/catch` ma koszt wydajności, więc będzie można używać go tylko wtedy, gdy ich naprawdę potrzebujesz, czyli gdzie (a) mogą wystąpić w wydanej wersji aplikacji i gdzie (b) Dokumentacja metody wskazuje, że należy sprawdzić, czy jest to wyjątek (przy założeniu, że dokumentacja jest kompletna). W wielu przypadkach odpowiednio obsłużyć wyjątek, a użytkownik nigdy nie musi wiedzieć o nim.

Poniżej przedstawiono kilka ważnych wskazówki dotyczące obsługi wyjątków:

* Unikaj używania pustego bloku catch, takiego jak `catch (Exception) {}`, który nie podejmuje odpowiednich działań, aby uwidocznić lub obsłużyć błąd. Blok catch pusta lub informacyjne można ukryć wyjątki i może sprawić, że kod utrudnia debugowanie zamiast łatwiejsze.

* Użyj bloku `try/catch` wokół konkretnej funkcji, która zgłasza wyjątek (`ReadObject`, w aplikacji przykładowej). Jeśli używasz wokół większych fragmentów kodu znajdą ukrywanie lokalizacji błędu. Na przykład nie należy używać bloku `try/catch` wokół wywołania funkcji nadrzędnej `ReadToObject`, pokazanej tutaj lub nie wiadomo, gdzie wystąpił wyjątek.

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

* W przypadku nieznanych funkcji, które są dołączane do aplikacji, szczególnie tych, które współdziałają z danymi zewnętrznymi (takimi jak żądanie sieci Web), zapoznaj się z dokumentacją, aby zobaczyć, jakie wyjątki może zgłosić funkcja. Może to być kluczowych informacji do obsługi błędów właściwe i do debugowania aplikacji.

W przypadku przykładowej aplikacji Popraw `SerializationException` w metodzie `GetJsonData`, zmieniając `4o` na `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Wyjaśnienia intencji Twojego kodu za pomocą potwierdzeń

Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**). Spowoduje to ponowne uruchomienie aplikacji w mniejszej liczby czynności. Zostaną wyświetlone następujące dane wyjściowe, w oknie konsoli.

![Wartość null w danych wyjściowych](../debugger/media/write-better-code-using-assert-null-output.png)

Możesz zobaczyć coś w poniższych danych wyjściowych, który nie jest całkowicie poprawny. **Nazwa** i **nazwisko** dla trzeciego rekordu są puste!

Jest to dobry moment, aby poznać przydatną technikę kodowania, często nieużywaną, która polega na wykorzystaniu instrukcji `assert` w funkcjach. Dodając następujący kod, należy uwzględnić sprawdzanie środowiska uruchomieniowego, aby upewnić się, że `firstname` i `lastname` nie są `null`. Zastąp następujący kod w metodzie `UpdateRecords`:

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

Po dodaniu `assert` instrukcji, takich jak to, do funkcji w trakcie procesu tworzenia, możesz pomóc określić cel kodu. W poprzednim przykładzie możemy określ następujące ustawienia:

* Prawidłowy ciąg jest wymagany dla imię
* Prawidłowy ciąg jest wymagany dla nazwisko

Określając opcje w ten sposób, możesz wymusić wymagań. Jest to proste i przydatną metodę, która służy do powierzchni błędów podczas projektowania. (instrukcje`assert` są również używane jako element główny w testach jednostkowych).

Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**).

> [!NOTE]
> Kod `assert` jest aktywny tylko w kompilacji debugowania.

Po ponownym uruchomieniu debuger zatrzymuje się w instrukcji `assert`, ponieważ wyrażenie `users[i].firstname != null` oblicza `false` zamiast `true`.

![Asercja rozwiązuje na wartość false](../debugger/media/write-better-code-using-assert.png)

Wystąpił błąd `assert` informuje o problemie, który należy zbadać. `assert` może obejmować wiele scenariuszy, w których niekoniecznie widzisz wyjątek. W tym przykładzie użytkownik nie zobaczy wyjątku, a wartość `null` zostanie dodana jako `firstname` na liście rekordów. Może to spowodować problemy później (takie jak widać w danych wyjściowych konsoli) i może być trudniejsze do debugowania.

> [!NOTE]
> W scenariuszach, w których wywoływana jest metoda dla `null` wartość, `NullReferenceException` wyniki. Zwykle chcesz uniknąć używania bloku `try/catch` dla ogólnego wyjątku, czyli wyjątku, który nie jest powiązany z określoną funkcją biblioteki. Każdy obiekt może zgłosić `NullReferenceException`. Jeśli nie masz pewności, sprawdź w dokumentacji dotyczącej funkcji biblioteki.

Podczas procesu debugowania warto zachować konkretną instrukcję `assert`, dopóki nie będzie wiadomo, że trzeba ją zamienić na rzeczywistą poprawkę kodu. Załóżmy, że możesz zdecydować, czy użytkownik może wystąpić wyjątek w kompilacji wydania aplikacji. W takim przypadku musisz wykonać refaktoryzację kodu, aby upewnić się, że Twoja aplikacja nie zgłosić wyjątek krytyczny lub spowodować inny błąd. Tak aby rozwiązać ten kod, Zastąp następujący kod:

```csharp
if (existingUser == false)
{
    User user = new User();
```

przy użyciu tego kodu:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Korzystając z tego kodu, spełniasz wymagania dotyczące kodu i upewnij się, że rekord o wartości `firstname` lub `lastname` `null` nie został dodany do danych.

W tym przykładzie dodaliśmy dwie `assert` instrukcji wewnątrz pętli. Zazwyczaj w przypadku używania `assert`najlepiej dodać instrukcje `assert` w punkcie wejścia (początku) funkcji lub metody. Obecnie przeglądasz metodę `UpdateRecords` w przykładowej aplikacji. W tej metodzie wiadomo, że masz problemy, jeśli jeden z argumentów metody jest `null`, więc sprawdź je w instrukcji `assert` w punkcie wejścia funkcji.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

W przypadku powyższych instrukcji zamiarem jest załadowanie istniejących danych (`db`) i pobranie nowych danych (`users`) przed aktualizacją.

Można użyć `assert` z dowolnym rodzajem wyrażenia, które jest rozpoznawane jako `true` lub `false`. Na przykład, można dodać instrukcję `assert` taką jak.

```csharp
Debug.Assert(users[0].points > 0);
```

Powyższy kod jest przydatne, jeśli chcesz określić następujące opcje: nową wartość punktu większą niż zero (0) jest wymagany do zaktualizowania rekordu użytkownika.

## <a name="inspect-your-code-in-the-debugger"></a>Sprawdzanie kodu w debugerze

OK teraz, gdy zostały rozwiązane wszystkie krytyczne zasoby, które jest nie tak z przykładowej aplikacji, możesz przejść na inne rzeczy ważne!

Pokazaliśmy pomocnika wyjątków debugera, ale debuger jest znacznie bardziej zaawansowane narzędzie, które umożliwia także wykonywać inne czynności, takie jak kroku przez kod, aby zbadać jego zmienne. Te bardziej zaawansowanych możliwości są przydatne w wielu scenariuszach, w szczególności następujące:

* Podjęto próbę wyizolować błąd środowiska uruchomieniowego w kodzie, ale nie można użyć go za pomocą metod i narzędzi omówionych wcześniej.

* Chcesz zweryfikować Twojego kodu, to znaczy, obejrzyj podczas jego uruchamiania, aby upewnić się, jest zachowuje się w taki sposób, w których oczekujesz i sposób, co ma się.

    Jest to istotne, aby obejrzeć kodu podczas jego uruchamiania. Możesz dowiedzieć się więcej o swoim kodzie w ten sposób i można często zidentyfikować usterek przed ich manifestu żadne objawy oczywiste.

Aby dowiedzieć się, jak korzystać z najważniejszych funkcji debugera, zobacz [debugowanie dla bezwzględnych początkujących](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Błędów innego rodzaju obejmują nieefektywny kod, który powoduje, że aplikacja działał wolno lub używają zbyt dużo pamięci. Ogólnie rzecz biorąc Optymalizacja wydajności jest coś, co można zrobić później w tworzenie aplikacji. Jednakże, możesz napotkać problemy z wydajnością wcześnie (na przykład, możesz zobaczyć część aplikacja działa wolno), i może być konieczne do testowania aplikacji przy użyciu narzędzi do profilowania na wczesnym etapie. Aby uzyskać więcej informacji na temat narzędzi profilowania, takich jak narzędzie użycie procesora CPU i Analizator pamięci, zobacz [najpierw przejrzyj narzędzia profilowania](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Następne kroki

W tym artykule wyjaśniono sposób uniknięcia i rozwiązać wiele typowych błędów w kodzie i kiedy należy używać debugera. Następnie Dowiedz się więcej o naprawiaj usterki za pomocą debugera programu Visual Studio.

> [!div class="nextstepaction"]
> [Debugowanie dla bezwzględnych początkujących](../debugger/debugging-absolute-beginners.md)
