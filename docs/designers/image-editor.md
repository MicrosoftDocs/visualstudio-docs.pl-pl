---
title: Edytor obrazów
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd7d9aed75876b47a6574d46b226f5baec336883
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589321"
---
# <a name="image-editor"></a>Edytor obrazów

W tym artykule opisano sposób pracy z **Edytorem obrazów** programu Visual Studio w celu wyświetlania i modyfikowania zasobów tekstur i obrazów.

**Edytor obrazów** służy do pracy z rodzajami rozszerzonych tekstur i formatów obrazów, które są używane w tworzeniu aplikacji DirectX. Obejmuje to obsługę popularnych formatów plików obrazów i kodowania kolorów, funkcje, takie jak kanały alfa i mapowanie MIP, a także wiele wysoce skompresowanych, przyspieszonych sprzętowo formatów tekstur obsługiwanych przez directx.

## <a name="supported-formats"></a>Obsługiwane formaty

**Edytor obrazów** obsługuje następujące formaty obrazów:

|Nazwa formatu|Rozszerzenie nazwy pliku|
|-----------------| - |
|Portable Network Graphics|*.png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Powierzchnia bezpośredniego rysowania|*.dds*|
|Graphics Interchange Format|*.gif*|
|Bitmapy|*.bmp*, *.dib*|
|Format pliku obrazu z tagiem|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano sposób dodawania obrazu do projektu programu Visual Studio i konfigurowania go pod kątem wymagań.

