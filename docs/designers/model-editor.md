---
title: Edytor kodu
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13ca91c431f574190a5cddbe17f1b042685056bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635033"
---
# <a name="model-editor"></a>Edytor modelu

W tym dokumencie opisano sposób pracy z **edytorem modelu** programu Visual Studio w celu wyświetlania, tworzenia i modyfikowania modeli 3W.

Korzystając z **Edytora modelu** , można tworzyć podstawowe modele 3W od podstaw lub wyświetlać i modyfikować bardziej złożone modele 3W, które zostały utworzone przy użyciu w pełni funkcjonalnego narzędzia do modelowania 3W.

## <a name="supported-formats"></a>Obsługiwane formaty

**Edytor modelu** obsługuje kilka formatów modelu 3W, które są używane w programowaniu aplikacji DirectX:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|
|-----------------| - | - |
|Plik wymiany AutoDesk FBX|*. FBX*|Wyświetl, edytuj, utwórz|
|Plik w formacie Collada DAE|*. DAE*|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|
|OBJ|*. obj*|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano, jak dodać model 3D do projektu programu Visual C++ Studio i inne podstawowe informacje, które pomogą Ci rozpocząć pracę.

> [!NOTE]
> Automatyczna integracja kompilacji elementów graficznych, takich jak sceny 3W (pliki. FBX), jest obsługiwana C++ tylko w projektach.

### <a name="to-add-a-3d-model-to-your-project"></a>Aby dodać model 3D do projektu

1. Upewnij się, że masz zainstalowany wymagany składnik programu Visual Studio, który jest potrzebny do pracy z grafiką. Składnik jest nazywany **edytorami obrazów i modeli 3W**.

   Aby go zainstalować, Otwórz Instalator programu Visual Studio, wybierając pozycję **narzędzia**  > **Pobierz narzędzia i funkcje** z paska menu, a następnie wybierz kartę **poszczególne składniki** . Wybierz składnik **obrazy i edytory modelu 3W** w obszarze  **Kategoria gry i grafika** , a następnie wybierz polecenie **Modyfikuj**.

   ![Składnik edytorów obrazów i modeli 3W](media/image-3d-model-editors-component.png)

   Składnik zostanie uruchomiony.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla C++ projektu, do którego chcesz dodać obraz, a następnie wybierz polecenie **Dodaj**  > **nowy element**.

3. W oknie dialogowym **Dodaj nowy element** w obszarze Kategoria **grafiki** wybierz pozycję **scena 3D (. FBX)** .

   ![Okno dialogowe Dodawanie nowego elementu z wybraną sceną 3D](media/add-new-3d-scene.png)

   > [!NOTE]
   > Jeśli kategoria **grafika** nie jest widoczna w oknie dialogowym **Dodaj nowy element** i masz zainstalowany składnik **edytory obrazów i modeli 3W** , elementy graficzne nie są obsługiwane dla typu projektu.

4. Wprowadź **nazwę** pliku modelu, a następnie wybierz pozycję **Dodaj**.

### <a name="axis-orientation"></a>Orientacja osi

Program Visual Studio obsługuje każdą orientację osi 3D i ładuje informacje o orientacji osi z obsługiwanych przez niego formatów plików modeli. Jeśli orientacja osi nie zostanie określona, program Visual Studio domyślnie używa odpowiedniego systemu współrzędnych. **Wskaźnik osi** pokazuje bieżącą orientację osi w prawym dolnym rogu powierzchni projektowej. Na **wskaźniku osi**czerwony reprezentuje oś x, zielony reprezentuje oś y, a niebieska reprezentuje oś z.

### <a name="begin-your-3d-model"></a>Rozpocznij model 3W

