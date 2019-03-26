---
title: Debugowanie kodu dla całkowicie początkujących
description: Jeśli debugujesz po raz pierwszy, zapoznaj się z pomocą techniczną firmy kilka zasad, aby uzyskać pomoc przy uruchamianiu aplikacji w trybie debugowania przy użyciu programu Visual Studio
ms.date: 07/06/2018
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d846385349ad0dbcfe60bdf9b1fd7f1b5db507f
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476049"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Jak debugować dla całkowicie początkujących

Bez błędów kod, który napiszemy deweloperów oprogramowania zawsze nie co oczekiwano mu. Czasami robi czegoś zupełnie innego! W takim przypadku kolejnym krokiem jest zorientować się, dlaczego, a firma Microsoft może wydawać się po prostu zachować muszą wpatrywać się w naszym kodzie godzin, ale jest znacznie łatwiejsze i bardziej wydajne narzędzie debugowania lub debugera.

Debuger Niestety, nie jest coś, co magiczny sposób może ujawnić wszystkie problemy lub "błędy" w naszym kodzie. *Debugowanie* oznacza, że aby uruchomić kod krok po kroku, narzędzia debugowania, takich jak Visual Studio, aby znaleźć dokładny moment, w których w przypadku popełnienia programowania. Następnie rozumiesz, jakie poprawki, należy wprowadzić w kodzie i narzędzia do debugowania umożliwiają często tymczasowo zmienić tak, aby kontynuować program.

Skutecznego korzystania z debugera jest również umiejętności, która zajmuje czas i rozwiązaniem, aby dowiedzieć się więcej, ale ostatecznie to klient jest podstawowych zadań dla każdego dewelopera oprogramowania. W tym artykule następnie możemy wprowadzić podstawowe zasady debugowania i zapewniają wskazówki ułatwiające rozpoczęcie pracy.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnienie tego problemu, zadając sobie prawo

Ułatwia ustalenie problemu, który rozwiąże przed spróbować go naprawić. Oczekujemy, że już rozwiąże problem w kodzie, w przeciwnym razie nie można tutaj próbujesz zorientować się, jak go debugować! Dlatego przed rozpoczęciem debugowania upewnij się, że zidentyfikowaliśmy problem, który próbujesz rozwiązać:

* Oczekiwań swój kod, aby zrobić?

* Co się stało zamiast?

    Po przeprowadzeniu Napotkano błąd (wyjątku) podczas uruchamiania aplikacji, które może być dobrym znakiem! Wyjątek jest nieoczekiwane zdarzenie napotkała podczas uruchamiania kodu, zazwyczaj błąd pewnego rodzaju. Narzędzie do debugowania może potrwać do dokładnie miejscu w kodzie, na którym wystąpił wyjątek i pomoże Ci zbadać możliwe poprawki.

    Jeśli zdarzyło się coś innego, jaki jest objaw programu? Czy już podejrzewasz, której wystąpienia tego problemu w kodzie? Na przykład jeśli kod zawiera jakiś tekst, ale tekst jest niepoprawny, wiesz, że Twoje dane są uszkodzone lub kod, który Ustawianie tekstu wyświetlanego ma pewnego rodzaju błędów. Poprzez krokowe wykonywanie kodu w debugerze, można sprawdzić wszystkie zmiany do zmiennych, aby dowiedzieć się, kiedy i w jaki sposób są przypisane nieprawidłowe wartości.

## <a name="examine-your-assumptions"></a>Sprawdź swoje założenia

Zanim badania, błędu lub komunikat o błędzie, należy traktować założeń, które można oczekiwać, że niektóre wynik wprowadzone. Ukryte lub nieznany założenia może utrudniać identyfikowanie problemu, nawet wtedy, gdy chcesz dokładnie przyczyny problemu w debugerze. Masz długą listę możliwych założenia! Oto kilka pytań, aby zadać sobie zażąda założeń.

