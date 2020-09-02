---
title: Układ dla programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698394"
---
# <a name="layout-for-visual-studio"></a>Układ dla programu Visual Studio
Większość okien dialogowych programu Visual Studio to [układ okien](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)dialogowych, które są nienależącymi do nich oknach dialogowych, które są zgodne ze standardowymi [zasadami układu okien dialogowych systemu Windows](/windows/desktop/uxguide/win-dialog-box). Ponieważ program Visual Studio przechodzi do odświeżania interfejsu użytkownika, niektóre z bardziej widocznych okien dialogowych mają nowy projekt, który określa je jako środowiska definiowania produktu. Ten [Układ okna dialogowego z motywem](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ma wygląd z motywem.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Układ okna dialogowego narzędzi

- Wszystkie kontrolki w oknie dialogowym narzędzi powinny zacząć się od góry/do lewej i przepływać w dół.

- Nigdy nie Wyśrodkuj kontrolek w oknie dialogowym, aby wypełnić duży obszar.

- Użyj czcionki środowiska dla całego tekstu okna dialogowego. Podczas pisania specyfikacji wizualnej, określ czcionkę środowiska zamiast wybierać konkretną czcionkę i rozmiar. Sprawdź [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Używaj spójnych odstępów między kontrolkami i umieszczania w celu wspierania celu dla jakości w craftsmanship.

- Okna dialogowe mogą stać się bardziej złożone z większej liczby kontrolek, unikatowych juxtaposition formantów lub obu. W tych złożonych sytuacjach należy zapewnić odpowiednie miejsce między grupami kontrolek, aby umożliwić użytkownikowi przeanalizowanie przepływu logicznego.

### <a name="utility-dialog-layout-examples"></a>Przykłady układu okna dialogowego narzędzi
 Wszystkie wymiary są wyrażane jako piksele.

 ![Odstępy okna dialogowego dla etykiet powyżej kontrolek](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 — a_UtilitySpacingAbove")

 **Rysunek 08,01-a: wskazówki dotyczące odstępów dla okien dialogowych z etykietami powyżej formantów**

 ![Odstępy okna dialogowego dla etykiet po lewej stronie kontrolek](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 — b_UtilitySpacingLeft")

 **Rysunek 08,01-b: wskazówki dotyczące odstępów dla okien dialogowych z etykietami po lewej stronie formantów**

### <a name="layout-details"></a>Szczegóły układu

#### <a name="margins"></a>Marginesy

- Wszystkie okna dialogowe powinny zawierać obramowanie o 12 pikseli wokół wszystkich krawędzi.

- Marginesy w obrębie ramki grupy powinny mieć 9 pikseli od krawędzi ramki.

- Marginesy w kontrolce karty powinny mieć wartość 6 pikseli od krawędzi kontrolki karta.

#### <a name="command-buttons"></a>Przyciski poleceń

- Przyciski poleceń działają w ramce okna dialogowego, a nie w zawartości. Powinny one zostać umieszczone w prawym dolnym rogu i powinny mieć wystarczającą ilość miejsca powyżej, aby ustawić przyciski osobno oddzielone.

- Jeśli w oknie dialogowym znajdują się poziome przyciski, które działają w ramach okna dialogowego, alternatywna Konfiguracja przycisków poleceń jest stosem pionowym w prawym górnym rogu. Zobacz [wewnętrzne przyciski poleceń](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) poniżej.

- Spacja z lewej strony przycisków poleceń (Dolne lewe/środkowe okna dialogowego) jest traktowana jako część kontrolki operacji okna dialogowego. Jedyną kwestią, która powinna być intruz w tym miejscu, jest link do pomocy, który jest istotny dla ogólnego zadania lub okna dialogowego.

- Przyciski poleceń powinny mieć 75x23 pikseli.

- Przyciski poleceń powinny składać się z 6 pikseli.

  ![Wyrównanie przycisku podstawowego](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 — c_ButtonAlign")

  **Rysunek 08,01-c: podstawowe wyrównanie przycisku**

#### <a name="labels"></a>Etykiety

- Wyrównaj do lewej wszystkie etykiety.

- W przypadku etykiet, które znajdują się nad kontrolką, powinny one być wyrównane do lewej strony przy użyciu kontrolki poniżej, a dolna etykieta powinna mieć 5 pikseli powyżej górnej krawędzi drugiej kontrolki (na przykład pole kombi).

- W przypadku etykiet, które znajdują się po lewej stronie kontrolek, Minimalna szerokość między etykietą a kontrolką wejściową wynosi 10 pikseli. W celu wyrównania pól tekstowych, pól kombi lub innych kontrolek należy ustalić implikowaną drugą kolumnę.

- W etykietach jest rozróżniana wielkość liter i występuje dwukropek. Zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Odległość między kontrolkami
 Odpowiednio kontroluje stosy. Brak bezwzględnych wytycznych dla odstępów między kontrolkami skumulowanymi. Szczelność między kontrolkami może się różnić w zależności od okien dialogowych. Zalecane odstępy to 20 pikseli dla par kontrolek pionowych/etykiet i 9 pikseli dla par kontrolki poziomej/etykiet. Minimalna wielkość kontrolki dla par poziomych to 6 pikseli.

 ![Zalecana odległość między kontrolkami](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 — d_ControlDistance")

 **Rysunek 08,01-d: zalecenia dotyczące odległości między kontrolkami**

#### <a name="control-indentation"></a>Wcięcie kontrolki
 Gdy formanty są zagnieżdżone, Wyrównaj wewnętrzne kontrolki w poziomie przy użyciu lewej krawędzi kontrolki powyżej, zazwyczaj etykiety.

 ![Wyrównanie zagnieżdżonej kontrolki](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 — e_ControlAlign")

 **Rysunek 08,01-e: wyrównanie zagnieżdżonej kontrolki**

#### <a name="control-width"></a>Szerokość kontrolki
 Szerokość pola tekstowego lub innych podobnych kontrolek nie powinna być większa niż średnia wartość wejściowa pola. Średni wyraz w języku angielskim ma pięć znaków. Na przykład pole tekstowe, które wymaga długiej nazwy ścieżki, powinno być tak długo, jak w układzie poziomym, a lista rozwijana nazw platform powinna mieć tylko długość, która pozwala na najdłuższy wpis.

#### <a name="helper-text"></a>Tekst pomocnika

- W oknie dialogowym można wyświetlić tekst pomocnika, który zawiera więcej informacji na temat przeznaczenia okna dialogowego. Zwykle znajduje się u góry i może zawierać 1-2 zdań.

- Długość linii powinna być wygodna dla użytkownika do przeanalizowania i odczytu. Średnie okno dialogowe nie powinno mieć więcej niż 550 pikseli.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Wewnętrzne przyciski poleceń
 W bardziej skomplikowanych oknach dialogowych wewnętrzna kontrolka może mieć własne powiązane przyciski, które mogą mieć wpływ na miejsce, w którym znajdują się przyciski zatwierdzania okna dialogowego.

- Użyj wyrównania w pionie (kolumny) przycisków wewnętrznych, jeśli przycisk **OK** / **Anuluj** ma orientację poziomą w prawym dolnym rogu.

- Użyj wyrównania poziomego (wiersz) przycisków wewnętrznych, gdy przycisk **OK** / **Anuluj** jest zorientowany pionowo w prawym górnym rogu. Ta sytuacja jest mniej wspólna.

- Rozmiar wnętrza przycisku powinien być ukierunkowany na standardowy przycisk 75x23 pikseli, dopasowując do rozmiaru przycisków **OK** / **Cancel** . Jeśli etykieta przycisku powoduje przekroczenie rozmiaru przycisku standardowego, pozostałe przyciski w tym zestawie powinny być wyrównane z tym szerszym rozmiarem.

  ![Przyciski OK i Anuluj](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 — f_HorizOKCan")

  **Rysunek 08,01-f: pionowe przyciski wewnętrzne z poziomą OK/Anuluj**

  ![Przyciski OK i Anuluj](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 — g_VertOKCan")

  **Rysunek 08,01-g: poziome przyciski wewnętrzne z pionowym przyciskiem OK/Anuluj**

#### <a name="browse-button"></a>[Przeglądaj...] przycisk
 **[Przeglądaj...]** przyciski, które obserwują pole tekstowe, powinny wyszukiwać "Przeglądaj..." Pełna, łącznie z wielokropkiem. Jeśli ilość miejsca jest Ciasna lub na ekranie znajduje się wiele przycisków **[Przeglądaj...]** , przycisk można zmniejszyć do samego wielokropka.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Układ okna dialogowego z motywem
 Okna dialogowe z motywem w programie Visual Studio mają jaśniejszy wygląd i oferują więcej białych znaków. Typografia zapewnia większy nacisk i zainteresowania, oferuje więcej otwartych odstępów między wierszami i zróżnicowanie rozmiarów i wag czcionek. Tam, gdzie to możliwe, Chrome i paski tytułu zostały zredukowane lub usunięte. Układ tych okien dialogowych powinien być zgodny z tym wzorcem Basic:

1. Tło okna dialogowego jest białe.

2. W szarej wartości znajduje się obramowanie reguły z 1 pikselem.

3. Tytuł okna dialogowego nie znajduje się już na pasku tytułu, ale zapewnia wizualny interes i podkreśla większy rozmiar. (Zobacz sekcję rozmiar czcionki w polu [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)).

4. Etykiety połączone z dodatkowym tekstem, takie jak opis, powinny być **czcionką środowiska + pogrubienie**.

5. Kolumny wewnętrzne są oddzielane za pomocą reguły 1-pikselowej w jasnym kolorze szarym.

6. Linki domyślne nie mają podkreślenia. Stany aktywowania i naciśnięte mają zmianę koloru plus znak podkreślenia.

7. Przyciski zatwierdzania (na przykład **OK** / **Anuluj**) znajdują się w prawym dolnym rogu.

### <a name="themed-dialog-layout-examples"></a>Przykłady układu dialogu z motywem
 ![Układ okna dialogowego z motywem](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 — h_ThemedDialog")

 **Rysunek 08,01-h: okno dialogowe z motywem**

 ![Wymiary okna dialogowego z motywem](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 — i_ThemedDialogDimensions")

 **Rysunek 08,01-i: okno dialogowe z motywami**

 ![Czcionki okna dialogowego z motywem](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 — j_ThemedDialogFonts")

 **Rysunek 08,01-j: okna dialogowe z motywami**

 ![Kolory okna dialogowego z motywem](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 — k_ThemedDialogColors")

 **Rysunek 08,01-k: okno dialogowe z motywami**

## <a name="see-also"></a>Zobacz też
- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Kontrolki (system Windows)](/windows/desktop/uxguide/controls)
- [Okna dialogowe (system Windows)](/windows/desktop/uxguide/win-dialog-box)