W edytorze modelu każdy nowy obiekt zawsze zaczyna się od jednego z podstawowych kształtów 3W — lub *podstawowych*, które są wbudowane w Edytor modelu. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby dowiedzieć się, jak dodać obiekt pierwotny do sceny, zobacz [Tworzenie i Importowanie obiektów 3W](#Adding3DObjects). Aby uzyskać informacje na temat dodawania kolejnych wierzchołków do obiektu, zobacz [Modyfikowanie obiektów](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Pracuj z edytorem modelu

W poniższych sekcjach opisano, jak używać edytora modelu do pracy z modelami 3W.

### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu

Paski narzędzi edytora modelu zawierają polecenia, które ułatwiają współpracę z modelami 3W.

Polecenia, które mają wpływ na stan edytora modelu, znajdują się na pasku narzędzi **Tryb edytora modelu** w głównym oknie programu Visual Studio. Narzędzia modelowania i polecenia z skryptami znajdują się na pasku narzędzi **Edytora modelu** na powierzchni projektowej edytora modelu.

Oto pasek narzędzi **Tryb edytora modelu** :

![Modalny pasek narzędzi podglądu modeli.](../designers/media/digit-mre-modal-toolbar.png)

W tej tabeli opisano elementy na pasku narzędzi **Tryb edytora modelu** , które są wymienione w kolejności, w jakiej są wyświetlane od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybór**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|
|**Przesuwanie**|Umożliwia przenoszenie sceny 3D względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz **Ctrl** , aby tymczasowo aktywować tryb **przesuwania** .|
|**Zmieniać**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt w scenie, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> W trybie **wyboru** można powiększać i pomniejszać przy użyciu kółka myszy podczas naciskania i przytrzymania klawisza **Ctrl**.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie działa, gdy jest włączone rzutowanie **ortogonalne** .|
|**Świat lokalny**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|
|**Tryb przestawny**|Gdy ten element jest włączony, przekształcenia wpływają na położenie i orientację *punktu obrotu* wybranego obiektu (punkt obrotu definiuje centrum operacji tłumaczenia, skalowania i rotacji). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|
|**Zablokuj oś X**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Y**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Z**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Frame — obiekt**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|
|**Widokiem**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **FSB**<br /> Umieszcza widok przed sceną.<br /><br /> **Wstecz**<br /> Umieszcza widok za sceną.<br /><br /> **Lewym**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **Kliknij**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **Stop**<br /> Umieszcza widok pod sceną. **Uwaga:**  Jest to jedyny sposób zmiany kierunku widoku, gdy jest włączone rzutowanie **ortogonalne** .|
|**Projekcja**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywy**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Rzut**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy rzutowanie **ortogonalne** jest włączone, nie można użyć trybu **Orbita** do położenia widoku.|
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Ramka druciana**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Odświeżanie**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskie cieniowanie**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym program Visual Studio ponownie rysuje powierzchnię projektu, nawet jeśli nie jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Przełącz siatkę**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **Przybornik**.|
|**Konspekt dokumentu**|Alternatywnie pokazuje lub ukrywa okno **konspektu dokumentu** .|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa okno **Właściwości** .|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie przy użyciu D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie przy użyciu D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceną**<br /><br /> **Importujuj**<br /> Importuje obiekty z innego pliku modelu 3D do bieżącej sceny.<br /><br /> **Dołącz do elementu nadrzędnego**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłącz od elementu nadrzędnego**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Wybrany obiekt zostaje *obiektem głównym* w scenie. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Utwórz grupę**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scal obiekty**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Utwórz nowy obiekt z zaznaczenia wielokątnego**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć uzwojenie wielokątne**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacje**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Wyznacz triangulacją**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Widokiem**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Szybkość klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna po włączeniu opcji **tryb renderowania w czasie rzeczywistym** .<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **ukrytej** właściwości każdego obiektu do **wartości false**.<br /><br /> **Pokaż normalne wyglądy**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brakujące materiały**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokaż przestawkę**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3W w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Pokaż węzły zastępcze**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż normalne wierzchołki**<br /> Pokazuje normalną każdego wierzchołka. **Porada:**  Możesz wybrać przycisk **skrypty** , aby ponownie uruchomić ostatni skrypt.|

Oto pasek narzędzi **Edytora modelu** :

![Pasek narzędzi podglądu modelu](../designers/media/digit-mre-toolbar.png)

W następnej tabeli opisano elementy na pasku narzędzi **Edytora modelu** , które są wymienione w kolejności, w jakiej są wyświetlane od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Przetłumacz**|Przenosi zaznaczenie.|
|**Zasięgu**|Zmienia rozmiar zaznaczenia.|
|**Obróceni**|Obraca zaznaczenie.|
|**Wybierz punkt**|Ustawia **tryb wyboru** w celu wybrania poszczególnych punktów w obiekcie.|
|**Wybierz krawędź**|Ustawia **tryb wyboru** , aby wybrać krawędź (linię między dwoma wierzchołkami) obiektu.|
|**Wybierz miarę**|Ustawia **tryb wyboru** w celu wybrania kroju na obiekcie.|
|**Wybierz obiekt**|Ustawia **tryb wyboru** , aby wybrać cały obiekt.|
|**Fazowa**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|
|**Podzielić**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|

### <a name="control-the-view"></a>Kontrolowanie widoku

Scena 3D jest renderowana zgodnie z widokiem, który może być uważany za kamerę wirtualną, która ma położenie i orientację. Aby zmienić położenie i orientację, Użyj kontrolek widok na pasku narzędzi **Tryb edytora modelu** .

W poniższej tabeli opisano formanty widoku podstawowego.

|Formant widoku|Opis|
|------------------|-----------------|
|**Przesuwanie**|Umożliwia przenoszenie sceny 3D względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz **Ctrl** , aby tymczasowo aktywować tryb **przesuwania** .|
|**Zmieniać**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt w scenie, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> W trybie **wyboru** można powiększać i pomniejszać przy użyciu kółka myszy podczas naciskania i przytrzymania klawisza **Ctrl**.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie działa, gdy jest włączone rzutowanie **ortogonalne** .|
|**Frame — obiekt**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|

Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na pasku narzędzi **Edytor modelu** można wybrać rzutowanie **perspektywiczne** lub **ortogonalne** .

|Rzut|Opis|
|----------------|-----------------|
|**Perspektywy**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|
|**Rzut**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy rzutowanie **ortogonalne** jest włączone, nie można użyć trybu **Orbita** do arbitralnego pozycjonowania widoku.|

Przydatne może być wyświetlenie sceny 3D od znanego położenia i kąta, na przykład gdy chcesz porównać dwa podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku, na pasku narzędzi **Tryb edytora modelu** wybierz **Widok**, a następnie wybierz żądany wstępnie zdefiniowany widok — przód, wstecz, lewy, prawy, górny lub dolny. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład po wybraniu opcji **Wyświetl górny**aparat wirtualny przegląda źródło sceny bezpośrednio nad nią.

### <a name="view-additional-geometry-details"></a>Wyświetl dodatkowe szczegóły geometrii

Aby lepiej zrozumieć obiekt lub scenę 3D, można wyświetlić dodatkowe szczegóły geometryczne, takie jak normalne dla wierzchołków, normalne wartości, punkty obrotu aktywnego zaznaczenia oraz inne szczegóły. Aby je włączyć lub wyłączyć, na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**  > **Widok**, a następnie wybierz odpowiedni.

### Tworzenie i Importowanie obiektów 3D<a name="Adding3DObjects"></a>

Aby dodać wstępnie zdefiniowany kształt 3W do sceny, w **przyborniku**wybierz jeden z nich, a następnie przenieś go do powierzchni projektowej. Nowe kształty są umieszczane w źródle sceny. Edytor modelu zawiera siedem kształtów: **stożek**, **Cube**, **walcowy**, **Disc**, **płaszczyzna**, **kula**i **czajniczek**.

Aby zaimportować obiekt 3W z pliku, na pasku narzędzi **Edytor modelu** wybierz pozycję **Zaawansowane**  > **zarządzanie sceną**  > **zaimportować** > a następnie określ plik, który chcesz zaimportować.

### <a name="transform-objects"></a>obiekty przekształceń

Obiekt można *przekształcić* , zmieniając jego właściwości **obrotu**, **skali**i **tłumaczenia** . *Obrót* orientuje obiekt przez zastosowanie kolejnych rotacji wokół osi x, osi y i osi z zdefiniowanej przez punkt obrotu. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** zmienia rozmiar obiektu przez rozciągnięcie go przez określony czynnik wzdłuż jednej lub więcej osi wyśrodkowanych w punkcie obrotu. *Tłumaczenie* lokalizuje obiekt w trójwymiarowym miejscu względem jego elementu nadrzędnego, a nie punktu obrotu.

Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Przekształcanie obiektu przy użyciu narzędzi modelowania

1. W obszarze tryb **wyboru** wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. Na pasku narzędzi **Edytor modelu** wybierz narzędzie **Przekształć**, **Skaluj**lub **Obróć** . Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.

3. Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.

#### <a name="transform-an-object-by-setting-its-properties"></a>Przekształcanie obiektu przez ustawienie jego właściwości

1. W obszarze tryb **wyboru** wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. W oknie **Właściwości** Określ wartości właściwości **rotacja**, **Skala**i **translacja** .

    > [!IMPORTANT]
    > Dla właściwości **rotacja** Określ stopień obrotu wokół każdej z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.

Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.

Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Narzędzia**  > **manipulowanie formularzem bezpłatna** , aby włączyć (lub wyłączyć) tryb dowolnego formularza. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na pasku narzędzi **Tryb edytora modelu** wybierz dowolną kombinację przycisków **blokady X**, **Zablokuj Y**i **Zablokuj z** .

Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Przyciągaj** , aby włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.

### <a name="work-with-the-pivot-point"></a>Praca z punktem obrotu

Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na pasku narzędzi **Tryb edytora modelu** wybierz **tryb Pivot** , aby włączyć (lub wyłączyć) tryb obrotu. Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć narzędzi do **translacji** i **rotacji** do manipulowania punktem obrotu.

Aby zapoznać się z prezentacją, która pokazuje, jak używać punktu obrotu, zobacz [How to: Modify a Pivot a The 3D model](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Tryby lokalne i świata

Translacja i rotacja mogą wystąpić w lokalnym systemie współrzędnych (lub lokalnych punktach *odniesienia*) obiektu lub w układzie współrzędnych świata (lub w *światowej ramce odniesienia*). Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) tryb Światowy, na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **WorldLocal** .

### Modyfikuj obiekty<a name="ModifyingObjects"></a>

Kształt obiektu 3D można zmienić, przenosząc lub usuwając jego wierzchołki, krawędzie i twarze. Domyślnie Edytor modelu jest w *trybie obiektu*, dzięki czemu można wybierać i przetwarzać całe obiekty. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Tryby wyboru**, a następnie wybierz żądany tryb.

Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Narzędzia**  > **wyciągnięcie**.

#### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Narzędzia** ** >  Podziel**.

Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.

#### <a name="triangulate-a-face"></a>Triangulacja kroju

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Narzędzia**  > **triangulacja**.

#### <a name="merge-objects"></a>Scal obiekty

1. W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Narzędzia**  > **Scal obiekty**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Utwórz obiekt na podstawie zaznaczenia wielokątnego

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.

2. Na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**  > **Narzędzia**  > **Utwórz nowy obiekt z zaznaczenia Wielokąt**.

### <a name="work-with-materials-and-shaders"></a>Pracuj z materiałami i cieniami

Wygląd obiektu zależy od interakcji oświetlenia i materiału obiektu w scenie. Materiały są definiowane przez właściwości, które opisują, jak powierzchnia reaguje na różne typy światła, oraz przez program do cieniowania, który oblicza końcowy kolor każdego piksela na powierzchni obiektu na podstawie informacji o oświetleniu, map tekstur, map normalnych i innych danych.

Edytor modelu zawiera następujące materiały domyślne:

|Materiał|Opis|
|--------------|-----------------|
|**Bez oświetlenia**|Renderuje powierzchnię bez żadnego symulowanego oświetlenia.|
|**Lamberta**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia i oświetleniem rozproszonym.|
|**Podstawowego Phong**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia, oświetleniem rozproszonym i światłem odbitym.|

Każdy z tych materiałów stosuje jedną teksturę na powierzchni obiektu. Można ustawić różne tekstury dla każdego obiektu, który używa materiału.

Aby zmodyfikować sposób reakcji określonego obiektu na różne źródła światła w scenie, możesz zmienić właściwości oświetlenia materiału niezależnie od innych obiektów używających materiału. W tej tabeli opisano typowe właściwości oświetlenia:

|Właściwość oświetlenia|Opis|
| - |-----------------|
|**Otoczenia**|Opisuje wpływ oświetlenia otoczenia na powierzchnię.|
|**Rozpraszania**|Opisuje wpływ światła kierunkowego i punktowego na powierzchnię.|
|**Emisyjny**|W tym artykule opisano, jak powierzchnia emituje światło niezależne od innego oświetlenia.|
|**Odblasków**|Opisuje odbijanie światła kierunkowego i punktowego przez powierzchnię.|
|**Odblasków**|Opisuje szerokość i natężenie odbitego światła.|

W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W obszarze tryb **wyboru** zaznacz obiekt, którego materiał chcesz zmienić, a następnie w oknie **Właściwości** Zmień **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**,  **MaterialSpecularPower**lub inna dostępna właściwość. Materiał może uwidaczniać maksymalnie osiem tekstur, których właściwości są nazywane sekwencyjnie od **texture1** do **Texture8**.

Aby usunąć wszystkie materiały z obiektu, na pasku narzędzi **Edytor modelu** wybierz pozycję **skrypty**  > **materiały**  > **Usuń materiały**.

Można użyć **projektanta** programu do tworzenia niestandardowych materiałów programu do cieniowania, które można zastosować do obiektów w scenie 3D. Informacje o sposobach tworzenia niestandardowych materiałów programu do cieniowania można znaleźć w temacie [Shader Designer](../designers/shader-designer.md). Aby uzyskać informacje dotyczące sposobu zastosowania niestandardowego materiału do cieniowania do obiektu, zobacz [How to: Apply a Shader to a model 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Zarządzanie sceną

Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.

Można użyć okna **Konspekt dokumentu** , aby wyświetlić hierarchię sceny i wybrać węzły sceny. Po wybraniu węzła w konspekcie można użyć okna **Właściwości** , aby zmodyfikować jego właściwości.

Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Tworzenie hierarchii z obiektem nadrzędnym

1. W obszarze tryb **wyboru** wybierz co najmniej dwa obiekty. Pierwszy wybrany będzie obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Zarządzanie sceną**  > **Dołącz do elementu nadrzędnego**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Tworzenie hierarchii obiektów równorzędnych

1. W obszarze tryb **wyboru** wybierz co najmniej dwa obiekty. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno pozycje **skrypty**  > **Zarządzanie sceną**  > **Utwórz grupę**.

Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Aby wyświetlić węzły zastępcze, na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**  > **Zarządzanie sceną**  > **Pokaż węzły zastępcze**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.

Aby usunąć skojarzenie nadrzędny-podrzędny między dwoma obiektami, zaznacz obiekt podrzędny, a następnie na pasku narzędzi **Edytor modelu** wybierz pozycję **skrypty**  > **Zarządzanie sceną**  > **Odłącz od elementu nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełącz do trybu **wyboru**|**Ctrl** +**G**, **Ctrl** +**Q**<br /><br /> **Wolumin**|
|Przełącz do trybu **powiększenia**|**Ctrl** +**G**, **Ctrl** +**Z**<br /><br /> **Porządku**|
|Przełącz do trybu **kadrowania**|**Ctrl** +**G**, **Ctrl** +**P**<br /><br /> **K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Delete**|
|Anuluj bieżące zaznaczenie|**Escape** (**ESC**)|
|Powiększanie|**Kółko myszy do przodu**<br /><br /> **Ctrl** +**kółkiem myszy do przodu**<br /><br /> **Przesuń** +**kółkiem myszy do przodu**<br /><br /> **Ctrl** +**PageUp**<br /><br /> Znak plus ( **+** )|
|Pomniejszanie|**Kółko myszy do tyłu**<br /><br /> **Ctrl** +**kółkiem myszy do tyłu**<br /><br /> **Shift** +**kółkiem myszy do tyłu**<br /><br /> **Ctrl** +**PageDown**<br /><br /> Znak minusa ( **-** )|
|Przesunięcie kamery do góry|**PageDown**|
|Przesunięcie kamery w dół|**PageUp**|
|Przesunięcie kamery w lewo|**Kółko myszy w lewo**<br /><br /> **Ctrl** +**PageDown**|
|Przesunięcie kamery w prawo|**Kółko myszy w prawo**<br /><br /> **Ctrl** +**PageDown**|
|Widok góry modelu|**Ctrl** +**L**, **Ctrl** +**t**<br /><br /> **&**|
|Widok dołu modelu|**Ctrl** +**L**, **Ctrl** +**U**|
|Widok lewej strony modelu|**Ctrl** +**l**, **Ctrl** +**L**|
|Widok prawej strony modelu|**Ctrl** +**L**, **Ctrl** +**R**|
|Widok przodu modelu|**Ctrl** +**L**, **Ctrl** +**F**|
|Widok tyłu modelu|**Ctrl** +**L**, **Ctrl** +**B**|
|Umieść obiekt w ramce w oknie|**N**|
|Przełącz tryb szkieletowy|**Ctrl** +**L**, **Ctrl** +**W**|
|Przełącz przyciąganie do siatki|**Ctrl** +**G**, **Ctrl** +**N**|
|Przełącz tryb obracania|**Ctrl** +**G**, **Ctrl** +**V**|
|Przełącz ograniczenie osi x|**Ctrl** +**L**, **Ctrl** +**X**|
|Przełącz ograniczenie osi y|**Ctrl** +**L**, **Ctrl** +**Y**|
|Przełącz ograniczenie osi z|**Ctrl** +**L**, **Ctrl** +**Z**|
|Przełącz do trybu przesunięcia|**Ctrl** +**G**, **Ctrl** +**W**<br /><br /> **K**|
|Przełącz do trybu skalowania|**Ctrl** +**G**, **Ctrl** +**E**<br /><br /> **Adres**|
|Przełącz do trybu obrotu|**Ctrl** +**G**, **Ctrl** +**R**<br /><br /> **R**|
|Przełącz do trybu zaznaczania punktu|**Ctrl** +**L**, **Ctrl** +**1**|
|Przełącz do trybu zaznaczania krawędzi|**Ctrl** +**L**, **Ctrl** +**2**|
|Przełącz do trybu zaznaczania powierzchni|**Ctrl** +**L**, **Ctrl** +**3**|
|Przełącz do trybu zaznaczania obiektu|**Ctrl** +**L**, **Ctrl** +**4**|
|Przełącz do trybu orbity (kamery)|**Ctrl** +**G**, **Ctrl** +**O**|
|Wybierz następny obiekt w scenie|**Tabulator**|
|Wybierz poprzedni obiekt w scenie|**Karta** + **SHIFT**|
|Manipuluj zaznaczonym obiektem za pomocą bieżącego narzędzia.|Klawisze **strzałek**|
|Dezaktywuj bieżący manipulator|**Pytania**|
|Obracanie kamery|**Alt** +**przeciągnij** z lewym przyciskiem myszy|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3W dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera przegląd narzędzi programu Visual Studio, których można użyć do pracy z zasobami graficznymi, takimi jak tekstury i obrazy, modele 3W i efekty cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje, jak używać edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje, jak używać projektanta cieniowania programu Visual Studio do pracy z narzędziami do cieniowania.|