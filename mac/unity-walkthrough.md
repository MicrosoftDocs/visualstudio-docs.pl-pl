---
title: Wprowadzenie do tworzenia gier za pomocą platformy Unity
description: Wprowadzenie do unity i programu Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: c25df777a9af10859c70741a78c880a57c6f5b8e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984797"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Wprowadzenie do tworzenia gier z unity w programie Visual Studio dla komputerów Mac

Unity to silnik gry, który umożliwia tworzenie gier w języku C#. W tym przewodniku pokazano, jak rozpocząć tworzenie i debugowanie gier Unity przy użyciu programu Visual Studio dla komputerów Mac i visual studio dla komputerów Mac Tools for Unity rozszerzenie obok środowiska Unity.

Visual Studio for Mac Tools for Unity to bezpłatne rozszerzenie zainstalowane w programie Visual Studio dla komputerów Mac. Umożliwia deweloperom Unity korzystanie z funkcji zwiększających produktywność programu Visual Studio dla komputerów Mac, w tym doskonałej obsługi intellisense, funkcji debugowania i innych.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Dowiedz się więcej o rozwoju unity w programie Visual Studio dla komputerów Mac

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio dla[https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac)komputerów Mac ( )
- Unity 5.6.1 Personal Edition[https://store.unity.com](https://store.unity.com/)lub nowsza (, wymaga unity.com konta do uruchomienia)

## <a name="intended-audience"></a>Docelowi odbiorcy

To laboratorium jest przeznaczone dla deweloperów, którzy są zaznajomieni z języka C#, chociaż głębokie doświadczenie nie jest wymagane.

## <a name="task-1-creating-a-basic-unity-project"></a>Zadanie 1: Tworzenie podstawowego projektu Unity

1. Uruchom **Unity**. Zaloguj się, jeśli chcesz.

2. Kliknij **pozycję Nowy**.

    ![Nowy przycisk w jedności](media/unity-image1.png)

3. Ustaw **nazwę projektu** na **"UnityLab"** i wybierz **opcję 3D**. Kliknij **pozycję Utwórz projekt**.

    ![tworzenie nowego ekranu projektu](media/unity-image2.png)

4. Teraz patrzysz na domyślny interfejs Unity. Ma hierarchię scen z obiektami gry po lewej stronie, widok 3D pustej sceny pokazany w środku, okienko plików projektu na dole oraz inspektor i usługi po prawej stronie. Oczywiście, jest o wiele więcej niż to, ale to kilka z ważniejszych elementów.

    ![pusty interfejs jedności](media/unity-image3.png)

5. Dla deweloperów nowych w Unity wszystko, co działa w aplikacji będzie istnieć w kontekście **sceny**. Plik sceny to pojedynczy plik zawierający wszelkiego rodzaju metadane dotyczące zasobów używanych w projekcie dla bieżącej sceny i jego właściwości. Po spakowaniu aplikacji dla platformy wynikowa aplikacja będzie w końcu jest zbiorem jednej lub więcej scen, a także każdy kod zależny od platformy, który zostanie dodany. W projekcie można mieć dowolną liczbę scen.

6. Nowa scena ma tylko kamerę i światło kierunkowe. Scena wymaga **kamery,** aby wszystko było widoczne, a **odbiornika audio,** aby wszystko było słyszalne. Składniki te są dołączone do **GameObject**.

7. Wybierz obiekt **Aparat główny** z **okienka Hierarchia.**

    ![główny obiekt kamery wyróżniony w okienku hierarchii](media/unity-image4.png)

8. Wybierz okienko **Inspektora** z prawej strony okna, aby przejrzeć jego właściwości. Właściwości kamery obejmują informacje o transformacji, tło, typ projekcji, pole widzenia itd. Domyślnie dodano również komponent Audio Listener, który zasadniczo renderuje dźwięk sceny z wirtualnego mikrofonu podłączonego do kamery.

    ![okienko inspektora](media/unity-image5.png)

9. Wybierz obiekt **Światło kierunkowe.** Zapewnia to światło do sceny, dzięki czemu składniki, takie jak moduły cieniowania, wiedzą, jak renderować obiekty.

    ![obiekt światła kierunku podświetlony](media/unity-image6.png)

10. Użyj **Inspektora,** aby zobaczyć, że zawiera typowe właściwości oświetlenia, w tym typ, kolor, intensywność, typ cienia i tak dalej.

    ![patrząc na właściwości w okienku inspektora](media/unity-image7.png)

11. Należy podkreślić, że projekty w unity różnią się nieco od ich odpowiedników programu Visual Studio dla komputerów Mac. Na karcie **Projekt** u dołu kliknij prawym przyciskiem myszy folder **Zasoby** i wybierz polecenie **Pokaż w finderze**.

    ![ujawnić w akcji kontekstu findera](media/unity-image8.png)

12. Projekty zawierają **zasoby,** **bibliotekę,** **ustawienia projektów**i foldery **Temp,** jak widać. Jednak jedynym, który pojawia się w interfejsie jest **folder Zasoby.** Folder **Biblioteka** jest lokalną pamięcią podręczną importowanych zasobów; zawiera wszystkie metadane dla zasobów. Folder **ProjectSettings** przechowuje ustawienia, które można skonfigurować. Temp **Temp** folder jest używany dla plików tymczasowych z Mono i Unity podczas procesu kompilacji. Istnieje również plik rozwiązania, który można otworzyć w programie Visual Studio dla komputerów Mac **(UnityLab.sln** tutaj).

    ![aktywa w finderze](media/unity-image9.png)

13. Zamknij okno **Finder** i wróć do **Unity**.

14. Folder **Zasoby** zawiera wszystkie zasoby-art, kod, dźwięk, itp. Teraz jest pusty, ale każdy plik, który wnosisz do projektu, trafi tutaj. Jest to zawsze folder najwyższego poziomu w **Edytorze Unity**. Ale zawsze dodawać i usuwać pliki za pośrednictwem interfejsu Unity (lub Visual Studio dla komputerów Mac) i nigdy za pośrednictwem systemu plików bezpośrednio.

    ![folder zasobów w jedności](media/unity-image10.png)

15. **GameObject** ma kluczowe znaczenie dla rozwoju w Unity, ponieważ prawie wszystko pochodzi od tego typu, w tym modele, światła, systemy cząstek i tak dalej. Dodaj nowy obiekt **cube** do sceny za pomocą menu **GameObject > 3D Object > Cube.**

    ![obiekt sześcianu w scenie](media/unity-image11.png)

16. Przyjrzyj się szybko właściwościom nowego **gameobject i** zobacz, że ma nazwę, znacznik, warstwę i transformację. Te właściwości są wspólne dla wszystkich **GameObjects**. Ponadto kilka składników zostały dołączone do **modułu,** aby zapewnić potrzebne funkcje, w tym filtr siatki, zderzacz pole i moduł renderowania.

    ![właściwości obiektu gry](media/unity-image12.png)

17. Zmień nazwę obiektu **Cube,** który ma domyślnie nazwę **"Cube",** na **"Enemy".** Pamiętaj, aby nacisnąć klawisz **Enter,** aby zapisać zmianę. To będzie kostka wroga w naszej prostej grze.

    ![właściwość zmiany nazwy obiektu modułu](media/unity-image13.png)

18. Dodaj kolejny obiekt **Cube** do sceny przy użyciu tego samego procesu, co powyżej, i nazwij ten **"Player"**.

    ![zmienianie nazwy drugiego obiektu modułu](media/unity-image14.png)

19. Oznacz obiekt gracza **"Player"** (zobacz Sterowanie rozwijane **tagiem** tuż pod polem nazwy). Użyjemy tego w skrypcie wroga, aby pomóc zlokalizować obiekt gry gracza.

    ![tagowanie obiektu odtwarzacza](media/unity-image15.png)

20. W widoku **Scena** odsuń obiekt gracza od obiektu przeciwnika wzdłuż osi Z za pomocą myszy. Można poruszać się wzdłuż osi Z, zaznaczając i przeciągając sześcian przez **czerwony** panel w kierunku **niebieskiej** linii. Ponieważ sześcian żyje w przestrzeni 3D, ale można go przeciągać tylko w 2D za każdym razem, oś, na której przeciągasz, jest szczególnie ważna.

    ![widok sceny z modułem](media/unity-image16.png)

21. Przesuń kostkę w dół i w prawo wzdłuż osi. Spowoduje to zaktualizowanie właściwości **Transform.Position** w **inspektorze**. Pamiętaj, aby przeciągnąć do lokalizacji podobne do tego, co pokazano tutaj, aby ułatwić późniejsze kroki w laboratorium.

    ![przesuwanie jednej kostki wzdłuż osi](media/unity-image17.png)

22. Teraz możesz dodać kod, aby napędzać logikę wroga, aby ścigał gracza. Kliknij prawym przyciskiem myszy folder **Zasoby** w konsoli **Projektu** i wybierz polecenie **Utwórz > skryptu C#.**

    ![Akcja kontekstu skryptu języka C#](media/unity-image18.png)

23. Nazwij nowy skrypt C# **"EnemyAI"**.

    ![Skrypt języka C#](media/unity-image19.png)

24. Aby dołączyć skrypty do obiektów gry, przeciągnij nowo utworzony skrypt na obiekt **Enemy** w okienku **Hierarchia.** Teraz ten obiekt będzie używać zachowań z tego skryptu.

    ![podświetlanie przedstawiające dodawanie skryptu do obiektu gry](media/unity-image20.png)

25. Wybierz **pozycję Plik > Zapisz sceny,** aby zapisać bieżącą scenę. Nazwij go **"MyScene"**.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Zadanie 2: Praca z programem Visual Studio dla komputerów Mac Tools for Unity

1. Najlepszym sposobem edycji kodu języka C# jest użycie programu Visual Studio dla komputerów Mac. Można skonfigurować Unity używać programu Visual Studio dla komputerów Mac jako jego domyślnego programu obsługi. Wybierz **pozycję Jedność > preferencje**.

2. Wybierz kartę **Narzędzia zewnętrzne.** Z listy rozwijanej **Edytor skryptów zewnętrznych** wybierz pozycję Przeglądaj i wybierz pozycję **Aplikacje/Visual Studio.app**. **Browse** Alternatywnie, jeśli istnieje już opcja **programu Visual Studio,** po prostu wybierz tę opcję.

    ![Karta narzędzia zewnętrzne w preferencjach](media/unity-image21.png)

3. Unity jest teraz skonfigurowany do używania **programu Visual Studio dla komputerów Mac** do edycji skryptów. Zamknij okno dialogowe **Preferencje jedności.**

    ![Visual Studio wybrane w preferencjach](media/unity-image22.png)

4. Kliknij dwukrotnie **EnemyAI.cs,** aby otworzyć go w **programie Visual Studio dla komputerów Mac**.

    ![Wrogi zasób wybrany w jedności](media/unity-image23.png)

5. Rozwiązanie programu Visual Studio jest proste. Zawiera folder **Zasoby** (ten sam z **Findera)** i **skrypt EnemyAI.cs** utworzony wcześniej. W bardziej zaawansowanych projektach hierarchia będzie prawdopodobnie wyglądać inaczej niż to, co widzisz w Unity.

    ![Podkładka rozrachowa w programie Visual Studio dla komputerów Mac](media/unity-image24.png)

6. **EnemyAI.cs** jest otwarty w edytorze. Skrypt początkowy zawiera tylko wycinki dla **startu** i **aktualizacji** metod.

7. Wymień początkowy kod wroga na poniższy kod.

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

8. Przyjrzyj się szybko prostemu zachowaniu wroga, które jest tutaj zdefiniowane. W **Start** metody, otrzymujemy odniesienie do obiektu gracza (przez jego tag), jak również jego **przekształcenie**. W metodzie **Aktualizacja,** która nazywa się każdą klatką, wróg będzie poruszał się w kierunku obiektu gracza. Słowa kluczowe i nazwy używają kodowania kolorami, aby ułatwić zrozumienie bazy kodu w programie Visual Studio dla komputerów Mac.

9. Zapisz zmiany w skrypcie przeciwnika w **programie Visual Studio dla komputerów Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Zadanie 3: Debugowanie projektu Unity

1. Ustaw punkt przerwania w pierwszym wierszu kodu w **Start** metody. Możesz kliknąć margines edytora w wierszu docelowym lub umieścić kursor na wierszu i nacisnąć **klawisz F9**.

    ![ustawianie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image25.png)

2. Kliknij przycisk **Rozpocznij debugowanie** lub naciśnij klawisz **F5**. Spowoduje to zbudowanie projektu i dołączyć go do Unity do debugowania.

    ![przycisk start w programie Visual Studio dla komputerów Mac](media/unity-image26.png)

3. Wróć do **Unity** i kliknij przycisk **Uruchom,** aby rozpocząć grę.

    ![przycisk uruchom w jedności](media/unity-image27.png)

4. Punkt przerwania powinien zostać trafiony i można teraz użyć narzędzia do debugowania programu Visual Studio dla komputerów Mac.

    ![breakpoint hit w programie Visual Studio dla komputerów Mac](media/unity-image28.png)

5. W panelu **Locals** znajdź **ten** wskaźnik, który odwołuje się do obiektu **EnemyAI.** Rozwiń odwołanie i zobacz, że możesz przeglądać skojarzone elementy członkowskie, takie jak **Prędkość**.

    ![lokalni debugowanie pad w visual studio dla mac](media/unity-image29.png)

6. Usuń punkt przerwania z **Start** metody w taki sam sposób, w jaki został dodany, klikając go na marginesie lub wybierając wiersz i naciśnij **klawisz F9**.

    ![breakpoint hit w programie Visual Studio dla komputerów Mac](media/unity-image30.png)

7. Naciśnij **klawisz F10,** aby przejść przez pierwszy wiersz kodu, który znajduje obiekt gry **Player** przy użyciu tagu jako parametru.

8. Najedź kursorem myszy na zmienną **odtwarzacza** w oknie edytora kodu, aby wyświetlić skojarzonych z nią członków. Można nawet rozwinąć nakładkę, aby wyświetlić właściwości podrzędne.

    ![debugowanie w programie Visual Studio dla edytora mac](media/unity-image31.png)

9. Naciśnij **klawisz F5** lub naciśnij przycisk **Uruchom,** aby kontynuować wykonywanie. Wróć do Jedności, aby zobaczyć, jak kostka przeciwnika wielokrotnie zbliża się do kostki gracza. Może być konieczne dostosowanie aparatu, jeśli nie jest on widoczny.

    ![scena grająca w jedności](media/unity-image32.png)

10. Przełącz się z powrotem do **programu Visual Studio dla komputerów Mac** i ustaw punkt przerwania w pierwszym wierszu metody **Update.** Należy go natychmiast uderzyć.

    ![ustawianie punktu przerwania w programie Visual Studio dla komputerów Mac](media/unity-image33.png)

11. Załóżmy, że szybkość jest zbyt szybka i chcemy przetestować wpływ zmiany bez ponownego uruchamiania aplikacji. Znajdź zmienną **Prędkość** w oknie **Autos** lub **Locals,** a następnie zmień ją na **"10"** i naciśnij **klawisz Enter**.

    ![dostosowywanie zmiennych w oknie dla mieszkańców](media/unity-image34.png)

12. Usuń punkt przerwania i naciśnij **klawisz F5,** aby wznowić wykonywanie.

13. Wróć do **unity,** aby wyświetlić uruchomionej aplikacji. Kostka przeciwnika porusza się teraz z piątą pierwotnej prędkości.

    ![jedność z uruchomię aplikacją](media/unity-image35.png)

14. Zatrzymaj aplikację Unity, klikając ponownie przycisk **Odtwórz.**

    ![zatrzymywanie aplikacji unity](media/unity-image36.png)

15. Wróć do **programu Visual Studio dla komputerów Mac**. Zatrzymaj sesję debugowania, klikając przycisk **Zatrzymaj.**

    ![zatrzymywanie sesji debugowania w programie Visual Studio dla komputerów Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Zadanie 4: Eksplorowanie funkcji unity w programie Visual Studio dla komputerów Mac

1. Visual Studio dla komputerów Mac zapewnia szybki dostęp do dokumentacji Unity w edytorze kodu. Umieść kursor gdzieś na symbolu **Vector3** w metodzie **Aktualizuj** i naciśnij **przycisk - Command + .**

    ![wybieranie metody w programie Visual Studio dla edytora mac](media/unity-image38.png)

2. Otworzy się nowe okno przeglądarki dla **vector3**. Zamknij okno przeglądarki po spełnieniu tej potrzeby.

    ![otwiera się okno przeglądarki w dokumentacji](media/unity-image39.png)

3. Visual Studio dla komputerów Mac zapewnia również niektórych pomocników do szybkiego tworzenia klas zachowania Unity. W **eksploratorze** **rozwiązań** kliknij prawym przyciskiem myszy pozycję Zasoby i wybierz polecenie **Dodaj > Nowe monobezachanie**.

    ![nowa akcja kontekstowa monobehaviour](media/unity-image40.png)

4. Nowo utworzona klasa udostępnia wycinki dla **startu** i **aktualizacji** metody. Po zamknięciu nawiasu klamrowego **Update** metody, zacznij wpisywać **"onmouseup"**. Podczas pisania należy zauważyć, że IntelliSense programu Visual Studio szybko zeruje się na metodę, którą planujesz zaimplementować. Wybierz go z podanej listy autouzupełniania. Wypełni skrót metody dla Ciebie, w tym wszelkie parametry.

    ![intellisense w visual studio dla komputerów Mac](media/unity-image41.png)

5. Wewnątrz **OnMouseUp** metody wpisz **"base".** , aby wyświetlić wszystkie metody podstawowe dostępne do wywołania. Można również eksplorować różne przeciążenia każdej funkcji za pomocą opcji stronicowania w prawym górnym rogu wysuwania intellisense.

    ![eksplorowanie przeciążeń w programie Visual Studio dla komputerów Mac](media/unity-image42.png)

6. Visual Studio dla komputerów Mac umożliwia również łatwe definiowanie nowych modułów cieniujących. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję Zasoby** i wybierz polecenie Dodaj > nowy moduł **cieniujący**.

    ![nowa akcja cieniowania w programie Visual Studio dla komputerów Mac](media/unity-image43.png)

7. Format pliku modułu cieniującego pobiera pełny kolor i czcionkę, aby ułatwić czytanie i zrozumienie.

    ![wyróżnianie składni](media/unity-image44.png)

8. Powrót do **jedności**. Zobaczysz, że ponieważ visual studio dla komputerów Mac współpracuje z tym samym systemem projektu, zmiany wprowadzone w każdym miejscu są automatycznie synchronizowane z innymi. Teraz łatwo jest zawsze używać najlepszego narzędzia do tego zadania.

    ![panel zasobów jedności](media/unity-image45.png)

## <a name="summary"></a>Podsumowanie

W tym laboratorium dowiesz się, jak rozpocząć tworzenie gry za pomocą unity i programu Visual Studio dla komputerów Mac. Zobacz, [https://unity3d.com/learn](https://unity3d.com/learn) aby dowiedzieć się więcej o Unity.
