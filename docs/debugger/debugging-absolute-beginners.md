---
title: Kod debugowania dla bezwzględnych początkujących
description: Jeśli debugowanie jest uruchamiane po raz pierwszy, zapoznaj się z kilkoma zasadami, które ułatwiają uruchamianie aplikacji w trybie debugowania przy użyciu Visual Studio
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee849354d82b11b8d94a737a2b546f686d04d34a
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386040"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Jak debugować dla bezwzględnych początkujących

Bez awarii kod, który piszemy jako deweloperzy oprogramowania, nie zawsze działa zgodnie z oczekiwaniami. Czasami robi to zupełnie inaczej! W takim przypadku następnym zadaniem jest ustalić, dlaczego i chociaż możemy być kuszeni, aby tylko przez wiele godzin wątlić w naszym kodzie, znacznie łatwiej i wydajniej jest używać narzędzia do debugowania lub debugera.

Niestety debuger nie jest czymś, co może w sposób magiczny ujawnić wszystkie problemy lub "usterki" w naszym kodzie. *Debugowanie* oznacza uruchamianie kodu krok po kroku w narzędziu do debugowania, Visual Studio w celu znalezienia dokładnego punktu, w którym popełniliśmy błąd programistyki. Następnie rozumiesz, jakie poprawki należy wprowadzić w kodzie, a narzędzia debugowania często umożliwiają tymczasowe zmiany, aby można było kontynuować uruchamianie programu.

Efektywne korzystanie z debugera jest również umiejętnością, która wymaga czasu i praktyki, aby się uczyć, ale ostatecznie jest podstawowym zadaniem dla każdego dewelopera oprogramowania. W tym artykule przedstawimy podstawowe zasady debugowania i przedstawimy porady, które pomogą Ci rozpocząć pracę.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnij problem, zadając sobie odpowiednie pytania

Pomaga to wyjaśnić problem, który natłokło Cię przed próbą jego rozwiązania. Oczekujemy, że masz już problem w kodzie. W przeciwnym razie nie będziesz tutaj próbować ustalić, jak go debugować. Dlatego przed rozpoczęciem debugowania upewnij się, że zidentyfikowano problem, który próbujesz rozwiązać:

* Czego oczekujesz od kodu?

* Co się stało?

    Jeśli podczas uruchamiania aplikacji wystąpił błąd (wyjątek), może to być dobrym rozwiązaniem. Wyjątkiem jest nieoczekiwane zdarzenie napotkane podczas uruchamiania kodu, zwykle błąd pewnego rodzaju. Narzędzie debugowania może przeprowadzić Cię do dokładnego miejsca w kodzie, w którym wystąpił wyjątek, i może pomóc w zbadaniu możliwych poprawek.

    Jeśli coś innego się stało, jaki jest objaw problemu? Czy podejrzewasz już, gdzie ten problem wystąpił w kodzie? Jeśli na przykład w kodzie jest wyświetlany tekst, ale tekst jest niepoprawny, oznacza to, że dane są nieprawidłowe lub kod, który ustawia wyświetlany tekst, zawiera jakiś błąd. Krok po kroku kodu w debugerze można zbadać każdą zmianę zmiennych, aby dowiedzieć się dokładnie, kiedy i jak niepoprawne wartości są przypisywane.

## <a name="examine-your-assumptions"></a>Badanie założeń

Zanim zbadasz usterkę lub błąd, pomyśl o założeniach, które sprawiły, że oczekujesz pewnego wyniku. Ukryte lub nieznane założenia mogą pomóc w zidentyfikowaniu problemu nawet wtedy, gdy patrzysz w prawo na przyczynę problemu w debugerze. Możesz mieć długą listę możliwych założeń! Oto kilka pytań, które należy zadać sobie w celu zakwestionowania założeń.

* Czy używasz odpowiedniego interfejsu API (czyli odpowiedniego obiektu, funkcji, metody lub właściwości)? Interfejs API, z których korzystasz, może nie robić tego, co myślisz. (Po przeanalizowaniu wywołania interfejsu API w debugerze jego rozwiązanie może wymagać podróży do dokumentacji w celu zidentyfikowania poprawnego interfejsu API).

