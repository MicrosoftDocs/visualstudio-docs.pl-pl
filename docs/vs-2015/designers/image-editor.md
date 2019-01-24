---
title: Edytor obrazów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0bda440c463082d62568bcdfd0525eebe2a17c61
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768306"
---
# <a name="image-editor"></a>Edytor obrazów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano sposób pracy z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora obrazów do wyświetlania i modyfikowania zasobów tekstur i obrazów.  
  
 Edytor obrazów można użyć do pracy z rodzajami zaawansowanych formaty tekstur i obrazów, które są używane w rozwoju aplikacji DirectX — w tym obsługę formatów plików obrazów popularnych i kodowanie kolorów, funkcje, takie jak kanałów alfa i mapowanie MIP oraz wielu wysoce skompresowany, przyspieszanych sprzętowo tekstury w formatach obsługiwanych przez DirectX.  
  
## <a name="supported-formats"></a>Obsługiwane formaty  
 Edytor obrazów obsługuje następujące formaty obrazów:  
  
|Nazwa formatu|Rozszerzenie nazwy pliku|  
|-----------------|-------------------------|  
|Portable Network Graphics|.png|  
|JPEG|.jpg, .jpeg, .jpe, .jfif|  
|Bezpośrednie powierzchni rysowania|.dds|  
|Graphics Interchange Format|.gif|  
|Mapy bitowej|.bmp, .dib|  
|Plik TIFF|.tif, .tiff|  
|TGA (Targa)|.TGA|  
  
## <a name="getting-started"></a>Wprowadzenie  
 W tej sekcji opisano sposób dodawania obrazu do usługi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu, a następnie skonfigurować go do swoich wymagań.  
  
#### <a name="to-add-an-image-to-your-project"></a>Aby dodać obraz do projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz dodać obraz do, a następnie wybierz **Dodaj**, **nowy element**.  
  
2.  W **Dodaj nowy element** dialogowego **zainstalowane**, wybierz opcję **grafiki**, a następnie wybierz odpowiedni format pliku obrazu. Aby dowiedzieć się, jak wybrać format pliku, w zależności od wymagań zobacz następującą sekcję.  
  
3.  Określ **nazwa** pliku obrazu i **lokalizacji** której ma zostać utworzony.  
  
4.  Wybierz **Dodaj** przycisku.  
  
### <a name="choosing-the-image-format"></a>Wybieranie formatu obrazu  
 W zależności od tego, jak zamierzasz korzystać z obrazu określonych formatów plików, może być bardziej odpowiednie niż inne. Na przykład niektóre formaty mogą nie obsługiwać funkcji, które należy — podobnie jak przezroczystość lub format określony kolor — lub może nie zapewniać odpowiedni kompresji dla rodzaju zawartości obrazu zaplanowano.  
  
 Poniższe informacje mogą pomóc Ci wybrać format obrazu, który odpowiada Twoim potrzebom.  
  
 **Obraz mapy bitowej (bmp)**  
 Format obrazu mapy bitowej. Format obrazu nieskompresowanych, który obsługuje 24-bitowe. Mapa bitowa nie obsługuje przezroczystość.  
  
 **Obraz GIF (.gif)**  
 Format obrazu Graphics (Interchange Format GIF). Format obrazu skompresowanej LZW, bezstratne, która obsługuje maksymalnie 256 kolorów. Nie nadaje się do fotografii i obrazów, które znacznej ilości szczegółów kolorów, ale zapewnia współczynniki kompresji dobre na samych obrazach niska color, które mają wysoki stopień spójności kolorów.  
  
 **JPG Image (.jpg)**  
 Format obrazu wspólnego fotograficzne ekspertów Group (JPEG). Format wysoce skompresowany, stratnej obrazu, który obsługuje 24-bitowe i nadaje się do ogólnego przeznaczenia kompresji obrazów, które mają wysoki stopień spójności kolor.  
  
 **Obraz PNG (.png)**  
 Format obrazu Portable Network Graphics (PNG). Format obrazu umiarkowanie skompresowany, bezstratne, obsługującego 24-bitowe i alfa przezroczystości. Nadaje się do zarówno naturalnych, jak i sztuczne obrazy, ale nie zapewnia współczynniki kompresji tak dobrze, jak stratnej formatów, takich jak JPG lub GIF.  
  
 **Obraz TIFF (.tif)**  
 Format obrazu w formacie Tagged Image File Format (TIFF lub TIF). Format obrazu elastyczne, która obsługuje kilka systemów kompresji.  
  
 **Tekstura DDS (.dds)**  
 Format tekstury DirectDraw Surface (DDS). Format wysoce skompresowany, stratnej teksturę, która obsługuje 24-bitowe i alfa przezroczystości. Jego współczynniki kompresji może być możliwie jak 8:1. Jest ona oparta na kompresji tekstury S3, która może dekompresja w sprzęt graficzny.  
  
 **Obraz TGA (.tga)**  
 Format obrazu Truevision kartą grafiki (TGA) (znany także jako Targa). Format obrazu skompresowanej uszkodzone elementy RLE, bezstratne obsługuje zarówno mapowanych na kolor (palety kolorów) lub bezpośrednio kolor obrazy maksymalnie 24-bitowe i alfa przezroczystości. Nie nadaje się do fotografii i obrazów, które znacznej ilości szczegółów kolorów, ale zapewnia współczynniki kompresji dobre dla obrazów, które mają długi zakresów kolorów identyczne.  
  
