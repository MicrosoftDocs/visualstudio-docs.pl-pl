---
title: Wprowadzenie do tworzenia gier za pomocą aparatu Unity
description: Wprowadzenie do aparatu Unity i Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: dd69156b1397ba6232d9143f54b0de1ef4506ecc
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68873449"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Wprowadzenie do tworzenia gier za pomocą aparatu Unity w Visual Studio dla komputerów Mac

Unity to aparat gier, który umożliwia tworzenie gier w programie C#. W tym instruktażu pokazano, jak rozpocząć opracowywanie i debugowanie gier Unity przy użyciu Visual Studio dla komputerów Mac i Visual Studio dla komputerów Mac narzędzia dla aparatu Unity obok środowiska Unity.

Visual Studio dla komputerów Mac Tools for Unity to bezpłatne rozszerzenie instalowane z Visual Studio dla komputerów Mac. Umożliwia ona deweloperom aparatu Unity korzystanie z funkcji produktywności Visual Studio dla komputerów Mac, w tym doskonałej obsługi technologii IntelliSense, funkcji debugowania i nie tylko.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Dowiedz się więcej na temat programowania w środowisku Unity przy użyciu Visual Studio dla komputerów Mac

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio dla komputerów Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Środowisko Unity 5.6.1 w wersji osobistej[https://store.unity.com](https://store.unity.com/)lub wyższej (wymaga konta Unity.com do uruchomienia)

## <a name="intended-audience"></a>Zamierzone odbiorcy

To laboratorium jest przeznaczone dla deweloperów C#, którzy znają, chociaż głębokie środowisko nie jest wymagane.

## <a name="task-1-creating-a-basic-unity-project"></a>Zadanie 1. Tworzenie podstawowego projektu Unity

1. Uruchom aparat **Unity**. Zaloguj się, jeśli jest to wymagane.

2. Kliknij przycisk **Nowy**.

    ![Nowy przycisk w środowisku Unity](media/unity-image1.png)

3. Ustaw **nazwę projektu** na **"UnityLab"** i wybierz pozycję **3D**. Kliknij przycisk **Tworzenie projektu**.

    ![Utwórz nowy ekran projektu](media/unity-image2.png)

4. Teraz przeglądasz domyślny interfejs Unity. Ma hierarchię sceny z obiektami gry po lewej stronie, widok 3W pustej sceny widocznej w środkowym okienku pliki projektu u dołu, a następnie Inspektor i usługi po prawej stronie. Oczywiście istnieje wiele więcej niż ten, ale te, które nie są częścią ważniejszych składników.

    ![pusty interfejs Unity](media/unity-image3.png)

5. Dla deweloperów, którzy są nowym programem Unity, wszystko, co działa w aplikacji, będzie istniało w kontekście **sceny**. Plik sceny to pojedynczy plik, który zawiera wszystkie rodzaje metadanych dotyczące zasobów używanych w projekcie dla bieżącej sceny i jej właściwości. Gdy aplikacja zostanie spakowana na platformę, utworzona aplikacja zakończy się kolekcją co najmniej jednego sceny oraz dowolnego dodawanego kodu zależnego od platformy. Projekt może mieć dowolną liczbę scen.

6. Nowa scena ma tylko aparat i światło kierunkowe. Scena wymaga, aby wszystkie elementy były widoczne, i **odbiornik audio** dla wszystkiego dźwiękowego. Te składniki są dołączone do **gry gameobject**.

7. Wybierz obiekt **Main Camera** z okienka **Hierarchia** .

    ![Obiekt Main Camera wyróżniony w okienku hierarchii](media/unity-image4.png)

8. Wybierz okienko **inspektora** z prawej strony okna, aby przejrzeć jego właściwości. Właściwości aparatu zawierają informacje o przekształceniu, tło, typ projekcji, pole widzenia i tak dalej. Składnik odbiornika audio został również dodany domyślnie, co zasadniczo renderuje dźwięk sceny z mikrofonu wirtualnego podłączonego do aparatu.

    ![okienko inspektora](media/unity-image5.png)

9. Wybierz **kierunek kierunkowego obiektu światła** . Zapewnia to jasne sceny, dzięki czemu składniki, takie jak cieniowanie, wiedzą, jak renderować obiekty.

    ![wyróżniony obiekt światła kierunku](media/unity-image6.png)

10. Użyj **inspektora** , aby zobaczyć, że zawiera on wspólne właściwości oświetlenia, takie jak typ, kolor, intensywność, typ cienia i tak dalej.

    ![spojrzenie na właściwości w okienku inspektora](media/unity-image7.png)

11. Ważne jest, aby wskazać, że projekty w środowisku Unity różnią się od ich Visual Studio dla komputerów Macych odpowiedników. Na karcie **projekt** u dołu kliknij prawym przyciskiem myszy folder **zasoby** i wybierz polecenie **Odsłoń w programie Finder**.

    ![Odsłoń w akcji kontekstu wyszukiwania](media/unity-image8.png)

12. Projekty zawierają **zasoby**, **biblioteki**, **ProjectSettings**i foldery **tymczasowe** , jak widać. Jednak tylko jeden, który jest wyświetlany w interfejsie jest folderem **zasobów** . Folder **biblioteki** to lokalna pamięć podręczna dla importowanych zasobów; zawiera wszystkie metadane dla zasobów. Folder **ProjectSettings** przechowuje ustawienia, które można skonfigurować. Folder **tymczasowy** jest używany dla plików tymczasowych z narzędzia mono i Unity podczas procesu kompilacji. Istnieje również plik rozwiązania, który można otworzyć w Visual Studio dla komputerów Mac (**UnityLab. sln** tutaj).

    ![zasoby w programie Finder](media/unity-image9.png)

13. Zamknij okno **Wyszukiwacz** i wróć do **aparatu Unity**.

14. Folder **zasobów** zawiera wszystkie zasoby — kompozycje, kod, dźwięk itp. Teraz jest ona pusta, ale każdy pojedynczy plik zostanie przeniesiony do projektu. Jest to zawsze folder najwyższego poziomu w **Edytorze aparatu Unity**. Ale zawsze należy dodawać i usuwać pliki za pośrednictwem interfejsu Unity (lub Visual Studio dla komputerów Mac) i nigdy bezpośrednio przez system plików.

    ![folder zasobów w środowisku Unity](media/unity-image10.png)

15. Program **gameobject** jest centralny do programowania w środowisku Unity, ponieważ niemal wszystko pochodzi od tego typu, w tym modele, sygnalizatory, systemy cząsteczek i tak dalej. Dodaj nowy obiekt **modułu** do sceny za pośrednictwem menu **Cube > obiektu 3D > module** .

    ![Obiekt modułu w scenie](media/unity-image11.png)

16. Zapoznaj się z właściwościami nowej **gry** i sprawdź, czy ma ona nazwę, tag, warstwę i przekształcenie. Te właściwości są wspólne dla wszystkich **GameObjects**. Ponadto do **modułu** dołączono kilka składników, aby zapewnić wymaganą funkcjonalność, w tym filtr sieci, składnik ramki i moduł renderujący.

    ![właściwości obiektu gry](media/unity-image12.png)

17. Zmień nazwę obiektu **modułu** o nazwie **"Cube"** domyślnie na **"Enemy"** . Naciśnij klawisz **Enter** , aby zapisać zmiany. Jest to moduł Enemy w naszej prostej grze.

    ![Właściwość zmiany nazwy obiektu modułu](media/unity-image13.png)

18. Dodaj kolejny obiekt **modułu** do sceny przy użyciu tego samego procesu jak powyżej, a następnie nadaj mu nazwę **"Player"** .

    ![Zmień nazwę drugiego obiektu modułu](media/unity-image14.png)

19. Oznacz również obiekt odtwarzacza **"Player"** (zobacz kontrolkę listy rozwijanej w polu Nazwa). Użyjemy tego w skrypcie Enemy, aby pomóc w znalezieniu obiektu gry odtwarzacza.

    ![tagowanie obiektu odtwarzacza](media/unity-image15.png)

20. W widoku **sceny** Przenieś obiekt odtwarzacza z obiektu Enemy wzdłuż osi z za pomocą myszy. Można poruszać się wzdłuż osi Z, zaznaczając i przeciągając moduł przez **czerwony** panel w kierunku **niebieskiego** wiersza. Ponieważ moduł znajduje się w przestrzeni 3D, ale można go przeciągnąć tylko w 2D za każdym razem, oś, na której przeciągniesz, jest szczególnie ważna.

    ![Widok sceny przedstawiający moduł](media/unity-image16.png)

21. Przenieś moduł w dół i w prawo wzdłuż osi. Spowoduje to zaktualizowanie właściwości **Transform. Position** w **Inspektorze**. Pamiętaj, aby przeciągać do lokalizacji podobnie jak pokazano w tym miejscu, aby ułatwić dalsze wykonywanie kolejnych kroków w laboratorium.

    ![Przesuwanie jednego modułu wzdłuż osi](media/unity-image17.png)

22. Teraz można dodać kod, aby uzyskać logikę Enemy, dzięki czemu będzie ona wykonywała gracz. Kliknij prawym przyciskiem myszy folder Assets w konsoli **projektu** i wybierz polecenie **Utwórz skrypt > C#** .

    ![C#Akcja kontekstu skryptu](media/unity-image18.png)

23. Nazwij nowy C# skrypt **"EnemyAI"** .

    ![C#napisy](media/unity-image19.png)

24. Aby dołączyć skrypty do obiektów gry, przeciągnij nowo utworzony skrypt do obiektu **Enemy** w okienku **Hierarchia** . Teraz obiekt będzie używać zachowań z tego skryptu.

    ![Podświetlanie pokazujący Dodawanie skryptu do obiektu gry](media/unity-image20.png)

25. Wybierz pozycję **plik > Zapisz sceny** , aby zapisać bieżącą scenę. Nadaj mu nazwę **"Moja scena"** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Zadanie 2. Praca z narzędziami Visual Studio dla komputerów Mac dla aparatu Unity

1. Najlepszym sposobem na edycję C# kodu jest użycie Visual Studio dla komputerów Mac. Środowisko Unity można skonfigurować tak, aby używało Visual Studio dla komputerów Mac jako domyślnej procedury obsługi. Wybierz pozycję **preferencje > aparatu Unity**.

2. Wybierz kartę **narzędzia zewnętrzne** . Z listy rozwijanej **Edytor skryptów zewnętrznych** wybierz pozycję **Przeglądaj** i wybierz pozycję **aplikacje/Visual Studio. aplikacja**. Alternatywnie, jeśli istnieje już opcja **programu Visual Studio** , po prostu wybierz ją.

    ![Karta narzędzia zewnętrzne w preferencjach](media/unity-image21.png)

3. Aparat Unity jest teraz skonfigurowany do używania **Visual Studio dla komputerów Mac** do edytowania skryptów. Zamknij okno dialogowe **preferencji aparatu Unity** .

    ![Visual Studio wybrane w preferencjach](media/unity-image22.png)

4. Kliknij dwukrotnie pozycję **EnemyAI.cs** , aby otworzyć ją w **Visual Studio dla komputerów Mac**.

    ![Enemy zasób wybrany w środowisku Unity](media/unity-image23.png)

5. Rozwiązanie Visual Studio jest proste. Zawiera on folder **zasobów** (taki sam, jak **Wyszukiwanie**) i utworzony wcześniej skrypt **EnemyAI.cs** . W bardziej zaawansowanych projektach hierarchia prawdopodobnie będzie wyglądać inaczej niż w środowisku Unity.

    ![Konsola rozwiązań w Visual Studio dla komputerów Mac](media/unity-image24.png)

6. **EnemyAI.cs** jest otwarty w edytorze. Skrypt początkowy zawiera tylko klasy zastępcze dla metod **Start** i **Update** .

7. Zastąp początkowy kod Enemy poniższym kodem.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Zapoznaj się z prostym zachowaniem Enemy, które jest zdefiniowane w tym miejscu. W metodzie **Start** otrzymujemy odwołanie do obiektu odtwarzacza (przez jego tag), a także jego transformację. W metodzie **Update** , która jest nazywana każdą ramką, Enemy przejdzie do obiektu odtwarzacza. Słowa kluczowe i nazwy używają kodowania kolor, aby ułatwić zrozumienie bazy kodu w Visual Studio dla komputerów Mac.

9. Zapisz zmiany w skrypcie Enemy w **Visual Studio dla komputerów Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Zadanie 3. Debugowanie projektu Unity

1. Ustaw punkt przerwania w pierwszym wierszu kodu w metodzie **Start** . Możesz kliknąć margines edytora w wierszu docelowym lub umieścić kursor w wierszu i nacisnąć klawisz **F9**.

    ![Ustawianie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image25.png)

2. Kliknij przycisk **Rozpocznij debugowanie** lub naciśnij klawisz **F5**. Spowoduje to skompilowanie projektu i dołączenie go do aparatu Unity w celu debugowania.

    ![przycisk Uruchom w programie Visual Studio dla komputerów Mac](media/unity-image26.png)

3. Wróć do **aparatu Unity** i kliknij przycisk **Uruchom** , aby rozpocząć grę.

    ![przycisk Uruchom w aparacie Unity](media/unity-image27.png)

4. Punkt przerwania powinien zostać trafiony i możesz teraz korzystać z narzędzi debugowania Visual Studio dla komputerów Mac.

    ![trafienie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image28.png)

5. Z poziomu konsoli **lokalnej** Zlokalizuj **ten** wskaźnik, który odwołuje się do obiektu **EnemyAI** . Rozwiń odwołanie i zobacz, że możesz przeglądać powiązane elementy członkowskie, takie jak **szybkość**.

    ![Konsola debugowania ustawień regionalnych w programie Visual Studio dla komputerów Mac](media/unity-image29.png)

6. Usuń punkt przerwania z metody **Start** w ten sam sposób, w jaki został dodany — przez kliknięcie go na marginesie lub zaznaczenie wiersza i naciśnięcie klawisza **F9**.

    ![trafienie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image30.png)

7. Naciśnij klawisz **F10** , aby przekroczyć pierwszy wiersz kodu, który odnajdzie obiekt Game **Player** przy użyciu tagu jako parametru.

8. Umieść kursor myszy nad zmienną **odtwarzacza** w oknie edytora kodu, aby wyświetlić jej skojarzone elementy członkowskie. Możesz nawet rozwinąć nakładkę, aby wyświetlić właściwości podrzędne.

    ![okno debugowania w edytorze programu Visual Studio dla komputerów Mac](media/unity-image31.png)

9. Naciśnij klawisz **F5** lub naciśnij przycisk **Run (Uruchom** ), aby kontynuować wykonywanie. Wróć do aparatu Unity, aby wielokrotnie widzieć moduł Enemy. Być może trzeba będzie dostosować kamerę, jeśli nie jest ona widoczna.

    ![Odtwarzanie sceny w środowisku Unity](media/unity-image32.png)

10. Przełącz się z powrotem do **Visual Studio dla komputerów Mac** i ustaw punkt przerwania w pierwszym wierszu metody **Update** . Należy ją natychmiast nacisnąć.

    ![Ustawianie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image33.png)

11. Załóżmy, że szybkość jest zbyt szybka i chcemy przetestować wpływ zmiany bez ponownego uruchamiania aplikacji. Znajdź zmienną **szybkość** w oknie **samochody** lub **Ustawienia lokalne** , a następnie zmień ją na **"10"** i naciśnij klawisz **Enter**.

    ![Dopasowywanie zmiennych w oknie zmiennych lokalnych](media/unity-image34.png)

12. Usuń punkt przerwania i naciśnij klawisz **F5** , aby wznowić wykonywanie.

13. Wróć do **aparatu Unity** , aby wyświetlić uruchomioną aplikację. Moduł Enemy jest teraz przenoszony na piątą szybkość pierwotną.

    ![okno aparatu Unity z uruchomioną aplikacją](media/unity-image35.png)

14. Zatrzymaj aplikację Unity, klikając ponownie przycisk **Odtwórz** .

    ![zatrzymywanie aplikacji aparatu Unity](media/unity-image36.png)

15. Wróć do **Visual Studio dla komputerów Mac**. Zatrzymaj sesję debugowania, klikając przycisk **Zatrzymaj** .

    ![Zatrzymywanie sesji debugowania w Visual Studio dla komputerów Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Zadanie 4: Eksplorowanie funkcji aparatu Unity w Visual Studio dla komputerów Mac

1. Visual Studio dla komputerów Mac zapewnia szybki dostęp do dokumentacji aparatu Unity w edytorze kodu. Umieść kursor w dowolnym miejscu w symbolu **Vector3** w metodzie **Update** i naciśnij pozycję **⌘ Command + '** .

    ![Wybieranie metody w edytorze programu Visual Studio dla komputerów Mac](media/unity-image38.png)

2. Zostanie otwarte nowe okno przeglądarki do dokumentacji programu **Vector3**. Zamknij okno przeglądarki, gdy zostanie spełnione.

    ![okno przeglądarki otwiera się w dokumentacji](media/unity-image39.png)

3. Visual Studio dla komputerów Mac udostępnia także pomocników do szybkiego tworzenia klas zachowań aparatu Unity. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **zasoby** i wybierz polecenie **Dodaj > nowe**działanie.

    ![Nowa akcja kontekstowa bezczynności](media/unity-image40.png)

4. Nowo utworzona klasa zawiera klasy zastępcze dla metod **Start** i **Update** . Po zamykającym nawiasie klamrowym metody **Update** zacznij pisać **"OnMouseUp"** . Podczas pisania należy zauważyć, że funkcja IntelliSense programu Visual Studio szybko zeruje się w metodzie, która ma zostać wdrożona. Wybierz ją z podanej listy autouzupełniania. Spowoduje to wypełnienie metody zastępczej, w tym wszystkich parametrów.

    ![Technologia IntelliSense w programie Visual Studio dla komputerów Mac](media/unity-image41.png)

5. Wewnątrz metody **OnMouseUp** wpisz **"Base".** Aby wyświetlić wszystkie metody podstawowe dostępne do wywołania. Można również poznać różne przeciążenia każdej funkcji przy użyciu opcji stronicowania w prawym górnym rogu okna wysuwanego IntelliSense.

    ![Eksplorowanie przeciążeń w programie Visual Studio dla komputerów Mac](media/unity-image42.png)

6. Visual Studio dla komputerów Mac umożliwia również łatwe zdefiniowanie nowych programów do cieniowania. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **zasoby** i wybierz polecenie **Dodaj > Nowy**program do cieniowania.

    ![Nowa akcja modułu cieniującego w programie Visual Studio dla komputerów Mac](media/unity-image43.png)

7. Format pliku programu do cieniowania uzyskuje pełny kolor i czcionki, aby ułatwić ich odczytywanie i zrozumienie.

    ![podświetlanie składni](media/unity-image44.png)

8. Wróć do **aparatu Unity**. Zobaczysz, że ponieważ Visual Studio dla komputerów Mac współpracuje z tym samym systemem projektu, zmiany wprowadzone w jednym miejscu są automatycznie synchronizowane z drugim. Teraz można łatwo korzystać z najlepszego narzędzia do wykonania zadania.

    ![Panel zasobów aparatu Unity](media/unity-image45.png)

## <a name="summary"></a>Podsumowanie

W tym laboratorium dowiesz się, jak rozpocząć tworzenie gry przy użyciu aparatu Unity i Visual Studio dla komputerów Mac. Zobacz [https://unity3d.com/learn](https://unity3d.com/learn) , aby dowiedzieć się więcej na temat aparatu Unity.
