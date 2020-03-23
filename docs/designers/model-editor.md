---
title: Edytor kodu
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7adee409ff6bb5721724b9acc2e76a11d32a4f54
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589854"
---
# <a name="model-editor"></a>Edytor modelu

W tym dokumencie opisano sposób pracy z **Edytorem modeli** programu Visual Studio w celu wyświetlania, tworzenia i modyfikowania modeli 3D.

**Edytor modeli** służy do tworzenia podstawowych modeli 3D od podstaw lub do wyświetlania i modyfikowania bardziej złożonych modeli 3D, które zostały utworzone przy użyciu w pełni funkcjonalnych narzędzi do modelowania 3D.

## <a name="supported-formats"></a>Obsługiwane formaty

**Edytor modeli** obsługuje kilka formatów modeli 3D, które są używane w tworzeniu aplikacji DirectX:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|
|-----------------| - | - |
|Plik wymiany AutoDesk FBX|*.fbx*|Wyświetl, edytuj, utwórz|
|Plik w formacie Collada DAE|*.dae*|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|
|OBJ|*.obj*|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano sposób dodawania modelu 3D do projektu programu Visual Studio C++ i inne podstawowe informacje, które pomogą Ci rozpocząć pracę.

> [!NOTE]
> Automatyczna integracja kompilacji elementów graficznych, takich jak sceny 3D (pliki fbx) jest obsługiwana tylko dla projektów W++.

### <a name="to-add-a-3d-model-to-your-project"></a>Aby dodać model 3D do projektu

1. Upewnij się, że masz zainstalowany wymagany składnik programu Visual Studio, który jest potrzebny do pracy z grafiką. Składnik nosi nazwę **Edytory obrazów i modeli 3D**.

   Aby go zainstalować, otwórz Instalatora programu Visual Studio, wybierając **pozycję Narzędzia** > **Pobierz narzędzia i funkcje** z paska menu, a następnie wybierz kartę **Poszczególne składniki.** Wybierz składnik **Edytory obrazów i modeli 3D** w kategorii **Gry i grafika,** a następnie wybierz pozycję **Modyfikuj**.

   ![Komponent edytorów obrazów i modeli 3D](media/image-3d-model-editors-component.png)

   Składnik rozpocznie instalację.

2. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu C++, do którego chcesz dodać obraz, a następnie wybierz pozycję **Dodaj** > **nowy element**.

3. W oknie dialogowym **Dodawanie nowego elementu** w kategorii **Grafika** wybierz pozycję **Scena 3D (.fbx)**.

   ![Okno dialogowe Dodawanie nowego elementu z zaznaczoną sceną 3D](media/add-new-3d-scene.png)

   > [!NOTE]
   > Jeśli nie widzisz kategorii **Grafika** w oknie dialogowym **Dodawanie nowego elementu** i masz zainstalowany składnik **Edytory obrazów i modeli 3D,** elementy graficzne nie są obsługiwane dla typu projektu.

4. Wprowadź **nazwę** pliku modelu, a następnie wybierz pozycję **Dodaj**.

### <a name="axis-orientation"></a>Orientacja osi

Program Visual Studio obsługuje każdą orientację osi 3D i ładuje informacje o orientacji osi z formatów plików modelu, które go obsługują. Jeśli nie określono orientacji osi, program Visual Studio domyślnie używa układu współrzędnych praworęcznych. **Wskaźnik osi** pokazuje aktualną orientację osi w prawym dolnym rogu powierzchni projektowej. Na **wskaźniku osi**kolor czerwony reprezentuje oś x, zielony reprezentuje oś y, a niebieski oznacza oś z.

### <a name="begin-your-3d-model"></a>Rozpoczynanie modelu 3D

