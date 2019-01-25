---
title: Model Editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9247eae19d32ecc21069836d52192e7d466de1b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802843"
---
# <a name="model-editor"></a>Edytor kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano sposób pracy z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora modelu do wyświetlania, tworzenia i modyfikowania modeli 3D.  
  
 Edytor modelu może być użyty do tworzenia podstawowych modeli trójwymiarowych od początku lub do wyświetlania i modyfikowania bardziej złożonych modeli trójwymiarowych, utworzonych przy użyciu profesjonalnych narzędzi do modelowania trójwymiarowego. Edytor modelu obsługuje kilka formatów modeli 3-W, które są używane w rozwoju aplikacji DirectX.  
  
## <a name="supported-formats"></a>Obsługiwane formaty  
 Edytor modelu obsługuje następujące formaty modeli:  
  
|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|  
|-----------------|--------------------|-------------------------------------------------|  
|Plik wymiany AutoDesk FBX|.fbx|Wyświetl, edytuj, utwórz|  
|Plik w formacie Collada DAE|.dae|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|  
|OBJ|.obj|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|  
  
## <a name="getting-started"></a>Wprowadzenie  
 Ta sekcja zawiera opis sposobu dodawania modelu 3-w do Twojej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu i zawiera podstawowe informacje wymagane do rozpoczęcia pracy.  
  
#### <a name="to-add-a-3-d-model-to-your-project"></a>Aby dodać model 3-W do projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz dodać obraz do, a następnie wybierz **Dodaj**, **nowy element**.  
  
2.  W **Dodaj nowy element** dialogowego **zainstalowane**, wybierz opcję **grafiki**, a następnie wybierz pozycję **Scena 3D (.fbx)**.  
  
3.  Określ **nazwa** pliku modelu i **lokalizacji** której ma zostać utworzony.  
  
4.  Wybierz **Dodaj** przycisku.  
  
### <a name="axis-orientation"></a>Orientacja osi  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje każdą orientację osi 3-w i ładuje informacje o orientacji osi z formatów plików modeli, które go obsługują. Jeśli określono nie orientacji osi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] domyślnie używa prawostronnego układu współrzędnych. **Wskaźnik osi** pokazuje bieżącą orientację osi w prawym dolnym rogu powierzchni projektowej. Na **wskaźnik osi**kolor czerwony odpowiada osi x, zielony reprezentuje oś y, a niebieski odpowiada osi z.  
  
