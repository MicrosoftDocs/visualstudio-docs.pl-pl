---
title: Debugowanie kodu dla początkujących
description: Jeśli debugujesz po raz pierwszy, poznaj kilka zasad ułatwiających uruchamianie aplikacji w trybie debugowania w programie Visual Studio
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c3cf9d5e4d72ed316344d1bda930d0416e9efe5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416400"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Jak debugować dla początkujących

Bez wątpienia kod, który piszemy jako programiści, nie zawsze robi to, czego oczekiwaliśmy. Czasami robi coś zupełnie innego! Gdy tak się stanie, następnym zadaniem jest dowiedzieć się, dlaczego i chociaż możemy być kuszeni, aby po prostu zachować patrząc na nasz kod godzinami, jest o wiele łatwiejsze i wydajne w użyciu narzędzia do debugowania lub debugera.

Debuger, niestety, nie jest czymś, co może magicznie ujawnić wszystkie problemy lub "błędy" w naszym kodzie. *Debugowanie* oznacza, aby uruchomić kod krok po kroku w narzędziu debugowania, takich jak Visual Studio, aby znaleźć dokładny punkt, w którym popełnisz błąd programowania. Następnie można zrozumieć, jakie poprawki należy wprowadzić w kodzie i narzędzia debugowania często pozwalają na wprowadzenie tymczasowych zmian, dzięki czemu można kontynuować uruchamianie programu.

Korzystanie debuger skutecznie jest również umiejętnością, która wymaga czasu i praktyki, aby dowiedzieć się, ale ostatecznie jest podstawowym zadaniem dla każdego programisty. W tym artykule, a następnie wprowadzamy podstawowe zasady debugowania i zawierają wskazówki, aby rozpocząć.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnij problem, zadając sobie właściwe pytania

Pomaga wyjaśnić problem, na który wpadłeś, zanim spróbujesz go rozwiązać. Spodziewamy się, że już wpadł na problem w kodzie, w przeciwnym razie nie byłoby tutaj próbuje dowiedzieć się, jak go debugować! Dlatego przed rozpoczęciem debugowania upewnij się, że zidentyfikowałeś problem, który próbujesz rozwiązać:

* Czego oczekiwałeś od kodu?

* Co się stało zamiast tego?

    Jeśli napotkałeś błąd (wyjątek) podczas uruchamiania aplikacji, może to być dobra rzecz! Wyjątek jest nieoczekiwane zdarzenie napotkane podczas uruchamiania kodu, zazwyczaj błąd pewnego rodzaju. Narzędzie do debugowania można zabrać do dokładnego miejsca w kodzie, gdzie wystąpił wyjątek i może pomóc w zbadaniu możliwych poprawek.

    Jeśli stało się coś innego, jaki jest objaw problemu? Czy podejrzewasz już, gdzie ten problem wystąpił w kodzie? Na przykład jeśli kod wyświetla jakiś tekst, ale tekst jest niepoprawny, wiesz, że dane są złe lub kod, który ustawia tekst wyświetlany ma jakiś błąd. Przechodząc przez kod w debugerze, można zbadać każdą zmianę zmiennych, aby dokładnie odnajdywać, kiedy i jak są przypisywane niepoprawne wartości.

## <a name="examine-your-assumptions"></a>Sprawdź swoje założenia

Zanim zbadasz błąd lub błąd, pomyśl o założeniach, które sprawiły, że spodziewasz się pewnego wyniku. Ukryte lub nieznane założenia mogą przeszkadzać w identyfikowaniu problemu, nawet jeśli patrzysz bezpośrednio na przyczynę problemu w debugerze. Możesz mieć długą listę możliwych założeń! Oto kilka pytań, które należy zadać sobie, aby zakwestionować swoje założenia.

* Czy używasz odpowiedniego interfejsu API (czyli odpowiedniego obiektu, funkcji, metody lub właściwości)? Interfejs API, którego używasz, może nie wykonywać tego, co uważasz za robi. (Po zbadaniu wywołania interfejsu API w debugerze, naprawienie go może wymagać podróży do dokumentacji w celu zidentyfikowania poprawnego interfejsu API).