### <a name="configuring-the-image"></a>Konfigurowanie obrazu  
 Przed rozpoczęciem pracy z obrazem, który został utworzony, można zmienić konfiguracji domyślnej. Na przykład możesz zmienić jego wymiary lub format koloru, która jest używana. Aby uzyskać informacje o sposobie konfigurowania tych i innych właściwości obrazu, zobacz [właściwości obrazu](#ImageProperties).  
  
> [!NOTE]
>  Aby zapisać swoją pracę, należy ustawić **Format koloru** właściwość, jeśli chcesz użyć formatu określony kolor. Jeśli format pliku obsługuje kompresję, można dostosować ustawienia kompresji podczas zapisywania pliku po raz pierwszy lub po wybraniu **Zapisz jako**.  
  
## <a name="working-with-the-image-editor"></a>Praca z edytora obrazów  
 W tej sekcji opisano, jak można użyć edytora obrazów, aby zmodyfikować teksturami i obrazami.  
  
### <a name="image-editor-toolbars"></a>Paski narzędzi edytora obrazów  
 Edytor obrazów zawiera pasków narzędzi polecenia ułatwiające pracę z obrazami.  
  
 Polecenia, które wpływają na stan edytora obrazów znajdują się na **tryb edytora obrazów** narzędzi oraz zaawansowane polecenia. Pasek narzędzi znajduje się wzdłuż krawędzi najwyższego poziomu powierzchni projektowania edytora obrazu. Narzędzia do rysowania znajdują się na **edytora obrazów** narzędzi wzdłuż lewej krawędzi, powierzchni projektowania edytora obrazów.  
  
 Oto **tryb edytora obrazów** narzędzi:  
  
 ![Modalne paska narzędzi edytora obrazów. ](../designers/media/digit-tre-modal-toolbar.png "Cyfry TRE-modalne — pasek narzędzi")  
  
 W tej tabeli opisano elementy na **tryb edytora obrazów** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od lewej do prawej.  
  
|Element paska narzędzi|Opis|  
|------------------|-----------------|  
|**Select**|Umożliwia wybór prostokątny obszar obrazu. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|  
|**Zaznacz dowolny kształt**|Umożliwia wybór nieregularne obszaru obrazu. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|  
|**Wybór Różdżka**|Umożliwia wybór obszaru podobnie kolorowe obrazu. *Tolerancji*— czyli maksymalna różnica między sąsiadujących kolorów w ramach których są one traktowane jako podobne — można skonfigurować, aby uwzględnić mniejszych lub szerszy zakres podobne kolory. Po wybraniu regionu, można wycinania, kopiowania, przenieść, skalowanie, obracanie, przerzucić lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|  
|**Przesuwanie**|Umożliwia przenoszenie obrazu względem ramki okna. W **Pan** tryb, wybierz punkt na obrazie, a następnie przesuwaj go.<br /><br /> Można tymczasowo uaktywnić **Pan** tryb przez naciśnięcie i przytrzymanie klawisza Ctrl.|  
|**Zoom**|Umożliwia wyświetlanie więcej lub mniej szczegółów obrazu względem ramki okna. W **powiększenia** tryb, wybierz punkt na obrazie a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> Można powiększać lub pomniejszać, naciskając i przytrzymując klawisz Ctrl podczas możesz użyć kółka myszy lub naciśnij znak Plus (+) lub Minus (-).|  
|**Powiększ do rzeczywistego rozmiaru**|Wyświetla obraz przy użyciu relacji 1:1 między piksele obrazu i pikseli ekranu.|  
|**Dopasuj widok do rozmiaru**|Wyświetla pełnego obrazu w ramki okna.|  
|**Dopasuj widok do szerokości**|Wyświetla całą szerokość obrazu ramki okna.|  
|**Siatka**|Włącza lub wyłącza siatki, który pokazuje pikseli. Siatka mogą nie być wyświetlane, dopóki powiększenie obrazu.|  
|**Wyświetlanie następnego poziomu MIP**|Aktywuje następnego poziomu MIP większe w łańcuch mapy MIP. Aktywne poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|  
|**Wyświetl poprzedniego poziomu MIP**|Aktywuje następnego poziomu MIP mniejszych w łańcuch mapy MIP. Aktywne poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępna tylko dla tekstur, które mają poziomy MIP.|  
|**Kanał czerwony**<br /><br /> **Kanał zielony**<br /><br /> **Kanał niebieski**<br /><br /> **Kanał alfa**|Włącza lub wyłącza kanał określony kolor. **Uwaga:**  Systematycznie włączając lub wyłączając kanałów koloru, można wyizolować problemy, które są powiązane z co najmniej jeden z nich. Na przykład można zidentyfikować niepoprawne alfa przezroczystości.|  
|**Tło**|Włącza lub wyłącza wyświetlanie tło przezroczyste fragmenty obrazu. Można skonfigurować sposób wyświetlania tła, wybierając następujące opcje:<br /><br /> **Szachownica**<br /> Użyto kolor zielony, wraz z określonego tłem, aby wyświetlić tło jako wzorzec szachownicy. Ta opcja umożliwia sprawić, że przezroczysty części obrazu bardziej oczywista.<br /><br /> Białe tło<br /> Użyto kolor biały, aby wyświetlić tło.<br /><br /> Czarne tło<br /> Użyto kolor czarny, aby wyświetlić tło.<br /><br /> Tło animowane<br /> Przesuwa wzorzec szachownicy powoli. Ta opcja umożliwia sprawić, że przezroczysty części obrazu bardziej oczywista.|  
|**Właściwości**|Zamiennie otwiera i zamyka **właściwości** okna.|  
|**Zaawansowane**|Zawiera dodatkowe polecenia i opcje.<br /><br /> **Filtry**<br /><br /> Zapewnia kilka wspólnych filtrów obrazu: **Czarno-biały**, **Rozmycie**, **rozjaśnić**, **ciemniejszy**, **wykrywania krawędzi**, **trójwymiarowej**, **Odwróć kolory**, **Ripple**, **ton Sepia**, i **doskonalenie**.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania edytora obrazów.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa programu Direct3D 11 Windows Advanced rasteryzacji platformy WARP () do renderowania powierzchni projektowania edytora obrazu.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć w poziomie**<br /> Podstawianie obrazu wokół jego osi poziomej lub x.<br /><br /> **Przerzuć w pionie**<br /> Podstawianie obrazu wokół jego osi pionowej lub y.<br /><br /> **Generuj Mips**<br /> Generuje poziomów MIP dla obrazu. Jeśli istnieje poziomów MIP, są ponownie tworzone z największego poziomu MIP. Wszelkie zmiany wprowadzone w mniejszym poziomom MIP zostaną utracone. Aby zapisać poziomów MIP, które zostały wygenerowane, musi być w formacie .dds zapisania obrazu.<br /><br /> **Widok**<br /><br /> **Szybkość klatek**<br /> Po włączeniu Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. **Porada:**  Możesz wybrać **zaawansowane** przycisk, aby ponownie uruchomić ostatnie polecenie.|  
  
 Oto **edytora obrazów** paska narzędzi.  
  
 ![Pasek narzędzi edytora obrazów](../designers/media/digit-tre-toolbar.png "cyfry-TRE — pasek narzędzi")  
  
 W poniższej tabeli opisano elementy na **edytora obrazów** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od góry do dołu.  
  
|Element paska narzędzi|Opis|  
|------------------|-----------------|  
|**Ołówka**|Używa kodowania aktywnego koloru do rysowania pociągnięcie aliasem. Można ustawić kolor i grubość obrysu w **właściwości** okna.|  
|**Pędzel**|Używa kodowania aktywnego koloru do rysowania pociągnięcie wygładzanie. Można ustawić kolor i grubość obrysu w **właściwości** okna.|  
|**Aerograf**|Używa wybór koloru active do rysowania pociągnięcie wygładzanie miesza wraz z obrazu, która staje się bardziej nasycony funkcji czasu. Można ustawić kolor i grubość obrysu w **właściwości** okna.|  
|**Eyedropper**|Ustawia kolor wybrany piksel wybór koloru active.|  
|**Wypełnienie**|Używa wybór koloru active do wypełnienia obszaru obrazu. Dotyczy region jest zdefiniowany jako pikseli, w których stosowane wypełnienie wraz z każdy piksel, który jest z nią połączona pikseli tego samego koloru i to ten sam kolor, sam. Jeśli wypełnienie jest stosowana w ramach aktywnego zaznaczenia, dotyczy region jest ograniczone przez zaznaczenie.<br /><br /> Domyślnie wybór koloru active jest zmieszana wraz z zainfekowanego region obrazu zgodnie z jego składnik alfa. Aby użyć wybór koloru active zastąpić dotyczy region, naciśnij i przytrzymaj klawisz Shift podczas używania narzędzia wypełnienia.|  
|**Gumka**|Jeśli obraz, który obsługuje kanał alfa, ustawia piksele, aby całkowicie przezroczysty kolor. W przeciwnym razie piksele Ustawia kolor tła active.|  
|**Wiersz**, **prostokąt**, **prostokąt zaokrąglony**, **wielokropka**|Rysuje kształt na obrazie. Można ustawić kolor i grubość konturu w **właściwości** okna.<br /><br /> Aby narysować elementu podstawowego, który ma równa szerokość i wysokość, naciśnij i przytrzymaj klawisz Shift podczas rysowania.|  
|**Text**|Używa wybór koloru pierwszego planu, aby rysować tekst. Kolor tła jest określany przez wybór koloru tła. Dla przezroczyste tło wartość alfa wybór koloru tła musi być 0. Gdy obszaru tekstu jest aktywna, można ustalić, czy tekst jest rysowana obrysu wygładzanie i można ustawić tekst **wartość**, **czcionki**, **rozmiar**, styl i —**Bold**, **Kursywa**, lub **podkreślona**— w **właściwości** okna. Zawartość i wygląd tekstu jest aktualnie finalizowana, gdy region tekst nie jest już aktywna.|  
|**Obróć**|Obrót 90 stopni w prawo.|  
|**TRIM**|Przycina obraz do aktywnego zaznaczenia.|  
  
### <a name="working-with-mip-levels"></a>Praca z poziomów MIP  
 Niektóre formaty obrazów — na przykład, DirectDraw Surface (.dds) — Obsługa poziomów MIP przestrzeni tekstury poziomu z Detail (poziomu). Aby uzyskać informacje o tym, jak generować i pracować z poziomami MIP, zobacz [jak: Tworzenie i modyfikacja poziomów MIP](../designers/how-to-create-and-modify-mip-levels.md)  
  
### <a name="working-with-transparency"></a>Praca z przezroczystością  
 Niektóre formaty obrazów — na przykład, DirectDraw Surface (.dds) — obsługuje przezroczystość. Istnieje kilka sposobów, że jawność mogą być używane, w zależności od narzędzie, którego używasz. Aby określić stopień przejrzystości dla wyboru koloru w **właściwości** oknie **A** składnik (alfa) wybór koloru. Oto jak różne rodzaje kontroli narzędzi, jak przezroczystości są stosowane:  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|**Ołówek**, **pędzla**, **Aerograf**, **wiersza**, **prostokąt**, **prostokąt zaokrąglony** , **Elipsy**, **tekstu**|Aby dopasować wybór koloru aktywne, wraz z obrazu, w **właściwości** okna, rozwiń węzeł **kanały** grupy właściwości i ustaw **Rysowanie** pole wyboru na  **Alfa** kanał, a następnie narysuj normalnie.<br /><br /> Aby narysować przy użyciu wybór koloru aktywne i pozostawić wartość alfa odpowiadającą obrazu w miejscu, należy wyczyścić **Rysowanie** obok **alfa** kanał, a następnie narysuj normalnie.|  
|**Wypełnienie**|Aby dopasować wybór koloru aktywne, wraz z obrazu, po prostu wybrać obszar, aby wypełnić.<br /><br /> Umożliwia wybór koloru active — z uwzględnieniem wartości kanał alfa — Aby zastąpić obraz, naciśnij i przytrzymaj klawisz Shift, a następnie wybierz obszar, aby wypełnić.|  
  
###  <a name="ImageProperties"></a> Właściwości obrazu  
 Możesz użyć **właściwości** okna, aby określić różne właściwości obrazu. Na przykład można ustawić właściwości szerokości i wysokości rozmiaru.  
  
 W poniższej tabeli opisano właściwości obrazu.  
  
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
|Wycinek głębokości|Bieżącego wycinka głębi. Mogą być wyświetlane tylko pierwszy wycinek; wszystkie inne wycinki zostaną utracone przy zapisywaniu obrazu.|  
  
> [!NOTE]
>  Ponieważ **obrócić** właściwość ma zastosowanie do wszystkich narzędzi i wybranych regionach, zawsze pojawia się w dolnej części **właściwości** okna wraz z innymi właściwości narzędzia. **Obróć przez** zawsze jest wyświetlany, ponieważ obraz całej niejawnie zostaje wybrany, gdy nie ma żadnych wyboru ani narzędzie active. Aby uzyskać więcej informacji na temat **obrócić** właściwości, zobacz [właściwości narzędzia](#ToolProperties).  
  
#### <a name="resizing-images"></a>Zmiana rozmiaru obrazów  
 Poniżej przedstawiono dwa sposoby zmiany rozmiaru obrazu. W obu przypadkach edytora obrazów używa interpolacji liniowej Power bi do próbkowania obrazu.  
  
-   W **właściwości** okna, określ nowe wartości **szerokość** i **wysokość** właściwości.  
  
-   Wybierz całego obrazu, a następnie zmień rozmiar obrazu za pomocą znaczników obramowania.  
  
### <a name="working-with-tools"></a>Praca z narzędzia  
  
#### <a name="selected-regions"></a>Wybranych regionach  
 Opcje edytora obrazów zdefiniować regiony obrazu, które są aktywne — oznacza to, że region dotyczy narzędzi i przekształcenia. W przypadku aktywnego zaznaczenia poza wybrany region nie dotyczy większości narzędzi i przekształcenia. Jeśli nie ma aktywnego zaznaczenia, całego obrazu jest aktywny.  
  
 Większość narzędzi —**ołówka**, **pędzla**, **Aerograf**, **wypełnienia**, **Gumka**i podstawowych 2-D — i przekształcenia —**Obróć**, **Trim**, **Odwróć kolory**, **Przerzuć w poziomie**, i **Przerzuć w pionie** — ograniczone lub zdefiniowany przez aktywnego zaznaczenia. Jednak niektóre narzędzi —**Pipeta** i **tekstu**— i przekształcenia —**Generuj Mips**— nie dotyczy żadnych aktywnego zaznaczenia; tych narzędzi zawsze zachowują się tak, jakby cały Obraz jest aktywnego zaznaczenia.  
  
 Podczas wybierania regionu, można nacisnąć i przytrzymać klawisz Shift, aby dokonać wyboru proporcjonalnego (kwadrat); w przeciwnym razie zaznaczenia nie jest ograniczona.  
  
##### <a name="resizing-selections"></a>Opcje zmiany rozmiaru  
 Po wybraniu regionu, możesz zmienić rozmiar on lub jego zawartość obrazu, zmieniając rozmiar znacznika wyboru. Podczas, gdy zmianie rozmiaru wybranego regionu można użyć następujące klawisze modyfikujące, aby zmienić zachowanie wybranego regionu podczas zmiany rozmiaru (naciśnij i przytrzymaj klawisz klucza podczas zmiany rozmiaru).  
  
 Ctrl  
 Kopiuje zawartość wybranego regionu, zanim zmiany jego rozmiaru. Spowoduje to pozostawienie oryginalny obraz bez zmian podczas zmiany rozmiaru kopii.  
  
 Shift  
 Zmienia rozmiar wybranego regionu, proporcjonalnie do oryginalnego rozmiaru.  
  
 Alt  
 Zmienia rozmiar obszaru zaznaczenia. Spowoduje to pozostawienie obrazu w niezmienionej postaci.  
  
 Poniżej przedstawiono kombinacje klawiszy modyfikatora prawidłowy:  
  
|Ctrl|Shift|Alt|Opis|  
|----------|-----------|---------|-----------------|  
||||Zmienia rozmiar zawartości wybranego regionu.|  
||Shift||Proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|  
|||Alt|Zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|  
||Shift|Alt|Proporcjonalnie zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|  
|Ctrl|||Kopiuje, a następnie zmienia rozmiar zawartości wybranego regionu.|  
|Ctrl|Shift||Kopiuje, a następnie proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|  
  
####  <a name="ToolProperties"></a> Właściwości narzędzia  
 To narzędzie jest zaznaczone, ale można używać **właściwości** okna możliwość określania szczegółów o tym jak wpływa na obrazie. Na przykład można ustawić grubość **ołówka** narzędzia lub kolor **pędzla** narzędzia.  
  
 Możesz ustawić kolor pierwszego planu i kolor tła. Obie obsługują kanał alfa, zapewnienie nieprzezroczystość zdefiniowanych przez użytkownika. Ustawienia są stosowane do wszystkich narzędzi. Jeśli używasz myszy, lewy przycisk myszy odpowiada kolor pierwszego planu, a następnie prawym przyciskiem myszy odpowiada kolor tła.  
  
 W poniższej tabeli opisano właściwości narzędzia.  
  
|Narzędzie|Właściwości|  
|----------|----------------|  
|Wszystkie narzędzia i opcje|**Obróć o**<br /> Określa, w stopniach, czy zaznaczenie lub narzędzia efekt jest obracana wskazówek zegara.|  
|**Ołówek**, **pędzla**, **Aerograf**, **Gumka**|**Grubość**<br /> Określa rozmiar obszaru, który jest zależna od narzędzia.|  
|**Text**|**Wygładzanie**<br /> Rysuje tekst, który ma wygładzanie krawędzi. Dzięki temu tekst gładsze wygląd.<br /><br /> **Wartość**<br /> Tekst do narysowania.<br /><br /> **Czcionka**<br /> Czcionka używana ma zostać narysowany tekst.<br /><br /> **Rozmiar**<br /> Rozmiar tekstu.<br /><br /> **Bold**<br /> Sprawia, że czcionka pogrubienie.<br /><br /> **Kursywa**<br /> Sprawia, że czcionka italic.<br /><br /> **Podkreślony**<br /> Sprawia, że czcionka podkreślone.|  
|**Element 2-D**|**Wygładzanie**<br /> Rysuje podstawowych, które mają wygładzanie krawędzi. To daje im gładsze wygląd.<br /><br /> **Grubość**<br /> Określa grubość linii, który wchodzi w skład granicy podstawowego.<br /><br /> **Promień X**<br /> (Tylko w przypadku prostokąt zaokrąglony) Definiuje górną i dolną krawędzią element pierwotny zaokrąglania usługi radius.<br /><br /> **Promień Y**<br /> (Tylko w przypadku prostokąt zaokrąglony) Definiuje zaokrąglania usługi radius do lewej i prawej krawędzi element pierwotny.|  
|**Ołówek**, **pędzla**, **Aerograf**, **podstawowego 2-D**|**Channels**<br /> Włącza lub wyłącza określony kolor kanały do wyświetlania i rysowania. Jeśli **widoku** jest ustawiona dla określonego kanału koloru, tym kanale jest widoczne na obrazie; w przeciwnym razie nie jest on widoczny. Jeśli **Rysowanie** ustawiono dla określonego kanału koloru, że kanał jest objęte za pomocą rysowania operacji; w przeciwnym razie, nie jest.|  
|**Wybór Różdżka**, **wypełnienia**|**Tolerance**<br /> Definiuje maksymalną różnicę między sąsiadujących kolorów, w których są one traktowane jako podobnie, tak aby mniej lub bardziej podobne kolory zostały wprowadzone w ramach objęty lub wybranego regionu. Domyślnie wartość jest 32, co oznacza, że sąsiadujących pikseli w ciągu 32 odcienie koloru oryginalnego (jaśniejsze i ciemniejsze) są traktowane jako część obszaru.|  
  
## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
  
|Polecenie|Skróty klawiaturowe|  
|-------------|------------------------|  
|Przełącz się do **wybierz** tryb|S|  
|Przełącz się do **powiększenia** tryb|Z|  
|Przełącz się do **Pan** tryb|K|  
|Zaznacz wszystkie|Ctrl+A|  
|Usuń bieżące zaznaczenie|Usuwanie|  
|Anuluj bieżące zaznaczenie|Escape|  
|Powiększanie|Ctrl + obrót kółkiem myszy do przodu<br /><br /> Ctrl+PageUp<br /><br /> Znak plus (+)|  
|Pomniejszanie|CTRL obrót kółkiem myszy do tyłu<br /><br /> Ctrl-PageDown<br /><br /> Znak minusa (-)|  
|Przesuń w górę obrazu|Obrót kółkiem myszy do tyłu<br /><br /> PageDown|  
|Przesuń w dół obrazu|Obrót kółkiem myszy do przodu<br /><br /> PageUp|  
|Przesuń obrazu po lewej|Shift+obrót kółkiem myszy do tyłu<br /><br /> Ruch kółkiem myszy w lewo<br /><br /> Shift+PageDown|  
|Przesuń w prawo obrazu|Shift+obrót kółkiem myszy do przodu<br /><br /> Ruch kółkiem myszy w prawo<br /><br /> Shift+PageUp|  
|Powiększ do rzeczywistego rozmiaru|CTRL + 0 (zero)|  
|Dopasuj obraz do okna|Ctrl+G, Ctrl+F|  
|Obraz Dopasuj do szerokości okna|Ctrl+G, Ctrl+I|  
|Przełącz siatkę|Ctrl+G, Ctrl+G|  
|Przytnij obraz do bieżącego zaznaczenia|Ctrl+G, Ctrl+C|  
|Wyświetlanie następnego (szczegóły wyższej) Poziom MIP|Ctrl+G, Ctrl+6|  
|Wyświetl poprzednie (niższe szczegóły) Poziom MIP|Ctrl+G, Ctrl+7|  
|Przełącz kanału koloru czerwonego|Ctrl+G, Ctrl+1|  
|Przełącz kolor zielony kanału|Ctrl+G, Ctrl+2|  
|Przełącz koloru niebieskiego kanału|Ctrl+G, Ctrl+3|  
|Przełącz kanał alfa (przezroczystości)|Ctrl+G, Ctrl+4|  
|Przełącz wzorzec szachownicy alfa|Ctrl+G, Ctrl+B|  
|Przełącz się do kształt-narzędzie|L|  
|Przejdź do narzędzia zaznaczania Różdżka|M|  
|Przełącz do Ołówek narzędzia|P|  
|Przełącz się do narzędzia pędzla|B|  
|Przełącz do Wypełnianie kolorem-narzędzie|F|  
|Przejdź do narzędzia Gumka|E|  
|Przełącz się do narzędzie tekstowe|T|  
|Przejdź do narzędzia zaznaczania kolorów (Pipeta)|I|  
|Przenoszenie aktywnego zaznaczenia i jego zawartość.|Klawisze strzałek.|  
|Zmień rozmiar aktywnego zaznaczenia i jego zawartość.|CTRL + klawisze strzałek|  
|Przenoszenie aktywnego zaznaczenia, ale nie jego zawartość.|Shift + klawisze strzałek|  
|Zmień rozmiar aktywnego zaznaczenia, ale nie jego zawartość.|Shift + klawisze Ctrl + klawisze strzałek|  
|Bieżąca warstwa zatwierdzenia|Wróć|  
|Zmniejsz grubość narzędzia|[|  
|Zwiększ grubość narzędzia|]|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie narzędzi, których można używać w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do pracy z zasobami grafiki, takie jak tekstury i obrazy, modele 3D i efekty cieniowania.|  
|[Edytor modelu](../designers/model-editor.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora modelu do pracy z modelami 3-D.|  
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta modułu cieniującego do pracy z programów do cieniowania.|
