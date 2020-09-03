---
title: Edytor modelu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ede47ea89030aed0298961599f09df6444ed968
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664205"
---
# <a name="model-editor"></a>Edytor kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano sposób pracy z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorem modelu w celu wyświetlania, tworzenia i modyfikowania modeli trójwymiarowych.

 Edytor modelu może być użyty do tworzenia podstawowych modeli trójwymiarowych od początku lub do wyświetlania i modyfikowania bardziej złożonych modeli trójwymiarowych, utworzonych przy użyciu profesjonalnych narzędzi do modelowania trójwymiarowego. Edytor modelu obsługuje kilka formatów modeli 3-W, które są używane w rozwoju aplikacji DirectX.

## <a name="supported-formats"></a>Obsługiwane formaty
 Edytor modelu obsługuje następujące formaty modeli:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|
|-----------------|--------------------|-------------------------------------------------|
|Plik wymiany AutoDesk FBX|.fbx|Wyświetl, edytuj, utwórz|
|Plik w formacie Collada DAE|.dae|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|
|OBJ|.obj|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|

## <a name="getting-started"></a>Wprowadzenie
 W tej sekcji opisano, jak dodać model trójwymiarowy do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu i uzyskać podstawowe informacje potrzebne do rozpoczęcia pracy.

#### <a name="to-add-a-3-d-model-to-your-project"></a>Aby dodać model 3-W do projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, do którego chcesz dodać obraz, a następnie wybierz **Dodaj**, **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane**wybierz pozycję **grafika**, a następnie wybierz pozycję **scena 3D (. FBX)**.

3. Określ **nazwę** pliku modelu i **lokalizację** , w której ma zostać utworzona.

4. Wybierz przycisk **Dodaj**.

### <a name="axis-orientation"></a>Orientacja osi
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje każdą orientację osi 3-D i ładuje informacje o orientacji osi z formatów plików modelu, które je obsługują. Jeśli orientacja osi nie zostanie określona, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] domyślnie używa wbudowanego układu współrzędnych. **Wskaźnik osi** pokazuje bieżącą orientację osi w prawym dolnym rogu powierzchni projektowej. Na **wskaźniku osi**czerwony reprezentuje oś x, zielony reprezentuje oś y, a niebieska reprezentuje oś z.

