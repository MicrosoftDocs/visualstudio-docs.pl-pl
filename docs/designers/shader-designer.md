---
title: Shader Designer
description: Dowiedz się, jak współpracować z projektantem cieniowania programu Visual Studio, aby tworzyć, modyfikować i eksportować niestandardowe efekty wizualne, które są znane jako programy do cieniowania.
ms.custom: SEO-VS-2020
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b637c4cf1b065426bb4070d2e08bf59984c8ff23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902363"
---
# <a name="shader-designer"></a>Shader Designer

W tym dokumencie opisano sposób pracy z **projektantem cieniowania** programu Visual Studio w celu tworzenia, modyfikowania i eksportowania niestandardowych efektów wizualnych, które są znane jako programy do *cieniowania*.

Za pomocą **projektanta cieniowania** można tworzyć niestandardowe efekty wizualne dla swojej gry lub aplikacji, nawet jeśli nie znasz programowania w języku HLSL (High-Level Shader Language). Aby utworzyć program do cieniowania w **projektancie cieniowania**, można go określić jako Graf. Oznacza to, że należy dodać do *węzłów* powierzchni projektowej, które reprezentują dane i operacje, a następnie nawiązać połączenia między nimi w celu zdefiniowania sposobu przetwarzania danych przez operacje. W każdym węźle operacji jest dostępny podgląd efektu do tego punktu, aby można było wizualizować jego wyniki. Dane są przepływane przez węzły do końcowego węzła, który reprezentuje dane wyjściowe cieniowania.

## <a name="supported-formats"></a>Obsługiwane formaty

Projektant programu do **cieniowania** obsługuje następujące formaty programu do cieniowania:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (wyświetlanie, edytowanie i eksportowanie)|
|-----------------| - | - |
|Język ukierunkowanego modułu cieniującego wykresów|*. dgsl*|Wyświetl, edytuj|
|Program do cieniowania HLSL (kod źródłowy)|*. HLSL*|Eksportowanie|
|Program do cieniowania HLSL (kod bajtowy)|*. CSO*|Eksportowanie|
|Nagłówek C++ (tablica kodu bajtowego HLSL)|*. h*|Eksportowanie|

## <a name="get-started"></a>Rozpoczęcie pracy

W tej sekcji opisano sposób dodawania modułu cieniującego DGSL do projektu Visual Studio C++ i przedstawiono podstawowe informacje ułatwiające rozpoczęcie pracy.

> [!NOTE]
> Automatyczna integracja kompilacji elementów graficznych, takich jak grafy programu do cieniowania (pliki. dgsl), jest obsługiwana tylko dla projektów języka C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Aby dodać cieniowanie DGSL do projektu

1. Upewnij się, że masz zainstalowany wymagany składnik programu Visual Studio, który jest potrzebny do pracy z grafiką. Składnik jest nazywany **edytorami obrazów i modeli 3W**.

   Aby go zainstalować, Otwórz Instalator programu Visual Studio, wybierając pozycję **Narzędzia**  >  **Pobierz narzędzia i funkcje** z paska menu, a następnie wybierz kartę **poszczególne składniki** . Wybierz składnik **obrazy i edytory modelu 3W** w kategorii **gry i grafika** , a następnie wybierz polecenie **Modyfikuj**.

   ![Składnik edytorów obrazów i modeli 3W](media/image-3d-model-editors-component.png)

2. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu języka C++, do którego chcesz dodać program do cieniowania, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.

3. W oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane** wybierz pozycję **grafika**, a następnie wybierz pozycję **Wykres cieniowania wizualizacji (. dgsl)**.

   > [!NOTE]
   > Jeśli kategoria **grafika** nie jest widoczna w oknie dialogowym **Dodaj nowy element** i masz zainstalowany składnik **edytory obrazów i modeli 3W** , elementy graficzne nie są obsługiwane dla typu projektu.

4. Określ **nazwę** pliku programu do cieniowania i **lokalizację** , w której ma zostać utworzona.

5. Wybierz przycisk **Dodaj**.

### <a name="the-default-shader"></a>Domyślne cieniowanie

Za każdym razem, gdy tworzysz cieniowanie DGSL, rozpoczyna się to minimalny program do cieniowania, który ma tylko węzeł **koloru punktu** , który jest połączony z **końcowym** węzłem koloru. Mimo że ten program do cieniowania jest kompletny i funkcjonalny, nie wykonuje tego więcej. W związku z tym pierwszy krok tworzenia działającego programu do cieniowania często polega na usunięciu węzła **koloru punktu** lub rozłączeniu go od **końcowego węzła koloru** , aby zwolnić miejsce na inne węzły.