* Czy używasz interfejsu API poprawnie? Być może używasz odpowiedniego interfejsu API, ale nie używasz go w odpowiedni sposób.

* Czy kod zawiera jakieś literówki? Niektóre literówki, takie jak proste błędy pisowni nazwy zmiennej, mogą być trudne do zobaczenia, szczególnie w przypadku pracy z językami, które nie wymagają deklarowania zmiennych przed ich rozpoczęciem.

* Czy w kodzie wszedliśmy do zmiany i zakładaliśmy, że nie jest ona powiązana z problemem, który widzisz?

* Czy oczekiwano, że obiekt lub zmienna będzie zawierać określoną wartość (lub określony typ wartości), która różni się od tego, co naprawdę się stało?

* Czy znasz zamiar kodu? Debugowanie kodu innej osoby jest często trudniejsze. Jeśli nie jest to Twój kod, być może trzeba będzie poświęcić czas na uczenie się dokładnie tego, co robi kod, zanim będzie można go skutecznie debugować.

    > [!TIP]
    > Podczas pisania kodu zacznij od małego kodu, który działa. (Dobry przykładowy kod jest tutaj przydatny). Czasami łatwiej jest naprawić duży lub skomplikowany zestaw kodu, zaczynając od małego fragmentu kodu, który demonstruje podstawowe zadanie, które próbujesz osiągnąć. Następnie można przyrostowo modyfikować lub dodawać kod, testując w każdym punkcie pod uwagę błędy.

Zakwestionowanie założeń może skrócić czas, który zajmuje znalezienie problemu w kodzie. Możesz również skrócić czas rozwiązywania problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Przek omiń kod w trybie debugowania, aby dowiedzieć się, gdzie wystąpił problem

Gdy zwykle uruchamiasz aplikację, błędy i niepoprawne wyniki są dostępne dopiero po uruchomieniu kodu. Program może również nieoczekiwanie zakończyć działanie, nie informując Cię o tym.

Uruchomienie aplikacji w debugerze, nazywanym również trybem debugowania, oznacza, że debuger aktywnie monitoruje wszystko, co dzieje się podczas działania programu. Umożliwia ona również wstrzymanie aplikacji w dowolnym momencie w celu zbadania jej stanu, a następnie przechodzić przez kod wiersz po wierszu, aby obserwować wszystkie szczegóły w takim stanie.

W Visual Studio tryb debugowania można wprowadzić za pomocą klawisza **F5** (lub polecenia menu Rozpocznij debugowanie debugowania lub przycisku Rozpocznij debugowanie Na pasku  >   narzędzi Debugowanie).  ![](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") Jeśli wystąpią jakieś wyjątki, Visual Studio pomocnika wyjątków pozwala uzyskać dokładne informacje o punkcie wystąpienia wyjątku i udostępnia inne przydatne informacje. Aby uzyskać więcej informacji na temat obsługi wyjątków w kodzie, zobacz [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md).

Jeśli nie otrzymasz wyjątku, prawdopodobnie wiesz, gdzie szukać problemu w kodzie. W tym miejscu używasz *punktów przerwania z* debugerem, aby mieć możliwość dokładniejszego przeanalizowania kodu. Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie Visual Studio należy wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub sekwencji, w której działa kod.

W Visual Studio można szybko ustawić punkt przerwania, klikając lewy margines obok wiersza kodu. Lub umieść kursor w wierszu i naciśnij **klawisz F9.**

Aby zilustrować te pojęcia, przejmiemy cię przez przykładowy kod, który ma już kilka usterek. Używamy języka C#, ale funkcje debugowania dotyczą języków Visual Basic, C++, JavaScript, Python i innych obsługiwanych języków. Podano również przykładowy kod Visual Basic, ale zrzuty ekranu znajdują się w języku C#.

### <a name="create-a-sample-app-with-some-bugs"></a>Tworzenie przykładowej aplikacji (z pewnymi błędami)

Następnie utworzymy aplikację, która ma kilka usterek.

1. Musisz mieć zainstalowane Visual Studio i zainstalowane obciążenie development dla wielu platform platformy **.NET** Core.

    Jeśli nie masz jeszcze zainstalowanego Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads/) Visual Studio, aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, kliknij **pozycję** Narzędzia Pobierz  >  **narzędzia i funkcje.** Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na **platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.** Wpisz **console** (konsola) w polu wyszukiwania, wybierz język **C#** **lub Visual Basic,** a następnie wybierz pozycję **Aplikacja konsolowa** dla programu .NET Core. Wybierz pozycję **Next** (Dalej). Wpisz nazwę projektu, na przykład **ConsoleApp_FirstApp** kliknij przycisk **Dalej.**

    Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual C#** lub Visual Basic wybierz pozycję Aplikacja konsolowa,  **a** następnie w środkowym okienku wybierz pozycję Aplikacja konsolowa **(.NET Core).** Wpisz nazwę, na przykład **ConsoleApp_FirstApp** i kliknij przycisk **OK.**
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **Aplikacja** konsoli dla programu .NET Core, przejdź do strony **Narzędzia** Pobierz narzędzia i funkcje , co spowoduje  >  otwarcie Instalator programu Visual Studio. Wybierz obciążenie **tworzenie aplikacji międzyplatformowych na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

    Visual Studio projekt konsoli, który zostanie wyświetlony Eksplorator rozwiązań w okienku po prawej stronie.

