---
title: Shader Designer
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85ce7b0f270f0da8728b17610a683dcc17d06189
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589932"
---
# <a name="shader-designer"></a>Shader Designer

W tym dokumencie opisano sposób pracy z **projektantem programu** Visual Studio Shader Designer w celu tworzenia, modyfikowania i eksportowania niestandardowych efektów wizualnych, które są znane jako *moduły cieniowania.*

Projektanta **modułów cieniowania** można używać do tworzenia niestandardowych efektów wizualnych dla gry lub aplikacji, nawet jeśli nie znasz programowania języka cieniowania wysokiego poziomu (HLSL). Aby utworzyć moduł cieniujący w **projektancie modułu cieniującego,** należy go ułożyć jako wykres. Oznacza to, że można dodać do *węzłów* powierzchni projektowej, które reprezentują dane i operacje, a następnie nawiązać połączenia między nimi, aby zdefiniować sposób przetwarzania danych przez operacje. W każdym węźle operacji podgląd efektu do tego momentu jest dostarczany, dzięki czemu można wizualizować jego wynik. Dane przepływa przez węzły w kierunku węzła końcowego, który reprezentuje dane wyjściowe modułu cieniującego.

## <a name="supported-formats"></a>Obsługiwane formaty

**Projektant modułu cieniującego** obsługuje następujące formaty modułu cieniującego:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (wyświetlanie, edytowanie, eksportowanie)|
|-----------------| - | - |
|Skierowany język modułu cieniującego wykresu|*.dgsl*|Widok, edycja|
|Moduł cieniujący HLSL (kod źródłowy)|*.hlsl*|Eksportowanie|
|Moduł cieniujący HLSL (kod bajtowy)|*.cso*|Eksportowanie|
|Nagłówek C++ (tablica kodów bajtowych HLSL)|*.h*|Eksportowanie|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano sposób dodawania modułu cieniującego DGSL do projektu programu Visual Studio C++ i zawiera podstawowe informacje ułatwiające rozpoczęcie pracy.

> [!NOTE]
> Automatyczna integracja kompilacji elementów graficznych, takich jak wykresy modułu cieniującego (pliki dgsl) jest obsługiwana tylko dla projektów języka C++.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Aby dodać moduł cieniujący DGSL do projektu

1. Upewnij się, że masz zainstalowany wymagany składnik programu Visual Studio, który jest potrzebny do pracy z grafiką. Składnik nosi nazwę **Edytory obrazów i modeli 3D**.

   Aby go zainstalować, otwórz Instalatora programu Visual Studio, wybierając **pozycję Narzędzia** > **Pobierz narzędzia i funkcje** z paska menu, a następnie wybierz kartę **Poszczególne składniki.** Wybierz składnik **Edytory obrazów i modeli 3D** w kategorii **Gry i grafika,** a następnie wybierz pozycję **Modyfikuj**.

   ![Komponent edytorów obrazów i modeli 3D](media/image-3d-model-editors-component.png)

2. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu C++, do którego chcesz dodać moduł cieniujący, a następnie wybierz pozycję **Dodaj** > **nowy element**.

3. W oknie dialogowym **Dodawanie nowego elementu** w obszarze **Zainstalowane**wybierz pozycję **Grafika**, a następnie wybierz pozycję **Visual Shader Graph (.dgsl)**.

   > [!NOTE]
   > Jeśli nie widzisz kategorii **Grafika** w oknie dialogowym **Dodawanie nowego elementu** i masz zainstalowany składnik **Edytory obrazów i modeli 3D,** elementy graficzne nie są obsługiwane dla typu projektu.

4. Określ **nazwę** pliku modułu cieniującego i **lokalizację, w** której ma zostać utworzony.

5. Wybierz przycisk **Dodaj**.

### <a name="the-default-shader"></a>Domyślny moduł cieniujący

Za każdym razem, gdy tworzysz moduł cieniujący DGSL, rozpoczyna się on jako minimalny moduł cieniujący, który ma tylko węzeł **Kolor punktu** połączony z **węzłem Kolor końcowy.** Chociaż ten moduł cieniujący jest kompletny i funkcjonalny, nie robi wiele. W związku z tym pierwszym krokiem w tworzeniu działającego modułu cieniującego jest często usunięcie **węzła Kolor punktu** lub odłączenie go od **węzła Kolor końcowy,** aby zrobić miejsce dla innych węzłów.

## <a name="work-with-the-shader-designer"></a>Praca z projektantem modułu cieniującego

W poniższych sekcjach opisano sposób używania Projektanta modułów cieniucych do pracy z niestandardowymi modułami cieniu.

