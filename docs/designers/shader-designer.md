---
title: Shader Designer
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1703d867a529496bb5c524b62ae56ef8d25904b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893017"
---
# <a name="shader-designer"></a>Shader Designer

W tym dokumencie opisano sposób pracy z programem Visual Studio **Shader Designer** tworzenie, modyfikowanie i eksportowanie niestandardowych efektów wizualnych, które są znane jako *programów do cieniowania*.

Możesz użyć **Shader Designer** do tworzenia niestandardowych efektów wizualnych dla Twojej gry lub aplikacji, nawet jeśli nie znasz wysokiego poziomu shader language (HLSL) programowania. Do utworzenia modułu cieniującego w **Shader Designer**, określić ją jako wykres. Oznacza to, możesz dodać do powierzchni projektowej *węzłów* , reprezentowania danych i operacje, a następnie połączenia między nimi do definiowania sposobu operacji przetwarzania danych. W każdym węźle operacji Podgląd efekt do tego punktu znajduje się tak, aby wizualizować jego wynik. Dane przepływają przez węzły kierunku ostatni węzeł, który reprezentuje dane wyjściowe programu do cieniowania.

## <a name="supported-formats"></a>Obsługiwane formaty

**Shader Designer** obsługuje następujące formaty programu do cieniowania:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj eksport)|
|-----------------| - | - |
|Język programu do cieniowania wykresu bezpośredniego|*.dgsl*|Wyświetl, Edytuj|
|Modułu cieniującego HLSL (kodu źródłowego)|*.hlsl*|Eksportowanie|
|Modułu cieniującego HLSL (kodu bajtowego)|*.cso*|Eksportowanie|
|Nagłówek języka C++ (tablica kodu bajtowego języka HLSL)|*.h*|Eksportowanie|

## <a name="get-started"></a>Wprowadzenie

Ta sekcja zawiera opis sposobu dodawania modułu cieniującego DGSL do projektu Visual Studio C++ i zawiera podstawowe informacje, aby pomóc Ci rozpocząć pracę.

> [!NOTE]
> Integracji kompilacji automatyczne grafiki elementów, takich jak wykresy modułu cieniującego (.dgsl plików) jest obsługiwana tylko dla projektów C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Aby dodać modułu cieniującego DGSL do projektu

1. Upewnij się, że masz wymagany program Visual Studio zainstalowany składnik trzeba pracować z grafiki. Składnik ten jest wywoływany **obrazów i modeli 3W edytory**.

   Aby go zainstalować, otwórz Instalator programu Visual Studio, wybierając pozycję **narzędzia** > **Pobierz narzędzia i funkcje** menu paska, a następnie wybierz pozycję **poszczególne składniki**kartę. Wybierz **obrazów i modeli 3W edytory** składnika w obszarze **gier i aplikacji graficznych** kategorii, a następnie wybierz **Modyfikuj**.

   ![Obrazów i modeli 3W składnika edytorów](media/image-3d-model-editors-component.png)

2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu C++, do którego chcesz dodać programu do cieniowania, a następnie wybierz **Dodaj** > **nowy element**.

3. W **Dodaj nowy element** dialogowego **zainstalowane**, wybierz opcję **grafiki**, a następnie wybierz pozycję **wizualny wykres modułu cieniującego (.dgsl)**.

   > [!NOTE]
   > Jeśli nie widzisz **grafiki** kategorii **Dodaj nowy element** okna dialogowego, a **obrazów i modeli 3W edytory** zainstalowany składnik, graficzne elementy nie są obsługiwane. dla danego typu projektu.

4. Określ **nazwa** pliku programu do cieniowania i **lokalizacji** której ma zostać utworzony.

5. Wybierz **Dodaj** przycisku.

### <a name="the-default-shader"></a>Domyślne cieniowanie

Za każdym razem, Tworzenie modułu cieniującego DGSL, rozpoczyna jej jako minimalny programu do cieniowania, który został właśnie **koloru punktu** węzeł, który jest podłączony do **ostateczny kolor** węzła. Mimo że ten program do cieniowania jest kompletne i funkcjonalne, nie wiele. W związku z tym, pierwszym krokiem w tworzeniu cieniowania pracy jest często usunięcie **koloru punktu** węzła lub odłącz je od **ostateczny kolor** węzeł, aby zwolnić miejsce na innych węzłach.

## <a name="work-with-the-shader-designer"></a>Praca z projektanta cieniowania

