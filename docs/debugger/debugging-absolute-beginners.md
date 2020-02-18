---
title: Debugowanie kodu dla bezwzględnych początkujących
description: Jeśli debugujesz po raz pierwszy, zapoznaj się z kilkoma zasadami ułatwiającymi uruchomienie aplikacji w trybie debugowania w programie Visual Studio
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
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416400"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Jak debugować dla bezwzględnych początkujących

Bez błędów kod napisany jako deweloperzy oprogramowania nie zawsze wykonuje oczekiwane czynności. Czasami robi się coś całkowicie inaczej! Gdy tak się stanie, następnym zadaniem jest ustalenie przyczyny, a mimo to, że firma Microsoft może być skłonna do pogodzenia się w naszym kodzie, co znacznie ułatwia i wydajniej korzystać z narzędzia debugowania lub debugera.

Debuger, niestety, nie jest coś, które może w sposób magiczny ujawniać wszystkie problemy lub "usterki" w naszym kodzie. *Debugowanie* oznacza uruchamianie kodu krok po kroku w narzędziu do debugowania, takim jak Visual Studio, aby znaleźć dokładny punkt, w którym popełniono błąd programistyczny. Następnie można zrozumieć, jakie korekty należy wprowadzić w kodzie, a narzędzia debugowania często umożliwiają wprowadzanie tymczasowych zmian, aby można było kontynuować uruchamianie programu.

Efektywne korzystanie z debugera jest również umiejętnością, która wymaga czasu i ma na celu naukę, ale jest to ostatecznie podstawowe zadanie dla każdego dewelopera oprogramowania. W tym artykule wprowadzamy podstawowe zasady debugowania i podano porady ułatwiające rozpoczęcie pracy.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnij problem, pytając o odpowiednie pytania

Pomaga w wyjaśnieniu problemu, który został uruchomiony, przed podjęciem próby jego rozwiązania. Oczekujemy, że już wystąpił problem w kodzie. w przeciwnym razie nie będziesz próbować ustalić, jak debugować! Dlatego przed rozpoczęciem debugowania upewnij się, że został zidentyfikowany problem, który próbujesz rozwiązać:

* Jak oczekujesz, że Twój kod?

* Co się stało?

    Jeśli wystąpi błąd (wyjątek) podczas uruchamiania aplikacji, może to być dobry efekt. Wyjątek to nieoczekiwane zdarzenie napotkane podczas uruchamiania kodu, zazwyczaj jest to błąd pewnego rodzaju. Narzędzie debugowania może przechodzenie do dokładnego miejsca w kodzie, w którym wystąpił wyjątek, i może pomóc w zbadaniu możliwych poprawek.

    Jeśli coś innego się stało, jaki jest objaw problemu? Czy już podejrzewasz, że ten problem wystąpił w kodzie? Na przykład jeśli kod wyświetla jakiś tekst, ale tekst jest niepoprawny, wiadomo, że dane są nieprawidłowe lub kod, który ustawia wyświetlany tekst, ma jakiś błąd. Poprzez przechodzenie przez kod w debugerze można sprawdzić każdą zmianę w zmiennych, aby dokładnie odkryć, kiedy i jak są przypisywane nieprawidłowe wartości.

## <a name="examine-your-assumptions"></a>Badanie założeń

Przed zbadaniem usterki lub błędu, należy wziąć pod uwagę założenia, które wydają oczekiwany wynik. Ukryte lub nieznane założenia mogą pomóc w zidentyfikowaniu problemu nawet w przypadku poprawnego działania w debugerze. Być może masz długą listę możliwych założeń. Poniżej przedstawiono kilka pytań, które należy zadać sobie, aby zażądać założeń.

* Czy używasz prawego interfejsu API (czyli odpowiedniego obiektu, funkcji, metody lub właściwości)? Używany interfejs API może nie zrobić tego, co Twoim zdaniem. (Po sprawdzeniu wywołania interfejsu API w debugerze, jego naprawienie może wymagać przeprowadzenia podróży do dokumentacji, aby ułatwić identyfikację poprawnego interfejsu API).

