---
title: Pozwól Pomoc programu Visual Studio, możesz napisać C# kodu z mniej błędów
description: Dowiedz się, jak napisać lepszego kodu z mniej błędów
ms.custom: debug-experiments
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c16cfdc8d554ce9bf556ea707f977989e1dab72
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389380"
---
# <a name="fix-bugs-by-writing-better-c-code-using-visual-studio"></a>Usuwanie usterek, pisząc lepiej C# kodu za pomocą programu Visual Studio

Debugowanie kodu może być czasochłonne — a czasem zakłócenie — zadanie. Czasochłonne Dowiedz się, jak można debugować skutecznie. Rozbudowane środowisko IDE, takie jak Visual Studio może ułatwić zadanie w dużej mierze. Środowisko IDE może pomóc możesz debugować kod szybciej i nie tylko, jednak może również pomoc zapisu lepszego kodu przy użyciu mniejszej liczby usterek. Naszym celem w tym artykule jest umożliwiają całościowy obraz proces debugowania, dzięki czemu będzie wiadomo, kiedy należy używać analizator kodu, do używania debugera i kiedy należy używać innych narzędzi.

W tym artykule będziemy wyjaśniać, wykorzystując IDE, aby zwiększyć wydajność sesji debugowania. Firma Microsoft dotyku kilku zadań, takich jak:

* Przygotowanie kodu do debugowania przy użyciu analizatora kodu środowiska IDE

* Jak naprawić wyjątków (błędy środowiska wykonawczego)

* Jak zminimalizować błędy kodowania intencji

* Kiedy należy używać debugera

Aby zademonstrować te zadania, pokazujemy kilka najbardziej typowych błędów i usterek, które będzie występować podczas próby przeprowadzenia debugowania aplikacji. Mimo że kod przykładowy C#, informacje koncepcyjne poniżej ogólnie stosuje się do języka C++, Visual Basic, JavaScript i inne języki obsługiwane przez program Visual Studio (z wyjątkiem sytuacji, gdy podane). Zrzuty ekranu są w języku C#.

## <a name="follow-along-using-the-sample-app"></a>Z tego skorzystać, za pomocą przykładowej aplikacji

Jeśli wolisz, możesz utworzyć program .NET Framework lub .NET Core Aplikacja konsoli, która zawiera dokładnie usterek i błędów, które opisano w tym miejscu, możesz samodzielnie i wprowadzić poprawki, samodzielnie.

Aby utworzyć aplikację, Otwórz program Visual Studio, a następnie wybierz **Plik > Nowy projekt**. W obszarze **Visual C#** , wybierz **pulpitu Windows** lub **platformy .NET Core**, a następnie w środkowym okienku wybierz **aplikacja Konsolowa**. Wpisz nazwę, takich jak **Console_Parse_JSON** i kliknij przycisk **OK**. Program Visual Studio tworzy projekt. Wklej [przykładowego kodu](#sample-code) z projektem *Program.cs* pliku.

> [!NOTE]
> Jeśli nie widzisz **aplikację Konsolową** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** lub **programowanie dla wielu platform .NET Core** obciążenia, wybierz **Modyfikuj**.

## <a name="find-the-red-and-green-squiggles"></a>Znajdź zygzaki czerwonego i zielonego!

Przed podjęciem próby Uruchom przykładową aplikację i uruchom debuger, sprawdź kod w edytorze kodu dla czerwonego i zielonego faliste linie. Reprezentują te błędy i ostrzeżenia, które są identyfikowane przez analizator kodu środowiska IDE. Czerwone faliste linie błędów kompilacji, które należy naprawić przed uruchomić kod. Zielone symbole są ostrzeżenia. Chociaż często można uruchomić aplikację bez ustalenia ostrzeżenia, mogą być źródłem błędów i możesz często zaoszczędzić czas i problemy, badając ich. Te ostrzeżenia i błędy również pojawi się w **lista błędów** okna, jeśli użytkownik sobie tego życzy widoku listy.

W przykładowej aplikacji Zobacz kilka czerwone symbole, które trzeba naprawić, a jeden, zielony, który możesz przyjrzymy się. Oto pierwszy błąd.

![Błąd podczas pokazywania jako czerwona fala](../debugger/media/write-better-code-red-squiggle.png)

Aby naprawić ten błąd, zostanie przyjrzymy się inna funkcja IDE, reprezentowany przez ikonę żarówki.

## <a name="check-the-light-bulb"></a>Sprawdź żarówki.