Poniżej opisano sposób używania projektanta modułu cieniującego do pracy z niestandardowych programów do cieniowania.

### <a name="shader-designer-toolbars"></a>Paski narzędzi Projektanta cieniowania

Program Shader Designer, które zawierają paski narzędzi, polecenia ułatwiające działa z wykresami modułu cieniującego DGSL.

Polecenia, które wpływają na stan Shader Designer znajdują się na **trybu projektanta modułu cieniującego** narzędzi w głównym oknie programu Visual Studio. Narzędzia do projektowania i poleceń, które znajdują się na **Shader Designer** paska narzędzi na powierzchni projektowej projektanta modułu cieniującego.

Oto **trybu projektanta modułu cieniującego** narzędzi:

![Projektant programu do cieniowania modalne paska narzędzi.](../designers/media/digit-dsd-modal-toolbar.png)

W tej tabeli opisano elementy na **trybu projektanta modułu cieniującego** narzędzi, które są wymienione w kolejności, w którym są wyświetlane od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Select**|Umożliwia interakcję z węzłów i krawędzi na wykresie. W tym trybie można wybrać węzłów i przenieść lub usunąć je i można ustanowić krawędzi lub podziel je.|
|**Przesuwanie**|Umożliwia przenoszenie wykres modułu cieniującego w względem ramki okna. Aby panoramować, wybierz punkt na powierzchni projektowej i przesuwaj go.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać **Ctrl** aktywować **Pan** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie więcej lub mniej szczegółów wykres modułu cieniującego względem ramki okna. W **powiększenia** tryb, wybierz punkt na powierzchni projektowej a następnie przesuń w prawo lub w dół, aby powiększyć lub poziomie w lewo lub do powiększania.<br /><br /> W **wybierz** trybu, można nacisnąć i przytrzymać **Ctrl** Aby powiększyć lub pomniejszyć przy użyciu kółka myszy.|
|**Dopasuj widok do rozmiaru**|Wyświetla pełną cieniującego ramki okna.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym programu Visual Studio odrysowuje powierzchnię projektu, nawet wtedy, gdy jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Podgląd przy użyciu kuli**|Po włączeniu model Kula jest używany do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Podgląd przy użyciu modułu**|Po włączeniu modelu modułu jest używany do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Podgląd przy użyciu walca**|Po włączeniu model cylinder służy do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Podgląd przy użyciu stożka**|Po włączeniu model stożek służy do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Podgląd przy użyciu czajniczka**|Po włączeniu model czajniczek służy do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Podgląd przy użyciu płaszczyzny**|Po włączeniu modelu płaszczyzny służy do podglądu modułu cieniującego. Kształt tylko jeden (wersja zapoznawcza) w danym momencie może być włączone.|
|**Przybornik**|Zamiennie pokazuje i ukrywa **przybornika**.|
|**Właściwości**|Można również pokazuje lub ukrywa **właściwości** okna.|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Eksportuj**: Umożliwia eksportowanie cieniowania w różnych formatach.<br /><br /> **Eksportuj jako**: Eksportuje programu do cieniowania, jako kod źródłowy albo HLSL lub kodu bajtowego skompilowanego modułu cieniującego. Aby uzyskać więcej informacji na temat eksportowania programów do cieniowania, zobacz [jak: Eksport cieniowania](../designers/how-to-export-a-shader.md).<br /><br /> **Aparaty grafiki**: Umożliwia wybór modułu renderowania, który służy do wyświetlania na powierzchnię projektową.<br /><br /> **Renderowanie z D3D11**: Używa programu Direct3D 11 do renderowania powierzchni projektowej projektanta modułu cieniującego.<br /><br /> **Renderowanie z D3D11WARP**: Używa programu Direct3D 11 Windows Advanced rasteryzacji platformy WARP () do renderowania powierzchni projektowej projektanta modułu cieniującego.<br /><br /> **Widok**: Umożliwia wybór dodatkowe informacje na temat Shader Designer.<br /><br /> **Klatki, szybkości**: Po włączeniu Wyświetla bieżąca szybkość odtwarzania w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. Ta opcja jest przydatna po włączeniu **tryb renderowania w czasie rzeczywistym** opcji.|

> [!TIP]
> Możesz wybrać **zaawansowane** przycisk, aby ponownie uruchomić ostatnie polecenie.

### <a name="work-with-nodes-and-connections"></a>Praca z węzłów i połączeń