* Czy używasz interfejsu API poprawnie? Być może użyłeś odpowiedniego interfejsu API, ale nie użyłeś go we właściwy sposób.

* Czy kod zawiera literówki? Niektóre literówki, takie jak prosta pisownia nazwy zmiennej, mogą być trudne do zobaczenia, szczególnie podczas pracy z językami, które nie wymagają deklarowania zmiennych przed ich użyciem.

* Czy wwzmek do kodu i założyć, że nie ma związku z problemem, który widzisz?

* Czy spodziewałeś się, że obiekt lub zmienna będzie zawierać określoną wartość (lub określony typ wartości), która różni się od tego, co naprawdę się wydarzyło?

* Czy znasz intencję kodu? Często trudniej jest debugować cudzy kod. Jeśli nie jest to kod, jest możliwe, że może być konieczne poświęcanie czasu na uczenie się dokładnie, co robi kod, zanim będzie można debugować go skutecznie.

    > [!TIP]
    > Podczas pisania kodu, rozpocząć małe i rozpocząć od kodu, który działa! (Dobry przykładowy kod jest pomocny tutaj.) Czasami łatwiej jest naprawić duży lub skomplikowany zestaw kodu, zaczynając od małego fragmentu kodu, który pokazuje podstawowe zadanie, które próbujesz osiągnąć. Następnie można modyfikować lub dodawać kod przyrostowo, testując w każdym punkcie pod kątem błędów.

Kwestionując swoje założenia, można skrócić czas potrzebny do znalezienia problemu w kodzie. Można również skrócić czas potrzebny do rozwiązania problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Krok po kroku przez kod w trybie debugowania, aby dowiedzieć się, gdzie wystąpił problem

Po normalnym uruchomieniu aplikacji, widać błędy i niepoprawne wyniki tylko po uruchomieniu kodu. Program może również zakończyć się nieoczekiwanie, nie informując o tym, dlaczego.

Uruchamianie aplikacji w debugerze, nazywanym również *trybem debugowania,* oznacza, że debuger aktywnie monitoruje wszystko, co dzieje się podczas uruchamiania programu. Umożliwia również wstrzymanie aplikacji w dowolnym momencie, aby sprawdzić jej stan, a następnie krok po wierszu kodu, aby obserwować każdy szczegół, jak to się dzieje.

