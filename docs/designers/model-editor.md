---
title: Edytor kodu
ms.date: 04/12/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf26cf8f8d0e47c257d35acbe6e7af29e1416a69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833047"
---
# <a name="model-editor"></a>Edytor modelu

W tym dokumencie opisano sposób pracy z programem Visual Studio **edytora modelu** do wyświetlania, tworzenia i modyfikowania modeli 3D.

Możesz użyć **edytora modelu** na potrzeby tworzenia podstawowych modeli 3D od podstaw, lub do przeglądania i modyfikowania bardziej złożonych modeli 3W, które zostały utworzone przy użyciu w pełni funkcjonalne 3D, narzędzia do modelowania.

## <a name="supported-formats"></a>Obsługiwane formaty

**Edytora modelu** obsługuje kilka formatów modeli 3D, które są używane w rozwoju aplikacji DirectX:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|
|-----------------| - | - |
|Plik wymiany AutoDesk FBX|*.fbx*|Wyświetl, edytuj, utwórz|
|Plik w formacie Collada DAE|*DAE*|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|
|OBJ|*.obj*|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|

## <a name="get-started"></a>Wprowadzenie

Ta sekcja zawiera opis sposobu dodawania modelu 3D do projektu Visual Studio C++ i inne podstawowe informacje, które pomogą Ci rozpocząć pracę.

> [!NOTE]
> Integracji kompilacji automatyczne graficzne elementy, takie jak scen 3D (.fbx plików) jest obsługiwana tylko dla projektów C++.

### <a name="to-add-a-3d-model-to-your-project"></a>Aby dodać 3D model do projektu

1. Upewnij się, że masz wymagany program Visual Studio zainstalowany składnik trzeba pracować z grafiki. Składnik ten jest wywoływany **obrazów i modeli 3W edytory**.

   Aby go zainstalować, otwórz Instalator programu Visual Studio, wybierając pozycję **narzędzia** > **Pobierz narzędzia i funkcje** menu paska, a następnie wybierz pozycję **poszczególne składniki**kartę. Wybierz **obrazów i modeli 3W edytory** składnika w obszarze **gier i aplikacji graficznych** kategorii, a następnie wybierz **Modyfikuj**.

   ![Obrazów i modeli 3W składnika edytorów](media/image-3d-model-editors-component.png)

   Składnik uruchamia instalowanie.

2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu C++, aby dodać obraz do, a następnie wybierz **Dodaj** > **nowy element**.

3. W **Dodaj nowy element** dialogowego **grafiki** kategorii, wybierz opcję **Scena 3D (.fbx)**.

   ![Dodaj nowy element w oknie dialogowym z wybrane sceny 3D](media/add-new-3d-scene.png)

   > [!NOTE]
   > Jeśli nie widzisz **grafiki** kategorii **Dodaj nowy element** okna dialogowego, a **obrazów i modeli 3W edytory** zainstalowany składnik, graficzne elementy nie są obsługiwane. dla danego typu projektu.

4. Wprowadź **nazwa** z plikiem modelu, a następnie wybierz **Dodaj**.

### <a name="axis-orientation"></a>Orientacja osi

Visual Studio obsługuje każdą orientację osi 3D i ładuje informacje o orientacji osi z formatów plików modeli, które go obsługują. Jeśli określono nie orientacji osi, program Visual Studio domyślnie używa prawostronnego układu współrzędnych. **Wskaźnik osi** pokazuje bieżącą orientację osi w prawym dolnym rogu powierzchni projektowej. Na **wskaźnik osi**kolor czerwony odpowiada osi x, zielony reprezentuje oś y, a niebieski odpowiada osi z.

### <a name="begin-your-3d-model"></a>Rozpocznij modelu 3D