1. W *programie Program.cs* (lub *Program.vb)* zastąp cały kod domyślny następującym kodem. (Najpierw wybierz kartę poprawnego języka: C# lub Visual Basic).

   #### <a name="c"></a>[C#](#tab/csharp)

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

   #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    Imports System
    Imports System.Collections.Generic

    Namespace ConsoleApp_FirstApp
        Friend Class Program
            Public Shared Sub Main(ByVal args As String())
                Console.WriteLine("Welcome to Galaxy News!")
                Call IterateThroughList()
                Console.ReadKey()
            End Sub

            Private Shared Sub IterateThroughList()
                Dim theGalaxies = New List(Of Galaxy) From {
                    New Galaxy() With {
                        .Name = "Tadpole",
                        .MegaLightYears = 400,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Pinwheel",
                        .MegaLightYears = 25,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Cartwheel",
                        .MegaLightYears = 500,
                        .GalaxyType = New GType("L"c)
                    },
                    New Galaxy() With {
                        .Name = "Small Magellanic Cloud",
                        .MegaLightYears = 0.2,
                        .GalaxyType = New GType("I"c)
                    },
                    New Galaxy() With {
                        .Name = "Andromeda",
                        .MegaLightYears = 3,
                        .GalaxyType = New GType("S"c)
                    },
                    New Galaxy() With {
                        .Name = "Maffei 1",
                        .MegaLightYears = 11,
                        .GalaxyType = New GType("E"c)
                    }
                }
    
                For Each theGalaxy As Galaxy In theGalaxies
                    Console.WriteLine(theGalaxy.Name & "  " & theGalaxy.MegaLightYears & ",  " & theGalaxy.GalaxyType)
                Next

            End Sub
        End Class
    
        Public Class Galaxy
            Public Property Name As String
            Public Property MegaLightYears As Double
            Public Property GalaxyType As Object
        End Class
    
        Public Class GType
    
            Shared Operator &(ByVal left As String, ByVal right As GType) As String
                Return New String(left & right.ToString())
            End Operator
            Public Sub New(ByVal type As Char)
                Select Case type
                    Case "S"c
                        MyGType = GType.Type.Spiral
                    Case "E"c
                        MyGType = GType.Type.Elliptical
                    Case "l"c
                        MyGType = GType.Type.Irregular
                    Case "L"c
                        MyGType = GType.Type.Lenticular
                    Case Else
                End Select
    
            End Sub
    
            Private _MyGType As String
            Public Property MyGType As Object
                Get
                    Return _MyGType
                End Get
                Set(ByVal value As Object)
                    _MyGType = value.ToString()
                End Set
            End Property
    
            Private Enum Type
                Spiral
                Elliptical
                Irregular
                Lenticular
            End Enum
        End Class
    End Namespace
    ```

    ---

    Naszym celem dla tego kodu jest wyświetlenie nazwy galaxy, odległości do galaxy i typu galaxy na liście. Aby debugować, ważne jest zrozumienie intencji kodu. Oto format dla jednego wiersza z listy, który chcemy wyświetlić w danych wyjściowych:

    *galaxy name,* *distance,* *galaxy type*.

### <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij **klawisz F5** lub **przycisk Rozpocznij debugowanie,** ![aby rozpocząć](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") debugowanie na pasku narzędzi debugowania, który znajduje się powyżej edytora kodu.

    Aplikacja jest uruchamiana i debuger nie pokazuje nam żadnych wyjątków. Jednak dane wyjściowe, które zobaczysz w oknie konsoli, nie są takie, jakich oczekujesz. Oto oczekiwane dane wyjściowe:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Jednak widzimy to zamiast tego:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Patrząc na dane wyjściowe i na nasz kod, wiemy, że jest to nazwa klasy, która przechowuje `GType` typ galaxy. Próbujemy pokazać rzeczywisty typ galaxy (na przykład "Chcesz"), a nie nazwę klasy!

### <a name="debug-the-app"></a>Debugowanie aplikacji

1. Gdy aplikacja jest nadal uruchomiona, ustaw punkt przerwania, klikając lewy margines obok wywołania metody `Console.WriteLine` w tym wierszu kodu.

    #### <a name="c"></a>[C#](#tab/csharp)

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    For Each theGalaxy As Galaxy In theGalaxies
        Console.WriteLine(theGalaxy.Name & "  " & theGalaxy.MegaLightYears & ",  " & theGalaxy.GalaxyType)
    Next
    ```

    ---
    Po skonfigurowaniu punktu przerwania na lewym marginesie pojawi się czerwona kropka.

    Ponieważ w danych wyjściowych widzimy problem, rozpoczniemy debugowanie, patrząc na poprzedni kod, który ustawia dane wyjściowe w debugerze.

1. Kliknij przycisk **Restart** ![Restart App (Uruchom ponownie](../debugger/media/dbg-tour-restart.png "RestartApp") ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5).**

    Aplikacja jest wstrzymywana w ustawionym punkcie przerwania. Żółte wyróżnienie wskazuje, gdzie debuger jest wstrzymany (żółty wiersz kodu nie został jeszcze wykonany).

1. Umieść kursor na zmiennej po prawej stronie, a następnie po lewej stronie ikony `GalaxyType` klucza rozwiń pozycję `theGalaxy.GalaxyType` . Zobaczysz, `GalaxyType` że obiekt zawiera właściwość , a `MyGType` wartość właściwości jest ustawiona na `Spiral` .

    ![Zrzut ekranu Visual Studio debugera z wierszem kodu w kolorze żółtym i menu rozwiniętym poniżej właściwościGalaxy.GalaxyType na końcu wiersza.](../debugger/media/beginners-inspect-variable.png)

    "Przechowaj" to w rzeczywistości poprawna wartość, która była oczekiwana do wydrukowania w konsoli. Dlatego jest to dobry początek, że możesz uzyskać dostęp do tej wartości w tym kodzie podczas uruchamiania aplikacji. W tym scenariuszu używamy niepoprawnego interfejsu API. Zobaczymy, czy możemy rozwiązać ten problem podczas uruchamiania kodu w debugerze.

1. W tym samym kodzie, podczas debugowania, umieść kursor na końcu i `theGalaxy.GalaxyType` zmień go na `theGalaxy.GalaxyType.MyGType` . Mimo że można wprowadzić tę zmianę, edytor kodu wyświetla błąd wskazujący, że nie może skompilować tego kodu. (W Visual Basic nie zobaczysz błędu, a ta sekcja kodu działa)

    ![Zrzut ekranu Visual Studio debugera z wyróżniony na czerwono wierszem kodu oraz polem komunikatu Edytuj i kontynuuj z wybranym przyciskiem Edytuj.](../debugger/media/beginners-edit.png)

   > [!NOTE]
   > W przypadku debugowania Visual Basic przykładowego kodu pomiń kilka następnych kroków, dopóki nie zostanie zalecane kliknięcie przycisku **Uruchom ponownie** ![ponownie aplikację.](../debugger/media/dbg-tour-restart.png "RestartApp")

1. Kliknij **pozycję Edytuj** w **oknie komunikatu Edytuj i** kontynuuj. W oknie Lista błędów zostanie wyświetlony **komunikat o błędzie.** Błąd wskazuje, że wartość `'object'` nie zawiera definicji dla `MyGType` .

    ![Zrzut ekranu Visual Studio debugera z wierszem kodu wyróżniony na czerwono i oknem Listy błędów z dwoma błędami na liście.](../debugger/media/beginners-no-definition.png)

    Mimo że ustawiamy każdy galaxy obiektem typu (który ma właściwość ), debuger nie rozpoznaje obiektu `GType` `MyGType` jako obiektu typu `theGalaxy` `GType` . Co się dzieje? Chcesz sprawdzić dowolny kod, który ustawia typ galaxy. Gdy to zrobisz, zobaczysz, że klasa ma na pewno właściwość `GType` , ale coś nie jest w `MyGType` porządku. Komunikat o błędzie o błędzie wydaje się być wskazówką; dla interpretera języka typ wydaje się być obiektem typu, `object` `object` a nie obiektem typu `GType` .

1. Analizjąc kod związany z ustawianiem typu galaxy, można znaleźć, że właściwość klasy jest określona `GalaxyType` jako , a nie `Galaxy` `object` `GType` .

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Zmień powyższy kod na ten:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kliknij przycisk **Restart** ![Restart App (Uruchom](../debugger/media/dbg-tour-restart.png "RestartApp") ponownie ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5),** aby ponownie skompilować kod i uruchomić ponownie.

    Teraz, gdy debuger wstrzymuje się na , możesz zatrzymać wskaźnik myszy na i sprawdzić, czy `Console.WriteLine` `theGalaxy.GalaxyType.MyGType` wartość jest prawidłowo ustawiona.

1. Usuń punkt przerwania, klikając okrąg punktu przerwania na lewym marginesie (lub kliknij prawym przyciskiem myszy i wybierz pozycję **Punkt** przerwania Usuń punkt przerwania ), a następnie  >  naciśnij **klawisz F5,** aby kontynuować.

    Aplikacja zostanie uruchomiona i wyświetli dane wyjściowe. Teraz wygląda to całkiem dobrze, ale zauważysz jedną rzecz: Oczekiwano, że w danych wyjściowych konsoli będzie pojawiać się mały galaxy Magellanic Cloud jako nieregularna galaxy, ale w ogóle nie pokazuje on typu galaxy.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Ustaw punkt przerwania w tym wierszu kodu przed instrukcje switch (przed instrukcjeą Select w Visual Basic).

    #### <a name="c"></a>[C#](#tab/csharp)

    ```csharp
    public GType(char type)
    ```

    #### <a name="visual-basic"></a>[Visual Basic](#tab/visualbasic)

    ```vb
    Public Sub New(ByVal type As Char)
    ```

    ---

    Ten kod to miejsce, w którym ustawiono typ galaxy, więc chcemy przyjrzeć się mu bliżej.

1. Kliknij przycisk **Restart** ![Restart App (Uruchom ponownie](../debugger/media/dbg-tour-restart.png "RestartApp") ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5),** aby uruchomić ponownie.

    Debuger wstrzymuje się w wierszu kodu, w którym ustawiono punkt przerwania.

1. Umieść kursor nad `type` zmienną. Zobaczysz wartość (zgodnie `S` z kodem znaku). Interesuje Cię wartość , ponieważ wiesz, że jest to nieregularny typ `I` galaxy.

1. Naciśnij **klawisz F5** i ponownie umieść kursor `type` nad zmienną. Powtarzaj ten krok, aż zobaczysz wartość `I` w `type` zmiennej .

    ![Zrzut ekranu Visual Studio debugera z wierszem kodu w kolorze żółtym i małym oknem przedstawiającym wartość zmiennej typu jako 73 "I".](../debugger/media/beginners-inspecting-data.png)

1. Teraz naciśnij **klawisz F11** **(Debuguj**  >  **krok do** lub przycisk **Krok** do na pasku narzędzi debugowania).

    **Klawisz F11** dodaje debuger (i wykonuje kod) po jednej instrukcji na raz. **F10** **(Step Over)** to podobne polecenie, które jest bardzo przydatne podczas nauki korzystania z debugera.

1. **Naciskaj klawisz F11,** aż zatrzymasz się w wierszu kodu w instrukcji , aby uzyskać wartość `switch` "I" (instrukcja dla `Select` Visual Basic). W tym miejscu zobaczysz jasny problem wynikły z błędu pisowni. Oczekiwano, że kod przechodzi do miejsca, w którym jest ustawiany jako nieregularny typ galaxy, ale debuger zamiast tego całkowicie pomija ten kod i wstrzymuje się w sekcji instrukcji ( instrukcja w `MyGType` `default` `switch` `Else` Visual Basic).

    ![Znajdowanie literówki](../debugger/media/beginners-typo.png)

    Patrząc na kod, zobaczysz literówkę w `case 'l'` instrukcji . Powinna ona mieć wartość `case 'I'`.

1. Kliknij kod dla i `case 'l'` zastąp go . `case 'I'`

1. Usuń punkt przerwania, a następnie kliknij przycisk **Uruchom ponownie,** aby ponownie uruchomić aplikację.

    Usterki zostały naprawione teraz i zobaczysz dane wyjściowe, których oczekujesz!

    Naciśnij dowolny klawisz, aby zakończyć aplikację.

## <a name="summary"></a>Podsumowanie

Gdy zobaczysz problem, użyj debugera [](../debugger/navigating-through-code-with-the-debugger.md) i poleceń krokowych, takich jak **F10** i **F11,** aby znaleźć region kodu, w którym występuje problem.

> [!NOTE]
> Jeśli trudno jest zidentyfikować region kodu, w którym występuje problem, ustaw punkt przerwania w kodzie, który jest uruchamiany, zanim wystąpi problem, a następnie użyj poleceń krokowych, dopóki nie zobaczysz manifestu problemu. Punkty śledzenia mogą być [również służące do](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) rejestrować komunikaty w **oknie Dane** wyjściowe. Patrząc na zarejestrowane komunikaty (i patrząc, które komunikaty nie zostały jeszcze zarejestrowane!), często można odizolować region kodu z problemem. Może być konieczne powtórzenie tego procesu kilka razy, aby go zawęzić.

Po odnalezieniu regionu kodu, w którym występuje problem, użyj debugera do zbadania. Aby znaleźć przyczynę problemu, sprawdź kod problemu podczas uruchamiania aplikacji w debugerze:

* [Sprawdź zmienne i](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) sprawdź, czy zawierają one typy wartości, które powinny zawierać. Jeśli znajdziesz złą wartość, dowiedz się, gdzie została ustawiona zła wartość (aby dowiedzieć się, gdzie została ustawiona wartość, może być konieczne ponowne uruchomienie debugera, przyjrzenie się stosowi wywołań [lub](../debugger/how-to-use-the-call-stack-window.md)obu).

* Sprawdź, czy aplikacja wykonywa kod, który jest spodziewany. (Na przykład w przykładowej aplikacji oczekiwaliśmy, że kod instrukcji switch ustawi typ galaxy na nieregularny, ale aplikacja pominąła kod z powodu literówki).

> [!TIP]
> Aby znaleźć usterki, należy użyć debugera. Narzędzie debugowania może znaleźć usterki *tylko* wtedy, gdy zna zamiar kodu. Narzędzie może znać zamiar twojego kodu tylko wtedy, gdy Ty, deweloper, wyrażasz ten zamiar. Pisanie [testów jednostkowych](../test/improve-code-quality.md) to sposób, w jaki to robisz.

## <a name="next-steps"></a>Następne kroki

W tym artykule zajęliśmy się kilkoma ogólnymi pojęciami debugowania. Następnie możesz zacząć dowiedzieć się więcej o debugerze.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