W programie Visual Studio należy wprowadzić tryb debugowania przy użyciu **polecenia F5** (lub polecenia menu **Debugowania** > **Start debugowania** lub **przycisku Rozpocznij debugowanie** Start ![Debugowania](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania). Jeśli wystąpią wyjątki, Pomocnik wyjątków programu Visual Studio przeniesie Cię do dokładnego punktu, w którym wystąpił wyjątek i zawiera inne przydatne informacje. Aby uzyskać więcej informacji na temat obsługi wyjątków w kodzie, zobacz [Techniki debugowania i narzędzia](../debugger/write-better-code-with-visual-studio.md).

Jeśli nie otrzymasz wyjątku, prawdopodobnie masz dobry pomysł, gdzie szukać problemu w kodzie. Jest to, gdzie można użyć *punktów przerwania* z debugerem, aby dać sobie szansę, aby zbadać kod dokładniej. Punkty przerwania są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy wstrzymać uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub sekwencji, w której uruchamia się kod.

W programie Visual Studio można szybko ustawić punkt przerwania, klikając lewy margines obok wiersza kodu. Lub umieść kursor na linii i naciśnij **klawisz F9**.

Aby pomóc zilustrować te pojęcia, przebierzemy Cię przez przykładowy kod, który ma już kilka błędów. Używamy języka C#, ale funkcje debugowania dotyczą języka Visual Basic, C++, JavaScript, Python i innych obsługiwanych języków.

### <a name="create-a-sample-app-with-some-bugs"></a>Tworzenie przykładowej aplikacji (z niektórymi błędami)

Następnie utworzymy aplikację, która ma kilka błędów.

1. W zależności od typu aplikacji, który ma zostać utworzony, należy zainstalować program Visual Studio i obciążenie **programistyczne pulpitu platformy .NET** lub obciążenie **programistyczne .NET Core** na wielu platformach.

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, kliknij pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia instalator programu Visual Studio. Wybierz obciążenie **programistyczne dla komputerów .NET** (lub program **.NET Core cross platform development),** a następnie wybierz pozycję **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie początkowym wybierz pozycję **Utwórz nowy projekt**. Wpisz **konsolę** w polu wyszukiwania, a następnie wybierz **aplikację konsoli (.NET Core)** lub aplikację konsoli **(.NET Framework).** Wybierz pozycję **Dalej**. Wpisz nazwę projektu, taką jak **ConsoleApp-FirstApp,** a następnie kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Aplikacja konsoli**, a następnie w środkowym okienku wybierz aplikację **konsoli (.NET Framework)** lub **aplikację konsoli (.NET Core).** Wpisz nazwę, taką jak **ConsoleApp-FirstApp** i kliknij **przycisk OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **aplikacji konsoli (.NET Framework)** lub **aplikacji konsoli (net core),** przejdź do **pozycji Narzędzia** > **Pobierz narzędzia i funkcje**, który otwiera Instalator programu Visual Studio. Wybierz opcję **programowy platformy .NET Core dla różnych platform** lub obciążenia **programistycznego .NET dla komputerów stacjonarnych,** a następnie wybierz pozycję **Modyfikuj**.

    Visual Studio tworzy projekt konsoli, który pojawia się w Eksploratorze rozwiązań w prawym okienku.

1. W *Program.cs*zastąp cały domyślny kod następującym kodem:

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }

            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };

                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }

                // Expected Output:
                //  Tadpole  400,  Spiral
                //  Pinwheel  25,  Spiral
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }

        public class Galaxy
        {
            public string Name { get; set; }

            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }

        }

        public class GType
        {
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Naszym zamiarem jest wyświetlenie nazwy galaktyki, odległości od galaktyki i typu galaktyki na liście. Do debugowania, ważne jest, aby zrozumieć intencji kodu. Oto format jednego wiersza z listy, który chcemy pokazać na wyjściu:

    *nazwa galaktyki*, *odległość*, *typ galaktyki*.

### <a name="run-the-app"></a>Uruchomienie aplikacji

1. Naciśnij **klawisz F5** lub przycisk **Start Debugowania** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi Debugowania, znajdującym się nad edytorem kodu.

    Aplikacja uruchamia się i nie ma żadnych wyjątków wyświetlanych nam przez debugera. Jednak dane wyjściowe widoczne w oknie konsoli nie są zgodne z oczekiwaniami. Oto oczekiwane dane wyjściowe:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale widzimy to zamiast tego:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Patrząc na dane wyjściowe i nasz `GType` kod, wiemy, że jest to nazwa klasy, która przechowuje typ galaktyki. Staramy się pokazać rzeczywisty typ galaktyki (np.

### <a name="debug-the-app"></a>Debugowanie aplikacji

1. Gdy aplikacja jest nadal uruchomiona, ustaw punkt przerwania, klikając `Console.WriteLine` lewy margines obok wywołania metody w tym wierszu kodu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Po ustawieniu punktu przerwania na lewym marginesie pojawi się czerwona kropka.

    Ponieważ widzimy problem w danych wyjściowych, rozpoczniemy debugowanie, patrząc na poprzedni kod, który ustawia dane wyjściowe w debugerze.

1. Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5**).

    Aplikacja wstrzymuje się w punkcie przerwania, który można ustawić. Żółte podświetlenie wskazuje, gdzie debuger jest wstrzymany (żółta linia kodu nie została jeszcze wykonana).

1. Umieść wskaźnik `GalaxyType` myszy na zmiennej po prawej stronie, a następnie `theGalaxy.GalaxyType`po lewej stronie ikony klucza rozwiń węzeł . Zostanie wyświetlony, `GalaxyType` że `MyGType`zawiera właściwość , `Spiral`a wartość właściwości jest ustawiona na .

    ![Sprawdzanie zmiennej](../debugger/media/beginners-inspect-variable.png)

    "Spirala" jest rzeczywiście prawidłową wartością, którą spodziewałeś się wydrukować na konsoli! Dlatego jest to dobry początek, że można uzyskać dostęp do tej wartości w tym kodzie podczas uruchamiania aplikacji. W tym scenariuszu używamy niepoprawnego interfejsu API. Zobaczymy, czy możemy to naprawić podczas uruchamiania kodu w debugerze.

1. W tym samym kodzie, podczas gdy nadal debugowania, `theGalaxy.GalaxyType` umieścić kursor na końcu i zmienić go na `theGalaxy.GalaxyType.MyGType`. Chociaż można wprowadzić tę zmianę, edytor kodu pokazuje błąd wskazujący, że nie można skompilować tego kodu.

    ![Błąd składni](../debugger/media/beginners-edit.png)

1. Kliknij **pozycję Edytuj** w polu komunikatu Edytuj i **Kontynuuj.** Komunikat o błędzie jest teraz wyświetlany w oknie **Lista błędów.** Błąd wskazuje, że `'object'` nie zawiera definicji `MyGType`dla .

    ![Błąd składni](../debugger/media/beginners-no-definition.png)

    Mimo że każdą galaktykę ustawiamy `GType` za pomocą `MyGType` obiektu typu (który ma `theGalaxy` właściwość), debuger nie rozpoznaje obiektu jako obiektu typu. `GType` Co się dzieje? Chcesz przeglądać dowolny kod, który ustawia typ galaktyki. Kiedy to zrobisz, widzisz, `GType` że klasa na `MyGType`pewno ma właściwość , ale coś jest nie tak. Komunikat o `object` błędzie okazuje się być wskazówką; do interpretera języka, typ wydaje się być `object` obiektem typu zamiast `GType`obiektu typu .

1. Przeglądając kod związany z ustawieniem typu `GalaxyType` galaktyki, `Galaxy` można znaleźć `object` właściwość `GType`klasy jest określona jako zamiast .

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Zmień poprzedni kod na ten:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5),** aby ponownie skompilować kod i ponownie uruchomić komputer.

    Teraz, gdy debuger wstrzymuje się na `Console.WriteLine`, można najechać kursorem `theGalaxy.GalaxyType.MyGType`na , i zobaczyć, że wartość jest prawidłowo ustawiona.