* Czy używasz prawo interfejsu API (oznacza to, prawego obiektu, funkcji, metody lub właściwości) Nie może być interfejsu API, którego używasz, co uważasz, że robi. (Po badania wywołania interfejsu API w debugerze, naprawienie go może wymagać podróż do dokumentacji, aby ułatwić identyfikację poprawne interfejsu API.)

* Jest używany interfejs API prawidłowo? Może być używane po prawej stronie interfejsu API, ale nie był używany we właściwy sposób.

* Kod zawiera żadnych literówek? Niektóre błędy pisowni, takie jak proste podana przez Ciebie nazwę zmiennej może być trudne zobaczyć, szczególnie w przypadku pracy z językami, które nie wymagają zmienne być zadeklarowany przed ich używania.

* Czy wprowadzić zmiany do kodu i przyjęto założenie, że jest powiązany z problemem, który widzisz?

* Czy oczekujesz, że obiekt lub zmienna zawiera wartość (lub typ wartości) różni się od naprawdę co się stało?

* Czy wiesz, celem kod? Jest to często więcej trudne do debugowania, ktoś inny w kodzie. Jeśli nie jest kod, jest to możliwe, konieczne może być poświęcać czasu na uzyskiwanie dokładnie jakie dany kod realizuje przed można to debugować skutecznie.

    > [!TIP]
    > Podczas pisania kodu, zacznij od czegoś małego i rozpoczynać się kod, który działa! (Dobrym przykładowy kod jest przydatne w tym miejscu). Czasami jest łatwiejsze rozwiązywanie dużej lub złożonej zestawu kodu, zaczynając od małego fragmentu kodu, który demonstruje z podstawowym zadaniem, które próbujesz osiągnąć. Następnie można zmodyfikować lub przyrostowo, Dodaj kod testowania w każdym punkcie błędów.

Dzięki stawiania pytań założeń, może zmniejszyć czas potrzebny na znajdowanie problemu w kodzie. Może także zmniejszyć czas potrzebny do rozwiązania problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Przejść przez kod w trybie można znaleźć, w którym wystąpił błąd debugowania

Po uruchomieniu zwykle aplikacji, zobaczysz błędy i niepoprawne wyniki tylko wtedy, gdy kod zostało uruchomione. Program może być również nieoczekiwanego zakończenia działania bez informacją, dlaczego.

Uruchamianie aplikacji w debugerze, nazywany również *tryb debugowania*, oznacza, że debuger aktywnie monitoruje wszystko, co dzieje się jako program zostanie uruchomiony. Umożliwia on również wstrzymać aplikacji w dowolnym momencie, aby zbadać jego stan, a następnie krokowo kodu wiersz po wierszu, aby obejrzeć szczegóły każdego zdarzenia, jak to się dzieje.

W programie Visual Studio, wprowadź tryb debugowania przy użyciu **F5** (lub **debugowania** > **Rozpocznij debugowanie** polecenie menu lub **Rozpocznij debugowanie**  przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania). Jeśli wystąpią wyjątki, pomocnika wyjątków programu Visual Studio umożliwia przejście do dokładny moment, w którym wyjątek wystąpił i zawiera inne przydatne informacje. Aby uzyskać więcej informacji na temat sposobu obsługi wyjątków w kodzie, zobacz [debugowania, narzędzia i techniki](../debugger/write-better-code-with-visual-studio.md).

Jeśli nie wystąpi wyjątek, prawdopodobnie masz dobry pomysł gdzie szukać problem w kodzie. Jest to, gdzie możesz użyć *punktów przerwania* za pomocą debugera, aby przyznać sobie możliwość bardziej dokładnie sprawdź swój kod. Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie program Visual Studio wstrzymania uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych, lub zachowanie pamięci lub sekwencji, na których działa kod.

W programie Visual Studio można szybko Ustaw punkt przerwania, klikając w lewy margines obok wiersza kodu. Albo umieść kursor na wykres liniowy i naciśnij klawisz **F9**.