### <a name="beginning-your-3-d-model"></a>Rozpoczynanie tworzenia modelu 3-W  
 W edytorze modelu każdy nowy obiekt zawsze rozpoczyna się jako jeden z podstawowych kształtów 3-w — lub *podstawowych*— wbudowanych w Edytor modelu. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby uzyskać informacje o sposobie dodawania prymitywów do sceny, zobacz [tworzenie i importowanie obiektów 3-](#Adding3DObjects). Aby uzyskać informacje o tym, jak dodać więcej wierzchołków do obiektu, zobacz [modyfikowanie obiektów](#ModifyingObjects).  
  
## <a name="working-with-the-model-editor"></a>Praca z Edytorem modelu  
 W poniższych sekcjach opisano sposób używania Edytora modelu do pracy z modelami trójwymiarowymi.  
  
### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu  
 Na paskach narzędzi Edytora modelu są dostępne polecenia ułatwiające pracę z modelami 3-W.  
  
 Polecenia, które wpływają na stan edytora modelu znajdują się na **tryb edytora modelu** narzędzi w oknie głównym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna. Narzędzia do modelowania i polecenia skryptowe znajdują się na **edytora modelu** paska narzędzi na powierzchni projektowania edytora modelu.  
  
 Oto **tryb edytora modelu** narzędzi:  
  
 ![Przeglądarka modelu modalne paska narzędzi. ](../designers/media/digit-mre-modal-toolbar.png "Cyfry MRE-modalne — pasek narzędzi")  
  
 W tej tabeli opisano elementy na **tryb edytora modelu** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od lewej do prawej.  
  
|Element paska narzędzi|Opis|  
|------------------|-----------------|  
|**Select**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|  
|**Przesuwanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać klawisz Ctrl, aby aktywować **Pan** tymczasowo w trybie.|  
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenia** tryb, wybierz punkt w scenie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> W **wybierz** trybie można powiększyć lub przy użyciu kółka myszy naciśnij i przytrzymaj klawisz Ctrl.|  
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  W tym trybie nie ma efektu, gdy **prostopadły** jest włączone rzutowanie.|  
|**World Local**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|  
|**Tryb obrotu**|Po włączeniu tego elementu przekształcenia wpływają na położenie i orientację *punkt obrotu* wybranego obiektu (punkt obrotu definiuje środek operacji przesunięcia, skalowania i obrót). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|  
|**Zablokuj oś X**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|  
|**Zablokuj oś Y**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|  
|**Zablokuj oś Z**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|  
|**Obiekt w ramce**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|  
|**Widok**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **Frontonu**<br /> Umieszcza widok przed sceną.<br /><br /> **Wstecz**<br /> Umieszcza widok za sceną.<br /><br /> **po lewej stronie**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **po prawej stronie**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **dolny**<br /> Umieszcza widok pod sceną. **Uwaga:**  Jest to jedyny sposób zmiany kierunku widoku po **prostopadły** jest włączone rzutowanie.|  
|**Projekcja**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywa**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Ortogonalnym**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **prostopadły** włączono projekcję, nie można użyć **Orbita** trybu do ustawienia widoku.|  
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Szkielet**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Overdraw**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskie cieniowanie**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|  
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] odrysowuje powierzchnię projektu, nawet wtedy, gdy jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|  
|**Przełącz siatkę**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|  
|**Przybornik**|Zamiennie pokazuje i ukrywa **przybornika**.|  
|**Konspekt dokumentu**|Zamiennie pokazuje i ukrywa **konspekt dokumentu** okna.|  
|**Właściwości**|Zamiennie pokazuje i ukrywa **właściwości** okna.|  
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceną**<br /><br /> **Importujuj**<br /> Importuje obiekty z innego pliku modelu 3-W do bieżącej sceny.<br /><br /> **Dołącz do nadrzędnego**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłącz od nadrzędnego**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Zaznaczony obiekt staje się *główny obiekt* w scenie. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Tworzenie grupy**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scal obiekty**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Utwórz nowy obiekt z zaznaczenia wielokątnego**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć w Wielokącie**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacje**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Triangulacji**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Widok**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Szybkość klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna po włączeniu **tryb renderowania w czasie rzeczywistym** opcji.<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **ukryty** właściwości obiektu do **False**.<br /><br /> **Pokaż normalne powierzchni**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brakujące materiały**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokazuj przestawne**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3-W w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Pokaż węzły zastępcze**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż normalne wierzchołka**<br /> Pokazuje normalną każdego wierzchołka. **Porada:**  Możesz wybrać **skrypty** przycisk, aby ponownie uruchomić ostatni skrypt.|  
  
 Oto **edytora modelu** narzędzi:  
  
 ![Model pasku narzędzi programu Pomoc](../designers/media/digit-mre-toolbar.png "cyfry-MRE — pasek narzędzi")  
  
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
|**Extrude**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|  
|**Dzielenie**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|  
  
### <a name="controlling-the-view"></a>Kontrolowanie widoku  
 Scena 3-W jest renderowana zgodnie z widokiem. Można go traktować jako wirtualną kamerę, która ma pozycję i orientację. Aby zmienić położenie i orientację, użyj formantów widoku na **tryb edytora modelu** paska narzędzi.  
  
 W poniższej tabeli opisano formanty widoku podstawowego.  
  
|Formant widoku|Opis|  
|------------------|-----------------|  
|**Przesuwanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać klawisz Ctrl, aby aktywować **Pan** tymczasowo w trybie.|  
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenia** tryb, wybierz punkt w scenie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> W **wybierz** trybie można powiększyć lub przy użyciu kółka myszy naciśnij i przytrzymaj klawisz Ctrl.|  
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:**  W tym trybie nie ma efektu, gdy **prostopadły** jest włączone rzutowanie.|  
|**Obiekt w ramce**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|  
  
 Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na **edytora modelu** narzędzi, możesz wybrać dowolną **perspektywy** lub **prostopadły** projekcji.  
  
|Rzut|Opis|  
|----------------|-----------------|  
|**Perspektywa**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|  
|**Ortogonalnym**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **prostopadły** włączono projekcję, nie można użyć **Orbita** trybu do ustawienia widoku arbitralnie.|  
  
 Przydatne może okazać się wyświetlenie sceny trójwymiarowej ze znanego położenia i kąta, na przykład, gdy chcesz porównać dwie podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku, na **tryb edytora modelu** narzędzi wybierz **widoku**, a następnie wybierz wstępnie zdefiniowany widok ma — przodu, z tyłu, lewo, prawo, top lub bottom. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład, jeśli wybierzesz **Pokaż pierwszy wiersz**, wirtualna kamera spojrzy na źródło sceny bezpośrednio znad niej.  
  