### <a name="shader-designer-toolbars"></a>Paski narzędzi Projektanta modułów cieniucych

Paski narzędzi Projektanta modułów cieniucych zawierają polecenia ułatwiające pracę z wykresami modułów cieniowania DGSL.

Polecenia wpływające na stan projektanta modułu cieniującego znajdują się na pasku narzędzi **Tryb projektanta modułu cieniującego** w głównym oknie programu Visual Studio. Narzędzia i polecenia projektowania znajdują się na pasku narzędzi **Projektanta modułów cieniujących** na powierzchni projektowej projektanta modułu cieniującego.

Oto pasek narzędzi **Trybu projektanta modułu cieniującego:**

![Pasek narzędzi modacyjny projektanta modułu cieniującego.](../designers/media/digit-dsd-modal-toolbar.png)

W tej tabeli opisano elementy na pasku narzędzi **Tryb projektanta modułu cieniującego,** które są wyświetlane w kolejności, w jakiej są wyświetlane od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia interakcję z węzłami i krawędziami na wykresie. W tym trybie można wybrać węzły i przenieść je lub usunąć, a także ustanowić krawędzie lub je podzielić.|
|**Przesuwanie**|Umożliwia ruch wykresu modułu cieniującego względem ramki okna. Aby przesuwać, wybierz punkt na powierzchni projektowej i przesuń go.<br /><br /> W trybie **wyboru** można nacisnąć i przytrzymać **klawisz Ctrl,** aby tymczasowo włączyć tryb **przesuwania.**|
|**Zoom**|Umożliwia wyświetlanie mniej lub bardziej cieniowania wykresu szczegółów względem ramki okna. W trybie **powiększenia** wybierz punkt na powierzchni projektowej, a następnie przesuń go w prawo lub w dół, aby powiększyć, lub w lewo lub w górę, aby pomniejszyć widok.<br /><br /> W trybie **wyboru** można nacisnąć i przytrzymać **klawisz Ctrl,** aby powiększyć lub pomniejszyć widok za pomocą kółka myszy.|
|**Powiększenie, aby dopasować**|Wyświetla pełny wykres modułu cieniującego w ramce okna.|
|**Tryb renderowania w czasie rzeczywistym**|Gdy renderowanie w czasie rzeczywistym jest włączone, Visual Studio ponownie rysuje powierzchni projektowej, nawet wtedy, gdy nie jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Podgląd z kulą**|Gdy ta opcja jest włączona, model kuli jest używany do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Podgląd z modułem**|Po włączeniu model modułu jest używany do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Podgląd z cylindrem**|Po włączeniu model walca jest używany do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Podgląd ze stożkiem**|Gdy ta opcja jest włączona, model stożka jest używany do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Podgląd z czajniczek**|Po włączeniu model czajnika służy do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Podgląd z płaszczyzną**|Gdy ta opcja jest włączona, model płaszczyzny jest używany do podglądu modułu cieniującego. Można włączyć tylko jeden kształt podglądu naraz.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **przybornik**.|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa **właściwości** okna.|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Eksport:** Umożliwia eksport modułu cieniującego w kilku formatach.<br /><br /> **Eksportuj jako:** Eksportuje moduł cieniujący jako kod źródłowy HLSL lub jako skompilowany kod bajtowy modułu cieniującego. Aby uzyskać więcej informacji na temat eksportowania modułów cieniowania, zobacz [Jak: Eksportowanie modułu cieniującego](../designers/how-to-export-a-shader.md).<br /><br /> **Aparaty graficzne:** Umożliwia wybór modułu renderowania używanego do wyświetlania powierzchni projektowej.<br /><br /> **Renderowanie za pomocą D3D11:** Używa direct3D 11 do renderowania powierzchni projektowej projektanta modułu cieniującego.<br /><br /> **Render z D3D11WARP**: Używa Direct3D 11 Windows Advanced Rasterization Platform (WARP) do renderowania powierzchni projektowej projektanta modułu cieniującego.<br /><br /> **Widok**: Umożliwia wybór dodatkowych informacji o Projektancie modułu cieniującego.<br /><br /> **Liczba klatek na sekundę:** Po włączeniu wyświetlana jest bieżąca liczba klatek na sekundę w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. Ta opcja jest przydatna po włączeniu opcji Tryb renderowania w **czasie rzeczywistym.**|

> [!TIP]
> Możesz wybrać przycisk **Zaawansowane,** aby ponownie uruchomić ostatnie polecenie.

### <a name="work-with-nodes-and-connections"></a>Praca z węzłami i połączeniami