Aby te pojęcia, firma Microsoft przejście za pośrednictwem niektórych przykładowy kod, który ma już kilka błędów. Firma Microsoft przy użyciu języka C#, ale funkcje debugowania dotyczą Visual Basic, C++, JavaScript, Python i innych obsługiwanych języków.

### <a name="create-a-sample-app-with-some-bugs"></a>Utwórz przykładową aplikację (usterki)

Następnie zostanie utworzona aplikacja, która ma kilka błędów.

1. Konieczne jest posiadanie zainstalowanego programu Visual Studio, a następnie **programowanie aplikacji klasycznych dla platformy .NET** obciążenia lub **platformy .NET Core programowanie wieloplatformowych** zainstalowanym obciążeniem, w zależności od typu aplikacji, która ma zostać utworzony.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony, aby zainstalować go za darmo.

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, kliknij przycisk **narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** (lub **platformy .NET Core programowanie wieloplatformowych**) obciążeń, następnie wybierz **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **konsoli**, wybierz **szablony**, następnie wybierz **Utwórz nową aplikację konsoli (.NET Framework)** lub **Utwórz nową aplikację konsoli (.NET Core)**. W oknie dialogowym wybierz **Utwórz**. Wpisz nazwę, takich jak **ConsoleApp FirstApp** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okno dialogowe, w obszarze **Visual C#** , wybierz **aplikacja Konsolowa**, a następnie w środkowym okienku wybierz **aplikacji konsoli (.NET framework)**  lub **konsoli aplikacji (.NET Core)**. Wpisz nazwę, takich jak **ConsoleApp FirstApp** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz **Aplikacja konsoli (.NET Framework)** lub **Aplikacja konsoli (.NET Core)** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i Funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążenia lub **platformy .NET Core programowanie wieloplatformowych** obciążenia, wybierz **Modyfikuj**.

    Program Visual Studio tworzy projekt konsoli, która jest wyświetlana w Eksploratorze rozwiązań w okienku po prawej stronie.

1. W *Program.cs*, Zastąp domyślny kod następującym kodem:

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

    Naszym zamiarem dla tego kodu jest wyświetlić nazwę galaxy odległość galaxy i typ galaxy wszystkie listy. Aby debugować, jest ważne w celu zrozumienia intencji kodu. Oto format jeden wiersz na liście, które chcemy wyświetlić w danych wyjściowych:

    *Nazwa Galaxy*, *odległość*, *typu galaxy*.

### <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **F5** lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania znajdujące się powyżej edytora kodu.

    Aplikacja zostanie uruchomiona i nie ma żadnych wyjątków pokazano nam przez debuger. Dane wyjściowe, które są widoczne w oknie konsoli jest jednak inna niż oczekiwana. Oto oczekiwane dane wyjściowe:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale możemy zamiast tego zobacz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Trwa wyszukiwanie w danych wyjściowych oraz w naszym kodzie, wiemy, że `GType` jest nazwą klasy, która przechowuje typu galaxy. Firma Microsoft próby wyświetlenia rzeczywiste galaxy typu (na przykład "spirali"), nie nazwy klasy!

### <a name="debug-the-app"></a>Debugowanie aplikacji

1. Gdy aplikacja jest nadal uruchomione, ustaw punkt przerwania, klikając w lewy margines obok `Console.WriteLine` wywołania metody w tym wierszu kodu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Po ustawieniu punktu przerwania na lewym marginesie pojawi się czerwona kropka.

    Ponieważ widzimy problem w danych wyjściowych, firma Microsoft rozpocznie się debugowanie, analizując poprzedni kod, który ustawia dane wyjściowe w debugerze.

1. Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**).

    Wstrzymuje aplikacji w punkcie przerwania, który został ustawiony. Żółte wyróżnienie wskazuje, gdzie wstrzymana jest debugera (żółta linia kodu nie jeszcze wykonane).