### <a name="viewing-additional-geometry-details"></a>Wyświetlanie dodatkowych szczegółów geometrii  
 Aby lepiej zrozumieć obiekt lub scenę 3-W, można wyświetlić dodatkowe szczegóły geometrii, np. normalne wierzchołka, normalne powierzchni, punkty obrotu aktywnego zaznaczenia i inne szczegóły. Aby je włączyć lub wyłączyć, na **edytora modelu** narzędzi wybierz **skrypty**, **widoku**, a następnie wybierz żądaną opcję.  
  
###  <a name="Adding3DObjects"></a> Tworzenie i importowanie obiektów 3-w  
 Aby dodać wstępnie zdefiniowany kształt 3-w do sceny, w **przybornika**, wybierz jedną, a następnie przenieś go do powierzchni projektowej. Nowe kształty są umieszczane w źródle sceny. Edytor modelu zawiera siedem kształtów: **Stożek**, **modułu**, **Cylinder**, **dysku**, **płaszczyzny**, **kuli**i **Czajniczek**.  
  
 Aby importować obiekt 3-w z pliku, na **edytora modelu** narzędzi wybierz **zaawansowane**, **Zarządzanie sceną**, **zaimportować**, a następnie określ plik, który chcesz zaimportować.  
  
### <a name="transforming-objects"></a>Przekształcanie obiektów  
 Możesz *Przekształcanie* obiektu przez zmianę jego **obrotu**, **skalowania**, i **tłumaczenia** właściwości. *Obrót* ustawia obiekt przez zastosowanie kolejnych rotacji wokół osi x, y i z określonych przez jego punkt obrotu. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** zmienia rozmiar obiektu, rozciągając go o określony współczynnik wzdłuż jednej lub wielu osi wyśrodkowanych względem punktu obrotu. *Tłumaczenie* lokalizuje obiekt w 3-wymiarowej, względem jego elementu nadrzędnego, a nie jego punktu obrotu.  
  
 Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.  
  
##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Aby przekształcić obiekt za pomocą narzędzi do modelowania  
  
1.  W **wybierz** tryb, wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.  
  
2.  Na **edytora modelu** narzędzi, wybierz **Translate**, **skalowania**, lub **Obróć** narzędzia. Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.  
  
3.  Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.  
  
##### <a name="to-transform-an-object-by-setting-its-properties"></a>Aby przekształcić obiekt przez ustawienie jego właściwości  
  
1. W **wybierz** tryb, wybierz obiekt, który chcesz przekształcić. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.  
  
2. W **właściwości** okna, podaj wartości dla **obrotu**, **skalowania**, i **tłumaczenia** właściwości.  
  
   > [!IMPORTANT]
   >  Aby uzyskać **obrotu** właściwości, określ kąt obrotu wokół każdej z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.  
  
   Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.  
  
   Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **manipulacja** włączyć (lub wyłączyć) tryb dowolnego kształtu. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na **tryb edytora modelu** narzędzi, wybierz dowolną kombinację **Zablokuj X**, **Zablokuj Y**, i **Zablokuj Z** przycisków.  
  
   Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na **tryb edytora modelu** narzędzi, wybierz **przyciąganie** włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.  
  
### <a name="working-with-the-pivot-point"></a>Praca z punktem obrotu  
 Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na **tryb edytora modelu** narzędzi, wybierz **tryb obrotu** można włączyć (lub wyłączyć) tryb obrotu. Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć **tłumaczenia** i **obrotu** narzędzia do manipulowania punktem obrotu.  
  
 Demonstracyjne, który pokazuje, jak używać punktu obrotu, zobacz [jak: Modyfikowanie punktu obrotu modelu 3-D](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).  
  
### <a name="world-and-local-modes"></a>Tryby lokalne i świata  
 Przesunięcie i obrót mogą występować albo w lokalnym układzie współrzędnych (lub *lokalnej ramce odniesienia*) obiektu, albo w układzie współrzędnych świata (lub *ramce odniesienia world*). Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) tryb świata, na **tryb edytora modelu** narzędzi, wybierz **WorldLocal** przycisku.  
  