Użyj trybu **wyboru,** aby dodać, usunąć, zmienić położenie, połączyć i skonfigurować węzły. Oto jak wykonać te podstawowe operacje:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Aby wykonać podstawowe operacje w trybie wyboru

- Oto kroki tej procedury:

  - Aby dodać węzeł do wykresu, zaznacz go w **przyborniku,** a następnie przenieś go na powierzchnię projektową.

  - Aby usunąć węzeł z wykresu, zaznacz go, a następnie naciśnij klawisz **Delete**.

  - Aby zmienić położenie węzła, zaznacz go, a następnie przenieś go w nową lokalizację.

  - Aby połączyć dwa węzły, przenieś terminal wyjściowy jednego węzła do terminalu wejściowego drugiego węzła. Można podłączyć tylko zaciski, które mają zgodne typy. Linia między zaciskami pokazuje połączenie.

  - Aby usunąć połączenie, w menu skrótów dla jednego z podłączonych terminali wybierz polecenie **Przerwij łącza**.

  - Aby skonfigurować właściwości węzła, wybierz węzeł, a następnie w oknie **Właściwości** określ nowe wartości właściwości.

### <a name="preview-shaders"></a>Podgląd modułów cieniowania

Aby ułatwić zrozumienie, jak będzie wyświetlany moduł cieniujący w aplikacji, możesz skonfigurować sposób wyświetlania podglądu efektu. Aby przybliżyć aplikację, można wybrać jeden z kilku kształtów do renderowania, konfigurowania tekstur i innych parametrów materiałowych, włączania animacji efektów opartych na czasie i sprawdzania podglądu pod różnymi kątami.

#### <a name="shapes"></a>Kształty

Projektant modułu cieniującego zawiera sześć kształtów — kulę, kostkę, cylinder, stożek, czajnik i płaszczyznę — za pomocą którego można wyświetlić podgląd modułu cieniującego. W zależności od modułu cieniującego niektóre kształty mogą zapewniać lepszy podgląd.

Aby wybrać kształt podglądu, na pasku narzędzi **Tryby projektanta modułu cieniującego** wybierz odpowiedni kształt.

#### <a name="textures-and-material-parameters"></a>Tekstury i parametry materiału

Wiele modułów cieniowania polega na teksturach i właściwościach materiału, aby uzyskać unikatowy wygląd dla każdego rodzaju obiektu w aplikacji. Aby zobaczyć, jak będzie wyglądał moduł cieniujący w aplikacji, można ustawić tekstury i właściwości materiału, które są używane do renderowania podglądu, aby dopasować tekstury i parametry, które mogą być używane w aplikacji.

Aby powiązać inną teksturę z rejestrem tekstur lub zmodyfikować inne parametry materiału:

1. W trybie **wyboru** wybierz pusty obszar powierzchni projektowej. Powoduje to, że okno **Właściwości** do wyświetlania właściwości globalnego modułu cieniującego.

2. W oknie **Właściwości** określ nowe wartości właściwości tekstury i parametrów, które chcesz zmienić.

W poniższej tabeli przedstawiono parametry modułu cieniującego, które można modyfikować:

|Parametr|Właściwości|
|---------------|----------------|
|**Tekstura 1** - **Tekstura 8**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Nazwa pliku**: Pełna ścieżka pliku tekstury skojarzonego z tym rejestrem tekstur.|
|**Otoczenie materiału**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**: Rozproszony kolor bieżącego piksela z powodu oświetlenia pośredniego lub otoczenia.|
|**Materiał rozproszony**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość:** Kolor opisujący sposób rozpraszania bieżącego piksela przez bezpośrednie oświetlenie.|
|**Materiał Emissive**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**: Wkład koloru bieżącego piksela z powodu oświetlenia dostarczonego przez siebie.|
|**Materiał Specular**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość:** Kolor opisujący sposób, w jaki bieżący piksel odzwierciedla bezpośrednie oświetlenie.|
|**Moc lustrzana materiału**|**Access:** **Public,** aby umożliwić ustawienie właściwości z Edytora modeli; w przeciwnym **razie, Prywatne**.<br /><br /> **Wartość**: Wykładnik definiujący intensywność świateł lustrzanych w bieżącym pikselu.|

#### <a name="time-based-effects"></a>Efekty oparte na czasie

Niektóre moduły cieniowania mają składnik oparty na czasie, który animuje efekt. Aby pokazać, jak wygląda efekt w działaniu, podgląd musi być aktualizowany kilka razy na sekundę. Domyślnie podgląd jest aktualizowany tylko po zmianie modułu cieniującego; aby zmienić to zachowanie, aby można było wyświetlać efekty oparte na czasie, należy włączyć renderowanie w czasie rzeczywistym.