1. Umieść kursor nad `GalaxyType` rozwinąć zmiennej po prawej stronie, a następnie po lewej stronie ikona klucza `theGalaxy.GalaxyType`. Zobaczysz, że `GalaxyType` zawiera właściwość `MyGType`, a wartość właściwości jest równa `Spiral`.

    ![Sprawdzanie zmiennej](../debugger/media/beginners-inspect-variable.png)

    "Spirali" jest wartością poprawne, oczekiwana do wydruku do konsoli usługi! Dlatego jest dobry początek, że masz dostęp tę wartość, w tym kodzie, gdy aplikacja działa. W tym scenariuszu używamy niepoprawne interfejsu API. Zobaczymy, jeśli firma Microsoft może rozwiązać ten problem podczas uruchamiania kodu w debugerze.

1. W ten sam kod podczas debugowania nadal, umieść kursor na końcu `theGalaxy.GalaxyType` i zmień go na `theGalaxy.GalaxyType.MyGType`. Mimo że można wprowadzić tę zmianę, Edytor kodu dowiesz się, błąd wskazujący, że nie można go skompilować ten kod.

    ![Błąd składni](../debugger/media/beginners-edit.png)

1. Kliknij przycisk **Edytuj** w **Edytuj i Kontynuuj** okno komunikatu. Zostanie wyświetlony komunikat o błędzie teraz w **lista błędów** okna. Ten błąd wskazuje, że `'object'` nie zawiera definicji `MyGType`.

    ![Błąd składni](../debugger/media/beginners-no-definition.png)

    Nawet wtedy, gdy będziemy każdego galaxy z obiektem typu `GType` (który ma `MyGType` właściwości), debuger nie może rozpoznać `theGalaxy` obiektu jako obiekt typu `GType`. Co się dzieje? Chcesz przeszukać wszelki kod, który ustawia typ galaxy. Gdy to zrobisz, zobaczysz, że `GType` klasy zdecydowanie ma właściwość `MyGType`, ale coś nie jest PRAWDA. Komunikat o błędzie `object` okaże się sugeruje; do interpretera języka typ wydaje się być obiektem typu `object` zamiast obiektu typu `GType`.

1. Wyszukiwanie za pomocą kodu powiązany z ustawianiem typu galaxy, możesz znaleźć `GalaxyType` właściwość `Galaxy` nie jest określona jako `object` zamiast `GType`.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Zmiana poprzedni kod do tego:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**) aby ponownie skompilować kod i uruchomić ponownie.

    Teraz, gdy debuger wstrzymane na `Console.WriteLine`, możesz umieścić kursor `theGalaxy.GalaxyType.MyGType`i przekonać się, że wartość jest prawidłowo ustawiona.

1. Usuń punkt przerwania, klikając koło punkt przerwania na lewym marginesie (lub kliknij prawym przyciskiem myszy i wybierz pozycję **punktu przerwania** > **Usuń punkt przerwania**), a następnie naciśnij klawisz **F5** aby kontynuować.

    Aplikacja jest uruchamiana i wyświetla dane wyjściowe. Wygląda na to bardzo dobre teraz, ale zwracasz uwagę jedno; Oczekiwano galaxy małych chmury Magellanic pojawienie się jako nieregularne galaxy w danych wyjściowych konsoli, ale pokazuje bez typu galaxy w ogóle.

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

    Ten kod jest, którego ustawiono typ galaxy chcemy Przyjrzyj się bliżej go.

1. Kliknij przycisk **ponowne uruchomienie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku na pasku narzędzi debugowania (**Ctrl** + **Shift**   +  **F5**) do ponownego uruchomienia.

    Debuger zatrzymuje się w wierszu kodu, gdzie ustawić punkt przerwania.

1. Umieść kursor nad `type` zmiennej. Zobacz wartość `S` (po kod znaku). Interesuje Cię wartość `I`, ponieważ wiadomo, który jest typem nieregularne galaxy.

1. Naciśnij klawisz **F5** i umieść kursor nad `type` zmiennej ponownie. Powtórz ten krok, aż pojawi się wartość `I` w `type` zmiennej.

    ![Sprawdzanie zmiennej](../debugger/media/beginners-inspecting-data.png)