* Czy używasz interfejsu API poprawnie? Być może korzystasz z odpowiedniego interfejsu API, ale nie korzystasz z niego w odpowiedni sposób.

* Czy Twój kod zawiera jakiekolwiek literówki? Niektóre literówki, takie jak proste błędy pisowni nazwy zmiennej, mogą być trudne do sprawdzenia, szczególnie podczas pracy z językami, które nie wymagają zadeklarować zmiennych przed ich użyciem.

* Czy wprowadzono zmianę w kodzie i założono, że nie jest on związany z problemem, który widzisz?

* Czy oczekujesz, że obiekt lub zmienna zawierają określoną wartość (lub określony typ wartości), która różni się od tego, co naprawdę się stało?

* Czy znasz zamiar kodu? Często trudno jest debugować kod innej osoby. Jeśli nie jest to Twój kod, możliwe, że konieczne będzie poświęcenie czasu na dokładne zapoznanie się z kodem, aby można było efektywnie debugować.

    > [!TIP]
    > Podczas pisania kodu, Rozpocznij mały i zacznij od kodu, który działa! (Dobry przykładowy kod jest przydatny w tym miejscu). Czasami łatwiej jest poprawić duży lub skomplikowany zestaw kodu, rozpoczynając od małego fragmentu kodu, który demonstruje podstawowe zadanie, które chcesz osiągnąć. Następnie można zmodyfikować lub dodać kod przyrostowo, test w każdym punkcie w poszukiwaniu błędów.

Na podstawie założeń możesz skrócić czas potrzebny na znalezienie problemu w kodzie. Możesz również skrócić czas potrzebny na rozwiązanie problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Przechodzenie przez kod w trybie debugowania w celu znalezienia miejsca wystąpienia problemu

Gdy normalnie uruchamiasz aplikację, zobaczysz błędy i nieprawidłowe wyniki tylko wtedy, gdy kod został uruchomiony. Program może również zakończyć się nieoczekiwanie, nie informując o tym, dlaczego.

Uruchamianie aplikacji w debugerze, nazywanej również *trybem debugowania*, oznacza, że debuger aktywnie monitoruje wszystko, co dzieje się w trakcie działania programu. Umożliwia ona również Wstrzymywanie aplikacji w dowolnym momencie w celu sprawdzenia jej stanu, a następnie przechodzenie do kolejnych kroków w wierszu kodu, aby obejrzeć wszystkie szczegóły w miarę ich działania.

W programie Visual Studio można przejść do trybu debugowania za pomocą klawisza **F5** (lub polecenia **Debuguj** > **Rozpocznij debugowanie** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania). W przypadku wystąpienia dowolnego wyjątku pomocnik wyjątków programu Visual Studio przeprowadzi Cię do dokładnego punktu, w którym wystąpił wyjątek i udostępnia inne przydatne informacje. Aby uzyskać więcej informacji na temat obsługi wyjątków w kodzie, zobacz [techniki debugowania i narzędzia](../debugger/write-better-code-with-visual-studio.md).

Jeśli nie otrzymano wyjątku, prawdopodobnie masz dobry pomysł na to, gdzie szukać problemu w kodzie. Jest to miejsce, w którym można używać *punktów przerwania* z debugerem, aby dać sobie możliwość dokładnego badania kodu. Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie program Visual Studio ma wstrzymywać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub obsłużyć pamięć lub sekwencję, w której uruchamiany jest kod.

W programie Visual Studio można szybko ustawić punkt przerwania, klikając na lewym marginesie obok wiersza kodu. Lub umieść kursor w wierszu i naciśnij klawisz **F9**.

Aby ułatwić zilustrowanie tych koncepcji, przeprowadzimy Cię przez przykładowy kod, który ma już kilka błędów. Korzystamy C#z programu, ale funkcje debugowania mają zastosowanie do Visual Basic C++,, JavaScript, Python i innych obsługiwanych języków.