### <a name="beginning-your-3-d-model"></a>Rozpoczynanie tworzenia modelu 3-W
 W edytorze modelu każdy nowy obiekt zawsze zaczyna się od jednego z podstawowych kształtów 3-D — lub *podstawowych*— wbudowanych w Edytor modelu. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby dowiedzieć się, jak dodać obiekt pierwotny do sceny, zobacz [Tworzenie i Importowanie obiektów 3-D](#Adding3DObjects). Aby uzyskać informacje na temat dodawania kolejnych wierzchołków do obiektu, zobacz [Modyfikowanie obiektów](#ModifyingObjects).

## <a name="working-with-the-model-editor"></a>Praca z Edytorem modelu
 W poniższych sekcjach opisano sposób używania Edytora modelu do pracy z modelami trójwymiarowymi.

### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu
 Na paskach narzędzi Edytora modelu są dostępne polecenia ułatwiające pracę z modelami 3-W.

 Polecenia, które mają wpływ na stan edytora modelu, znajdują się na pasku narzędzi **Tryb edytora modelu** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie głównym. Narzędzia modelowania i polecenia z skryptami znajdują się na pasku narzędzi **Edytora modelu** na powierzchni projektowej edytora modelu.

 Oto pasek narzędzi **Tryb edytora modelu** :

 ![Modalny pasek narzędzi podglądu modeli.](../designers/media/digit-mre-modal-toolbar.png "Cyfra-MRE-modalny pasek narzędzi")

 W tej tabeli opisano elementy na pasku narzędzi **Tryb edytora modelu** , które są wymienione w kolejności, w jakiej są wyświetlane od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|
|**Panoramowanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz CTRL, aby tymczasowo aktywować tryb **przesuwania** .|
|**Powiększenie**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt w scenie, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> W trybie **wyboru** można powiększać i pomniejszać przy użyciu kółka myszy podczas naciskania i przytrzymania klawisza CTRL.|
|**Orbitowanie**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie działa, gdy jest włączone rzutowanie **ortogonalne** .|
|**Świat lokalny**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|
|**Tryb przestawny**|Gdy ten element jest włączony, przekształcenia wpływają na położenie i orientację *punktu obrotu* wybranego obiektu (punkt obrotu definiuje centrum operacji tłumaczenia, skalowania i rotacji). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|
|**Zablokuj oś X**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Y**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Zablokuj oś Z**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Frame — obiekt**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|
|**Wyświetlanie**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **Front**<br /> Umieszcza widok przed sceną.<br /><br /> **Wstecz**<br /> Umieszcza widok za sceną.<br /><br /> **Lewym**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **Kliknij**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **Dolne**<br /> Umieszcza widok pod sceną. **Uwaga:**  Jest to jedyny sposób zmiany kierunku widoku, gdy jest włączone rzutowanie **ortogonalne** .|
|**Rzut**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywa**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Rzut**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy rzutowanie **ortogonalne** jest włączone, nie można użyć trybu **Orbita** do położenia widoku.|
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Ramka druciana**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Odświeżanie**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskie cieniowanie**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym program ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rysuje powierzchnię projektu, nawet jeśli nie jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Przełączanie siatki**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **Przybornik**.|
|**Konspekt dokumentu**|Alternatywnie pokazuje lub ukrywa okno **konspektu dokumentu** .|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa okno **Właściwości** .|
|**Zaawansowany**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie przy użyciu D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie przy użyciu D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceną**<br /><br /> **Importuj**<br /> Importuje obiekty z innego pliku modelu 3-W do bieżącej sceny.<br /><br /> **Dołącz do elementu nadrzędnego**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłącz od elementu nadrzędnego**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Wybrany obiekt zostaje *obiektem głównym* w scenie. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Utwórz grupę**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scal obiekty**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Utwórz nowy obiekt z zaznaczenia wielokątnego**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć uzwojenie wielokątne**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacje**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Wyznacz triangulacją**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Wyświetlanie**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Szybkość klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna po włączeniu opcji **tryb renderowania w czasie rzeczywistym** .<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **ukrytej** właściwości każdego obiektu do **wartości false**.<br /><br /> **Pokaż normalne wyglądy**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brakujące materiały**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokaż przestawkę**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3-W w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Pokaż węzły zastępcze**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż normalne wierzchołki**<br /> Pokazuje normalną każdego wierzchołka. **Porada:**  Możesz wybrać przycisk **skrypty** , aby ponownie uruchomić ostatni skrypt.|

 Oto pasek narzędzi **Edytora modelu** :

 ![Pasek narzędzi podglądu modelu](../designers/media/digit-mre-toolbar.png "Cyfra — MRE — pasek narzędzi")

 W następnej tabeli opisano elementy na pasku narzędzi **Edytora modelu** , które są wymienione w kolejności, w jakiej są wyświetlane od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Przetłumacz**|Przenosi zaznaczenie.|
|**Skalowanie**|Zmienia rozmiar zaznaczenia.|
|**Obrót**|Obraca zaznaczenie.|
|**Wybierz punkt**|Ustawia **tryb wyboru** w celu wybrania poszczególnych punktów w obiekcie.|
|**Wybierz krawędź**|Ustawia **tryb wyboru** , aby wybrać krawędź (linię między dwoma wierzchołkami) obiektu.|
|**Wybierz miarę**|Ustawia **tryb wyboru** w celu wybrania kroju na obiekcie.|
|**Wybierz obiekt**|Ustawia **tryb wyboru** , aby wybrać cały obiekt.|
|**Fazowa**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|
|**Podzielić**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|

### <a name="controlling-the-view"></a>Kontrolowanie widoku
 Scena 3-W jest renderowana zgodnie z widokiem. Można go traktować jako wirtualną kamerę, która ma pozycję i orientację. Aby zmienić położenie i orientację, Użyj kontrolek widok na pasku narzędzi **Tryb edytora modelu** .

 W poniższej tabeli opisano formanty widoku podstawowego.

|Formant widoku|Opis|
|------------------|-----------------|
|**Panoramowanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz CTRL, aby tymczasowo aktywować tryb **przesuwania** .|
|**Powiększenie**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W trybie **powiększenia** wybierz punkt w scenie, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> W trybie **wyboru** można powiększać i pomniejszać przy użyciu kółka myszy podczas naciskania i przytrzymania klawisza CTRL.|
|**Orbitowanie**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  Ten tryb nie działa, gdy jest włączone rzutowanie **ortogonalne** .|
|**Frame — obiekt**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|

 Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na pasku narzędzi **Edytor modelu** można wybrać rzutowanie **perspektywiczne** lub **ortogonalne** .

|Rzut|Opis|
|----------------|-----------------|
|**Perspektywa**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|
|**Rzut**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy rzutowanie **ortogonalne** jest włączone, nie można użyć trybu **Orbita** do arbitralnego pozycjonowania widoku.|

 Przydatne może okazać się wyświetlenie sceny trójwymiarowej ze znanego położenia i kąta, na przykład, gdy chcesz porównać dwie podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku, na pasku narzędzi **Tryb edytora modelu** wybierz **Widok**, a następnie wybierz żądany wstępnie zdefiniowany widok — przód, wstecz, lewy, prawy, górny lub dolny. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład po wybraniu opcji **Wyświetl górny**aparat wirtualny przegląda źródło sceny bezpośrednio nad nią.

### <a name="viewing-additional-geometry-details"></a>Wyświetlanie dodatkowych szczegółów geometrii
 Aby lepiej zrozumieć obiekt lub scenę 3-W, można wyświetlić dodatkowe szczegóły geometrii, np. normalne wierzchołka, normalne powierzchni, punkty obrotu aktywnego zaznaczenia i inne szczegóły. Aby je włączyć lub wyłączyć, na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**, **Widok**, a następnie wybierz ten, który chcesz.

### <a name="creating-and-importing-3-d-objects"></a><a name="Adding3DObjects"></a> Tworzenie i Importowanie obiektów 3-D
 Aby dodać wstępnie zdefiniowany kształt 3-D do sceny, w **przyborniku**wybierz jeden z nich, a następnie przenieś go na powierzchnię projektu. Nowe kształty są umieszczane w źródle sceny. Edytor modelu zawiera siedem kształtów: **stożek**, **Cube**, **walcowy**, **Disc**, **płaszczyzna**, **kula**i **czajniczek**.

 Aby zaimportować obiekt trójwymiarowy z pliku, na pasku narzędzi **Edytor modelu** wybierz opcję **Zaawansowane**, **Zarządzanie sceną**, **Import**, a następnie określ plik, który chcesz zaimportować.

### <a name="transforming-objects"></a>Przekształcanie obiektów
 Obiekt można *przekształcić* , zmieniając jego właściwości **obrotu**, **skali**i **tłumaczenia** . *Obrót* orientuje obiekt przez zastosowanie kolejnych rotacji wokół osi x, osi y i osi z zdefiniowanej przez punkt obrotu. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** zmienia rozmiar obiektu przez rozciągnięcie go przez określony czynnik wzdłuż jednej lub więcej osi wyśrodkowanych w punkcie obrotu. *Tłumaczenie* lokalizuje obiekt w trójwymiarowym miejscu względem jego elementu nadrzędnego, a nie punktu obrotu.

 Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.

##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Aby przekształcić obiekt za pomocą narzędzi do modelowania

1. W obszarze tryb **wyboru** wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. Na pasku narzędzi **Edytor modelu** wybierz narzędzie **Przekształć**, **Skaluj**lub **Obróć** . Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.

3. Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.

##### <a name="to-transform-an-object-by-setting-its-properties"></a>Aby przekształcić obiekt przez ustawienie jego właściwości

1. W obszarze tryb **wyboru** wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. W oknie **Właściwości** Określ wartości właściwości **rotacja**, **Skala**i **translacja** .

   > [!IMPORTANT]
   > Dla właściwości **rotacja** Określ stopień obrotu wokół każdej z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.

   Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.

   Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **manipulowanie za pomocą dowolnego formularza** , aby włączyć (lub wyłączyć) tryb dowolnego formularza. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na pasku narzędzi **Tryb edytora modelu** wybierz dowolną kombinację przycisków **blokady X**, **Zablokuj Y**i **Zablokuj z** .

   Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Przyciągaj** , aby włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.

### <a name="working-with-the-pivot-point"></a>Praca z punktem obrotu
 Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na pasku narzędzi **Tryb edytora modelu** wybierz **tryb Pivot** , aby włączyć (lub wyłączyć) tryb obrotu. Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć narzędzi do **translacji** i **rotacji** do manipulowania punktem obrotu.

 Aby zapoznać się z prezentacją, która pokazuje, jak korzystać z punktu Pivot, zobacz [How to: Modify a Pivot Point of 3-D model](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Tryby lokalne i świata
 Translacja i rotacja mogą wystąpić w lokalnym systemie współrzędnych (lub lokalnych punktach *odniesienia*) obiektu lub w układzie współrzędnych świata (lub w *światowej ramce odniesienia*). Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) tryb Światowy, na pasku narzędzi **Tryb edytora modelu** wybierz przycisk **WorldLocal** .

### <a name="modifying-objects"></a><a name="ModifyingObjects"></a> Modyfikowanie obiektów
 Kształt obiektu 3-W można zmienić, przenosząc lub usuwając jego wierzchołki, krawędzie i powierzchnie. Domyślnie Edytor modelu jest w *trybie obiektu*, dzięki czemu można wybierać i przetwarzać całe obiekty. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na pasku narzędzi **Tryb edytora modelu** wybierz pozycję **Tryby wyboru**, a następnie wybierz żądany tryb.

 Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.

##### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **wyciągnięcie**.

##### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **Podziel.**

   Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.

##### <a name="to-triangulate-a-face"></a>Aby przeprowadzić triangulację powierzchni

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **triangulacja**.

##### <a name="to-merge-objects"></a>Aby scalić obiekty

1. W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **Scal obiekty**.

##### <a name="to-create-an-object-from-a-polygon-selection"></a>Aby utworzyć obiekt z zaznaczenia wielokątnego

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Narzędzia**i **Utwórz nowy obiekt z zaznaczenia wielokątnego**.

### <a name="working-with-materials-and-shaders"></a>Praca z materiałami i modułami cieniującymi
 Wygląd obiektu zależy od interakcji oświetlenia i materiału obiektu w scenie. Materiały są definiowane przez właściwości, które opisują, jak powierzchnia reaguje na różne typy światła, oraz przez program do cieniowania, który oblicza końcowy kolor każdego piksela na powierzchni obiektu na podstawie informacji o oświetleniu, map tekstur, map normalnych i innych danych.

 Edytor modelu zawiera następujące materiały domyślne:

|Materiał|Opis|
|--------------|-----------------|
|Nieoświetlona|Renderuje powierzchnię bez żadnego symulowanego oświetlenia.|
|Lambert|Renderuje powierzchnię z symulowanym oświetleniem otoczenia i oświetleniem rozproszonym.|
|Phong|Renderuje powierzchnię z symulowanym oświetleniem otoczenia, oświetleniem rozproszonym i światłem odbitym.|

 Każdy z tych materiałów stosuje jedną teksturę na powierzchni obiektu. Można ustawić różne tekstury dla każdego obiektu, który używa materiału.

 Aby zmodyfikować sposób reakcji określonego obiektu na różne źródła światła w scenie, możesz zmienić właściwości oświetlenia materiału niezależnie od innych obiektów używających materiału. W tej tabeli opisano typowe właściwości oświetlenia:

|Właściwość oświetlenia|Opis|
|-----------------------|-----------------|
|Otoczenie|Opisuje wpływ oświetlenia otoczenia na powierzchnię.|
|Rozproszone|Opisuje wpływ światła kierunkowego i punktowego na powierzchnię.|
|Emisyjne|W tym artykule opisano, jak powierzchnia emituje światło niezależne od innego oświetlenia.|
|Odbite|Opisuje odbijanie światła kierunkowego i punktowego przez powierzchnię.|
|Siła odbicia|Opisuje szerokość i natężenie odbitego światła.|

 W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W obszarze tryb **wyboru** zaznacz obiekt, którego materiał chcesz zmienić, a następnie w oknie **Właściwości** Zmień wartość **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**lub inną dostępną właściwość. Materiał może uwidaczniać maksymalnie osiem tekstur, których właściwości są nazywane sekwencyjnie od **texture1** do **Texture8**.

 Aby usunąć wszystkie materiały z obiektu, na pasku narzędzi **Edytor modelu** wybierz **skrypty**, **materiały**, **Usuń materiały**.

 Można użyć **projektanta** programu do tworzenia niestandardowych materiałów programu do cieniowania, które można zastosować do obiektów w scenie 3-D. Informacje o sposobach tworzenia niestandardowych materiałów programu do cieniowania można znaleźć w temacie [Shader Designer](../designers/shader-designer.md). Aby uzyskać informacje dotyczące sposobu zastosowania niestandardowego materiału programu do cieniowania do obiektu, zobacz [How to: Apply a Shader to a 3-D model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Zarządzanie sceną
 Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.

 Można użyć okna **Konspekt dokumentu** , aby wyświetlić hierarchię sceny i wybrać węzły sceny. Po wybraniu węzła w konspekcie można użyć okna **Właściwości** , aby zmodyfikować jego właściwości.

 Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.

##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Aby utworzyć hierarchię zawierającą obiekt nadrzędny

1. W obszarze tryb **wyboru** wybierz co najmniej dwa obiekty. Pierwszy wybrany będzie obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**, **Zarządzanie sceną**, **Dołącz do elementu nadrzędnego**.

##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Aby utworzyć obiekty hierarchii elementów równorzędnych

1. W obszarze tryb **wyboru** wybierz co najmniej dwa obiekty. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.

2. Na pasku narzędzi **Edytor modelu** wybierz kolejno opcje **skrypty**, **Zarządzanie scenami**i **Utwórz grupę**.

   Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Aby wyświetlić węzły zastępcze, na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**, **Zarządzanie sceną**, **Pokaż węzły zastępcze**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.

   Aby usunąć skojarzenie nadrzędny-podrzędny między dwoma obiektami, zaznacz obiekt podrzędny, a następnie na pasku narzędzi **Edytor modelu** wybierz opcję **skrypty**, **Zarządzanie sceną**, **Odłącz od elementu nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------|------------------------|
|Przełącz do trybu **wyboru**|Ctrl+G, Gtrl+Q<br /><br /> S|
|Przełącz do trybu **powiększenia**|Ctrl+G, Ctrl+Z<br /><br /> Z|
|Przełącz do trybu **kadrowania**|Ctrl+G, Ctrl+P<br /><br /> K|
|Zaznacz wszystko|Ctrl+A|
|Usuń bieżące zaznaczenie|Usuń|
|Anuluj bieżące zaznaczenie|Escape|
|Powiększanie|Obrót kółkiem myszy do przodu<br /><br /> Ctrl + obrót kółkiem myszy do przodu<br /><br /> Shift+obrót kółkiem myszy do przodu<br /><br /> Ctrl+PageUp<br /><br /> Znak plus (+)|
|Pomniejszanie|Obrót kółkiem myszy do tyłu<br /><br /> CTRL + obrót kółkiem myszy do tyłu<br /><br /> Shift+obrót kółkiem myszy do tyłu<br /><br /> Ctrl+PageDown<br /><br /> Znak minusa (-)|
|Przesunięcie kamery do góry|PageDown|
|Przesunięcie kamery w dół|PageUp|
|Przesunięcie kamery w lewo|Ruch kółkiem myszy w lewo<br /><br /> Ctrl+PageDown|
|Przesunięcie kamery w prawo|Ruch kółkiem myszy w prawo<br /><br /> Ctrl+PageDown|
|Widok góry modelu|Ctrl+L, Ctrl+T<br /><br /> T|
|Widok dołu modelu|Ctrl+L, Ctrl+U|
|Widok lewej strony modelu|Ctrl+L, Ctrl+L|
|Widok prawej strony modelu|Ctrl+L, Ctrl+R|
|Widok przodu modelu|Ctrl+L, Ctrl+F|
|Widok tyłu modelu|Ctrl+L, Ctrl+B|
|Umieść obiekt w ramce w oknie|F|
|Przełącz tryb szkieletowy|Ctrl+L, Ctrl+W|
|Przełącz przyciąganie do siatki|Ctrl+G, Ctrl+N|
|Przełącz tryb obracania|Ctrl+G, Ctrl+V|
|Przełącz ograniczenie osi x|Ctrl+L, Ctrl+X|
|Przełącz ograniczenie osi y|Ctrl+L, Ctrl+Y|
|Przełącz ograniczenie osi z|Ctrl+L, Ctrl+Z|
|Przełącz do trybu przesunięcia|Ctrl+G, Ctrl+W<br /><br /> W|
|Przełącz do trybu skalowania|Ctrl+G, Ctrl+E<br /><br /> E|
|Przełącz do trybu obrotu|Ctrl+G, Ctrl+R<br /><br /> R|
|Przełącz do trybu zaznaczania punktu|Ctrl+L, Ctrl+1|
|Przełącz do trybu zaznaczania krawędzi|Ctrl+L, Ctrl+2|
|Przełącz do trybu zaznaczania powierzchni|Ctrl+L, Ctrl+3|
|Przełącz do trybu zaznaczania obiektu|Ctrl+L, Ctrl+4|
|Przełącz do trybu orbity (kamery)|Ctrl+G, Ctrl+O|
|Wybierz następny obiekt w scenie|Tab|
|Wybierz poprzedni obiekt w scenie|Shift+Tab|
|Manipuluj zaznaczonym obiektem za pomocą bieżącego narzędzia.|Klawisze strzałek|
|Dezaktywuj bieżący manipulator|Q|
|Obracanie kamery|Alt + przeciągnięcie lewym przyciskiem myszy|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi, których można użyć do pracy z zasobami graficznymi, takimi jak tekstury i obrazy, modele trójwymiarowe i efekty cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora obrazów do pracy z teksturami i obrazami.|
|[Projektant programu do cieniowania](../designers/shader-designer.md)|Opisuje, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta cieniowania do pracy z narzędziami do cieniowania.|