1. Usuń punkt przerwania, klikając okrąg punktu przerwania na lewym marginesie (lub kliknij prawym przyciskiem myszy i wybierz polecenie **Punkt przerwania** > **Usuń punkt przerwania),** a następnie naciśnij **klawisz F5,** aby kontynuować.

    Aplikacja uruchamia i wyświetla dane wyjściowe. Wygląda to całkiem nieźle teraz, ale można zauważyć jedną rzecz; spodziewałeś się, że galaktyka Small Magellanic Cloud pojawi się jako galaktyka nieregularna w wyjściu konsoli, ale nie pokazuje żadnego typu galaktyki.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Ustaw punkt przerwania w tym wierszu kodu.

    ```csharp
    public GType(char type)
    ```

    Ten kod jest tam, gdzie jest ustawiony typ galaktyki, więc chcemy przyjrzeć się mu bliżej.

1. Kliknij przycisk **Uruchom ponownie** ![aplikację](../debugger/media/dbg-tour-restart.png "Uruchom aplikację RestartApp") na pasku narzędzi Debugowania **(Ctrl** + **Shift** + **F5),** aby ponownie uruchomić komputer.

    Debuger wstrzymuje w wierszu kodu, w którym można ustawić punkt przerwania.

1. Umieść wskaźnik `type` myszy na zmiennej. Zobaczysz wartość `S` (po kodzie znaku). Jesteś zainteresowany wartością `I`, ponieważ wiesz, że jest nieregularny typ galaktyki.