## <a name="work-with-the-shader-designer"></a>Współpraca z projektantem programu do cieniowania

W poniższych sekcjach opisano, jak używać projektanta cieniowania do pracy z niestandardowymi narzędziami do cieniowania.

### <a name="shader-designer-toolbars"></a>Paski narzędzi projektanta cieniowania

Paski narzędzi projektanta cieniowania zawierają polecenia, które ułatwiają korzystanie z grafów cieniowania DGSL.

Polecenia, które mają wpływ na stan projektanta cieniowania, znajdują się na pasku narzędzi **tryb projektanta cieniowania** w głównym oknie programu Visual Studio. Narzędzia i polecenia projektowania znajdują się na pasku narzędzi **projektanta cieniowania** na powierzchni projektowej projektanta programu do cieniowania.

Oto pasek narzędzi **tryb projektanta cieniowania** :

![Modalny pasek narzędzi projektanta programu do cieniowania.](../designers/media/digit-dsd-modal-toolbar.png)

W tej tabeli opisano elementy na pasku narzędzi **tryb projektanta cieniowania** , które są wymienione w kolejności, w jakiej są wyświetlane od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia interakcję z węzłami i krawędziami na wykresie. W tym trybie można wybrać węzły i przenieść je lub usunąć. można również ustalić krawędzie lub je podzielić.|
|**Panoramowanie**|Włącza przenoszenie grafu cieniowania względem ramki okna. Aby przesunąć, wybierz punkt na powierzchni projektowej i przenieś go wokół siebie.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz **Ctrl** , aby tymczasowo aktywować tryb **przesuwania** .|
|**Powiększenie**|Umożliwia wyświetlanie większej lub mniejszej liczby szczegółów grafu cieniowania względem ramki okna. W trybie **powiększenia** wybierz punkt na powierzchni projektowej, a następnie przenieś go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć.<br /><br /> W trybie **Wybierz** możesz nacisnąć i przytrzymać klawisz **Ctrl** , aby powiększyć lub pomniejszyć, używając kółka myszy.|
|**Dopasuj do rozmiaru**|Wyświetla wykres pełnego modułu cieniującego w ramce okna.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym program Visual Studio ponownie rysuje powierzchnię projektu, nawet jeśli nie jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Podgląd przy użyciu sfery**|Po włączeniu Model sfery jest używany do podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Podgląd przy użyciu modułu**|Po włączeniu Model modułu jest używany do podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Podgląd przy użyciu walca**|Po włączeniu Model walcowy służy do wyświetlania podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Podgląd z stożek**|Po włączeniu Model stożkowy jest używany do podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Podgląd przy użyciu czajniczek**|Po włączeniu Model elementu czajniczek jest używany do podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Podgląd przy użyciu płaszczyzny**|Po włączeniu Model płaszczyzny jest używany do podglądu cieniowania. Można włączyć tylko jeden kształt podglądu w danym momencie.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **Przybornik**.|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa okno **Właściwości** .|
|**Zaawansowany**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Eksport**: umożliwia eksportowanie cieniowania w kilku formatach.<br /><br /> **Eksportuj jako**: Eksportuje program do cieniowania jako kod źródłowy HLSL lub jako skompilowany plik kodu programu do cieniowania. Aby uzyskać więcej informacji o sposobach eksportowania programów do cieniowania, zobacz [How to: Export a Shader](../designers/how-to-export-a-shader.md).<br /><br /> **Aparaty grafiki**: włącza wybór modułu renderowania, który jest używany do wyświetlania powierzchni projektowej.<br /><br /> **Renderowanie przy użyciu d3d11**: używa programu Direct3D 11 do renderowania powierzchni projektowej projektanta cieniowania.<br /><br /> **Renderowanie przy użyciu D3D11WARP**: używa platformy Direct3D 11 Windows Advanced rasteryzacji (Wypaczenie), aby renderować powierzchnię projektowania projektanta programu do cieniowania.<br /><br /> **Widok**: umożliwia wybranie dodatkowych informacji na temat projektanta programu do cieniowania.<br /><br /> **Szybkość klatek**: po włączeniu wyświetla bieżącą stawkę klatki w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. Ta opcja jest przydatna po włączeniu opcji **tryb renderowania w czasie rzeczywistym** .|

> [!TIP]
> Możesz wybrać przycisk **Zaawansowane** , aby ponownie uruchomić ostatnie polecenie.

### <a name="work-with-nodes-and-connections"></a>Pracuj z węzłami i połączeniami