Aby włączyć renderowanie w czasie rzeczywistym, na pasku narzędzi Projektanta modułu cieniującego wybierz pozycję **Renderowanie w czasie rzeczywistym**.

#### <a name="examine-the-effect"></a>Zbadaj efekt

Na wiele modułów cieniowania mają wpływ zmienne, takie jak kąt widzenia lub oświetlenie kierunkowe. Aby sprawdzić, jak efekt reaguje w miarę zmiany tych zmiennych, można swobodnie obracać kształt podglądu i obserwować zachowanie modułu cieniującego.

Aby obrócić kształt, naciśnij i przytrzymaj **klawisz Alt**, a następnie zaznacz dowolny punkt na powierzchni projektowej i przesuń go.

### <a name="export-shaders"></a>Eksportowanie modułów cieniujących

Aby można było użyć modułu cieniującego w aplikacji, należy go wyeksportować w formacie zrozumiałym dla programu DirectX.

Programy cieniowania można eksportować jako kod źródłowy HLSL lub jako skompilowany kod bajtowy modułu cieniującego. Kod źródłowy HLSL jest eksportowany do pliku tekstowego z rozszerzeniem nazwy pliku *.hlsl.* Kod bajtowy modułu cieniującego można wyeksportować albo do surowego pliku binarnego z rozszerzeniem nazwy pliku *cso,* albo do pliku nagłówka C++ (*.h),* który koduje bajtowy moduł cieniujący do tablicy.

Aby uzyskać więcej informacji na temat eksportowania modułów cieniowania, zobacz [Jak: Eksportowanie modułu cieniującego](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------| - |
|Przełączanie do trybu **wyboru**|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|Przełączanie do trybu **powiększenia**|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|Przełączanie do trybu **przesuwania**|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **K**|
|Zaznacz wszystkie|**Ctrl**+**A**|
|Usuń bieżące zaznaczenie|**Usuwanie**|
|Anuluj bieżące zaznaczenie|**Ucieczka** (**Esc**)|
|Powiększanie|**Ctrl**+**Kółko myszy do przodu**<br /><br /> Znak Plus**+**( )|
|Pomniejszanie|**Ctrl**+**Kółko myszy do tyłu**<br /><br /> Znak minus**-**( )|
|Przesuwanie powierzchni projektowej w górę|**Obrót kółkiem myszy do tyłu**<br /><br /> **PageDown**|
|Przesuwanie powierzchni projektowej w dół|**Obrót kółkiem myszy do przodu**<br /><br /> **PageUp**|
|Przesuwanie powierzchni projektowej w lewo|**Shift**+**Kółko myszy do tyłu**<br /><br /> **Ruch kółkiem myszy w lewo**<br /><br /> **Przesuń**+**pagedown**|
|Przesuwanie powierzchni projektowej w prawo|**Przesunięcie**+**kółka myszy do przodu**<br /><br /> **Ruch kółkiem myszy w prawo**<br /><br /> **Przesunięcie**+**strony**|
|Przenoszenie fokusu klawiatury do innego węzła|Klawisze **strzałek**|
|Wybierz węzeł, który ma fokus klawiatury (dodaje węzeł do grupy wyboru)|**Spacja shift**+**Spacebar**|
|Przełączanie zaznaczenia węzła z fokusem klawiatury|**Spacja Ctrl**+**Spacebar**|
|Przełączanie bieżącego zaznaczenia (jeśli nie wybrano żadnych węzłów, wybierz węzeł z fokusem klawiatury)|**Spacja**|
|Przenoszenie bieżącego zaznaczenia w górę|**Strzałka shift**+**w górę**|
|Przenoszenie bieżącego zaznaczenia w dół|**Strzałka shift**+**w dół**|
|Przenoszenie bieżącego zaznaczenia w lewo|**Przesunięcie**+**strzałki w lewo**|
|Przenoszenie bieżącego zaznaczenia w prawo|**Shift**+**Strzałka w prawo**.|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D w grach i aplikacjach](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie narzędzi programu Visual Studio, których można używać do pracy z teksturami i obrazami, modelami 3D i efektami modułu cieniującego.|
|[Edytor obrazów](../designers/image-editor.md)|W tym artykule opisano, jak używać Edytora obrazów programu Visual Studio do pracy z teksturami i obrazami.|
|[Edytor modeli](../designers/model-editor.md)|W tym artykule opisano sposób korzystania z Edytora modeli programu Visual Studio do pracy z modelami 3D.|