W edytorze modelu każdy nowy obiekt zawsze rozpoczyna się jako jeden z podstawowych kształtów 3D — lub *podstawowych*— wbudowanych w Edytor modelu. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby uzyskać informacje o sposobie dodawania prymitywów do sceny, zobacz [tworzenie i importowanie obiektów 3D](#Adding3DObjects). Aby uzyskać informacje o tym, jak dodać więcej wierzchołków do obiektu, zobacz [modyfikować obiekty](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Praca z edytorem modelu

Poniżej opisano sposób używania edytora modelu do pracy z modelami 3D.

### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu

Edytor modelu zawiera paski narzędzi, polecenia ułatwiające Praca z modelami 3D.

Polecenia, które wpływają na stan edytora modelu znajdują się na **tryb edytora modelu** narzędzi w głównym oknie programu Visual Studio. Narzędzia do modelowania i polecenia skryptowe znajdują się na **edytora modelu** paska narzędzi na powierzchni projektowania edytora modelu.

Oto **tryb edytora modelu** narzędzi:

![Przeglądarka modelu modalne paska narzędzi.](../designers/media/digit-mre-modal-toolbar.png)

W tej tabeli opisano elementy na **tryb edytora modelu** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Select**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|
|**Przesuwanie**|Umożliwia ruch sceny 3D w względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać **Ctrl** aktywować **Pan** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenia** tryb, wybierz punkt w scenie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> W **wybierz** trybie można powiększyć lub przy użyciu kółka myszy podczas trzymania wciśniętego **Ctrl**.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  W tym trybie nie ma efektu, gdy **prostopadły** jest włączone rzutowanie.|
|**Lokalne świata**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|
|**Tryb obrotu**|Po włączeniu tego elementu przekształcenia wpływają na położenie i orientację *punkt obrotu* wybranego obiektu (punkt obrotu definiuje środek operacji przesunięcia, skalowania i obrót). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|
|**Zablokuj oś X**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Y**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Z**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Obiekt w ramce**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|
|**Widok**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **Frontonu**<br /> Umieszcza widok przed sceną.<br /><br /> **Wstecz**<br /> Umieszcza widok za sceną.<br /><br /> **po lewej stronie**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **po prawej stronie**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **dolny**<br /> Umieszcza widok pod sceną. **Uwaga:**  Jest to jedyny sposób zmiany kierunku widoku po **prostopadły** jest włączone rzutowanie.|
|**Projekcja**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywa**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Ortogonalnym**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **prostopadły** włączono projekcję, nie można użyć **Orbita** trybu do ustawienia widoku.|
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Szkielet**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Overdraw**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskie cieniowanie**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym programu Visual Studio odrysowuje powierzchnię projektu, nawet wtedy, gdy jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Przełącz siatkę**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|
|**Przybornik**|Zamiennie pokazuje i ukrywa **przybornika**.|
|**Konspekt dokumentu**|Zamiennie pokazuje i ukrywa **konspekt dokumentu** okna.|
|**Właściwości**|Zamiennie pokazuje i ukrywa **właściwości** okna.|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceną**<br /><br /> **Importujuj**<br /> Importuje obiekty z innego pliku modelu 3D do bieżącej sceny.<br /><br /> **Dołącz do nadrzędnego**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłącz od nadrzędnego**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Zaznaczony obiekt staje się *główny obiekt* w scenie. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Tworzenie grupy**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scal obiekty**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Utwórz nowy obiekt z zaznaczenia wielokątnego**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć w Wielokącie**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacje**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Triangulacji**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Widok**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Szybkość klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna po włączeniu **tryb renderowania w czasie rzeczywistym** opcji.<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **ukryty** właściwości obiektu do **False**.<br /><br /> **Pokaż normalne powierzchni**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brakujące materiały**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokazuj przestawne**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3D w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Pokaż węzły zastępcze**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż normalne wierzchołka**<br /> Pokazuje normalną każdego wierzchołka. **Porada:**  Możesz wybrać **skrypty** przycisk, aby ponownie uruchomić ostatni skrypt.|

Oto **edytora modelu** narzędzi:

![Model pasku narzędzi programu Pomoc](../designers/media/digit-mre-toolbar.png)

W następnej tabeli opisano elementy na **edytora modelu** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Przetłumacz**|Przenosi zaznaczenie.|
|**Skala**|Zmienia rozmiar zaznaczenia.|
|**Obróć**|Obraca zaznaczenie.|
|**Wybierz punkt**|Zestawy **trybu zaznaczania** można wybierać poszczególne punkty obiektu.|
|**Wybierz krawędź**|Zestawy **trybu zaznaczania** aby wybierał krawędź (linię między dwoma wierzchołkami) obiektu.|
|**Wybierz pierwszy plan**|Zestawy **trybu zaznaczania** na powierzchnię obiektu.|
|**Wybierz obiekt**|Zestawy **trybu zaznaczania** aby wybierał cały obiekt.|
|**Wyciągnięcie**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|
|**Dzielenie**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|

### <a name="control-the-view"></a>Formant widoku

Sceny 3D jest renderowana zgodnie z widoku, który można traktować jako wirtualną kamerę, która ma pozycję i orientację. Aby zmienić położenie i orientację, użyj formantów widoku na **tryb edytora modelu** paska narzędzi.

W poniższej tabeli opisano formanty widoku podstawowego.

|Formant widoku|Opis|
|------------------|-----------------|
|**Przesuwanie**|Umożliwia ruch sceny 3D w względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać **Ctrl** aktywować **Pan** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenia** tryb, wybierz punkt w scenie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> W **wybierz** trybie można powiększyć lub przy użyciu kółka myszy podczas trzymania wciśniętego **Ctrl**.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  W tym trybie nie ma efektu, gdy **prostopadły** jest włączone rzutowanie.|
|**Obiekt w ramce**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|

Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na **edytora modelu** narzędzi, możesz wybrać dowolną **perspektywy** lub **prostopadły** projekcji.

|Rzut|Opis|
|----------------|-----------------|
|**Perspektywa**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|
|**Ortogonalnym**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **prostopadły** włączono projekcję, nie można użyć **Orbita** trybu do ustawienia widoku arbitralnie.|

Może być przydatna wyświetlić sceny 3D ze znanego położenia i kąta, na przykład, jeśli chcesz porównać dwie podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku, na **tryb edytora modelu** narzędzi wybierz **widoku**, a następnie wybierz wstępnie zdefiniowany widok ma — przodu, z tyłu, lewo, prawo, top lub bottom. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład, jeśli wybierzesz **Pokaż pierwszy wiersz**, wirtualna kamera spojrzy na źródło sceny bezpośrednio znad niej.

### <a name="view-additional-geometry-details"></a>Wyświetl dodatkowe szczegóły geometrii

Aby lepiej zrozumieć obiekt 3D lub scenę, można wyświetlić dodatkowe szczegóły geometrii np. normalne wierzchołka, normalne powierzchni, punkty obrotu aktywnego zaznaczenia i inne szczegóły. Aby je włączyć lub wyłączyć, na **edytora modelu** narzędzi wybierz **skrypty** > **widoku**, a następnie wybierz żądaną opcję.

### Tworzenie i importowanie obiektów 3D <a name="Adding3DObjects"></a>

Aby dodać wstępnie zdefiniowany kształt 3D do sceny, w **przybornika**, wybierz jedną, a następnie przenieś go do powierzchni projektowej. Nowe kształty są umieszczane w źródle sceny. Edytor modelu zawiera siedem kształtów: **Stożek**, **modułu**, **Cylinder**, **dysku**, **płaszczyzny**, **kuli**i **Czajniczek**.

Można zaimportować obiektu 3D z pliku, na **edytora modelu** narzędzi, wybierz **zaawansowane** > **Zarządzanie sceną** > **importowania**  > i określ plik, który chcesz zaimportować.

### <a name="transform-objects"></a>obiekty przekształceń

Możesz *Przekształcanie* obiektu przez zmianę jego **obrotu**, **skalowania**, i **tłumaczenia** właściwości. *Obrót* ustawia obiekt przez zastosowanie kolejnych rotacji wokół osi x, y i z określonych przez jego punkt obrotu. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** zmienia rozmiar obiektu, rozciągając go o określony współczynnik wzdłuż jednej lub wielu osi wyśrodkowanych względem punktu obrotu. *Tłumaczenie* lokalizuje obiekt w 3-wymiarowej, względem jego elementu nadrzędnego, a nie jego punktu obrotu.

Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Przekształcić obiekt za pomocą narzędzi do modelowania

1. W **wybierz** tryb, wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. Na **edytora modelu** narzędzi, wybierz **Translate**, **skalowania**, lub **Obróć** narzędzia. Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.

3. Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.

#### <a name="transform-an-object-by-setting-its-properties"></a>Przekształcanie obiektu przez ustawienie jego właściwości

1. W **wybierz** tryb, wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. W **właściwości** okna, podaj wartości dla **obrotu**, **skalowania**, i **tłumaczenia** właściwości.

    > [!IMPORTANT]
    > Aby uzyskać **obrotu** właściwości, określ kąt obrotu wokół każdej z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.

Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.

Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **manipulacja** do włączyć (lub wyłączyć) tryb dowolnego kształtu. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na **tryb edytora modelu** narzędzi, wybierz dowolną kombinację **Zablokuj X**, **Zablokuj Y**, i **Zablokuj Z** przycisków.

Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na **tryb edytora modelu** narzędzi, wybierz **przyciąganie** włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.

### <a name="work-with-the-pivot-point"></a>Praca z punktem obrotu

Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na **tryb edytora modelu** narzędzi, wybierz **tryb obrotu** można włączyć (lub wyłączyć) tryb obrotu. Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć **tłumaczenia** i **obrotu** narzędzia do manipulowania punktem obrotu.

Demonstracyjne, który pokazuje, jak używać punktu obrotu, zobacz [jak: Modyfikowanie punktu obrotu modelu 3D](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Tryby lokalne i świata

Przesunięcie i obrót mogą występować albo w lokalnym układzie współrzędnych (lub *lokalnej ramce odniesienia*) obiektu, albo w układzie współrzędnych świata (lub *ramce odniesienia world*). Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) tryb świata, na **tryb edytora modelu** narzędzi, wybierz **WorldLocal** przycisku.

### Modyfikowanie obiektów <a name="ModifyingObjects"></a>

Możesz zmienić kształt obiektu 3D, przenosząc lub usuwając jego wierzchołki, krawędzie i powierzchnie. Domyślnie Edytor modelu jest w *trybie obiektu*, dzięki czemu można wybierać i przekształcać całe obiekty. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na **tryb edytora modelu** narzędzi, wybierz **tryby wyboru**, a następnie wybierz żądany tryb.

Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **wyciągnięcie**.

#### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **Podziel na mniejsze**.

Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.

#### <a name="triangulate-a-face"></a>Przeprowadzić triangulację powierzchni

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **triangulacja**.

#### <a name="merge-objects"></a>Scal obiekty

1. W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **Scal obiekty**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Utwórz obiekt z zaznaczenia wielokątnego

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **narzędzia** > **Utwórz nowy obiekt z zaznaczenia wielokątnego**.

### <a name="work-with-materials-and-shaders"></a>Praca z materiałami i modułami cieniującymi

Wygląd obiektu zależy od interakcji oświetlenia i materiału obiektu w scenie. Materiały są definiowane przez właściwości, które opisują, jak powierzchnia reaguje na różne typy światła, oraz przez program do cieniowania, który oblicza końcowy kolor każdego piksela na powierzchni obiektu na podstawie informacji o oświetleniu, map tekstur, map normalnych i innych danych.

Edytor modelu zawiera następujące materiały domyślne:

|Materiał|Opis|
|--------------|-----------------|
|**Nieoświetlona**|Renderuje powierzchnię bez żadnego symulowanego oświetlenia.|
|**Lamberta**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia i oświetleniem rozproszonym.|
|**Phong**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia, oświetleniem rozproszonym i światłem odbitym.|

Każdy z tych materiałów stosuje jedną teksturę na powierzchni obiektu. Można ustawić różne tekstury dla każdego obiektu, który używa materiału.

Aby zmodyfikować sposób reakcji określonego obiektu na różne źródła światła w scenie, możesz zmienić właściwości oświetlenia materiału niezależnie od innych obiektów używających materiału. W tej tabeli opisano typowe właściwości oświetlenia:

|Właściwość oświetlenia|Opis|
| - |-----------------|
|**Otoczenia**|Opisuje wpływ oświetlenia otoczenia na powierzchnię.|
|**Rozpraszania**|Opisuje wpływ światła kierunkowego i punktowego na powierzchnię.|
|**Emisyjny**|W tym artykule opisano, jak powierzchnia emituje światło niezależne od innego oświetlenia.|
|**Odblasku**|Opisuje odbijanie światła kierunkowego i punktowego przez powierzchnię.|
|**Moc odblasku**|Opisuje szerokość i natężenie odbitego światła.|

W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W **wybierz** tryb, wybierz obiekt, którego materiał chcesz zmienić, a następnie w polu **właściwości** oknie zmiany **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, lub inne dostępne właściwości. Materiał może udostępniać do ośmiu tekstur, którego właściwości są nazywane kolejno od **Texture1** do **tekstura8**.

Aby usunąć wszystkie materiały z obiektu na **edytora modelu** narzędzi, wybierz **skrypty** > **materiałów** > **Usuń Materiały**.

Możesz użyć **Shader Designer** utworzyć niestandardowe materiały modułu cieniującego, które można stosować do obiektów, sceny 3D. Aby uzyskać informacje o tym, jak utworzyć niestandardowe materiały modułu cieniującego, zobacz [Shader Designer](../designers/shader-designer.md). Aby uzyskać informacje dotyczące sposobu stosowania niestandardowego materiału cieniowania do obiektu, zobacz [jak: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Zarządzanie sceną

Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.

Możesz użyć **konspekt dokumentu** okna, aby wyświetlić hierarchię sceny i wybrać węzły sceny. Po wybraniu węzła konspektu można użyć **właściwości** okna, aby zmodyfikować jego właściwości.

Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Tworzenie hierarchii, która ma obiekt nadrzędny

1. W **wybierz** tryb, wybierz dwa lub więcej obiektów. Pierwszy wybrany będzie obiektem nadrzędnym.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **Zarządzanie sceną** > **Dołącz do nadrzędnego**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Utworzyć obiekty hierarchii elementów równorzędnych

1. W **wybierz** tryb, wybierz dwa lub więcej obiektów. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.

2. Na **edytora modelu** narzędzi, wybierz **skrypty** > **Zarządzanie sceną** > **Utwórz grupę**.

Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Aby wyświetlić węzły zastępcze na **edytora modelu** narzędzi, wybierz **skrypty** > **Zarządzanie sceną** > **Pokaż Węzły zastępcze**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.

Aby usunąć skojarzenie nadrzędny podrzędny między dwoma obiektami, zaznacz obiekt podrzędny, a następnie na **edytora modelu** narzędzi, wybierz **skrypty** > **Zarządzanie sceną**  >  **Odłącz od nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełącz się do **wybierz** tryb|**CTRL**+**G**, **Ctrl**+**funkcji pytania i odpowiedzi**<br /><br /> **S**|
|Przełącz się do **powiększenia** tryb|**CTRL**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Przełącz się do **Pan** tryb|**CTRL**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Zaznacz wszystkie|**CTRL**+**A**|
|Usuń bieżące zaznaczenie|**Delete**|
|Anuluj bieżące zaznaczenie|**Znak ucieczki** (**Esc**)|
|Powiększanie|**Obrót kółkiem myszy do przodu**<br /><br /> **CTRL**+**kółkiem myszy do przodu**<br /><br /> **SHIFT**+**kółkiem myszy do przodu**<br /><br /> **CTRL**+**PageUp**<br /><br /> Znak plus (**+**)|
|Pomniejszanie|**Obrót kółkiem myszy do tyłu**<br /><br /> **CTRL**+**obrót kółkiem myszy do tyłu**<br /><br /> **SHIFT**+**obrót kółkiem myszy do tyłu**<br /><br /> **CTRL**+**PageDown**<br /><br /> Znak minus (**-**)|
|Przesunięcie kamery do góry|**PageDown**|
|Przesunięcie kamery w dół|**PageUp**|
|Przesunięcie kamery w lewo|**Obrót kółkiem myszy w lewo**<br /><br /> **CTRL**+**PageDown**|
|Przesunięcie kamery w prawo|**Obrót kółkiem myszy do prawej**<br /><br /> **CTRL**+**PageDown**|
|Widok góry modelu|**CTRL**+**L**, **Ctrl**+**T**<br /><br /> **T**|
|Widok dołu modelu|**CTRL**+**L**, **Ctrl**+**U**|
|Widok lewej strony modelu|**CTRL**+**L**, **Ctrl**+**L**|
|Widok prawej strony modelu|**CTRL**+**L**, **Ctrl**+**R**|
|Widok przodu modelu|**CTRL**+**L**, **Ctrl**+**F**|
|Widok tyłu modelu|**CTRL**+**L**, **Ctrl**+**B**|
|Umieść obiekt w ramce w oknie|**F**|
|Przełącz tryb szkieletowy|**CTRL**+**L**, **Ctrl**+**W**|
|Przełącz przyciąganie do siatki|**CTRL**+**G**, **Ctrl**+**N**|
|Przełącz tryb obracania|**CTRL**+**G**, **Ctrl**+**V**|
|Przełącz ograniczenie osi x|**CTRL**+**L**, **Ctrl**+**X**|
|Przełącz ograniczenie osi y|**CTRL**+**L**, **Ctrl**+**Y**|
|Przełącz ograniczenie osi z|**CTRL**+**L**, **Ctrl**+**Z**|
|Przełącz do trybu przesunięcia|**CTRL**+**G**, **Ctrl**+**W**<br /><br /> **W**|
|Przełącz do trybu skalowania|**CTRL**+**G**, **Ctrl**+**E**<br /><br /> **E**|
|Przełącz do trybu obrotu|**CTRL**+**G**, **Ctrl**+**R**<br /><br /> **R**|
|Przełącz do trybu zaznaczania punktu|**CTRL**+**L**, **Ctrl**+**1**|
|Przełącz do trybu zaznaczania krawędzi|**CTRL**+**L**, **Ctrl**+**2**|
|Przełącz do trybu zaznaczania powierzchni|**CTRL**+**L**, **Ctrl**+**3**|
|Przełącz do trybu zaznaczania obiektu|**CTRL**+**L**, **Ctrl**+**4**|
|Przełącz do trybu orbity (kamery)|**CTRL**+**G**, **Ctrl**+**O**|
|Wybierz następny obiekt w scenie|**Karta**|
|Wybierz poprzedni obiekt w scenie|**SHIFT**+**kartę**|
|Manipuluj zaznaczonym obiektem za pomocą bieżącego narzędzia.|**Strzałkę** kluczy|
|Dezaktywuj bieżący manipulator|**PYTANIA I ODPOWIEDZI**|
|Obracanie kamery|**ALT**+**przeciągania** za pomocą lewego przycisku myszy|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Omówienie narzędzi Visual Studio, które służą do pracy z zasobami grafiki, takie jak tekstury i obrazy, modele 3D i efekty cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób używania edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje sposób używania projektanta programu do cieniowania programu Visual Studio do pracy z programów do cieniowania.|