Użyj trybu **SELECT** , aby dodawać, usuwać, zmieniać położenie, łączyć i konfigurować węzły. Poniżej przedstawiono sposób wykonywania tych podstawowych operacji:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Aby wykonać operacje podstawowe w trybie wyboru

- Oto kroki tej procedury:

  - Aby dodać węzeł do wykresu, wybierz go w **przyborniku** , a następnie przenieś do powierzchni projektowej.

  - Aby usunąć węzeł z grafu, zaznacz go, a następnie naciśnij klawisz **delete**.

  - Aby zmienić położenie węzła, zaznacz go, a następnie przenieś do nowej lokalizacji.

  - Aby połączyć dwa węzły, Przenieś Terminal wyjściowy jednego węzła do terminalu wejściowego drugiego węzła. Możliwe jest połączenie tylko terminali, które mają zgodne typy. Linia między terminalami pokazuje połączenie.

  - Aby usunąć połączenie, w menu skrótów dla jednego z podłączonych terminali wybierz opcję **Przerwij linki**.

  - Aby skonfigurować właściwości węzła, wybierz węzeł, a następnie w oknie **Właściwości** Określ nowe wartości właściwości.

### <a name="preview-shaders"></a>Podgląd programów do cieniowania

Aby ułatwić zrozumienie, w jaki sposób program do cieniowania będzie widoczny w aplikacji, możesz skonfigurować sposób wyświetlania podglądu. Aby przybliżyć aplikację, możesz wybrać jeden z kilku kształtów do renderowania, skonfigurować tekstury i inne parametry materiałowe, włączyć animację efektów opartych na czasie i sprawdzić podgląd z różnych kątów.

#### <a name="shapes"></a>Kształty

Projektant programu do cieniowania zawiera sześć kształtów — sfera, moduł, cylinder, stożek, czajniczek i płaszczyznę, których można użyć do podglądu cieniowania. W zależności od modułu cieniującego Niektóre kształty mogą dać lepszy Podgląd.

Aby wybrać kształt podglądu, na pasku narzędzi **tryby projektanta cieniowania** wybierz odpowiedni kształt.

#### <a name="textures-and-material-parameters"></a>Tekstury i parametry materiału

Wiele programów do cieniowania polega na teksturach i właściwościach materiału w celu utworzenia unikatowego wyglądu każdego rodzaju obiektu w aplikacji. Aby zobaczyć, jak będzie wyglądać program do cieniowania w aplikacji, możesz ustawić tekstury i właściwości materiałowe, które są używane do renderowania podglądu, tak aby pasowały do tekstur i parametrów, które mogą być używane w aplikacji.

Aby powiązać inną teksturę z rejestrem tekstury lub zmodyfikować inne parametry materiałowe:

1. W obszarze tryb **wyboru** zaznacz pusty obszar na powierzchni projektowej. Powoduje to wyświetlenie właściwości globalnego cieniowania w oknie **Właściwości** .

2. W oknie **Właściwości** Określ nowe wartości właściwości tekstury i parametrów, które chcesz zmienić.

W poniższej tabeli przedstawiono parametry programu do cieniowania, które można modyfikować:

|Parametr|Właściwości|
|---------------|----------------|
|**Tekstura 1**  -  **Tekstura 8**|**Dostęp**:                             **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Nazwa pliku**: pełna ścieżka pliku tekstury skojarzonego z tym rejestrem tekstury.|
|**Otoczenie materiału**|**Dostęp**:                             **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**: kolor rozpraszania bieżącego piksela ze względu na pośrednie lub oświetlenie otoczenia.|
|**Rozpraszanie materiału**|**Dostęp**: **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**: kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|
|**Emisyjny materiału**|**Dostęp**:                              **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**: udział koloru bieżącego piksela ze względu na własne oświetlenie.|
|**Odblasków materiału**|**Dostęp**:                              **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**: kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|
|**Odblasków materiału**|**Dostęp**:                             **publiczny** , aby zezwalać na ustawienie właściwości z edytora modelu; w przeciwnym razie **prywatny**.<br /><br /> **Wartość**: wykładnik, który definiuje intensywność odblasków świateł na bieżącym pikselu.|

#### <a name="time-based-effects"></a>Efekty zależne od czasu

Niektóre programy do cieniowania mają składnik oparty na czasie, który Animuj efekt. Aby pokazać, jak działa efekt, wersja zapoznawcza musi być aktualizowana kilka razy na sekundę. Domyślnie wersja zapoznawcza jest aktualizowana tylko wtedy, gdy cieniowanie zostanie zmienione; Aby zmienić to zachowanie, tak aby można było wyświetlić efekty zależne od czasu, należy włączyć renderowanie w czasie rzeczywistym.