1. Naciśnij **klawisz F5** `type` i ponownie najedź kursorem na zmienną. Powtarzaj ten krok, aż `I` zobaczysz `type` wartość zmiennej.

    ![Sprawdzanie zmiennej](../debugger/media/beginners-inspecting-data.png)

1. Teraz naciśnij **klawisz F11** **(Debug** > **Step Into** lub Step **Into** button na pasku narzędzi Debugowania).

    **F11** zaliczki debugera (i wykonuje kod) jedną instrukcję naraz. **F10** (**Step Over**) jest podobne polecenie, i oba są bardzo przydatne podczas nauki korzystania z debugera.

1. Naciskaj **klawisz F11,** aż zatrzymasz się w wierszu `switch` kodu w instrukcji dla wartości "I". Tutaj widzisz wyraźny problem wynikający z literówki. Oczekuje się, że kod, `MyGType` aby przejść do miejsca, w którym ustawia jako nieregularny typ galaktyki, ale debuger zamiast tego pomija ten kod całkowicie i wstrzymuje w `default` sekcji `switch` instrukcji.

    ![Znajdź literówkę](../debugger/media/beginners-typo.png)

    Patrząc na kod, widzisz literówkę `case 'l'` w instrukcji. należy zastąpić wartością `case 'I'`.

1. Kliknij kod i `case 'l'` zastąp `case 'I'`go .

1. Usuń punkt przerwania, a następnie kliknij przycisk **Uruchom ponownie,** aby ponownie uruchomić aplikację.

    Błędy zostały naprawione teraz i widzisz wyjście, którego oczekujesz!

    Naciśnij dowolny klawisz, aby zakończyć aplikację.

## <a name="summary"></a>Podsumowanie

Po wyświetleniu problemu użyj debugera i [poleceń kroku,](../debugger/navigating-through-code-with-the-debugger.md) takich jak **F10** i **F11,** aby znaleźć region kodu z problemem.

> [!NOTE]
> Jeśli jest trudne do zidentyfikowania regionu kodu, w którym występuje problem, należy ustawić punkt przerwania w kodzie, który jest uruchamiany przed wystąpieniem problemu, a następnie użyć poleceń kroku, dopóki nie pojawi się manifest problemu. Można również użyć punktów śledzenia do rejestrowania [komunikatów](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) do okna **Dane wyjściowe.** Patrząc na rejestrowane wiadomości (i zauważając, które wiadomości nie zostały jeszcze zarejestrowane!), często można wyizolować region kodu z problemem. Może być konieczne powtórzenie tego procesu kilka razy, aby go zawęzić.

Po znalezieniu regionu kodu z problemem, użyj debugera do zbadania. Aby znaleźć przyczynę problemu, sprawdź kod problemu podczas uruchamiania aplikacji w debugerze:

* [Sprawdź zmienne](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) i sprawdź, czy zawierają one typ wartości, które powinny zawierać. Jeśli znajdziesz złą wartość, dowiedz się, gdzie ustawiono złą wartość (aby dowiedzieć się, gdzie ustawiono wartość, może być konieczne ponowne uruchomienie debugera, przyjrzenie się [stosowi wywołań](../debugger/how-to-use-the-call-stack-window.md)lub obu).

* Sprawdź, czy aplikacja wykonuje kod, którego oczekujesz. (Na przykład w przykładowej aplikacji spodziewaliśmy się, że kod instrukcji switch ustawi typ galaktyki na Nieregularny, ale aplikacja pominąła kod z powodu literówki).

> [!TIP]
> Używasz debugera, aby pomóc Ci znaleźć błędy. Narzędzie do debugowania można znaleźć błędy *dla Ciebie* tylko wtedy, gdy zna intencji kodu. Narzędzie może znać intencji kodu tylko wtedy, gdy, deweloper, wyrazić tę intencję. Pisanie [testów jednostkowych](../test/improve-code-quality.md) jest jak to zrobić.

## <a name="next-steps"></a>Następne kroki

W tym artykule poznaliśmy kilka ogólnych pojęć debugowania. Następnie można rozpocząć dowiedzieć się więcej na temat debugera.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
