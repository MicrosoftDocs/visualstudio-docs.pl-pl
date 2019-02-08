---
title: Edytor obrazów
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9783029eab9597624be459fe88b51a495328b5be
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938192"
---
# <a name="image-editor"></a>Edytor obrazów

W tym artykule opisano sposób pracy z programem Visual Studio **edytora obrazów** do wyświetlania i modyfikowania zasobów tekstur i obrazów.

Możesz użyć **edytora obrazów** do pracy z rodzajami zaawansowanych formaty tekstur i obrazów, które są używane w rozwoju aplikacji DirectX. W tym obsługę formatów plików obrazów popularnych i kodowanie kolorów, funkcje, takie jak kanałów alfa i mapowanie MIP, a wiele tekstury wysoce skompresowanym, przyspieszanych sprzętowo formaty obsługiwane przez DirectX.

## <a name="supported-formats"></a>Obsługiwane formaty

**Edytora obrazów** obsługuje następujące formaty obrazów:

|Nazwa formatu|Rozszerzenie nazwy pliku|
|-----------------| - |
|Portable Network Graphics|*.png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Bezpośrednie powierzchni rysowania|*.dds*|
|Graphics Interchange Format|*Obraz GIF*|
|Mapy bitowej|*.bmp*, *.dib*|
|Plik TIFF|*.tif*, *TIFF*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano, jak dodać obraz do projektu programu Visual Studio i skonfiguruj go zgodnie z wymaganiami dotyczącymi.