Aby włączyć renderowanie w czasie rzeczywistym, na pasku narzędzi projektanta cieniowania wybierz opcję **renderowanie** w czasie rzeczywistym.

#### <a name="examine-the-effect"></a>Badanie efektu

Na wiele programów do cieniowania wpływają zmienne, takie jak kąt wyświetlania lub oświetlenie kierunkowe. Aby sprawdzić, jak efekt reaguje na zmiany zmiennych, można swobodnie obrócić kształt w wersji zapoznawczej i obserwować zachowanie programu do cieniowania.

Aby obrócić kształt, naciśnij i przytrzymaj klawisz **Alt**, a następnie wybierz dowolny punkt na powierzchni projektowej i przenieś go.

### <a name="export-shaders"></a>Eksportowanie programów do cieniowania

Zanim będzie można użyć programu do cieniowania w aplikacji, musisz go wyeksportować w formacie rozpoznawanym przez technologię DirectX.

Program do cieniowania można eksportować jako kod źródłowy HLSL lub w postaci kodu bajtowego skompilowanego programu do cieniowania. Kod źródłowy HLSL jest eksportowany do pliku tekstowego, który ma rozszerzenie nazwy pliku *. HLSL* . Kod bajtowy programu do cieniowania można wyeksportować do pliku binarnego RAW, który ma rozszerzenie nazwy pliku *. CSO* lub do pliku nagłówkowego C++ (*. h*), który koduje kod bajtowy modułu cieniującego do tablicy.

Aby uzyskać więcej informacji o sposobach eksportowania programów do cieniowania, zobacz [How to: Export a Shader](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełącz do trybu **wyboru**|**Ctrl** + **G**, **Ctrl** + **Q**<br /><br /> **S**|
|Przełącz do trybu **powiększenia**|**Ctrl** + **G**, **Ctrl** + **Z**<br /><br /> **Porządku**|
|Przełącz do trybu **kadrowania**|**Ctrl** + **G**, **Ctrl** + **P**<br /><br /> **K**|
|Zaznacz wszystko|**Ctrl** + **A**|
|Usuń bieżące zaznaczenie|**Usuwanie**|
|Anuluj bieżące zaznaczenie|**Escape** (**ESC**)|
|Powiększanie|**Ctrl** + **Kółko myszy do przodu**<br /><br /> Znak plus ( **+** )|
|Pomniejszanie|**Ctrl** + **Kółko myszy do tyłu**<br /><br /> Znak minus ( **-** )|
|Przesuń powierzchnię projektu w górę|**Obrót kółkiem myszy do tyłu**<br /><br /> **PageDown**|
|Przesuń powierzchnię projektu w dół|**Obrót kółkiem myszy do przodu**<br /><br /> **PageUp**|
|Przesuń powierzchnię projektu w lewo|**SHIFT** + **Kółko myszy do tyłu**<br /><br /> **Ruch kółkiem myszy w lewo**<br /><br /> **SHIFT** + **PageDown**|
|Przesuń powierzchnię projektu w prawo|**SHIFT** + **Kółko myszy do przodu**<br /><br /> **Ruch kółkiem myszy w prawo**<br /><br /> **SHIFT** + **PageUp**|
|Przesuwanie fokusu klawiatury do innego węzła|Klawisze **strzałek**|
|Wybierz węzeł, który ma fokus klawiatury (dodaje węzeł do grupy wyboru)|**SHIFT** + **Spacja**|
|Przełącz zaznaczenie węzła, który ma fokus klawiatury|**Ctrl** + **Spacja**|
|Przełącz bieżące zaznaczenie (jeśli nie wybrano żadnych węzłów, zaznacz węzeł z fokusem klawiatury)|**Spacja**|
|Przenieś bieżące zaznaczenie w górę|**SHIFT** + **Strzałka w górę**|
|Przenieś bieżące zaznaczenie w dół|**SHIFT** + **Strzałka w dół**|
|Przenieś bieżące zaznaczenie w lewo|**SHIFT** + **Strzałka w lewo**|
|Przenieś bieżące zaznaczenie w prawo|**SHIFT** + **Strzałka w prawo**.|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3W dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera przegląd narzędzi programu Visual Studio, których można użyć do pracy z teksturami i obrazami, modelami 3W i efektami cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje, jak używać edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Edytor modelu](../designers/model-editor.md)|Opisuje sposób używania Edytora modelu programu Visual Studio do pracy z modelami 3W.|