1. Teraz naciśnij **F11** (**debugowania** > **Step Into** lub **Step Into** przycisku na pasku narzędzi debugowania).

    **F11** umożliwia przejście do (i wykonuje kod) używana jedna instrukcja w danym momencie. **F10** (**Step Over**) jest podobne polecenie, a oba są bardzo przydatne podczas nauki korzystania z debugera.

1. Naciśnij klawisz **F11** aż do zatrzymania na wiersz kodu w `switch` instrukcja dla wartości "I". W tym miejscu zobaczysz problemu wyczyść wynikające z błąd pisowni. Oczekiwano kodu, aby przejść do której ustawia `MyGType` jako nieregularnie galaxy typu, ale debuger zamiast całkowicie pomija ten kod i zatrzymuje się na `default` części `switch` instrukcji.

    ![Znajdź błąd pisowni](../debugger/media/beginners-typo.png)

    Patrząc na kod, zostanie wyświetlony błąd pisowni w `case 'l'` instrukcji. Należy go `case 'I'`.

1. Kliknij w kodzie dla `case 'l'` i zastąp go wartością `case 'I'`.

1. Usuń punkt przerwania, a następnie kliknij przycisk **ponowne uruchomienie** przycisk, aby ponownie uruchomić aplikację.

    Błędy zostały teraz usunięte i zostaną wyświetlone dane wyjściowe oczekujesz, że!

    Naciśnij dowolny klawisz, aby zakończyć aplikację.

## <a name="summary"></a>Podsumowanie

Gdy pojawi się problem, za pomocą debugera i [krok polecenia](../debugger/navigating-through-code-with-the-debugger.md) takich jak **F10** i **F11** można odnaleźć regionu kodu z tym problemem.

> [!NOTE]
> Jeśli jest trudny do identyfikowania obszar kodu, w którym występuje problem, ustaw punkt przerwania w kodzie, który jest uruchamiany przed wystąpieniem problemu, a następnie użyj polecenia krok, aż pojawi się problem manifestu. Można również użyć [punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) do rejestrowania wiadomości do **dane wyjściowe** okna. Dzięki spojrzenie na zarejestrowane komunikaty (i obserwowanie wiadomości, które nie zostały jeszcze zarejestrowane!), często można odizolować region kodu z tym problemem. Może być konieczne Powtórz ten proces kilka razy, aby zawęzić je.

Po znalezieniu region kodu z tym problemem, należy użyć debugera, aby zbadać. Aby znaleźć przyczynę problemu, należy sprawdzić kod problemu podczas uruchamiania aplikacji w debugerze:

* [Sprawdzanie zmiennych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) i sprawdź, czy zawierają one typ wartości, które powinny zawierać. Jeśli okaże się zła wartość, Dowiedz się, jeżeli Zła wartość została ustawiona (Aby dowiedzieć się, gdzie wartość została ustawiona, konieczne może być albo ponownie uruchom debuger, Przyjrzyj się [stos wywołań](../debugger/how-to-use-the-call-stack-window.md), i / lub).

* Sprawdź, czy aplikacja wykonuje kod, który powinien być. (Na przykład w przykładowej aplikacji, Oczekiwano kodu dla instrukcji switch ustawić automatyczny typ galaxy nieregularne, ale aplikacja pominięte kodu ze względu na błąd pisowni.)

> [!TIP]
> Możesz użyć debugera, aby pomóc w znalezieniu błędów. Narzędzie do debugowania można znaleźć błędy *dla Ciebie* tylko wtedy, gdy wie celem swój kod. To narzędzie można tylko zamiar kodu, jeśli informacje możesz developer, express, tym przeznaczeniem. Zapisywanie [testów jednostkowych](../test/improve-code-quality.md) się, jak to zrobić.

## <a name="next-steps"></a>Następne kroki

W tym artykule wyjaśniono kilka ogólnych pojęć debugowania. Następnie można uruchomić dowiedzieć się więcej na temat debugera.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