### <a name="add-an-image-to-your-project"></a>Dodawanie obrazu do projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz dodać obraz do, a następnie wybierz **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** dialogowego **zainstalowane**, wybierz opcję **grafiki**, a następnie wybierz odpowiedni format pliku obrazu.

   > [!NOTE]
   > Jeśli nie widzisz **grafiki** kategorii **Dodaj nowy element** okno dialogowe, użytkownik może być konieczne zainstalowanie **obrazów i modeli 3W edytory** składnika. Zamknij okno dialogowe, a następnie wybierz pozycję **narzędzia** > **Pobierz narzędzia i funkcje** na pasku menu, aby otworzyć **Instalatora programu Visual Studio**. Wybierz **poszczególne składniki** , a następnie wybierz pozycję **obrazów i modeli 3W edytory** składnika w obszarze **gier i aplikacji graficznych** kategorii. Wybierz **zmodyfikować**.
   >
   > ![Obrazów i modeli 3W składnika edytorów](media/image-3d-model-editors-component.png)

   Aby dowiedzieć się, jak wybrać format pliku, w zależności od wymagań, zobacz [wybierz format obrazu](#choose-the-image-format).

3. Określ **nazwa** pliku obrazu i **lokalizacji** której ma zostać utworzony.

4. Wybierz **Dodaj** przycisku.

### <a name="choose-the-image-format"></a>Wybierz format obrazu

W zależności od tego, jak zamierzasz korzystać z obrazu określonych formatów plików, może być bardziej odpowiednie niż inne. Na przykład niektóre formaty mogą nie obsługiwać format określony kolor, przezroczystość lub funkcji, których potrzebują, na przykład. Niektóre formaty mogą jednak nie zapewniać odpowiedni kompresji dla rodzaju zawartości obrazu, który zaplanowano.

Poniższe informacje mogą pomóc Ci wybrać format obrazu, który odpowiada Twoim potrzebom:

**Obraz mapy bitowej (bmp)**

Format obrazu mapy bitowej. Format obrazu nieskompresowanych, który obsługuje 24-bitowe. Mapa bitowa nie obsługuje przezroczystość.

**Obraz GIF (.gif)**

Format obrazu Graphics (Interchange Format GIF). Format obrazu skompresowanej LZW, bezstratne, która obsługuje maksymalnie 256 kolorów. Nie nadaje się do fotografii i obrazów, które znacznej ilości szczegółów kolorów, ale zapewnia współczynniki kompresji dobre na samych obrazach niska color, które mają wysoki stopień spójności kolorów.

**JPG Image (.jpg)**

Format obrazu wspólnego fotograficzne ekspertów Group (JPEG). Format wysoce skompresowanym, stratnej obrazu, który obsługuje 24-bitowe i nadaje się do ogólnego przeznaczenia kompresji obrazów, które mają wysoki stopień spójności kolor.

**Obraz PNG (.png)**

Format obrazu Portable Network Graphics (PNG). Format obrazu średnio skompresowany, bezstratne, obsługującego 24-bitowe i alfa przezroczystości. Nadaje się do zarówno naturalnych, jak i sztuczne obrazy, ale nie zapewnia współczynniki kompresji tak dobrze, jak stratnej formatów, takich jak JPG lub GIF.

**Obraz TIFF (.tif)**

Format obrazu w formacie Tagged Image File Format (TIFF lub TIF). Format obrazu elastyczne, która obsługuje kilka systemów kompresji.

**Tekstura DDS (.dds)**

Format tekstury DirectDraw Surface (DDS). Format wysoce skompresowanym, stratnej teksturę, która obsługuje 24-bitowe i alfa przezroczystości. Jego współczynniki kompresji może być możliwie jak 8:1. Jest ona oparta na kompresji tekstury S3, która może dekompresja w sprzęt graficzny.

**Obraz TGA (.tga)**

Format obrazu Truevision kartą grafiki (TGA) (znany także jako Targa). Format obrazu skompresowanej uszkodzone elementy RLE, bezstratne obsługuje zarówno mapowanych na kolor (palety kolorów) lub bezpośrednio kolor obrazy maksymalnie 24-bitowe i alfa przezroczystości. Nie nadaje się do fotografii i obrazów, które znacznej ilości szczegółów kolorów, ale zapewnia współczynniki kompresji dobre dla obrazów, które mają długi zakresów kolorów identyczne.

### <a name="configure-the-image"></a>Skonfiguruj obraz

Przed rozpoczęciem pracy z obrazem, który został utworzony, można zmienić konfiguracji domyślnej. Na przykład możesz zmienić jego wymiary lub format koloru, która jest używana. Aby uzyskać informacje o sposobie konfigurowania tych i innych właściwości obrazu, zobacz [właściwości obrazu](#image-properties).

> [!NOTE]
> Aby zapisać swoją pracę, należy ustawić **Format koloru** właściwość, jeśli chcesz użyć formatu określony kolor. Jeśli format pliku obsługuje kompresję, można dostosować ustawienia kompresji podczas zapisywania pliku po raz pierwszy lub po wybraniu **Zapisz jako**.

## <a name="work-with-the-image-editor"></a>Praca z edytora obrazów

W tej sekcji opisano sposób używania **edytora obrazów** do modyfikowania teksturami i obrazami.

Polecenia, które wpływają na stan **edytora obrazów** znajdują się na **tryb edytora obrazów** narzędzi oraz zaawansowane polecenia. Pasek narzędzi znajdują się wzdłuż krawędzi najwyższego poziomu **edytora obrazów** powierzchni projektowej. Narzędzia do rysowania znajdują się na **edytora obrazów** narzędzi wzdłuż lewej krawędzi **edytora obrazów** powierzchni projektowej.

### <a name="image-editor-mode-toolbar"></a>Pasek narzędzi tryb edytora obrazów

![Pasek narzędzi tryb edytora obrazów w programie Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

W poniższej tabeli opisano elementy na **tryb edytora obrazów** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Select**|Umożliwia wybór prostokątny obszar obrazu. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Zaznacz dowolny kształt**|Umożliwia wybór nieregularne obszaru obrazu. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Wybór Różdżka**|Umożliwia wybór podobnym kolorze obszaru obrazu. *Tolerancji*— czyli maksymalna różnica między sąsiadujących kolorów w ramach których są one traktowane jako podobne — można skonfigurować, aby uwzględnić mniejszych lub szerszy zakres podobne kolory. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Przesuwanie**|Umożliwia przenoszenie obrazu względem ramki okna. W **Pan** tryb, wybierz punkt na obrazie, a następnie przesuwaj go.<br /><br /> Można tymczasowo uaktywnić **Pan** tryb przez naciśnięcie i przytrzymanie **Ctrl** klucza.|
|**Zoom**|Umożliwia wyświetlanie więcej lub mniej szczegółów obrazu względem ramki okna. W **powiększenia** tryb, wybierz punkt na obrazie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> Można powiększyć lub pomniejszyć przez naciśnięcie i przytrzymanie **Ctrl** podczas możesz użyć kółka myszy lub naciśnij znak plus (**+**) lub znak minus (**-**) .|
|**Powiększ do rzeczywistego rozmiaru**|Wyświetla obraz przy użyciu relacji 1:1 między piksele obrazu i pikseli ekranu.|
|**Dopasuj widok do rozmiaru**|Wyświetla pełnego obrazu w ramki okna.|
|**Dopasuj widok do szerokości**|Wyświetla całą szerokość obrazu ramki okna.|
|**Siatka**|Włącza lub wyłącza siatki, który pokazuje pikseli. Siatka mogą nie być wyświetlane, dopóki powiększenie obrazu.|
|**Wyświetlanie następnego poziomu MIP**|Aktywuje następnego poziomu MIP większe w łańcuch mapy MIP. Aktywne poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|
|**Wyświetl poprzedniego poziomu MIP**|Aktywuje następnego poziomu MIP mniejszych w łańcuch mapy MIP. Aktywne poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|
|**Kanał czerwony**<br /><br /> **Kanał zielony**<br /><br /> **Kanał niebieski**<br /><br /> **Kanał alfa**|Włącza lub wyłącza kanał określony kolor. **Uwaga:**  Systematycznie włączając lub wyłączając kanałów koloru, można wyizolować problemy, które są powiązane z co najmniej jeden z nich. Na przykład można zidentyfikować niepoprawne alfa przezroczystości.|
|**Tło**|Włącza lub wyłącza wyświetlanie tło przezroczyste fragmenty obrazu. Można skonfigurować sposób wyświetlania tła, wybierając następujące opcje:<br /><br /> **Szachownica**<br /> Użyto kolor zielony, wraz z określonego tłem, aby wyświetlić tło jako wzorzec szachownicy. Ta opcja umożliwia sprawić, że przezroczysty części obrazu bardziej oczywista.<br /><br /> Białe tło<br /> Użyto kolor biały, aby wyświetlić tło.<br /><br /> Czarne tło<br /> Użyto kolor czarny, aby wyświetlić tło.<br /><br /> Tło animowane<br /> Przesuwa wzorzec szachownicy powoli. Ta opcja umożliwia sprawić, że przezroczysty części obrazu bardziej oczywista.|
|**Właściwości**|Zamiennie otwiera i zamyka **właściwości** okna.|
|**Zaawansowane**|Zawiera dodatkowe polecenia i opcje.<br /><br /> **Filtry**<br /><br /> Zapewnia kilka wspólnych filtrów obrazu: **Czarno-biały**, **Rozmycie**, **rozjaśnić**, **ciemniejszy**, **wykrywania krawędzi**, **trójwymiarowej**, **Odwróć kolory**, **Ripple**, **ton Sepia**, i **doskonalenie**.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa programu Direct3D 11 do renderowania **edytora obrazów** powierzchni projektowej.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa programu Direct3D 11 Windows Advanced rasteryzacji platformy WARP () do renderowania **edytora obrazów** powierzchni projektowej.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć w poziomie**<br /> Podstawianie obrazu wokół jego osi poziomej lub x.<br /><br /> **Przerzuć w pionie**<br /> Podstawianie obrazu wokół jego osi pionowej lub y.<br /><br /> **Generuj Mips**<br /> Generuje poziomów MIP dla obrazu. Jeśli istnieje poziomów MIP, są ponownie tworzone z największego poziomu MIP. Wszelkie zmiany wprowadzone w mniejszym poziomom MIP zostaną utracone. Aby zapisać poziomów MIP, które zostały wygenerowane, należy użyć *.dds* formatu w celu zapisania obrazu.<br /><br /> **Widok**<br /><br /> **Szybkość klatek**<br /> Po włączeniu Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. **Porada:** Możesz wybrać **zaawansowane** przycisk, aby ponownie uruchomić ostatnie polecenie.|

### <a name="image-editor-toolbar"></a>Pasek narzędzi edytora obrazów

![Pasek narzędzi edytora obrazów](../designers/media/digit-tre-toolbar.png)

W poniższej tabeli opisano elementy na **edytora obrazów** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od góry do dołu:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Ołówka**|Używa kodowania aktywnego koloru do rysowania pociągnięcie aliasem. Można ustawić kolor i grubość obrysu w **właściwości** okna.|
|**Pędzel**|Używa kodowania aktywnego koloru do rysowania pociągnięcie wygładzanie. Można ustawić kolor i grubość obrysu w **właściwości** okna.|
|**Aerograf**|Używa wybór koloru active do rysowania pociągnięcie wygładzanie miesza wraz z obrazu, która staje się bardziej nasycony funkcji czasu. Można ustawić kolor i grubość obrysu w **właściwości** okna.|
|**Eyedropper**|Ustawia kolor wybrany piksel wybór koloru active.|
|**Wypełnienie**|Używa wybór koloru active do wypełnienia obszaru obrazu. Dotyczy region jest zdefiniowany jako pikseli, w których stosowane wypełnienie wraz z każdy piksel, który jest z nią połączona pikseli tego samego koloru i to ten sam kolor, sam. Jeśli wypełnienie jest stosowana w ramach aktywnego zaznaczenia, dotyczy region jest ograniczone przez zaznaczenie.<br /><br /> Domyślnie wybór koloru active jest zmieszana wraz z zainfekowanego region obrazu zgodnie z jego składnik alfa. Aby użyć wybór koloru active zastąpić dotyczy region, naciśnij i przytrzymaj klawisz **Shift** klucza podczas używania narzędzia wypełnienia.|
|**Gumka**|Jeśli obraz, który obsługuje kanał alfa, ustawia piksele, aby całkowicie przezroczysty kolor. W przeciwnym razie piksele Ustawia kolor tła active.|
|**Wiersz**, **prostokąt**, **prostokąt zaokrąglony**, **wielokropka**|Rysuje kształt na obrazie. Można ustawić kolor i grubość konturu w **właściwości** okna.<br /><br /> Aby narysować elementu podstawowego, który ma równa szerokość i wysokość, naciśnij i przytrzymaj **Shift** podczas rysowania.|
|**Text**|Używa wybór koloru pierwszego planu, aby rysować tekst. Kolor tła jest określany przez wybór koloru tła. Dla przezroczyste tło wartość alfa wybór koloru tła musi być 0. Gdy obszaru tekstu jest aktywna, można ustalić, czy tekst jest rysowana obrysu wygładzanie i można ustawić tekst **wartość**, **czcionki**, **rozmiar**, styl i —**Bold**, **Kursywa**, lub **podkreślona**— w **właściwości** okna. Zawartość i wygląd tekstu jest aktualnie finalizowana, gdy region tekst nie jest już aktywna.|
|**Obróć**|Obrót 90 stopni w prawo.|
|**TRIM**|Przycina obraz do aktywnego zaznaczenia.|

### <a name="work-with-mip-levels"></a>Praca z poziomów MIP

Niektóre obraz formatów, na przykład, DirectDraw Surface (*.dds*), Obsługa poziomów MIP przestrzeni tekstury poziomu z Detail (poziomu). Aby uzyskać informacje o tym, jak generować i pracować z poziomami MIP, zobacz [jak: Tworzenie i modyfikacja poziomów MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Praca z przezroczystością

Niektóre obraz formatów, na przykład, DirectDraw Surface (*.dds*), obsługują przezroczystość. Istnieje kilka sposobów, można użyć przezroczystości, w zależności od tego narzędzia, którego używasz. Aby określić stopień przejrzystości dla wyboru koloru w **właściwości** oknie **A** składnik (alfa) wybór koloru.

W poniższej tabeli opisano, jak różne rodzaje kontroli narzędzi, jak przezroczystości są stosowane:

|Narzędzie|Opis|
|----------|-----------------|
|**Ołówek**, **pędzla**, **Aerograf**, **wiersza**, **prostokąt**, **prostokąt zaokrąglony** , **Elipsy**, **tekstu**|Aby dopasować wybór koloru aktywne, wraz z obrazu, w **właściwości** okna, rozwiń węzeł **kanały** grupy właściwości i ustaw **Rysowanie** pole wyboru na  **Alfa** kanał, a następnie narysuj normalnie.<br /><br /> Aby narysować przy użyciu wybór koloru aktywne i pozostawić wartość alfa odpowiadającą obrazu w miejscu, należy wyczyścić **Rysowanie** obok **alfa** kanał, a następnie narysuj normalnie.|
|**Wypełnienie**|Aby dopasować wybór koloru aktywne, wraz z obrazu, po prostu wybrać obszar, aby wypełnić.<br /><br /> Umożliwia wybór koloru active — z uwzględnieniem wartości kanał alfa — Aby zastąpić obraz, naciśnij i przytrzymaj klawisz **Shift** , a następnie wybierz obszar, aby wypełnić.|

### <a name="image-properties"></a>Właściwości obrazu

Możesz użyć **właściwości** okna, aby określić różne właściwości obrazu. Na przykład można ustawić właściwości szerokości i wysokości rozmiaru.

W poniższej tabeli opisano właściwości obrazu:

|Właściwość|Opis|
|--------------|-----------------|
|Szerokość|Szerokość obrazu.|
|Wysokość|Wysokość obrazu.|
|Liczba bitów na piksel|Liczba bitów, które reprezentują każdego piksela. Wartość tej właściwości zależy od **Format koloru** obrazu.|
|Zaznaczenie przezroczyste|**Wartość true,** mieszania warstwy wybór wraz z głównym obrazu, na podstawie wartości alfa warstwy wyboru; w przeciwnym razie **False**. Ten element jest dostępna tylko dla obrazów, które obsługują alfa.|
|Format|Format koloru z obrazu. Można określić wiele formatów kolorów, zależnie od formatu obrazu. Format koloru definiuje liczbę i rodzaj kanałów koloru, które są uwzględniane w obrazie, a także rozmiar i kodowanie różnych kanałów.|
|Poziom mipmapy|Aktywne poziom MIP. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|
|Liczba poziomów MIP|Całkowita liczba poziomów MIP na obrazie. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|
|Liczba ramek|Całkowita liczba klatek na obrazie. Ten element jest dostępna tylko dla obrazów, które obsługuje tablic tekstury.|
|Klatka|Bieżąca ramka. Mogą być wyświetlane tylko pierwsza ramka; wszystkie inne ramki zostaną utracone przy zapisywaniu obrazu.|
|Liczba wycinków głębi|Całkowita liczba wycinków głębi w obrazie. Ten element jest dostępna tylko dla obrazów, które obsługują tekstury woluminu.|
|Wycinek głębokości|Bieżącego wycinka głębi. Mogą być wyświetlane tylko pierwszy wycinek; wszystkie inne wycinki zostaną utracone podczas zapisywania obrazu.|

> [!NOTE]
> Ponieważ **obrócić** właściwość ma zastosowanie do wszystkich narzędzi i wybranych regionach, zawsze pojawia się w dolnej części **właściwości** okna wraz z innymi właściwości narzędzia. **Obróć przez** zawsze jest wyświetlany, ponieważ obraz całej niejawnie zostaje wybrany, gdy nie ma żadnych wyboru ani narzędzie active. Aby uzyskać więcej informacji na temat **obrócić** właściwości, zobacz [narzędzia właściwości](#tool -properties).

### <a name="resize-images"></a>Zmiana rozmiaru obrazów

Istnieją dwa sposoby, aby zmienić rozmiar obrazu. W obu przypadkach **edytora obrazów** używa warianty punktowego interpolacji do próbkowania obrazu.

- W **właściwości** okna, określ nowe wartości **szerokość** i **wysokość** właściwości.

- Wybierz całego obrazu, a następnie zmień rozmiar obrazu za pomocą znaczników obramowania.

### <a name="selected-regions"></a>Wybranych regionach

Opcje na **edytora obrazów** zdefiniować regiony obrazu, które są aktywne. Aktywne regiony są zagrożone narzędzi i przekształcenia. W przypadku aktywnego zaznaczenia poza wybrany region nie dotyczy większości narzędzi i przekształcenia. Jeśli nie ma aktywnego zaznaczenia, całego obrazu jest aktywny.

Większość narzędzi (**ołówka**, **pędzla**, **Aerograf**, **wypełnienia**, **Gumka**i 2D podstawowych) i przekształcenia (**Obróć**, **Trim**, **Odwróć kolory**, **Przerzuć w poziomie**, i **Przerzuć w pionie** ) są ograniczone lub zdefiniowany przez aktywnego zaznaczenia. Jednak niektóre narzędzia (**Pipeta** i **tekstu**) i przekształcenia (**Generuj Mips**) nie ma wpływu na dowolnym aktywnego zaznaczenia. Te narzędzia zawsze zachowują się tak, jakby cały obraz jest aktywnego zaznaczenia.

Podczas wyboru regionu, można nacisnąć i przytrzymać **Shift** proporcjonalna Zaznaczanie (kwadratowy). W przeciwnym razie zaznaczenia nie jest ograniczona.

#### <a name="resize-selections"></a>Zmień rozmiar zaznaczenia

Po wybraniu regionu, możesz zmienić rozmiar on lub jego zawartość obrazu, zmieniając rozmiar znacznika wyboru. Natomiast w przypadku zmiany rozmiaru wybranego regionu, można użyć następujące klawisze modyfikujące, aby zmienić zachowanie wybranego regionu, gdy zmieniasz rozmiar:

**CTRL** — kopiuje zawartość wybranego regionu, zanim zmiany jego rozmiaru. Spowoduje to pozostawienie oryginalny obraz bez zmian podczas zmiany rozmiaru kopii.

**SHIFT** — zmienia rozmiar wybranego regionu, proporcjonalnie do oryginalnego rozmiaru.

**ALT** — zmienia rozmiar regionu zaznaczenia. Spowoduje to pozostawienie obrazu w niezmienionej postaci.

W poniższej tabeli opisano modyfikator prawidłowe kombinacje klawiszy:

|Ctrl|Shift|Alt|Opis|
|----------|-----------|---------|-----------------|
||||Zmienia rozmiar zawartości wybranego regionu.|
||**SHIFT**||Proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|
|||**ALT**|Zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
||**SHIFT**|**ALT**|Proporcjonalnie zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
|**Ctrl**|||Kopiuje, a następnie zmienia rozmiar zawartości wybranego regionu.|
|**Ctrl**|**SHIFT**||Kopiuje, a następnie proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|

### <a name="tool-properties"></a>Właściwości narzędzia

To narzędzie jest zaznaczone, ale można używać **właściwości** okna możliwość określania szczegółów o tym jak wpływa na obrazie. Na przykład można ustawić grubość **ołówka** narzędzia lub kolor **pędzla** narzędzia.

Możesz ustawić kolor pierwszego planu i kolor tła. Obie obsługują kanał alfa, zapewnienie nieprzezroczystość zdefiniowanych przez użytkownika. Ustawienia są stosowane do wszystkich narzędzi. Jeśli używasz myszy, lewy przycisk myszy odpowiada kolor pierwszego planu, a następnie prawym przyciskiem myszy odpowiada kolor tła.

W poniższej tabeli opisano właściwości narzędzia:

|Narzędzie|Właściwości|
|----------|----------------|
|Wszystkie narzędzia i opcje|**Obróć o**<br /> Określa, w stopniach, czy zaznaczenie lub narzędzia efekt jest obracana wskazówek zegara.|
|**Ołówek**, **pędzla**, **Aerograf**, **Gumka**|**Grubość**<br /> Określa rozmiar obszaru, który jest zależna od narzędzia.|
|**Text**|**Wygładzanie**<br /> Rysuje tekst, który ma wygładzanie krawędzi. Dzięki temu tekst gładsze wygląd.<br /><br /> **Wartość**<br /> Tekst do narysowania.<br /><br /> **Czcionka**<br /> Czcionka używana ma zostać narysowany tekst.<br /><br /> **Rozmiar**<br /> Rozmiar tekstu.<br /><br /> **Bold**<br /> Sprawia, że czcionka pogrubienie.<br /><br /> **Kursywa**<br /> Sprawia, że czcionka italic.<br /><br /> **Podkreślony**<br /> Sprawia, że czcionka podkreślone.|
|**2D podstawowego**|**Wygładzanie**<br /> Rysuje podstawowych, które mają wygładzanie krawędzi. To daje im gładsze wygląd.<br /><br /> **Grubość**<br /> Określa grubość linii, który wchodzi w skład granicy podstawowego.<br /><br /> **Promień X**<br /> (Tylko w przypadku prostokąt zaokrąglony) Definiuje górną i dolną krawędzią element pierwotny zaokrąglania usługi radius.<br /><br /> **Promień Y**<br /> (Tylko w przypadku prostokąt zaokrąglony) Definiuje zaokrąglania usługi radius do lewej i prawej krawędzi element pierwotny.|
|**Pencil**, **Brush**, **Airbrush**, **2D Primitive**|**Channels**<br /> Włącza lub wyłącza określony kolor kanały do wyświetlania i rysowania. Jeśli **widoku** jest ustawiona dla określonego kanału koloru, tym kanale jest widoczne na obrazie; w przeciwnym razie nie jest on widoczny. Jeśli **Rysowanie** ustawiono dla określonego kanału koloru, że kanał jest objęte za pomocą rysowania operacji; w przeciwnym razie, nie jest.|
|**Wybór Różdżka**, **wypełnienia**|**Tolerance**<br /> Definiuje maksymalną różnicę między sąsiadujących kolorów, w których są one traktowane jako podobnie, tak aby mniej lub bardziej podobne kolory zostały wprowadzone w ramach objęty lub wybranego regionu. Domyślnie wartość jest 32, co oznacza, że sąsiadujących pikseli w ciągu 32 odcienie koloru oryginalnego (jaśniejsze i ciemniejsze) są traktowane jako część obszaru.|

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełącz się do **wybierz** tryb|**S**|
|Przełącz się do **powiększenia** tryb|**Z**|
|Przełącz się do **Pan** tryb|**K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Delete**|
|Anuluj bieżące zaznaczenie|**ESC** (ucieczki)|
|Powiększanie|**CTRL**+**kółkiem myszy do przodu**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Znak plus (**+**)|
|Pomniejszanie|**CTRL**-**obrót kółkiem myszy do tyłu**<br /><br /> **Ctrl**-**PageDown**<br /><br /> Znak minus (**-**)|
|Przesuń w górę obrazu|**Obrót kółkiem myszy do tyłu**<br /><br /> **PageDown**|
|Przesuń w dół obrazu|**Obrót kółkiem myszy do przodu**<br /><br /> **PageUp**|
|Przesuń obrazu po lewej|**SHIFT**+**obrót kółkiem myszy do tyłu**<br /><br /> **Obrót kółkiem myszy w lewo**<br /><br /> **Shift**+**PageDown**|
|Przesuń w prawo obrazu|**SHIFT**+**kółkiem myszy do przodu**<br /><br /> **Obrót kółkiem myszy do prawej**<br /><br /> **SHIFT**+**PageUp**|
|Powiększ do rzeczywistego rozmiaru|**CTRL**+**0** (zero)|
|Dopasuj obraz do okna|**Ctrl**+**G**, **Ctrl**+**F**|
|Obraz Dopasuj do szerokości okna|**Ctrl**+**G**, **Ctrl**+**I**|
|Przełącz siatkę|**Ctrl**+**G**, **Ctrl**+**G**|
|Przytnij obraz do bieżącego zaznaczenia|**Ctrl**+**G**, **Ctrl**+**C**|
|Wyświetlanie następnego (szczegóły wyższej) Poziom MIP|**Ctrl**+**G**, **Ctrl**+**6**|
|Wyświetl poprzednie (niższe szczegóły) Poziom MIP|**Ctrl**+**G**, **Ctrl**+**7**|
|Przełącz kanału koloru czerwonego|**Ctrl**+**G**, **Ctrl**+**1**|
|Przełącz kolor zielony kanału|**Ctrl**+**G**, **Ctrl**+**2**|
|Przełącz koloru niebieskiego kanału|**Ctrl**+**G**, **Ctrl**+**3**|
|Przełącz kanał alfa (przezroczystości)|**Ctrl**+**G**, **Ctrl**+**4**|
|Przełącz wzorzec szachownicy alfa|**Ctrl**+**G**, **Ctrl**+**B**|
|Przełącz się do kształt-narzędzie|**L**|
|Przejdź do narzędzia zaznaczania Różdżka|**M**|
|Przełącz do Ołówek narzędzia|**P**|
|Przełącz się do narzędzia pędzla|**B**|
|Przełącz do Wypełnianie kolorem-narzędzie|**F**|
|Przejdź do narzędzia Gumka|**E**|
|Przełącz się do narzędzie tekstowe|**T**|
|Przejdź do narzędzia zaznaczania kolorów (Pipeta)|**I**|
|Przenoszenie aktywnego zaznaczenia i jego zawartość.|**Strzałka** kluczy.|
|Zmień rozmiar aktywnego zaznaczenia i jego zawartość.|**CTRL**+**strzałkę** kluczy|
|Przenoszenie aktywnego zaznaczenia, ale nie jego zawartość.|**SHIFT**+**strzałkę** kluczy|
|Zmień rozmiar aktywnego zaznaczenia, ale nie jego zawartość.|**SHIFT**+**Ctrl**+**strzałkę** kluczy|
|Bieżąca warstwa zatwierdzenia|**Return**|
|Zmniejsz grubość narzędzia|**[**|
|Zwiększ grubość narzędzia|**]**|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Omówienie narzędzi, których można użyć w programie Visual Studio do pracy z zasobami grafiki, takie jak tekstury i obrazy, modele 3D i efekty cieniowania.|
|[Edytor modelu](../designers/model-editor.md)|Opisuje sposób używania edytora modelu programu Visual Studio do pracy z modelami 3D.|
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje sposób używania projektanta programu do cieniowania programu Visual Studio do pracy z programów do cieniowania.|