###  <a name="ModifyingObjects"></a> Modyfikowanie obiektów  
 Kształt obiektu 3-W można zmienić, przenosząc lub usuwając jego wierzchołki, krawędzie i powierzchnie. Domyślnie Edytor modelu jest w *trybie obiektu*, dzięki czemu można wybierać i przekształcać całe obiekty. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na **tryb edytora modelu** narzędzi, wybierz **tryby wyboru**, a następnie wybierz żądany tryb.  
  
 Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.  
  
##### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu  
  
1.  W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.  
  
2.  Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **wyciągnięcie**.  
  
##### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze  
  
1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.  
  
2. Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **Podziel na mniejsze**.  
  
   Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.  
  
##### <a name="to-triangulate-a-face"></a>Aby przeprowadzić triangulację powierzchni  
  
1.  W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.  
  
2.  Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **triangulacja**.  
  
##### <a name="to-merge-objects"></a>Aby scalić obiekty  
  
1.  W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.  
  
2.  Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **Scal obiekty**.  
  
##### <a name="to-create-an-object-from-a-polygon-selection"></a>Aby utworzyć obiekt z zaznaczenia wielokątnego  
  
1.  W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.  
  
2.  Na **edytora modelu** narzędzi, wybierz **skrypty**, **narzędzia**, **Utwórz nowy obiekt z zaznaczenia wielokątnego**.  
  
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
  
 W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W **wybierz** tryb, wybierz obiekt, którego materiał chcesz zmienić, a następnie w polu **właściwości** oknie zmiany **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, lub inne dostępne właściwości. Materiał może udostępniać do ośmiu tekstur, którego właściwości są nazywane kolejno od **Texture1** do **tekstura8**.  
  
 Aby usunąć wszystkie materiały z obiektu na **edytora modelu** narzędzi, wybierz **skrypty**, **materiałów**, **usuwanie materiałów**.  
  
 Możesz użyć **Shader Designer** utworzyć niestandardowe materiały modułu cieniującego, które można zastosować do obiektów 3-D sceny. Aby uzyskać informacje o tym, jak utworzyć niestandardowe materiały modułu cieniującego, zobacz [Shader Designer](../designers/shader-designer.md). Aby uzyskać informacje dotyczące sposobu stosowania niestandardowego materiału cieniowania do obiektu, zobacz [jak: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
### <a name="scene-management"></a>Zarządzanie sceną  
 Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.  
  
 Możesz użyć **konspekt dokumentu** okna, aby wyświetlić hierarchię sceny i wybrać węzły sceny. Po wybraniu węzła konspektu można użyć **właściwości** okna, aby zmodyfikować jego właściwości.  
  
 Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.  
  
##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Aby utworzyć hierarchię zawierającą obiekt nadrzędny  
  
1.  W **wybierz** tryb, wybierz dwa lub więcej obiektów. Pierwszy wybrany będzie obiektem nadrzędnym.  
  
2.  Na **edytora modelu** narzędzi, wybierz **skrypty**, **Zarządzanie sceną**, **Dołącz do nadrzędnego**.  
  
##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Aby utworzyć obiekty hierarchii elementów równorzędnych  
  
1. W **wybierz** tryb, wybierz dwa lub więcej obiektów. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.  
  
2. Na **edytora modelu** narzędzi, wybierz **skrypty**, **Zarządzanie sceną**, **Utwórz grupę**.  
  
   Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Aby wyświetlić węzły zastępcze na **edytora modelu** narzędzi, wybierz **skrypty**, **Zarządzanie sceną**, **Pokaż węzły zastępcze**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.  
  
   Aby usunąć skojarzenie nadrzędny podrzędny między dwoma obiektami, zaznacz obiekt podrzędny, a następnie na **edytora modelu** narzędzi, wybierz **skrypty**, **Zarządzanie sceną**, **Odłącz od nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.  
  
## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
  
|Polecenie|Skróty klawiaturowe|  
|-------------|------------------------|  
|Przełącz się do **wybierz** tryb|Ctrl+G, Gtrl+Q<br /><br /> S|  
|Przełącz się do **powiększenia** tryb|Ctrl+G, Ctrl+Z<br /><br /> Z|  
|Przełącz się do **Pan** tryb|Ctrl+G, Ctrl+P<br /><br /> K|  
|Zaznacz wszystkie|Ctrl+A|  
|Usuń bieżące zaznaczenie|Usuwanie|  
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
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia, które służą do pracy z zasobami grafiki, takie jak tekstury i obrazy, modele 3D i efekty cieniowania.|  
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora obrazów do pracy z teksturami i obrazami.|  
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta modułu cieniującego do pracy z programów do cieniowania.|
