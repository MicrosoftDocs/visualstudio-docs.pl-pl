---
title: Wprowadzenie rozpoczęcie tworzenia gier za pomocą aparatu Unity w programie Visual Studio dla komputerów Mac
description: Wprowadzenie do aparatu Unity i programu Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/20/2019
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: 8f14d21468336dba220a76ad8978f136d50f96f1
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836396"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Wprowadzenie rozpoczęcie tworzenia gier za pomocą aparatu Unity w programie Visual Studio dla komputerów Mac 

Unity jest aparat do tworzenia gier, który pozwala na tworzenie gier w C#. Ten poradnik pokazuje, jak rozpocząć pracę, opracowywania i debugowania gier Unity w programie Visual Studio dla komputerów Mac i Visual Studio dla komputerów Mac Tools dla rozszerzenia aparatu Unity razem środowiska Unity.

Program Visual Studio dla komputerów Mac Tools for Unity to bezpłatne rozszerzenie, instalowane z Visual Studio dla komputerów Mac. Umożliwia ona deweloperom Unity skorzystać z funkcji produktywności programu Visual Studio dla komputerów Mac, łącznie z doskonałą obsługę funkcji IntelliSense, debugowania, funkcje i nie tylko.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Dowiedz się więcej o programowaniu dla aparatu Unity za pomocą programu Visual Studio dla komputerów Mac

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio for Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition lub nowszy ([https://store.unity.com](https://store.unity.com/), wymaga konta unity.com, aby uruchomić)

## <a name="intended-audience"></a>Odbiorców

W tym laboratorium jest przeznaczona dla deweloperów, którzy są zaznajomieni z C#, ale doświadczenie nie jest wymagana.

## <a name="task-1-creating-a-basic-unity-project"></a>Zadanie 1. Tworzenie podstawowego projektu środowiska Unity

1. Uruchom **Unity**. Zarejestruj się, jeśli jest to wymagane.

2. Kliknij przycisk **Nowy**.

    ![Nowy przycisk na platformie unity](media/unity-image1.png)

3. Ustaw **Nazwa projektu** do **"UnityLab"** i wybierz **3D**. Kliknij przycisk **Tworzenie projektu**.

    ![Utwórz nowy projekt ekran](media/unity-image2.png)

4. Teraz patrzysz domyślny interfejs aparatu Unity. Hierarchia sceny przy użyciu obiektów gry w nim po lewej stronie, a widok 3W sceny puste, wyświetlany na środku, w okienku pliki projektu, na dole i Inspektor i usług, po prawej stronie. Oczywiście jest o wiele więcej do niego niż, ale są kilka składników niezwykle ważne.

    ![Interfejs puste aparatu unity](media/unity-image3.png)

5. Dla deweloperów Unity nowe, wszystko, co jest uruchamiany w aplikacji będą istnieć w kontekście **sceny**. Plik sceny jest pojedynczy plik, który zawiera szeroką gamę metadane dotyczące zasobów używanych w projekcie dla bieżącej sceny i jego właściwości. Podczas pakowania aplikacji dla platformy, wynikowa aplikacja ostatecznie jest kolekcja sceny co najmniej jeden, a także dowolny kod zależny od platformy, jakie dodasz. Może mieć dowolną liczbę sceny zgodnie z potrzebami w projekcie.

6. Nową scenę po prostu zawiera aparat fotograficzny i światła kierunkowego. Scena wymaga **aparatu** dla wszystkich elementów, które mają być wyświetlane i **odbiornika Audio** dla wszystkich elementów słyszalny. Te składniki są dołączone do **elementy GameObject**.

7. Wybierz **aparatu Main** obiektu z **hierarchii** okienka.

    ![Obiekt główny aparatu wyróżnione w okienku hierarchii](media/unity-image4.png)

8. Wybierz **Inspektor** w okienku z prawej strony okna, aby przejrzeć ich właściwości. Właściwości kamery obejmują informacje o transformacji, tło, typu projekcji, pole widzenia i tak dalej. Odbiornik Audio składnik został również dodany domyślnie, co zasadniczo renderowanie sceny dźwięku z mikrofonu wirtualnego dołączony do aparatu.

    ![Inspektor okienko](media/unity-image5.png)

9. Wybierz **światła kierunkowego** obiektu. Zapewnia to światła do sceny, dzięki czemu wiadomo, składników, takich jak programy do cieniowania sposób renderowania obiektów.

    ![Kierunek obiektu światła wyróżniony](media/unity-image6.png)

10. Użyj **Inspektor** aby zobaczyć, że zawiera on typowe właściwości oświetlenia, łącznie z typu, kolorów, intensywność, typ w tle i tak dalej.

    ![Spojrzenie na właściwości w panelu Inspektor](media/unity-image7.png)

11. Warto wspomnieć, że projekty Unity są nieco inne niż ich program Visual Studio for Mac odpowiedniki. W **projektu** karty na dole kliknij prawym przyciskiem myszy **zasoby** i wybierz polecenie **Odsłoń w programie Finder**.

    ![Odsłoń w programie finder kontekstu akcji](media/unity-image8.png)

12. Projekty zawierają **zasoby**, **biblioteki**, **ProjectSettings**, i **Temp** folderów nie jest widoczne. Jednak jest jedyną, która jest wyświetlana w interfejsie **zasoby** folderu. **Biblioteki** folder jest lokalnej pamięci podręcznej dla importowanych zasobów; przechowuje wszystkie metadane dla zasobów. **ProjectSettings** folder przechowuje ustawienia można skonfigurować. **Temp** folder jest używany dla tymczasowych plików z platformy Mono i Unity podczas procesu kompilacji. Jest również plik rozwiązania, które można otworzyć w programie Visual Studio dla komputerów Mac (**UnityLab.sln** poniżej).

    ![zasoby w programie finder](media/unity-image9.png)

13. Zamknij **wyszukiwania** okna i wrócić do **Unity**.

14. **Zasoby** folder zawiera wszystkie swoje grafikę zasoby kodu, audio, itp. Jest on pusty teraz, ale miejsce na każdy pojedynczy plik, który doprowadzić do projektu. Zawsze jest to folder najwyższego poziomu w **Unity Editor**. Jednak zawsze dodawania i usuwania plików za pośrednictwem interfejsu aparatu Unity (lub programu Visual Studio dla komputerów Mac) i nigdy nie za pośrednictwem bezpośrednio za pomocą systemu plików.

    ![folderu zasobów na platformie unity](media/unity-image10.png)

15. **Elementy GameObject** stanowi podstawę do tworzenia na platformie Unity, prawie wszystko, co wynika z tego typu, w tym modele, światła, układy cząsteczek i tak dalej. Dodaj nową **modułu** obiektu do sceny za pośrednictwem **elementy GameObject > obiektu 3D > modułu** menu.

    ![obiekt modułu w scenie](media/unity-image11.png)

16. Szybko wyświetlić właściwości nowej **elementy GameObject** i zobaczyć, że ma nazwę, tagów, warstwy i przekształcania. Te właściwości są wspólne dla wszystkich **GameObjects**. Ponadto kilka składników zostały dołączone do **modułu** zapewnienie potrzebne w tym funkcje siatki filtru, pole collider i renderowania.

    ![właściwości obiektu gry](media/unity-image12.png)

17. Zmień nazwę **modułu** obiektu, który ma taką nazwę **"Module"** domyślnie do **"Wroga"** . Upewnij się, że naciśnij **Enter** można zapisać zmiany. Są to przeciwnika modułu w naszym prostej grze.

    ![właściwości Zmień nazwę obiektu modułu](media/unity-image13.png)

18. Dodaj kolejną **modułu** obiektu do sceny, przy użyciu tego samego procesu jak powyżej, a nazwą tego jednego **"Player"** .

    ![Zmień nazwę drugiego obiektu modułu](media/unity-image14.png)

19. Tag obiektu player **"Player"** również (zobacz **Tag** lista rozwijana tuż poniżej pola nazwy). Użyjemy w skrypcie przeciwnika do lokalizowania obiektu gry odtwarzacza.

    ![znakowanie obiektu player](media/unity-image15.png)

20. W **sceny** wyświetlanie, Przenieś obiekt player od obiektu przeciwnika wzdłuż osi Z, za pomocą myszy. Można przenieść wzdłuż osi Z, zaznaczając i przeciągając modułu przez jego **czerwony** panelu kierunku **niebieski** wiersza. Ponieważ moduł znajduje się w przestrzeni 3D, ale można tylko wtedy można przeciągnąć w 2D każdorazowo, osi, na którym możesz przeciągnąć jest szczególnie ważne.

    ![Moduł wyświetlanie widoku sceny](media/unity-image16.png)

21. Przenieś modułu w dół i w prawo, wzdłuż osi. Spowoduje to zaktualizowanie **Transform.Position** właściwość **Inspektor**. Pamiętaj przeciągnąć do lokalizacji, podobnie jak co pokazuje, w tym miejscu ułatwiają dalszych krokach w środowisku laboratoryjnym.

    ![Przenoszenie jeden moduł wzdłuż osi](media/unity-image17.png)

22. Teraz możesz dodać działał kod służący do dysku przeciwnika logiki tak, aby go wykonuje odtwarzacza. Kliknij prawym przyciskiem myszy **zasoby** folderu w **projektu** konsoli, a następnie wybierz pozycję **Utwórz > C# skryptu**.

    ![C#Akcja kontekstu skryptu](media/unity-image18.png)

23. Nadaj nazwę nowej C# skryptu **"EnemyAI"** .

    ![Skrypt języka C#](media/unity-image19.png)

24. Aby dołączyć skryptów obiektów gry, przeciągnij nowo utworzony skrypt na **wroga** obiektu **hierarchii** okienko. Ten obiekt będzie korzystał zachowania tego skryptu.

    ![Wyróżnianie przedstawiający Dodawanie skryptu do obiektu gry](media/unity-image20.png)

25. Wybierz **Plik > Zapisz sceny** można zapisać bieżącej sceny. Nadaj mu nazwę **"MyScene"** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Zadanie 2. Praca z programem Visual Studio dla komputerów Mac Tools for Unity

1. Najlepszym sposobem, aby edytować C# kodu jest użycie programu Visual Studio dla komputerów Mac. Można skonfigurować Unity używać programu Visual Studio dla komputerów Mac jako jego domyślny program obsługi. Wybierz **Unity > Preferencje**.

2. Wybierz **zewnętrznych narzędzi** kartę. Z **Edytor skryptów zewnętrznych** listy rozwijanej wybierz **Przeglądaj** i wybierz **Studio.app aplikacji/Visual**. Alternatywnie Jeśli istnieje już **programu Visual Studio** , po prostu wybierz, które.

    ![narzędzia zewnętrzne karty w preferencji](media/unity-image21.png)

3. Unity jest teraz skonfigurowane do użycia **programu Visual Studio dla komputerów Mac** edycji skryptów. Zamknij **preferencje Unity** okna dialogowego.

    ![Program Visual Studio w preferencjach zaznaczona](media/unity-image22.png)

4. Kliknij dwukrotnie **EnemyAI.cs** aby otworzyć go w **programu Visual Studio dla komputerów Mac**.

    ![Zasób przeciwnika wybrane na platformie unity](media/unity-image23.png)

5. Rozwiązanie programu Visual Studio jest bardzo proste. Zawiera on **zasoby** folder (taka sama jak jedną **wyszukiwania**) i **EnemyAI.cs** skrypt utworzony wcześniej. W bardziej zaawansowanych projektów hierarchii będzie prawdopodobnie wyglądają inaczej niż to, co widać na platformie Unity.

    ![Konsola rozwiązań w programie Visual Studio dla komputerów Mac](media/unity-image24.png)

6. **EnemyAI.cs** jest otwarty w edytorze. Początkowego skryptu po prostu zawiera klasy zastępcze dla **Start** i **aktualizacji** metody.

7. Zastąp kod początkowy przeciwnika poniższy kod.

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

8. Przyjrzyj się szybkie proste przeciwnika zachowanie, która jest zdefiniowana w tym miejscu. W **Start** metody, możemy uzyskać odwołanie do obiektu player (po jego znaczniku), oraz jego **Przekształcanie**. W **aktualizacji** metody, która jest wywoływana w każdej klatce, wroga zostaną przeniesione do obiektu player. Słowa kluczowe i nazwy używają kodowanie kolorów, aby ułatwić zrozumienie bazy kodu w programie Visual Studio dla komputerów Mac.

9. Zapisz zmiany przeciwnika skryptu w **programu Visual Studio dla komputerów Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Zadanie 3. Debugowanie projektu środowiska Unity

1. Ustaw punkt przerwania w pierwszym wierszu kodu w **Start** metody. Możesz kliknąć przycisk marginesu edytora w lokalizacji kursora wiersza lub miejsca docelowego wiersza, a następnie naciśnij klawisz **F9**.

    ![Ustawianie punktu przerwania w programie visual studio dla komputerów mac](media/unity-image25.png)

2. Kliknij przycisk **Rozpocznij debugowanie** przycisk lub naciśnij klawisz **F5**. Spowoduje to skompilować projekt i Dołącz do aparatu Unity, do debugowania.

    ![przycisk Start w programie visual studio dla komputerów mac](media/unity-image26.png)

3. Wróć do **Unity** i kliknij przycisk **Uruchom** przycisk, aby rozpocząć grę.

    ![przycisk uruchamiania na platformie unity](media/unity-image27.png)

4. Punkt przerwania powinien trafiony i można teraz używać programu Visual Studio dla komputerów Mac tools debugowania.

    ![punkt przerwania w programie visual studio dla komputerów mac](media/unity-image28.png)

5. Z **lokalne** konsoli, odszukaj **to** wskaźnika, który odwołuje się **EnemyAI** obiektu. Rozwiń węzeł odwołania i zobacz przeglądać skojarzonych elementów członkowskich, takich jak **szybkość**.

    ![lokalne debugowanie konsoli w programie visual studio dla komputerów mac](media/unity-image29.png)

6. Usuń punkt przerwania z **Start** metoda taki sam sposób, który był dodane przez kliknięcie go na marginesie albo wybranie wiersza i naciśnij klawisz **F9**.

    ![punkt przerwania w programie visual studio dla komputerów mac](media/unity-image30.png)

7. Naciśnij klawisz **F10** do Przekrocz pierwszy wiersz kodu, który umożliwia znalezienie **Player** obiektu gry przy użyciu tagu jako parametr.

8. Umieść kursor myszy nad **player** zmiennej w ramach okna edytora kodu, aby wyświetlić jego składowe skojarzone. Można nawet rozwinąć nakładki, aby wyświetlić właściwości podrzędnej.

    ![debugowanie w oknie programu visual studio dla komputerów mac edytora](media/unity-image31.png)

9. Naciśnij klawisz **F5** lub naciśnij **Uruchom** przycisk, aby kontynuować wykonywanie. Powrót do aparatu Unity, aby zobaczyć moduł przeciwnika wielokrotnie podejście modułu odtwarzacza. Może być konieczne dostosowanie kamery, jeśli nie jest widoczny.

    ![Scena odtwarzanie na platformie unity](media/unity-image32.png)

10. Przejdź z powrotem do **programu Visual Studio dla komputerów Mac** i ustaw punkt przerwania w pierwszym wierszu **aktualizacji** metody. Powinien być trafień natychmiast.

    ![ustawienie punktu przerwania w programie visual studio dla komputerów mac](media/unity-image33.png)

11. Załóżmy, że prędkość jest za duża i chcemy sprawdzić wpływ zmiany bez ponownego uruchamiania aplikacji. Znajdź **szybkość** zmiennej w ramach **Autos** lub **lokalne** okna, a następnie zmień jego **"10"** i naciśnij klawisz **Enter** .

    ![Dostosowywanie zmienne w oknie zmienne lokalne](media/unity-image34.png)

12. Usuń punkt przerwania, a następnie naciśnij klawisz **F5** można wznowić wykonywania.

13. Wróć do **Unity** Aby wyświetlić uruchomioną aplikację. Przeciwnika modułu jest przenoszona na piątej szybkość, oryginalnym.

    ![Okno Unity z uruchomioną aplikacją](media/unity-image35.png)

14. Zatrzymywanie aplikacji platformy Unity, klikając **Odtwórz** ponownie przycisk.

    ![Trwa zatrzymywanie aplikacji unity](media/unity-image36.png)

15. Wróć do **programu Visual Studio dla komputerów Mac**. Zatrzymaj sesję debugowania, klikając **zatrzymać** przycisku.

    ![zatrzymywanie sesji debugowania w programie Visual Studio dla komputerów Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Zadanie 4. Poznawanie funkcji aparatu Unity w programie Visual Studio dla komputerów Mac

1. Program Visual Studio for Mac zapewnia szybki dostęp do dokumentacji aparatu Unity w edytorze kodu. Umieść kursor w jakimś miejscu w **Vector3** symboli w ramach **aktualizacji** metodę i naciśnij klawisz **⌘ polecenia + "** .

    ![Wybieranie metody w programie visual studio dla komputerów mac edytora](media/unity-image38.png)

2. Nowe okno przeglądarki otwiera się z dokumentacją dotyczącą **Vector3**. Zamknij okno przeglądarki, jeśli jest spełniony.

    ![zostanie otwarte okno przeglądarki w dokumentacji](media/unity-image39.png)

3. Visual Studio dla komputerów Mac udostępnia również niektóre pomocnicy do szybkiego tworzenia klas zachowanie aparatu Unity. Z **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zasoby** i wybierz **Dodaj > Nowy element MonoBehaviour**.

    ![Nowa akcja kontekstu obiekt monobehaviour](media/unity-image40.png)

4. Nowo utworzony klasa udostępnia wycinki **Start** i **aktualizacji** metody. Po zamykającym nawiasem klamrowym **aktualizacji** metody, zacznij pisać **"onmouseup"** . Podczas wpisywania, zwróć uwagę, że funkcja IntelliSense programu Visual Studio szybko zero metody, które zamierzasz wdrożyć. Wybierz go z listy autouzupełniania podana. Jego wypełni szkieletu metody dla Ciebie, uwzględniając wszelkie parametry.

    ![funkcja IntelliSense w programie visual studio dla komputerów mac](media/unity-image41.png)

5. Wewnątrz **OnMouseUp** metoda, typ **"podstawowe".** Aby wyświetlić wszystkie dostępne do wywołania metody podstawowej. Możesz też zapoznać się z innego przeciążenia każdej funkcji przy użyciu opcji stronicowania w prawym górnym rogu wysuwane okno technologii IntelliSense.

    ![Eksplorowanie przeciążenia w programie visual studio dla komputerów mac](media/unity-image42.png)

6. Program Visual Studio for Mac umożliwia także łatwo definiować nowych programów do cieniowania. Z **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zasoby** i wybierz **Dodaj > Nowy element Shader**.

    ![Nowa akcja programu do cieniowania w programie visual studio dla komputerów mac](media/unity-image43.png)

7. Format pliku programu do cieniowania pobiera pełnego koloru i czcionki traktowania, aby ułatwić do odczytania i zrozumienia.

    ![Wyróżnianie składni](media/unity-image44.png)

8. Wróć do **Unity**. Zobaczysz, że od czasu działania programu Visual Studio dla komputerów Mac przy użyciu tego samego systemu projektu, zmiany wprowadzone w dowolnym miejscu są automatycznie synchronizowane razem z innymi. Teraz jest łatwe do zawsze przy użyciu najlepszych narzędzi dla zadania.

    ![panel zasobów aparatu Unity](media/unity-image45.png)

## <a name="summary"></a>Podsumowanie

W tym środowisku laboratoryjnym wyjaśniono sposób rozpoczynania tworzenia gier dzięki aparatowi Unity i programu Visual Studio dla komputerów Mac. Zobacz [ https://unity3d.com/learn ](https://unity3d.com/learn) Aby dowiedzieć się więcej na temat aparatu Unity.