### <a name="create-a-sample-app-with-some-bugs"></a>Tworzenie przykładowej aplikacji (z niektórymi usterkami)

Następnie utworzymy aplikację, która zawiera kilka błędów.

1. W zależności od typu aplikacji, który chcesz utworzyć, musisz mieć zainstalowany program Visual Studio i obciążenie **Programowanie aplikacji klasycznych platformy .NET** .

    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, kliknij pozycję **narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie programu **.NET Desktop Development** (lub **Programowanie dla wielu platform w środowisku .NET Core**), a następnie wybierz polecenie **Modyfikuj**.

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**. Wpisz w polu wyszukiwania **konsolę** , a następnie wybierz pozycję **Aplikacja konsolowa (.NET Core)** lub **Aplikacja konsolowa (.NET Framework)** . Wybierz pozycję **Dalej**. Wpisz nazwę projektu, na przykład **ConsoleApp-FirstApp** , a następnie kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **C#Wizualizacja**wybierz pozycję **Aplikacja konsolowa**, a następnie w środkowym okienku wybierz pozycję **Aplikacja konsolowa (.NET Framework)** lub **Aplikacja konsolowa (.NET Core)** . Wpisz nazwę, taką jak **ConsoleApp-FirstApp** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **aplikacja konsoli (.NET Framework)** lub **Aplikacja konsolowa (.NET Core)** , przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz opcję **Programowanie dla wielu platform w środowisku .NET Core** lub **środowisko programistyczne programu .NET Desktop** , a następnie wybierz polecenie **Modyfikuj**.

    Program Visual Studio tworzy projekt konsoli, który pojawia się w Eksplorator rozwiązań w okienku po prawej stronie.

1. W *program.cs*Zastąp cały kod domyślny następującym kodem:

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

    Naszym celem tego kodu jest wyświetlenie nazwy programu Galaxy, odległości od programu Galaxy i typu "wszystkie" na liście. Aby debugować, ważne jest zrozumienie intencji kodu. Oto format jednego wiersza z listy, który ma być wyświetlany w danych wyjściowych:

    *Nazwa programu Galaxy*, *odległość*, *Typ Galaxy*.

### <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **F5** lub przycisk **Rozpocznij debugowanie** ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi debugowania znajdującym się powyżej edytora kodu.

    Aplikacja zostanie uruchomiona i nie ma żadnych wyjątków pokazywanych przez debuger. Jednak dane wyjściowe wyświetlane w oknie konsoli nie są oczekiwane. Oto oczekiwane dane wyjściowe:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Jednak zamiast tego zobaczymy następujący:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Patrząc na dane wyjściowe i w naszym kodzie, wiemy, że `GType` jest nazwą klasy, w której jest przechowywany typ Galaxy. Próbujemy pokazać rzeczywisty typ Galaxy (na przykład "spirala"), a nie nazwę klasy!

### <a name="debug-the-app"></a>Debugowanie aplikacji

1. Gdy aplikacja nadal działa, ustaw punkt przerwania, klikając na lewym marginesie obok wywołania metody `Console.WriteLine` w tym wierszu kodu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Po ustawieniu punktu przerwania na lewym marginesie pojawia się czerwona kropka.

    Ponieważ widzimy problem w danych wyjściowych, rozpocznie się debugowanie, sprawdzając poprzedni kod, który ustawia dane wyjściowe w debugerze.

1. Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**).

    Aplikacja wstrzymuje się w ustawionym punkcie przerwania. Żółte wyróżnienie wskazuje, gdzie debuger jest wstrzymany (żółty wiersz kodu nie został jeszcze wykonany).

1. Umieść kursor nad zmienną `GalaxyType` po prawej stronie, a następnie po lewej stronie ikony klucz rozwiń pozycję `theGalaxy.GalaxyType`. Zobaczysz, że `GalaxyType` zawiera `MyGType`właściwości, a wartość właściwości jest ustawiona na `Spiral`.

    ![Inspekcja zmiennej](../debugger/media/beginners-inspect-variable.png)

    "Spirala" jest w rzeczywistości poprawną wartością, którą spodziewasz się wydrukować w konsoli. Dlatego warto uzyskać dostęp do tej wartości w tym kodzie podczas uruchamiania aplikacji. W tym scenariuszu używamy nieprawidłowego interfejsu API. Zobaczymy, czy możemy rozwiązać ten problem podczas uruchamiania kodu w debugerze.