Użyj **wybierz** tryb do dodawania, usuwania, zmienić położenie, łączenie i konfigurowanie węzłów. Poniżej przedstawiono sposób wykonywania tych operacji podstawowe:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Aby wykonywać podstawowe operacje w trybie wybierz

- Oto jak:

   - Aby dodać węzła do wykresu, wybierz ją w **przybornika** i przenieś go do powierzchni projektowej.

   - Aby usunąć węzeł z wykresu, wybierz ją, a następnie naciśnij klawisz **Usuń**.

   - Aby zmienić położenie węzeł, zaznacz ją, a następnie przenieś go do nowej lokalizacji.

   - Aby połączyć z dwoma węzłami, Przenieś terminalu danych wyjściowych z jednym węzłem do terminal wejścia innego węzła. Może być połączona tylko terminale, które mają niezgodne typy. Linię między terminali Pokazuje połączenia.

   - Aby usunąć połączenie, w menu skrótów dla jednej z połączonych terminali, wybierz **Przerwij linki**.

   - Aby skonfigurować właściwości węzła, wybierz węzeł, a następnie w **właściwości** okna, określ nowe wartości właściwości.

### <a name="preview-shaders"></a>Programy do cieniowania (wersja zapoznawcza)

Aby lepiej zrozumieć, jak cieniowania pojawi się w aplikacji, można skonfigurować, jak Twoja efekt jest przeglądany. Zbliżenie aplikacji, można wybrać jedną z kilku kształtów do renderowania, skonfiguruj tekstury i inne parametry materiału, Włącz animacji opartych na czasie efekty i zbadać pod różnymi kątami w wersji zapoznawczej.

#### <a name="shapes"></a>Kształty

Projektant programu do cieniowania zawiera sześć kształty — kuli, moduł, cylinder stożek, czajniczek i płaszczyznę — służące do podglądu modułu cieniującego. W zależności od modułu cieniującego niektórych kształtów może ułatwić lepsze (wersja zapoznawcza).

Aby wybrać kształt (wersja zapoznawcza) na **tryby Projektant programu do cieniowania** narzędzi, wybierz kształt, którego chcesz.

#### <a name="textures-and-material-parameters"></a>Tekstury i parametry materiału

Wiele modułów cieniujących zależą od tego, tekstury i właściwości materiału w celu wygenerowania unikatowego wyglądu dla każdego rodzaju obiektu w aplikacji. Aby zobaczyć, cieniowanie tak, jak będzie wyglądał w swojej aplikacji, można ustawić tekstury i właściwości materiału, które są używane do renderowania (wersja zapoznawcza), aby dopasować tekstury i parametry, które można wykorzystać w swojej aplikacji.

Aby powiązać różne tekstury rejestr tekstury lub zmodyfikować inne parametry materiału:

1. W **wybierz** tryb, wybierz pusty obszar powierzchni projektu. Powoduje to, że **właściwości** okno, aby wyświetlić właściwości globalnego programu do cieniowania.

2. W **właściwości** okna, określ nowe wartości dla właściwości tekstury i parametrów, które chcesz zmienić.

W poniższej tabeli przedstawiono programu do cieniowania, parametry, które można zmodyfikować:

|Parametr|Właściwości|
|---------------|----------------|
|**Tekstury 1** - **tekstury 8**|**Dostęp do**:                             **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Nazwa pliku**: Pełna ścieżka pliku tekstury, który jest skojarzony z tym rejestrem tekstury.|
|**Otoczenie materiału**|**Dostęp do**:                             **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: Kolor rozpraszania bieżącego piksela z powodu oświetlenia pośredniego — lub otoczenia —.|
|**Rozpraszanie materiału**|**Dostęp do**: **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**:  Kolor, który opisuje, jak diffuses przez bieżący piksel oświetlenia bezpośredniego.|
|**Emisja materiału**|**Dostęp do**:                              **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: Udział koloru materiału bieżącego piksela ze względu na własnym podana oświetlenia.|
|**Odblask materiału**|**Dostęp do**:                              **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: Kolor opisujący Odbijanie oświetlenia bezpośredniego przez bieżącego piksela.|
|**Moc odblasku materiału**|**Dostęp do**:                             **Publiczne** umożliwia właściwość można ustawić w edytorze modeli w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: Wykładnik definiujący intensywność światła odbitego na bieżącego piksela.|

#### <a name="time-based-effects"></a>Wpływ na podstawie czasu