### <a name="add-an-image-to-your-project"></a>Dodawanie obrazu do projektu

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, do którego chcesz dodać obraz, a następnie wybierz pozycję **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodawanie nowego elementu** w obszarze **Zainstalowane**wybierz pozycję **Grafika**, a następnie wybierz odpowiedni format pliku obrazu.

   > [!NOTE]
   > Jeśli nie widzisz kategorii **Grafika** w oknie dialogowym **Dodawanie nowego elementu,** może być konieczne zainstalowanie składnika **Edytory obrazów i modeli 3D.** Zamknij okno dialogowe, a następnie wybierz polecenie **Narzędzia** > **Pobierz narzędzia i funkcje** z paska menu, aby otworzyć instalator programu Visual **Studio**. Wybierz kartę **Poszczególne składniki,** a następnie wybierz składnik **Edytory obrazów i modeli 3D** w kategorii **Gry i grafika.** Wybierz **pozycję Modyfikuj**.
   >
   > ![Komponent edytorów obrazów i modeli 3D](media/image-3d-model-editors-component.png)

   Aby uzyskać informacje o wyborze formatu pliku na podstawie wymagań, zobacz [Wybieranie formatu obrazu](#choose-the-image-format).

3. Określ **nazwę** pliku obrazu i **lokalizację,** w której ma zostać utworzony.

4. Wybierz przycisk **Dodaj**.

### <a name="choose-the-image-format"></a>Wybieranie formatu obrazu

W zależności od tego, jak zamierzasz używać obrazu, niektóre formaty plików mogą być bardziej odpowiednie niż inne. Na przykład niektóre formaty mogą nie obsługiwać funkcji, której potrzebujesz, na przykład przezroczystości lub określonego formatu kolorów. Niektóre formaty mogą nie zapewniać odpowiedniej kompresji dla rodzaju zaplanowanej zawartości obrazu.

Następujące informacje mogą pomóc w wyborze formatu obrazu, który odpowiada Twoim potrzebom:

**Obraz bitmapowy (bmp)**

Format obrazu mapy bitowej. Nieskompresowany format obrazu obsługujący kolor 24-bitowy. Format mapy bitowej nie obsługuje przezroczystości.

**Obraz GIF (.gif)**

Format obrazu Format wymiany grafiki (GIF). Skompresowany przez LZW, bezstratny format obrazu, który obsługuje do 256 kolorów. Nie nadaje się do zdjęć i obrazów, które mają znaczną ilość szczegółów kolorów, ale zapewnia dobre współczynniki kompresji dla obrazów o niskiej jakości kolorów, które mają wysoki stopień spójności kolorów.

**Obraz JPG (.jpg)**

Format obrazu Joint Photographic Experts Group (JPEG). Wysoce skompresowany, stratny format obrazu, który obsługuje kolor 24-bitowy i nadaje się do kompresji obrazów ogólnego przeznaczenia, które mają wysoki stopień spójności kolorów.

**Obraz PNG (png)**

Format obrazu przenośnej grafiki sieciowej (PNG). Umiarkowanie skompresowany, bezstratny format obrazu obsługujący 24-bitowy kolor i przezroczystość alfa. Nadaje się zarówno do obrazów naturalnych, jak i sztucznych, ale nie zapewnia współczynników kompresji tak dobrych, jak formaty stratne, takie jak JPG lub GIF.

**Obraz TIFF (.tif)**

Format obrazu Format pliku o oznakowaniu (TIFF lub TIF). Elastyczny format obrazu obsługujący kilka schematów kompresji.

**Tekstura DDS (.dds)**

Format tekstury powierzchni DirectDraw (DDS). Bardzo skompresowany, stratny format tekstury obsługujący 24-bitowy kolor i przezroczystość alfa. Jego współczynniki kompresji mogą wynosić nawet 8:1. Jest on oparty na kompresji tekstury S3, która może być dekompresowana na sprzęcie graficznym.

**Obraz TGA (.tga)**

Format obrazu Truevision Graphics Adapter (TGA) (znany również jako Targa). Skompresowany rle, bezstratny format obrazu, który obsługuje zarówno kolor odwzorowany (paleta kolorów) lub bezpośrednie kolorowe obrazy o maksymalnie 24-bitowym kolorze i przezroczystości alfa. Nie nadaje się do zdjęć i obrazów, które mają znaczną ilość szczegółów kolorów, ale zapewnia dobre współczynniki kompresji dla obrazów, które mają długie rozpiętości identycznych kolorów.

### <a name="configure-the-image"></a>Konfigurowanie obrazu

Przed rozpoczęciem pracy z utworzonym obrazem można zmienić jego domyślną konfigurację. Można na przykład zmienić jego wymiary lub używany format kolorów. Aby uzyskać informacje dotyczące konfigurowania tych i innych właściwości obrazu, zobacz [Właściwości obrazu](#image-properties).

> [!NOTE]
> Przed zapisaniem pracy należy ustawić właściwość **Format kolorów,** jeśli chcesz użyć określonego formatu kolorów. Jeśli format pliku obsługuje kompresję, można dostosować ustawienia kompresji podczas zapisywania pliku po raz pierwszy lub po **wybraniu**opcji Zapisz jako .

## <a name="work-with-the-image-editor"></a>Praca z Edytorem obrazów

W tej sekcji opisano sposób modyfikowania tekstur i obrazów za pomocą **Edytora obrazów.**

Polecenia wpływające na stan **Edytora obrazów** znajdują się na pasku narzędzi **Tryb edytora obrazów** wraz z zaawansowanymi poleceniami. Pasek narzędzi znajduje się wzdłuż górnej krawędzi powierzchni projektu **Edytora obrazów.** Narzędzia do rysowania znajdują się na pasku narzędzi **Edytor obrazów** wzdłuż lewej krawędzi powierzchni projektu **Edytora obrazów.**

### <a name="image-editor-mode-toolbar"></a>Pasek narzędzi Trybu edytora obrazów

![Pasek narzędzi trybu edytora obrazów w programie Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

W poniższej tabeli opisano elementy na pasku narzędzi **Tryb edytora obrazów,** które są wyświetlane w kolejności, w jakiej są wyświetlane od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Włącza wybór prostokątnego regionu obrazu. Po wybraniu regionu można go wyciąć, skopiować, przenieść, skalować, obracać, przerzucać lub usuwać. W przypadku aktywnego zaznaczenia narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Nieregularny wybór**|Umożliwia wybór nieregularnego obszaru obrazu. Po wybraniu regionu można go wyciąć, skopiować, przenieść, skalować, obracać, przerzucać lub usuwać. W przypadku aktywnego zaznaczenia narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Wybór różdżki**|Umożliwia wybór podobnie kolorowego regionu obrazu. *Tolerancję*— czyli maksymalną różnicę między sąsiednimi kolorami, w których są one uważane za podobne — można skonfigurować tak, aby zawierała mniejszy lub szerszy zakres podobnych kolorów. Po wybraniu regionu można go wyciąć, skopiować, przenieść, skalować, obracać, przerzucać lub usuwać. W przypadku aktywnego zaznaczenia narzędzia do rysowania mają wpływ tylko na wybrany region.|
|**Przesuwanie**|Umożliwia ruch obrazu względem ramki okna. W trybie **Przesuwania** wybierz punkt na obrazie, a następnie przesuń go.<br /><br /> Tryb **przesuwania** można tymczasowo włączyć, naciskając i przytrzymując klawisz **Ctrl.**|
|**Zoom**|Umożliwia wyświetlanie mniej lub bardziej szczegółowych szczegółów obrazu względem ramki okna. W trybie **powiększenia** zaznacz punkt obrazu, a następnie przesuń go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć widok.<br /><br /> Możesz powiększyć lub pomniejszyć, naciskając i przytrzymując **klawisz Ctrl** podczas używania kółka myszy lub naciśnięcia znaku plus (**+**) lub znaku minus (**-**).|
|**Powiększanie do rzeczywistego rozmiaru**|Wyświetla obraz przy użyciu relacji 1:1 między pikselami obrazu a pikselami ekranu.|
|**Powiększenie, aby pasowało**|Wyświetla pełny obraz w ramce okna.|
|**Powiększenie do szerokości**|Wyświetla pełną szerokość obrazu w ramce okna.|
|**Siatka**|Włącza lub wyłącza siatkę, która pokazuje granice pikseli. Siatka może nie być wyświetlana, dopóki nie powiększysz obrazu.|
|**Wyświetl następny poziom MIP**|Aktywuje następny większy poziom MIP w łańcuchu map MIP. Aktywny poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|**Wyświetl poprzedni poziom MIP**|Aktywuje następny mniejszy poziom MIP w łańcuchu map MIP. Aktywny poziom MIP jest wyświetlany na powierzchni projektowej. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|**Czerwony kanał**<br /><br /> **Zielony kanał**<br /><br /> **Niebieski kanał**<br /><br /> **Kanał Alfa**|Włącza lub wyłącza określony kanał kolorów. **Uwaga:**  Systematycznie włączając lub wyłączając kanały kolorów, można wyizolować problemy związane z jednym lub kilkoma z nich. Na przykład można zidentyfikować niepoprawną przezroczystość alfa.|
|**Tło**|Włącza lub wyłącza wyświetlanie tła za pośrednictwem przezroczystych części obrazu. Sposób wyświetlania tła można skonfigurować, wybierając spośród następujących opcji:<br /><br /> **Szachownica**<br /> Używa koloru zielonego wraz z określonym kolorem tła, aby wyświetlić tło jako wzór szachownicy. Za pomocą tej opcji można sprawić, że przezroczyste części obrazu będą bardziej widoczne.<br /><br /> Białe tło<br /> Używa koloru białego do wyświetlania tła.<br /><br /> Czarne tło<br /> Używa koloru czarnego do wyświetlania tła.<br /><br /> Animowanie tła<br /> Przesuwa wzór szachownicy powoli. Za pomocą tej opcji można sprawić, że przezroczyste części obrazu będą bardziej widoczne.|
|**Właściwości**|Alternatywnie otwiera lub zamyka okno **Właściwości.**|
|**Zaawansowane**|Zawiera dodatkowe polecenia i opcje.<br /><br /> **Filtry**<br /><br /> Zawiera kilka typowych filtrów obrazu: **czarno-biały**, **Rozmycie,** **Rozjaśnianie,** **Ciemnienie,** **Wykrywanie krawędzi,** **Płaskorześnia,** **Odwrócone kolory,** **Tętnienie,** **Dźwięk Sepii**i **Wyostrzanie**.<br /><br /> **Silniki graficzne**<br /><br /> **Renderowanie za pomocą D3D11**<br /> Używa direct3D 11 do renderowania powierzchni projektu **Edytora obrazów.**<br /><br /> **Renderowanie za pomocą D3D11WARP**<br /> Używa direct3D 11 Windows Advanced Rasterization Platform (WARP) do renderowania powierzchni projektu **Edytora obrazów.**<br /><br /> **narzędzia**<br /><br /> **Przerzuć w poziomie**<br /> Transponuje obraz wokół osi poziomej lub x.<br /><br /> **Odwróć w pionie**<br /> Transponuje obraz wokół jego pionowej lub y osi.<br /><br /> **Generowanie mips**<br /> Generuje poziomy MIP dla obrazu. Jeśli poziomy MIP już istnieją, są one odtworzone z największego poziomu MIP. Wszelkie zmiany wprowadzone do mniejszych poziomów MIP są tracone. Aby zapisać wygenerowane poziomy MIP, należy użyć formatu *.dds,* aby zapisać obraz.<br /><br /> **Widok**<br /><br /> **Klatek**<br /> Gdy ta opcja jest włączona, wyświetla liczbę klatek na sekundę w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. **Wskazówka:** Możesz wybrać przycisk **Zaawansowane,** aby ponownie uruchomić ostatnie polecenie.|

### <a name="image-editor-toolbar"></a>Pasek narzędzi Edytor obrazów

![Pasek narzędzi Edytor obrazów](../designers/media/digit-tre-toolbar.png)

W poniższej tabeli opisano elementy na pasku narzędzi **Edytor obrazów,** które są wyświetlane w kolejności, w jakiej są wyświetlane od góry do dołu:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Ołówek**|Używa aktywnego zaznaczenia kolorów do rysowania obrysu aliasowego. Kolor i grubość **obrysu** można ustawić w oknie Właściwości.|
|**Pędzla**|Używa aktywnego zaznaczenia kolorów do rysowania obrysu wygładzone. Kolor i grubość **obrysu** można ustawić w oknie Właściwości.|
|**Airbrush**|Używa aktywnego zaznaczenia kolorów do rysowania wygładzanego obrysu, który miesza się z obrazem i staje się bardziej nasycony jako funkcja czasu. Kolor i grubość **obrysu** można ustawić w oknie Właściwości.|
|**Kroplomierz**|Ustawia aktywne zaznaczenie kolorów na kolor zaznaczonego piksela.|
|**Wypełnienia**|Używa aktywnego zaznaczenia kolorów, aby wypełnić obszar obrazu. Region, którego dotyczy problem, jest definiowany jako piksel, w którym jest stosowane wypełnienie, wraz z każdym pikselem połączonym z nim pikselami tego samego koloru i który jest tym samym kolorem. Jeśli wypełnienie jest stosowane w aktywnym zaznaczeniu, wybrany region jest ograniczony przez zaznaczenie.<br /><br /> Domyślnie aktywne zaznaczenie kolorów jest mieszane z obszarem obrazu, którego dotyczy problem, zgodnie z jego komponentem alfa. Aby użyć aktywnego zaznaczenia kolorów do nadpisywały obszar, którego dotyczy problem, naciśnij i przytrzymaj klawisz **Shift** podczas korzystania z narzędzia wypełniania.|
|**Gumka**|Ustawia piksele na w pełni przezroczysty kolor, jeśli obraz obsługuje kanał alfa. W przeciwnym razie ustawia piksele na aktywny kolor tła.|
|**Linia,** **Prostokąt**, **Prostokąt zaokrąglony,** **Elipsa**|Rysuje kształt na obrazie. Kolor i grubość konturu można ustawić w oknie **Właściwości.**<br /><br /> Aby narysować prymityw o równej szerokości i wysokości, naciśnij i przytrzymaj **klawisz Shift** podczas rysowania.|
|**Tekst**|Używa zaznaczenia koloru pierwszego planu do rysowania tekstu. Kolor tła jest określany przez wybór koloru tła. W przypadku przezroczystego tła wartość alfa zaznaczenia koloru tła musi wynosić 0. Gdy region tekstu jest aktywny, można określić, czy tekst jest rysowany obrysem wygładzonym, a w oknie **Właściwości** można ustawić tekst **Wartość,** **Czcionka,** **Rozmiar**i styl —**Pogrubienie**, **Kursywa**lub **Podkreślone**. Zawartość i wygląd tekstu jest finalizowany, gdy region tekstu nie jest już aktywny.|
|**Obrót**|Obraca obraz o 90 stopni w kierunku zgodnym z ruchem wskazówek zegara.|
|**Przycinanie**|Przycina obraz do aktywnego zaznaczenia.|

### <a name="work-with-mip-levels"></a>Praca z poziomami MIP

Niektóre formaty obrazów, na przykład DirectDraw Surface *(.dds),* obsługują poziomy MIP dla poziomu szczegółowości przestrzeni tekstury (LOD). Aby uzyskać informacje dotyczące generowania poziomów procedury MCI i pracy z nią, zobacz [Jak: Tworzenie i modyfikowanie poziomów procedury MIP](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Praca z przezroczystością

Niektóre formaty obrazów, na przykład DirectDraw Surface *(.dds),* obsługują przezroczystość. Przezroczystość można używać na kilka sposobów, w zależności od używanego narzędzia. Aby określić poziom przezroczystości dla zaznaczenia kolorów, w oknie **Właściwości** ustaw składnik **A** (alfa) zaznaczenia kolorów.

W poniższej tabeli opisano, jak różne rodzaje narzędzi kontrolują sposób stosowania przezroczystości:

|Narzędzie|Opis|
|----------|-----------------|
|**Ołówek**, **Pędzel**, **Aerograf**, **Linia**, **Prostokąt**, **Prostokąt zaokrąglony**, **Elipsa**, **Tekst**|Aby mieszać aktywne zaznaczenie kolorów razem z obrazem, w oknie **Właściwości** rozwiń grupę właściwości **Kanały** i ustaw pole wyboru **Rysuj** na kanale **Alfa,** a następnie narysuj normalnie.<br /><br /> Aby rysować za pomocą aktywnego zaznaczenia kolorów i pozostawić wartość alfa obrazu na miejscu, wyczyść pole wyboru **Rysuj** kanał **Alfa,** a następnie narysuj normalnie.|
|**Wypełnienia**|Aby połączyć aktywne zaznaczenie kolorów razem z obrazem, wystarczy wybrać obszar do wypełnienia.<br /><br /> Aby użyć aktywnego zaznaczenia kolorów , w tym wartości kanału alfa, aby zastąpić obraz, naciśnij i przytrzymaj **klawisz Shift,** a następnie wybierz obszar do wypełnienia.|

### <a name="image-properties"></a>Właściwości obrazu

Okno **Właściwości** służy do określania różnych właściwości obrazu. Można na przykład ustawić właściwości szerokości i wysokości, aby zmienić rozmiar obrazu.

W poniższej tabeli opisano właściwości obrazu:

|Właściwość|Opis|
|--------------|-----------------|
|impulsów|Szerokość obrazu.|
|Właściwość Height|Wysokość obrazu.|
|Bity na piksel|Liczba bitów reprezentujących każdy piksel. Wartość tej właściwości zależy od **formatu koloru** obrazu.|
|Wybór przezroczysty|**True,** aby połączyć warstwę zaznaczenia z obrazem głównym, na podstawie wartości alfa warstwy zaznaczenia; w przeciwnym razie **False**. Ten element jest dostępny tylko dla obrazów obsługujących alfa.|
|Format|Format koloru obrazu. W zależności od formatu obrazu można określić różne formaty kolorów. Format kolorów definiuje liczbę i rodzaj kanałów kolorów, które są zawarte w obrazie, a także rozmiar i kodowanie różnych kanałów.|
|Poziom MIP|Aktywny poziom MIP. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|Liczba poziomów MIP|Całkowita liczba poziomów MIP na obrazie. Ten element jest dostępny tylko dla tekstur, które mają poziomy MIP.|
|Liczba klatek|Całkowita liczba klatek na obrazie. Ten element jest dostępny tylko dla obrazów obsługujących tablice tekstur.|
|Klatka|Bieżąca ramka. Można wyświetlić tylko pierwszą klatkę; wszystkie pozostałe klatki zostaną utracone po zapisaniu obrazu.|
|Liczba plasterków głębokości|Całkowita liczba wycinków głębi na obrazie. Ten element jest dostępny tylko dla obrazów obsługujących tekstury woluminu.|
|Plasterek głębokości|Bieżący plasterek głębokości. Można wyświetlić tylko pierwszy plasterek; wszystkie pozostałe plasterki zostaną utracone podczas zapisywania obrazu.|

> [!NOTE]
> Ponieważ **właściwość Obróć według** ma zastosowanie do wszystkich narzędzi i wybranych regionów, zawsze pojawia się u dołu okna **Właściwości** wraz z innymi właściwościami narzędzia. **Obróć przez** jest zawsze wyświetlany, ponieważ cały obraz jest niejawnie zaznaczone, gdy nie ma innego zaznaczenia lub aktywnego narzędzia. Aby uzyskać więcej informacji na temat właściwości **Obróć według,** zobacz [Właściwości narzędzia](#tool -properties).

### <a name="resize-images"></a>Ponowne rozmiary obrazów

Rozmiar obrazu można zmienić na dwa sposoby. W obu przypadkach **Edytor obrazów** używa interpolacji dwuliniowej do ponownegopróbowania obrazu.

- W oknie **Właściwości** określ nowe wartości właściwości **Szerokość** i **Wysokość.**

- Zaznacz cały obraz i użyj znaczników obramowania, aby zmienić jego rozmiar.

### <a name="selected-regions"></a>Wybrane regiony

Zaznaczenia w **Edytorze obrazów** definiują regiony obrazu, które są aktywne. Aktywne regiony są dotknięte narzędziami i przekształceniami. W przypadku aktywnego zaznaczenia większość narzędzi i przekształceń nie ma wpływu na obszary poza wybranym regionem. Jeśli nie ma aktywnego zaznaczenia, cały obraz jest aktywny.

Większość narzędzi **(Ołówek,** **Pędzel,** **Aerograf,** **Wypełnienie,** **Gumka**i 2D prymitywów) i przekształcenia **(Obróć,** **Przytnij,** **Odwróć kolory,** **Przerzuć poziomo**i **Przerzuć w pionie)** są ograniczone lub zdefiniowane przez aktywne zaznaczenie. Jednak niektóre narzędzia **(Kroplomierz** i **tekst)** i przekształcenia **(Generowanie mipsów)** nie mają wpływu na żadne aktywne zaznaczenie. Narzędzia te zawsze zachowują się tak, jakby cały obraz był aktywnym zaznaczeniem.

Podczas wybierania regionu można nacisnąć i przytrzymać **klawisz Shift,** aby zaznaczyć proporcjonalnie (kwadrat). W przeciwnym razie zaznaczenie nie jest ograniczone.

#### <a name="resize-selections"></a>Ponowne zaznaczanie rozmiaru

Po wybraniu regionu można zmienić jego rozmiar lub jego zawartość obrazu, zmieniając rozmiar znacznika zaznaczenia. Podczas zmiany rozmiaru wybranego regionu można użyć następujących klawiszy modyfikujących, aby zmienić zachowanie wybranego regionu podczas zmiany jego rozmiaru:

**Ctrl** — kopiuje zawartość wybranego regionu przed jego ponownym szesnastką. Spowoduje to, że oryginalny obraz pozostaje nienaruszony podczas zmieniania jego rozmiarów.

**Shift** — zmienia rozmiar wybranego regionu proporcjonalnie do jego pierwotnego rozmiaru.

**Alt** — zmienia rozmiar regionu zaznaczenia. To pozostawia obraz niezmodyfikowany.

W poniższej tabeli opisano prawidłowe kombinacje klawiszy modyfikatora:

|Ctrl|Przesunięcia|Alt|Opis|
|----------|-----------|---------|-----------------|
||||Rozmiar zawartości wybranego regionu.|
||**Przesunięcia**||Proporcjonalnie zmienić rozmiar zawartości wybranego regionu.|
|||**Alt**|Zmienić rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
||**Przesunięcia**|**Alt**|Proporcjonalnie zmienić rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
|**Ctrl**|||Kopiuje, a następnie edytuje rozmiar zawartości wybranego regionu.|
|**Ctrl**|**Przesunięcia**||Kopie, a następnie proporcjonalnie zmienić rozmiar zawartości wybranego regionu.|

### <a name="tool-properties"></a>Właściwości narzędzia

Gdy narzędzie jest zaznaczone, można użyć okna **Właściwości,** aby określić szczegóły dotyczące jego wpływu na obraz. Można na przykład ustawić grubość narzędzia **Ołówek** lub kolor narzędzia **Pędzel.**

Można ustawić zarówno kolor pierwszego planu, jak i kolor tła. Oba obsługują kanał alfa, aby zapewnić krycie zdefiniowane przez użytkownika. Ustawienia dotyczą wszystkich narzędzi. Jeśli używasz myszy, lewy przycisk myszy odpowiada kolorowi pierwszego planu, a prawy przycisk myszy odpowiada kolorowi tła.

W poniższej tabeli opisano właściwości narzędzia:

|Narzędzie|Właściwości|
|----------|----------------|
|Wszystkie narzędzia i selekcje|**Obracanie o**<br /> Określa w stopniach, w których efekt zaznaczenia lub narzędzia jest obracany w kierunku zgodnym z ruchem wskazówek zegara.|
|**Ołówek**, **Szczotka**, **Aerograf**, **Gumka**|**Grubość**<br /> Określa rozmiar obszaru, na który ma wpływ narzędzie.|
|**Tekst**|**Wygładowy**<br /> Rysuje tekst, który ma wygładzane krawędzie. Dzięki temu tekst jest gładszy.<br /><br /> **Wartość**<br /> Tekst, który ma zostać narysowany.<br /><br /> **Czcionka**<br /> Czcionka używana do rysowania tekstu.<br /><br /> **Rozmiar**<br /> Rozmiar tekstu.<br /><br /> **Pogrubienie**<br /> Sprawia, że czcionka jest pogrubiona.<br /><br /> **Kursywa**<br /> Sprawia, że czcionka jest kursywą.<br /><br /> **Podkreślony**<br /> Sprawia, że czcionka jest podkreślona.|
|**Prymityw 2D**|**Wygładowy**<br /> Rysuje prymitywy, które mają wygładzane krawędzie. To nadaje im gładszy wygląd.<br /><br /> **Grubość**<br /> Definiuje grubość linii, która tworzy granicę prymitywu.<br /><br /> **Promień X**<br /> (Tylko prostokąt zaokrąglony) Definiuje promień zaokrąglania górnej i dolnej krawędzi pierwotnego.<br /><br /> **Promień Y**<br /> (Tylko prostokąt zaokrąglony) Definiuje promień zaokrąglania dla lewej i prawej krawędzi pierwotnego.|
|**Ołówek**, **Szczotka**, **Aerograf**, **2D Prymitywne**|**Kanały**<br /> Włącza lub wyłącza określone kanały kolorów do wyświetlania i rysowania. Jeśli **widok** jest ustawiony dla określonego kanału kolorów, ten kanał jest widoczny na obrazie; w przeciwnym razie nie jest widoczny. Jeśli **draw** jest ustawiony dla określonego kanału kolorów, na ten kanał mają wpływ operacje rysowania; w przeciwnym razie tak nie jest.|
|**Wybór różdżki**, **Wypełnienie**|**Tolerancji**<br /> Definiuje maksymalną różnicę między sąsiednimi kolorami, w których są uważane za podobne, tak aby mniej lub więcej podobnych kolorów było częścią dotkniętego lub wybranego regionu. Domyślnie wartość wynosi 32, co oznacza, że sąsiednie piksele w obrębie 32 odcieni (jaśniejsze lub ciemniejsze) oryginalnego koloru są uważane za część regionu.|

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełączanie do trybu **wyboru**|**S**|
|Przełączanie do trybu **powiększenia**|**Z**|
|Przełączanie do trybu **przesuwania**|**K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Usuwanie**|
|Anuluj bieżące zaznaczenie|**Esc** (ucieczka)|
|Powiększanie|**Ctrl**+**Kółko myszy do przodu**<br /><br /> **PageUp ctrl**+**PageUp**<br /><br /> Znak Plus**+**( )|
|Pomniejszanie|**Ctrl**-**Kółko myszy do tyłu**<br /><br /> **Przychylenia**-**strony** Ctrl<br /><br /> Znak minus**-**( )|
|Przesuwanie obrazu w górę|**Obrót kółkiem myszy do tyłu**<br /><br /> **PageDown**|
|Przesuwanie obrazu w dół|**Obrót kółkiem myszy do przodu**<br /><br /> **PageUp**|
|Przesuwanie obrazu w lewo|**Shift**+**Kółko myszy do tyłu**<br /><br /> **Ruch kółkiem myszy w lewo**<br /><br /> **Przesuń**+**pagedown**|
|Przesuwanie obrazu w prawo|**Przesunięcie**+**kółka myszy do przodu**<br /><br /> **Ruch kółkiem myszy w prawo**<br /><br /> **Przesunięcie**+**strony**|
|Powiększanie do rzeczywistego rozmiaru|**Ctrl**+**0** (zero)|
|Dopasowywać obraz do okna|**Ctrl**+**G**, **Ctrl**+**F**|
|Dopasowywać obraz do szerokości okna|**Ctrl**+**G**, **Ctrl**+**I**|
|Przełączanie siatki|**Ctrl**+**G**, **Ctrl**+**G**|
|Przycinanie obrazu do bieżącego zaznaczenia|**Ctrl**+**G**, **Ctrl**+**C**|
|Zobacz następny (wyższy szczegół) poziom MIP|**Ctrl**+**G**, **Ctrl**+**6**|
|Wyświetlanie poprzedniego (niższego szczegółu) poziomu MIP|**Ctrl**+**G**, **Ctrl**+**7**|
|Przełączanie kanału koloru czerwonego|**Ctrl**+**G**, **Ctrl**+**1**|
|Przełączanie kanału koloru zielonego|**Ctrl**+**G**, **Ctrl**+**2**|
|Przełączanie niebieskiego kanału kolorów|**Ctrl**+**G**, **Ctrl**+**3**|
|Przełączanie kanału alfa (przezroczystości)|**Ctrl**+**G**, **Ctrl**+**4**|
|Przełączanie wzoru szachownicy alfa|**Ctrl**+**G**, **Ctrl**+**B**|
|Przełączanie na narzędzie do nieregularnego zaznaczania|**L**|
|Przełącz na narzędzie do zaznaczania różdżki|**M**|
|Przełącz się na narzędzie ołówkowe|**P**|
|Przełącz na narzędzie pędzel|**B**|
|Przełącz do narzędzia wypełniającego|**F**|
|Przełączanie do narzędzia gumki|**E**|
|Przełączanie do narzędzia tekstowego|**T**|
|Przełączanie do narzędzia wyboru koloru (kroplomierza)|**I**|
|Przenieś aktywne zaznaczenie i jego zawartość.|**Klawisze strzałek.**|
|Zmienić rozmiar aktywnego zaznaczenia i jego zawartości.|**Klawisze**+**strzałek** ctrl|
|Przenieś aktywne zaznaczenie, ale nie jego zawartość.|**Klawisze strzałek shift**+**Arrow**|
|Zmienić rozmiar aktywnego zaznaczenia, ale nie jego zawartości.|**Shift**+**Klawisze strzałek** **Ctrl**+|
|Zatwierdzanie bieżącej warstwy|**Zwraca**|
|Zmniejszanie grubości narzędzia|**[**|
|Zwiększanie grubości narzędzia|**]**|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D w grach i aplikacjach](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie narzędzi, których można używać w programie Visual Studio do pracy z zasobami graficznymi, takimi jak tekstury i obrazy, modele 3D i efekty modułu cieniującego.|
|[Edytor modelu](../designers/model-editor.md)|W tym artykule opisano sposób korzystania z Edytora modeli programu Visual Studio do pracy z modelami 3D.|
|[Projektant cieniowania](../designers/shader-designer.md)|W tym artykule opisano, jak używać Projektanta modułu cieniującego programu Visual Studio do pracy z modułami cieniu.|