W Edytorze modeli każdy nowy obiekt zawsze zaczyna się jako jeden z podstawowych kształtów 3D lub podstawowych , które są *wbudowane*w Edytor modeli. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby uzyskać informacje dotyczące dodawania obiektu pierwotnego do sceny, zobacz [Tworzenie i importowanie obiektów 3D](#Adding3DObjects). Aby uzyskać informacje dotyczące dodawania kolejnych wierzchołków do obiektu, zobacz [Modyfikowanie obiektów](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Praca z Edytorem modeli

W poniższych sekcjach opisano sposób korzystania z Edytora modeli do pracy z modelami 3D.

### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu

Paski narzędzi Edytora modeli zawierają polecenia ułatwiające pracę z modelami 3D.

Polecenia wpływające na stan Edytora modeli znajdują się na pasku narzędzi **Tryb edytora modelu** w głównym oknie programu Visual Studio. Narzędzia modelowania i polecenia skryptowe znajdują się na pasku narzędzi **Edytora modeli** na powierzchni projektu Edytora modeli.

Oto pasek narzędzi **Trybu edytora modelu:**

![Pasek narzędzi modalnej przeglądarki modelu.](../designers/media/digit-mre-modal-toolbar.png)

W tej tabeli opisano elementy na pasku narzędzi **Tryb edytora modelu,** które są wyświetlane w kolejności, w jakiej pojawiają się od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|
|**Przesuwanie**|Umożliwia ruch sceny 3D względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **wyboru** można nacisnąć i przytrzymać **klawisz Ctrl,** aby tymczasowo włączyć tryb **przesuwania.**|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt sceny, a następnie przesuń go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć widok.<br /><br /> W trybie **wyboru** można powiększać lub pomniejszać za pomocą kółka myszy podczas naciskania i przytrzymywać **klawisza Ctrl**.|
|**Orbitowanie**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie ma wpływu, gdy **projekcja ortograficzna** jest włączona.|
|**Świat lokalny**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|
|**Tryb przestawny**|Gdy ten element jest włączony, przekształcenia wpływają na położenie i orientację *punktu obrotu* zaznaczonego obiektu (punkt obrotu definiuje środek operacji translacji, skalowania i obrotu). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|
|**Zablokuj oś X**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Oś blokady Y**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Oś blokady Z**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Obiekt ramki**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|
|**Widok**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **Front**<br /> Umieszcza widok przed sceną.<br /><br /> **Back**<br /> Umieszcza widok za sceną.<br /><br /> **Lewej**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **Prawo**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **Dolnej części**<br /> Umieszcza widok pod sceną. **Uwaga:**  Jest to jedyny sposób, aby zmienić kierunek widoku, gdy **projekcja ortogoniczna** jest włączona.|
|**Projekcja**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywa**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Prostokątnego**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Po włączeniu projekcji **ortogonalnej** nie można użyć trybu **Orbita,** aby ustawić widok.|
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Rama druciana**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Przerysowywu**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskie cieniowanie**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|
|**Tryb renderowania w czasie rzeczywistym**|Gdy renderowanie w czasie rzeczywistym jest włączone, Visual Studio ponownie rysuje powierzchni projektowej, nawet wtedy, gdy nie jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Przełączanie siatki**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **przybornik**.|
|**Konspekt dokumentu**|Naprzemiennie pokazuje lub ukrywa okno **Konspekt dokumentu.**|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa okno **Właściwości.**|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Silniki graficzne**<br /><br /> **Renderowanie za pomocą D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie za pomocą D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceną**<br /><br /> **Import**<br /> Importuje obiekty z innego pliku modelu 3D do bieżącej sceny.<br /><br /> **Dołącz do rodzica**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłączyć od rodzica**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Zaznaczony obiekt staje się *obiektem głównym* w scenie. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Utwórz grupę**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scalanie obiektów**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Tworzenie nowego obiektu z zaznaczenia wielokąta**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **narzędzia**<br /><br /> **Uzwojenie wielokąta odwróć**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacje**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Triangulacji**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Widok**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna po włączeniu opcji Tryb renderowania w **czasie rzeczywistym.**<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **właściwości Hidden** każdego obiektu do **wartości False**.<br /><br /> **Pokaż normals twarzy**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brakujące materiały**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokaż przestawianie**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3D w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Pokaż węzły zastępcze**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż normals wierzchołków**<br /> Pokazuje normalną każdego wierzchołka. **Wskazówka:**  Można wybrać przycisk **Skrypty,** aby ponownie uruchomić ostatni skrypt.|

Oto pasek narzędzi **Edytor modeli:**

![Pasek narzędzi Przeglądarki modeli](../designers/media/digit-mre-toolbar.png)

Następna tabela opisuje elementy na pasku narzędzi **Edytora modeli,** które są wyświetlane w kolejności, w jakiej pojawiają się od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Przetłumacz**|Przenosi zaznaczenie.|
|**Skali**|Zmienia rozmiar zaznaczenia.|
|**Obrót**|Obraca zaznaczenie.|
|**Wybierz punkt**|Ustawia **tryb zaznaczania,** aby wybrać poszczególne punkty na obiekcie.|
|**Wybierz krawędź**|Ustawia **tryb zaznaczania,** aby wybrać krawędź (linię między dwoma wierzchołkami) na obiekcie.|
|**Wybierz ścianę**|Ustawia **tryb zaznaczania,** aby wybrać ścianę na obiekcie.|
|**Zaznaczanie obiektu**|Ustawia **tryb zaznaczania,** aby zaznaczyć cały obiekt.|
|**Wyciągnięcie**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|
|**Podzielić**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|

### <a name="control-the-view"></a>Sterowanie widokiem

Scena 3D jest renderowana zgodnie z widokiem, który można traktować jako wirtualną kamerę, która ma pozycję i orientację. Aby zmienić położenie i orientację, użyj kontrolek widoku na pasku narzędzi **Tryb edytora modelu.**

W poniższej tabeli opisano formanty widoku podstawowego.

|Formant widoku|Opis|
|------------------|-----------------|
|**Przesuwanie**|Umożliwia ruch sceny 3D względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **wyboru** można nacisnąć i przytrzymać **klawisz Ctrl,** aby tymczasowo włączyć tryb **przesuwania.**|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt sceny, a następnie przesuń go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć widok.<br /><br /> W trybie **wyboru** można powiększać lub pomniejszać za pomocą kółka myszy podczas naciskania i przytrzymywać **klawisza Ctrl**.|
|**Orbitowanie**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie ma wpływu, gdy **projekcja ortograficzna** jest włączona.|
|**Obiekt ramki**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|

Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na pasku narzędzi **Edytor modelu** można wybrać rzut **perspektywiczny** lub **ortograficzny.**

|Projekcja|Opis|
|----------------|-----------------|
|**Perspektywa**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|
|**Prostokątnego**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Po włączeniu projekcji **ortogonalnej** nie można użyć trybu **Orbita,** aby dowolnie ustawić widok.|

Przydatne może być wyświetlenie sceny 3D ze znanej pozycji i kąta, na przykład, gdy chcesz porównać dwie podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku, na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Widok**, a następnie wybierz wstępnie zdefiniowany widok — przedni, tylny, lewy, prawy, górny lub dolny. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład, jeśli wybierzesz **Widok z góry,** wirtualna kamera spojrzy na początek sceny bezpośrednio nad nią.

### <a name="view-additional-geometry-details"></a>Wyświetlanie dodatkowych szczegółów geometrii

Aby lepiej zrozumieć obiekt lub scenę 3D, można wyświetlić dodatkowe szczegóły geometrii, takie jak normals dla wierzchołków, normalsy na ścianę, punkty obrotu aktywnego zaznaczenia i inne szczegóły. Aby je włączyć lub wyłączyć, na pasku narzędzi **Edytor modeli** wybierz pozycję**Widok** **skryptów,** > a następnie wybierz odpowiedni widok.

### <a name="create-and-import-3d-objects"></a>Tworzenie i importowanie obiektów 3D<a name="Adding3DObjects"></a>

Aby dodać wstępnie zdefiniowany kształt 3D do sceny, w **przyborniku**zaznacz odpowiedni kształt, a następnie przesuń go na powierzchnię projektową. Nowe kształty są umieszczane w źródle sceny. Edytor modeli zawiera siedem kształtów: **Stożek,** **Kostka,** **Cylinder,** **Płyta,** **Płaszczyzna,** Kula i **Czajnik.** **Sphere**

Aby zaimportować obiekt 3D z pliku, na pasku narzędzi **Edytor modeli** wybierz polecenie **Zaawansowane** > **zarządzanie scenami** > **importuj** > a następnie określ plik, który chcesz zaimportować.

### <a name="transform-objects"></a>obiekty przekształceń

Obiekt można *przekształcić,* zmieniając jego właściwości **Obrót,** **Skala**i **Tłumaczenie.** *Obrót* orientuje obiekt, stosując kolejne obroty wokół osi x, osi y i osi Z zdefiniowanej przez jego punkt obrotu. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** umożliwia zmienić rozmiar obiektu przez rozciągnięcie go o określony współczynnik wzdłuż jednej lub kilku osi wyśrodkowanych na jego punkcie obrotu. *Tłumaczenie* lokalizuje obiekt w przestrzeni 3-wymiarowej względem jego elementu nadrzędnego zamiast punktu obrotu.

Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Przekształcanie obiektu przy użyciu narzędzi do modelowania

1. W trybie **wyboru** zaznacz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. Na pasku narzędzi **Edytor modelu** wybierz narzędzie Tłumacz , **Skaluj**lub **Translate** **Obróć.** Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.

3. Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.

#### <a name="transform-an-object-by-setting-its-properties"></a>Przekształcanie obiektu przez ustawienie jego właściwości

1. W trybie **wyboru** zaznacz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. W oknie **Właściwości** określ wartości właściwości **Obrót,** **Skala**i **Translacja.**

    > [!IMPORTANT]
    > Dla **Rotation** właściwości, określ stopień obrotu wokół każdej z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.

Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.

Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na pasku narzędzi **Edytor modelu** wybierz pozycję**Narzędzia** >  **skryptów** > **Do manipulowania swobodną,** aby włączyć (lub wyłączyć) tryb dowolny. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na **pasku** narzędzi Tryb edytora modelu wybierz dowolną kombinację przycisków **Zablokuj X,** **Zablokuj Y**i **Zablokuj Z.**

Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Przyciągaj,** aby włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.

### <a name="work-with-the-pivot-point"></a>Praca z punktem obrotu

Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na pasku narzędzi **Tryb edytora modelu** wybierz **tryb przestawny,** aby włączyć (lub wyłączyć) tryb przestawny. Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć narzędzia **Translacja** i **Obrót,** aby manipulować punktem obrotu.

Aby zapoznać się z prezentacją, która pokazuje, jak używać punktu obrotu, zobacz [Jak: Zmodyfikować punkt obrotu modelu 3D](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Tryby lokalne i świata

Translacja i obrót mogą wystąpić w lokalnym układzie współrzędnych (lub *lokalnej ramce odniesienia)* obiektu lub w układzie współrzędnych świata (lub *w światowej ramce odniesienia).* Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) tryb światowy, na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **WorldLocal.**

### <a name="modify-objects"></a>Modyfikowanie obiektów<a name="ModifyingObjects"></a>

Kształt obiektu 3D można zmienić, przesuwając lub usuwając jego wierzchołki, krawędzie i ściany. Domyślnie Edytor modelu jest w *trybie obiektu,* dzięki czemu można zaznaczać i przekształcać całe obiekty. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Tryby zaznaczenia**, a następnie wybierz odpowiedni tryb.

Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.

2. Na **pasku** narzędzi Edytor modeli wybierz pozycję **Narzędzia skryptów** > **Tools** > **wyciągnięcia**.

#### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.

2. Na **pasku** narzędzi Edytor modeli wybierz pozycję **Narzędzia skryptów** > **Tools** > **Podziel**.

Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.

#### <a name="triangulate-a-face"></a>Triangulacji twarzy

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.

2. Na pasku narzędzi **Edytor modeli** wybierz pozycję**Narzędzia** >  **skryptów** > **triangulate**.

#### <a name="merge-objects"></a>Scalanie obiektów

1. W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.

2. Na **pasku** narzędzi Edytor modeli wybierz pozycję **Narzędzia skryptów** > **scalania** > **obiektów**.

#### <a name="create-an-object-from-a-polygon-selection"></a>Tworzenie obiektu na podstawie zaznaczenia wielokąta

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.

2. Na **pasku** narzędzi Edytor modeli wybierz pozycję**Narzędzia** >  **skryptów** > **Tworzenie nowego obiektu z zaznaczenia wielokąta**.

### <a name="work-with-materials-and-shaders"></a>Praca z materiałami i modułami cieniu.

Wygląd obiektu zależy od interakcji oświetlenia i materiału obiektu w scenie. Materiały są definiowane przez właściwości, które opisują, jak powierzchnia reaguje na różne typy światła, oraz przez program do cieniowania, który oblicza końcowy kolor każdego piksela na powierzchni obiektu na podstawie informacji o oświetleniu, map tekstur, map normalnych i innych danych.

Edytor modelu zawiera następujące materiały domyślne:

|Materiał|Opis|
|--------------|-----------------|
|**Nieoświetlona**|Renderuje powierzchnię bez żadnego symulowanego oświetlenia.|
|**Lambert**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia i oświetleniem rozproszonym.|
|**Phong**|Renderuje powierzchnię z symulowanym oświetleniem otoczenia, oświetleniem rozproszonym i światłem odbitym.|

Każdy z tych materiałów stosuje jedną teksturę na powierzchni obiektu. Można ustawić różne tekstury dla każdego obiektu, który używa materiału.

Aby zmodyfikować sposób reakcji określonego obiektu na różne źródła światła w scenie, możesz zmienić właściwości oświetlenia materiału niezależnie od innych obiektów używających materiału. W tej tabeli opisano typowe właściwości oświetlenia:

|Właściwość oświetlenia|Opis|
| - |-----------------|
|**Otoczenie**|Opisuje wpływ oświetlenia otoczenia na powierzchnię.|
|**Rozproszone**|Opisuje wpływ światła kierunkowego i punktowego na powierzchnię.|
|**Emisyjne**|W tym artykule opisano, jak powierzchnia emituje światło niezależne od innego oświetlenia.|
|**Odbite**|Opisuje odbijanie światła kierunkowego i punktowego przez powierzchnię.|
|**Siła odbicia**|Opisuje szerokość i natężenie odbitego światła.|

W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W trybie **wyboru** zaznacz obiekt, którego materiał chcesz zmienić, a następnie w oknie **Właściwości** zmień **właściwość MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**lub inną dostępną właściwość. Materiał może ujawnić maksymalnie osiem tekstur, których właściwości są nazywane sekwencyjnie od **Texture1** do **Texture8**.

Aby usunąć wszystkie materiały z obiektu, na **pasku** narzędzi Edytor modeli wybierz pozycję**Materiały** >  **skrypty** > **Usuń materiały**.

**Projektant modułu cieniującego** służy do tworzenia niestandardowych materiałów modułu cieniującego, które można zastosować do obiektów sceny 3D. Aby uzyskać informacje dotyczące tworzenia niestandardowych materiałów modułu cieniującego, zobacz [Projektant modułu cieniującego](../designers/shader-designer.md). Aby uzyskać informacje dotyczące stosowania niestandardowego materiału modułu cieniującego do obiektu, zobacz [Jak: Stosowanie modułu cieniującego do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Zarządzanie sceną

Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.

Za pomocą okna **Konspekt dokumentu** można wyświetlić hierarchię scen i wybrać węzły sceny. Po wybraniu węzła w konspekcie można użyć okna **Właściwości,** aby zmodyfikować jego właściwości.

Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Tworzenie hierarchii zawierającej obiekt nadrzędny

1. W trybie **wyboru** zaznacz co najmniej dwa obiekty. Pierwszy wybrany będzie obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modeli** wybierz pozycję Zarządzanie**scenami** >  **skryptów** > **Dołączanie do strony nadrzędnej**.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Tworzenie hierarchii obiektów równorzędnych

1. W trybie **wyboru** zaznacz co najmniej dwa obiekty. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modeli** wybierz pozycję**Zarządzanie** >  **scenami skryptów** > **Utwórz grupę**.

Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Aby wyświetlić węzły zastępcze, na pasku narzędzi **Edytor modeli** wybierz pozycję**Zarządzanie** >  **scenami skryptów** > **Pokaż węzły zastępcze**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.

Aby usunąć skojarzenie nadrzędny-podrzędny między dwoma obiektami, zaznacz obiekt podrzędny, a następnie na pasku narzędzi **Edytor modelu** wybierz pozycję **Scripts** > **Scene ManagementOdłączanie** > **z obiektu Nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełączanie do trybu **wyboru**|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Przełączanie do trybu **powiększenia**|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Przełączanie do trybu **przesuwania**|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Usuwanie**|
|Anuluj bieżące zaznaczenie|**Ucieczka** (**Esc**)|
|Powiększanie|**Obrót kółkiem myszy do przodu**<br /><br /> **Ctrl**+**Kółko myszy do przodu**<br /><br /> **Przesunięcie**+**kółka myszy do przodu**<br /><br /> **PageUp ctrl**+**PageUp**<br /><br /> Znak Plus**+**( )|
|Pomniejszanie|**Obrót kółkiem myszy do tyłu**<br /><br /> **Ctrl**+**Kółko myszy do tyłu**<br /><br /> **Shift**+**Kółko myszy do tyłu**<br /><br /> **Przychylenia**+**strony** Ctrl<br /><br /> Znak minus**-**( )|
|Przesunięcie kamery do góry|**PageDown**|
|Przesunięcie kamery w dół|**PageUp**|
|Przesunięcie kamery w lewo|**Ruch kółkiem myszy w lewo**<br /><br /> **Przychylenia**+**strony** Ctrl|
|Przesunięcie kamery w prawo|**Ruch kółkiem myszy w prawo**<br /><br /> **Przychylenia**+**strony** Ctrl|
|Widok góry modelu|**Ctrl**+**L**, **Ctrl**+**T**<br /><br /> **T**|
|Widok dołu modelu|**Ctrl**+**L**, **Ctrl**+**U**|
|Widok lewej strony modelu|**Ctrl**+**L**, **Ctrl**+**L**|
|Widok prawej strony modelu|**Ctrl**+**L**, **Ctrl**+**R**|
|Widok przodu modelu|**Ctrl**+**L**, **Ctrl**+**F**|
|Widok tyłu modelu|**Ctrl**+**L**, **Ctrl**+**B**|
|Umieść obiekt w ramce w oknie|**F**|
|Przełącz tryb szkieletowy|**Ctrl**+**L**, **Ctrl**+**W**|
|Przełącz przyciąganie do siatki|**Ctrl**+**G**, **Ctrl**+**N**|
|Przełącz tryb obracania|**Ctrl**+**G**, **Ctrl**+**V**|
|Przełącz ograniczenie osi x|**Ctrl**+**L**, **Ctrl**+**X**|
|Przełącz ograniczenie osi y|**Ctrl**+**L**, **Ctrl**+**Y**|
|Przełącz ograniczenie osi z|**Ctrl**+**L**, **Ctrl**+**Z**|
|Przełącz do trybu przesunięcia|**Ctrl**+**G**, **Ctrl**+**W**<br /><br /> **W**|
|Przełącz do trybu skalowania|**Ctrl**+**G**, **Ctrl**+**E**<br /><br /> **E**|
|Przełącz do trybu obrotu|**Ctrl**+**G**, **Ctrl**+**R**<br /><br /> **R**|
|Przełącz do trybu zaznaczania punktu|**Ctrl**+**L**, **Ctrl**+**1**|
|Przełącz do trybu zaznaczania krawędzi|**Ctrl**+**L**, **Ctrl**+**2**|
|Przełącz do trybu zaznaczania powierzchni|**Ctrl**+**L**, **Ctrl**+**3**|
|Przełącz do trybu zaznaczania obiektu|**Ctrl**+**L**, **Ctrl**+**4**|
|Przełącz do trybu orbity (kamery)|**Ctrl**+**G**, **Ctrl**+**O**|
|Wybierz następny obiekt w scenie|**Zakładka**|
|Wybierz poprzedni obiekt w scenie|**Shift**+**Karta** Shift|
|Manipuluj zaznaczonym obiektem za pomocą bieżącego narzędzia.|Klawisze **strzałek**|
|Dezaktywuj bieżący manipulator|**P**|
|Obracanie kamery|**Alt**+**Przeciągnij** lewym przyciskiem myszy|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D w grach i aplikacjach](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie narzędzi programu Visual Studio, których można używać do pracy z zasobami graficznymi, takimi jak tekstury i obrazy, modele 3D i efekty modułu cieniującego.|
|[Edytor obrazów](../designers/image-editor.md)|W tym artykule opisano, jak używać Edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Projektant modułu cieniującego](../designers/shader-designer.md)|W tym artykule opisano, jak używać Projektanta modułu cieniującego programu Visual Studio do pracy z modułami cieniu.|