1. W tym samym kodzie, podczas gdy nadal trwa debugowanie, umieść kursor na końcu `theGalaxy.GalaxyType` i zmień go na `theGalaxy.GalaxyType.MyGType`. Chociaż można wprowadzić tę zmianę, w edytorze kodu zostanie wyświetlony komunikat o błędzie informujący o tym, że nie można skompilować tego kodu.

    ![Błąd składniowy](../debugger/media/beginners-edit.png)

1. Kliknij przycisk **Edytuj** w oknie wiadomości **Edytuj i Kontynuuj** . W oknie **Lista błędów** zostanie wyświetlony komunikat o błędzie. Błąd oznacza, że `'object'` nie zawiera definicji `MyGType`.

    ![Błąd składniowy](../debugger/media/beginners-no-definition.png)

    Mimo że ustawimy każdy element Galaxy przy użyciu obiektu typu `GType` (który ma właściwość `MyGType`), debuger nie rozpoznaje obiektu `theGalaxy` jako obiektu typu `GType`. Co się dzieje? Chcesz sprawdzić kod, który ustawia typ Galaxy. Gdy to zrobisz, zobaczysz, że Klasa `GType` w nieskończoność ma właściwość `MyGType`, ale coś nie jest właściwe. Komunikat o błędzie dotyczący `object` się wyłączać jako wskazówki. do interpretera języka, typ wydaje się być obiektem typu `object`, a nie obiektem typu `GType`.

1. Przeglądając kod związany z ustawieniem typu Galaxy, znajdziesz Właściwość `GalaxyType` klasy `Galaxy` jest określony jako `object` zamiast `GType`.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Zmień poprzedni kod na następujący:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kliknij przycisk **Uruchom** ![ponownie uruchom aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**), aby ponownie skompilować kod i przeprowadzić ponowne uruchomienie.

    Teraz, gdy debuger zatrzymuje się w `Console.WriteLine`, można umieścić wskaźnik myszy nad `theGalaxy.GalaxyType.MyGType`i zobaczyć, że wartość jest prawidłowo ustawiona.

1. Usuń punkt przerwania, klikając okrąg punktu przerwania na lewym marginesie (lub kliknij prawym przyciskiem myszy i wybierz polecenie **punkt przerwania** > **Usuń punkt przerwania**), a następnie naciśnij klawisz **F5** , aby kontynuować.

    Aplikacja zostanie uruchomiona i wyświetli dane wyjściowe. Jest to bardzo dobre teraz, ale należy zauważyć, że jest to konieczne. oczekiwano, że mały Magellanic Cloud Galaxy będzie widoczny jako nieregularne oprogramowanie Galaxy w danych wyjściowych w konsoli, ale w ogóle nie pokazuje typu Galaxy.

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

    Ten kod wskazuje, że typ Galaxy jest ustawiony, więc chcemy dokładniej zapoznać się z nim.

1. Kliknij przycisk **Uruchom** ![ponownie aplikację Uruchom ponownie](../debugger/media/dbg-tour-restart.png "RestartApp") na pasku narzędzi debugowania (**Ctrl** + **SHIFT** + **F5**), aby uruchomić go ponownie.

    Debuger wstrzymuje się w wierszu kodu, w którym jest ustawiony punkt przerwania.

1. Umieść kursor nad zmienną `type`. Zobaczysz wartość `S` (po kodzie znaku). Interesuje Cię wartość `I`, ponieważ wiadomo, że jest to nieregularnego typu Galaxy.

1. Naciśnij klawisz **F5** i ponownie umieść wskaźnik myszy na zmiennej `type`. Powtórz ten krok, dopóki nie zostanie wyświetlona wartość `I` w zmiennej `type`.

    ![Inspekcja zmiennej](../debugger/media/beginners-inspecting-data.png)