Niektóre programy do cieniowania mają animuje efekt składnik oparte na czasie. Aby pokazać, jak wygląda efekt w działaniu, korzystania z wersji zapoznawczej musi zostać zaktualizowane kilka razy na sekundę. Domyślnie program wersji zapoznawczej są aktualizowane tylko po zmianie programu do cieniowania; Aby zmienić to zachowanie, dzięki czemu można wyświetlić wpływ na podstawie czasu, należy włączyć renderowania w czasie rzeczywistym.

Aby włączyć renderowania w czasie rzeczywistym, na pasku narzędzi Projektanta modułu cieniującego wybierz **renderowania w czasie rzeczywistym**.

#### <a name="examine-the-effect"></a>Sprawdź efekt

Wiele programów do cieniowania są zagrożone zmiennych, takich jak wyświetlanie kąt lub kierunkowe oświetlenia. Aby sprawdzić, jak efekt reaguje po zmianie tych zmiennych, możesz swobodnie obróci prostokąt (wersja zapoznawcza) i obserwować zachowanie programu do cieniowania.

Aby obrócić kształt, naciśnij i przytrzymaj **Alt**, a następnie wybrać dowolny punkt na powierzchni projektowej i przenieś ją.

### <a name="export-shaders"></a>Eksportowanie programów do cieniowania

Zanim użyjesz modułu cieniującego w swojej aplikacji, należy go wyeksportować w formacie, który rozumie DirectX.

Programy do cieniowania można wyeksportować jako kod źródłowy języka HLSL lub kodu bajtowego skompilowanego modułu cieniującego. Kod źródłowy języka HLSL jest eksportowany do pliku tekstowego, który ma *.hlsl* rozszerzenie nazwy pliku. Kod bajtowy programu do cieniowania można albo pierwotne plik binarny, który został wyeksportowany *.cso* rozszerzenie nazwy pliku lub do nagłówka C++ (*.h*) plików, które koduje kodu bajtowego programu cieniującego w tablicy.

Aby uzyskać więcej informacji na temat eksportowania programów do cieniowania, zobacz [jak: Eksport cieniowania](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełącz się do **wybierz** tryb|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Przełącz się do **powiększenia** tryb|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Przełącz się do **Pan** tryb|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Delete**|
|Anuluj bieżące zaznaczenie|**Znak ucieczki** (**Esc**)|
|Powiększanie|**CTRL**+**kółkiem myszy do przodu**<br /><br /> Znak plus (**+**)|
|Pomniejszanie|**CTRL**+**obrót kółkiem myszy do tyłu**<br /><br /> Znak minus (**-**)|
|Przesuń w górę powierzchni projektowej|**Obrót kółkiem myszy do tyłu**<br /><br /> **PageDown**|
|Przesuń w dół na powierzchnię projektową|**Obrót kółkiem myszy do przodu**<br /><br /> **PageUp**|
|Przesuń w lewo powierzchni projektowej|**SHIFT**+**obrót kółkiem myszy do tyłu**<br /><br /> **Obrót kółkiem myszy w lewo**<br /><br /> **Shift**+**PageDown**|
|Przesuń w prawo powierzchni projektowej|**SHIFT**+**kółkiem myszy do przodu**<br /><br /> **Obrót kółkiem myszy do prawej**<br /><br /> **SHIFT**+**PageUp**|
|Przenieś fokus klawiatury do innego węzła|**Strzałkę** kluczy|
|Wybierz węzeł, który ma fokus klawiatury (dodaje węzeł do grupy zaznaczenia)|**SHIFT**+**spacja**|
|Przełącz zaznaczenie węzła, który ma fokus klawiatury|**Ctrl**+**Spacebar**|
|Przełączanie bieżącego zaznaczenia (Jeśli nie zaznaczono żadnych węzłów, wybierz węzeł, który ma fokus klawiatury)|**SPACJA**|
|Przenieś bieżący wybór w górę|**SHIFT**+**Strzałka w górę**|
|Przenieś bieżący wybór w dół|**SHIFT**+**strzałkę w dół**|
|Bieżące zaznaczenie w lewo|**SHIFT**+**Strzałka w lewo**|
|Przenieś bieżący wybór w prawo|**SHIFT**+**Strzałka w prawo**.|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Omówienie narzędzi Visual Studio, które służą do pracy z tekstury i obrazy, modele 3D i efekty cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób używania edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Edytor modelu](../designers/model-editor.md)|Opisuje sposób używania edytora modelu programu Visual Studio do pracy z modelami 3D.|