Pierwszy czerwona fala reprezentuje błąd kompilacji. Umieść kursor nad nim, a następnie zostanie wyświetlony komunikat ```The name `Encoding` does not exist in the current context```.

Należy zauważyć, że ten błąd wskazuje ikonę żarówki, aby lewym dolnym rogu. Wraz z ikony śrubokręt ![ikonę śrubokręt](../ide/media/screwdriver-icon.png), ikona żarówki z funkcją ![ikoną żarówki](../ide/media/light-bulb-icon.png) reprezentuje szybkie akcje, które mogą pomóc Ci rozwiązać albo przeprowadź refaktoryzację kodu wbudowanego. Reprezentuje żarówki problemów *powinien* naprawić. Śrubokręt jest w przypadku problemów, które można wybrać, aby rozwiązać problem. Użyj pierwszego sugerowanej poprawki, aby rozwiązać ten problem, klikając pozycję **przy użyciu System.Text** po lewej stronie.

![Użyj żarówki, aby naprawić kod](../debugger/media/write-better-code-missing-include.png)

Po kliknięciu tego elementu, program Visual Studio dodaje `using System.Text` instrukcji na górze *Program.cs* plików i czerwona fala zniknie. (Jeśli nie masz pewności, co zrobić będzie sugerowanej poprawki, wybierz **podgląd zmian** łącza po prawej stronie przed zastosowaniem poprawki.)

Poprzedni błąd jest popularnym, który zazwyczaj naprawić, dodając nowe `using` instrukcji w kodzie. Istnieją takie jak kilka błędów wspólne, podobne do tego jednego ```The type or namespace `Name` cannot be found.``` te rodzaje błędów może wskazywać na Brak odwołania do zestawu (kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Dodaj** > **odwołania**), nieprawidłowo zapisana nazwa lub Brak biblioteki, który chcesz dodać, za pomocą narzędzia NuGet (kliknij projekt prawym przyciskiem myszy i wybierz polecenie **Zarządzaj pakietami NuGet**).

## <a name="fix-the-errors-and-warnings"></a>Napraw błędy i ostrzeżenia

Istnieje kilka więcej zygzaki przyjrzenie się w tym kodzie. W tym miejscu zobaczysz typowy błąd konwersji typu. Po umieszczeniu wężyk zobaczysz, że kod próbuje przekonwertować ciąg na liczbę całkowitą, która nie jest obsługiwana, chyba że dodasz kod jawne, aby konwersji.

![Błąd konwersji typu](../debugger/media/write-better-code-conversion-error.png)

Analizator kodu nie można odgadnąć zgodne z zamiarami użytkownika, dlatego są nie żarówki, aby Ci pomóc tym razem. Aby naprawić ten błąd, musisz wiedzieć celem kodu. W tym przykładzie nie jest zbyt trudne do zobaczenia, który `points` powinien być wartością numeryczną (liczba całkowita), ponieważ próbujesz dodać `points` do `totalpoints`.

Aby naprawić ten błąd, zmień `points` członkiem `User` klasy z tego:

```csharp
[DataMember]
internal string points;
```

Następujące zmiany:

```csharp
[DataMember]
internal int points;
```

Pozbycie czerwoną linią falistą w edytorze kodu.

Następnie umieść kursor nad linią falistą w deklaracji zielony `points` element członkowski danych. Analizator kodu informujący o tym, że zmienna nigdy nie jest przypisywana wartość.

![Komunikat ostrzegawczy dotyczący nieprzypisanej zmiennej](../debugger/media/write-better-code-warning-message.png)

Zazwyczaj jest to problem, który musi mieć stałą. Jednak w przykładowej aplikacji w rzeczywistości przechowujesz dane w `points` zmiennych podczas procesu deserializacji, a następnie dodając tę wartość do `totalpoints` element członkowski danych. W tym przykładzie znana celem kod i można bezpiecznie zignorować to ostrzeżenie. Jednakże jeśli chcesz wyeliminować ostrzeżenia, możesz zastąpić następujący kod:

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

Naciśnij klawisz **F5** (**Debuguj > Rozpocznij debugowanie**) lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie ") na pasku narzędzi debugowania.

W tym momencie Przykładowa aplikacja zgłasza `SerializationException` wyjątku (błąd czasu wykonywania). Oznacza to, że aplikacja zastosowana podlewka na dane, które podejmuje próbę serializacji. Ponieważ aplikacja jest uruchomiona w trybie debugowania (debuger dołączony), pomocnika wyjątków debugera spowoduje przejście bezpośrednio do kodu, który wygenerował wyjątek i zapewnia komunikat o błędzie przydatne.