1. Teraz naciśnij klawisz **F11** (**Debuguj** > **Wkrocz do** lub przycisk **wejdź do kroku** na pasku narzędzi debugowania).

    **F11** przesuwa debuger (i wykonuje kod) jedną instrukcję w danym momencie. **F10** (**Step over**) jest podobnym poleceniem i obie są niezwykle przydatne podczas uczenia się, jak korzystać z debugera.

1. Naciśnij klawisz **F11** do momentu zatrzymania wiersza kodu w instrukcji `switch` dla wartości "I". Tutaj zobaczysz wyraźny problem wynikający z błędów. Oczekiwano kodu, do którego ma nastąpić jego ustawienie `MyGType` jako nieregularnego typu Galaxy, ale debuger zamiast tego całkowicie pomija ten kod i zatrzymuje się w sekcji `default` instrukcji `switch`.

    ![Znajdź literówki](../debugger/media/beginners-typo.png)

    Patrząc na kod, zobaczysz literówkę w instrukcji `case 'l'`. należy zastąpić wartością `case 'I'`.

1. Kliknij kod dla `case 'l'` i zastąp go `case 'I'`.

1. Usuń punkt przerwania, a następnie kliknij przycisk **Uruchom ponownie** , aby ponownie uruchomić aplikację.

    Usterki zostały rozwiązane teraz i zobaczysz dane wyjściowe, których oczekujesz!

    Naciśnij dowolny klawisz, aby zakończyć aplikację.

## <a name="summary"></a>Podsumowanie

Gdy zobaczysz problem, Użyj poleceń debugera i [kroku](../debugger/navigating-through-code-with-the-debugger.md) , takich jak **F10** i **F11** , aby znaleźć region kodu z problemem.

> [!NOTE]
> Jeśli jest trudne do zidentyfikowania regionu kodu, w którym występuje problem, ustaw punkt przerwania w kodzie, który jest uruchamiany przed wystąpieniem problemu, a następnie Użyj poleceń Step do momentu wyświetlenia manifestu problemu. Możesz również użyć [punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) do rejestrowania komunikatów w oknie **danych wyjściowych** . Przeglądając zarejestrowane komunikaty (i obserwowanie, które wiadomości nie zostały jeszcze zarejestrowane), możesz często izolować region kodu z powodu problemu. Może być konieczne powtórzenie tego procesu kilka razy, aby zawęzić go.

Po znalezieniu regionu kodu z problemem Użyj debugera, aby zbadać. Aby znaleźć przyczynę problemu, sprawdź kod problemu podczas uruchamiania aplikacji w debugerze:

* [Zbadaj zmienne](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) i sprawdź, czy zawierają one typ wartości, które powinny zawierać. Jeśli znajdziesz nieprawidłową wartość, Dowiedz się, gdzie została ustawiona zła wartość (aby znaleźć miejsce ustawienia wartości, może być konieczne ponowne uruchomienie debugera, przyjrzyj się [stosowi wywołań](../debugger/how-to-use-the-call-stack-window.md)lub obu).

* Sprawdź, czy aplikacja wykonuje oczekiwany kod. (Na przykład w przykładowej aplikacji oczekujemy, że kod instrukcji switch, aby ustawić typ Galaxy na nieregularne, ale aplikacja pominął kod z powodu literówki).

> [!TIP]
> Za pomocą debugera można znaleźć błędy. Narzędzie debugowania może *znaleźć błędy tylko wtedy,* gdy znają zamiar Twojego kodu. Narzędzie może znać tylko zamiar Twojego kodu, jeśli jesteś deweloperem. W tym celu należy napisać [testy jednostkowe](../test/improve-code-quality.md) .

## <a name="next-steps"></a>Następne kroki

W tym artykule przedstawiono kilka ogólnych pojęć dotyczących debugowania. Następnie możesz zacząć dowiedzieć się więcej o debugerze.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