![Występuje SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Komunikat o błędzie powoduje, że użytkownik, wartość `4o` nie może być analizowana jako liczba całkowita. Tak, w tym przykładzie wiesz, dane są nieprawidłowe: `4o` powinien być `40`. Jednakże jeśli nie masz kontrolę nad danymi w scenariuszu rzeczywistego (np. otrzymujesz z usługi sieci web), co można zrobić na jego temat? Jak można to naprawić?

Po osiągnięciu wyjątek, należy poprosić (i odpowiedzi) na kilka pytań:

* Jest to wyjątek po prostu usterkę, która będzie można naprawić? Ewentualnie

* Ten wyjątek jest coś, co użytkownicy mogą występować?

Jeśli jest to pierwsza, naprawić błąd. (W przykładowej aplikacji, która oznacza Napraw nieprawidłowe dane). Po drugie, może być konieczne do obsługi wyjątków w kodzie przy użyciu `try/catch` bloku (spojrzymy na inne możliwe poprawki w następnej sekcji). W przykładowej aplikacji Zastąp następujący kod:

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

A `try/catch` bloku ma wzrost kosztów wydajności, więc tylko będziesz chciał Użyj ich, gdy naprawdę potrzebne, oznacza to, gdzie a sytuacja może wystąpić w wersji aplikacji, jak i gdzie (b) dokumentacji dla metody wskazuje, że należy sprawdzić, wyjątek (przy założeniu, że dokumentacja została zakończona!). W wielu przypadkach odpowiednio obsłużyć wyjątek, a użytkownik nigdy nie musi wiedzieć o nim.

Poniżej przedstawiono kilka ważnych wskazówki dotyczące obsługi wyjątków:

* Należy unikać blok catch pusty, takie jak `catch (Exception) {}`, która nie przyjmuje odpowiednią akcję, aby udostępnić lub obsłużyć błąd. Blok catch pusta lub informacyjne można ukryć wyjątki i może sprawić, że kod utrudnia debugowanie zamiast łatwiejsze.

* Użyj `try/catch` bloku wokół określonych funkcji, która zgłasza wyjątek (`ReadObject`, w przykładowej aplikacji). Jeśli używasz wokół większych fragmentów kodu znajdą ukrywanie lokalizacji błędu. Na przykład nie używaj `try/catch` bloku wokół wywołania funkcji nadrzędnej `ReadToObject`, pokazano poniżej, lub nie jest wiadomo dokładnie, gdzie wyjątek wystąpił.

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

* Dla nieznanego funkcje, które zawierają w swojej aplikacji, expecially tych interakcji z danymi zewnętrznymi (np. żądania sieci web) zapoznaj się z dokumentacją, aby zobaczyć, jakie wyjątki funkcji będzie prawdopodobnie zgłaszany. Może to być kluczowych informacji do obsługi błędów właściwe i do debugowania aplikacji.

Dla przykładowej aplikacji, należy naprawić `SerializationException` w `GetJsonData` metody, zmieniając `4o` do `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Wyjaśnienia intencji Twojego kodu za pomocą potwierdzeń

Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**). Spowoduje to ponowne uruchomienie aplikacji w mniejszej liczby czynności. Zostaną wyświetlone następujące dane wyjściowe, w oknie konsoli.

![Wartość null w danych wyjściowych](../debugger/media/write-better-code-using-assert-null-output.png)

Możesz zobaczyć coś w poniższych danych wyjściowych, który nie jest całkowicie poprawny. **Nazwa** i **lastname** dla trzeciego rekordu są puste!

Jest to dobry moment, aby porozmawiać na temat przydatne praktyk kodowania, często niewykorzystane, który jest użycie `assert` instrukcji w funkcji. Przez dodanie poniższego kodu, obejmują Sprawdzanie czasu wykonywania, aby upewnić się, że `firstname` i `lastname` nie są `null`. Zastąp następujący kod w `UpdateRecords` metody:

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

Dodając `assert` instrukcje następująco funkcji podczas procesu projektowania, możesz pomóc określić celem swój kod. W poprzednim przykładzie możemy określ następujące ustawienia:

* Prawidłowy ciąg jest wymagany dla imię
* Prawidłowy ciąg jest wymagany dla nazwisko

Określając opcje w ten sposób, możesz wymusić wymagań. Jest to proste i przydatną metodę, która służy do powierzchni błędów podczas projektowania. (`assert` instrukcje są również używane jako główny element w testach jednostkowych.)

Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**).

> [!NOTE]
> `assert` Kodu jest aktywny tylko w kompilacji debugowania.

Po ponownym uruchomieniu, debuger zatrzymuje się na `assert` instrukcji, ponieważ wyrażenie `users[i].firstname != null` daje w wyniku `false` zamiast `true`.

![Asercja rozwiązuje na wartość false](../debugger/media/write-better-code-using-assert.png)

`assert` Błąd informujący o tym problemie, który chcesz zbadać. `assert` może obejmować wiele scenariuszy, w którym niekoniecznie nie widzisz wyjątek. W tym przykładzie użytkownik nie będzie widział wyjątek, a `null` wartość zostanie dodany jako `firstname` na liście rekordów. Może to spowodować problemy później (takie jak widać w danych wyjściowych konsoli) i może być trudniejsze do debugowania.

> [!NOTE]
> W scenariuszach, gdzie wywołania metody wobec `null` wartość `NullReferenceException` wyników. Zazwyczaj chcesz należy unikać `try/catch` zablokować na ogólny wyjątek, oznacza to, że wyjątek, który nie jest związany z funkcji w określonej bibliotece. Każdy obiekt może zgłosić `NullReferenceException`. Jeśli nie masz pewności, sprawdź w dokumentacji dotyczącej funkcji biblioteki.

Podczas debugowania, warto zachować określonego `assert` instrukcji, dopóki nie wiesz, musisz zastąpić poprawkę rzeczywisty kod. Załóżmy, że możesz zdecydować, czy użytkownik może wystąpić wyjątek w kompilacji wydania aplikacji. W takim przypadku musisz wykonać refaktoryzację kodu, aby upewnić się, że Twoja aplikacja nie zgłosić wyjątek krytyczny lub spowodować inny błąd. Tak aby rozwiązać ten kod, Zastąp następujący kod:

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

Korzystając z tego kodu, spełnianie wymagań dotyczących kodu i upewnij się, że rekord z `firstname` lub `lastname` wartość `null` nie została dodana do danych.

W tym przykładzie dodaliśmy dwa `assert` instrukcji wewnątrz pętli. Zwykle korzystając z `assert`, warto dodać `assert` instrukcji w punkcie wejścia (począwszy od), funkcji lub metody. Aktualnie patrzysz `UpdateRecords` metody w przykładowej aplikacji. W przypadku tej metody, wiesz, jesteś w problemy, jeśli jest jeden z argumentów metody `null`, dlatego należy sprawdzić je zarówno `assert` instrukcji w punkcie wejścia funkcji.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

W przypadku poprzednich instrukcji, zgodne z zamiarami użytkownika jest ładowania istniejących danych (`db`) i pobieranie nowych danych (`users`) przed zaktualizowaniem niczego.

Możesz użyć `assert` za pomocą dowolnego rodzaju wyrażenia, który jest rozpoznawany jako `true` lub `false`. Tak, na przykład można dodać `assert` instrukcji w następujący sposób.

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

Aby dowiedzieć się, jak korzystać z podstawowych funkcji debugera, zobacz [debugowania dla początkujących](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Błędów innego rodzaju obejmują nieefektywny kod, który powoduje, że aplikacja działał wolno lub używają zbyt dużo pamięci. Ogólnie rzecz biorąc Optymalizacja wydajności jest coś, co można zrobić później w tworzenie aplikacji. Jednakże, możesz napotkać problemy z wydajnością wcześnie (na przykład, możesz zobaczyć część aplikacja działa wolno), i może być konieczne do testowania aplikacji przy użyciu narzędzi do profilowania na wczesnym etapie. Aby uzyskać więcej informacji na temat narzędzi, takich jak narzędzie użycie procesora CPU i analizatora pamięci profilowania, zobacz [Pierwsze spojrzenie na narzędzi profilowania](../profiling/profiling-feature-tour.md).

## <a name="sample-code"></a> Przykładowy kod

Poniższy kod zawiera pewne błędy, które można rozwiązać, przy użyciu programu Visual Studio IDE. W tym miejscu aplikacja jest prosta aplikacja, która symuluje pobieranie danych JSON z niektórych operacji, podczas deserializacji danych do obiektu i aktualizowanie prostą listę nowych danych.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON_DotNetCore
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

## <a name="next-steps"></a>Następne kroki

W tym artykule wyjaśniono sposób uniknięcia i rozwiązać wiele typowych błędów w kodzie i kiedy należy używać debugera. Następnie Dowiedz się więcej o naprawiaj usterki za pomocą debugera programu Visual Studio.

> [!div class="nextstepaction"]
> [Debugowanie dla całkowicie początkujących](../debugger/debugging-absolute-beginners.md)
