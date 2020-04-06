---
title: Układ dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698394"
---
# <a name="layout-for-visual-studio"></a>Układ dla programu Visual Studio
Większość okien dialogowych programu Visual Studio to [układ okna dialogowego narzędzia,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)które są niekręgowanymi oknami dialogowymi zgodnymi ze standardowymi [zasadami układu okna dialogowego pulpitu systemu Windows.](/windows/desktop/uxguide/win-dialog-box) Jak Visual Studio przenosi się do odświeżenia interfejsu użytkownika, niektóre z bardziej znanych okien dialogowych mają nowy projekt, który ustanawia je jako środowiska definiujące produkt. Te [tematyce układu okna dialogowego](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) mają wygląd tematycznym.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Układ okna dialogowego narzędzia

- Wszystkie formanty w oknie dialogowym narzędzia powinny zaczynać się od góry/w lewo i przepływać w dół.

- Nigdy nie wyśrodkowaj kontrolek w oknie dialogowym, aby wypełnić duży obszar.

- Użyj czcionki środowiska dla całego tekstu okna dialogowego. Podczas pisania specyfikacji wizualnej należy określić czcionkę środowiska zamiast wybierania określonej czcionki i rozmiaru. Zobacz [Czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Użyj spójnych odstępów kontrolnych i rozmieszczenia, aby wspierać cel w zakresie jakości w rzemiośle.

- Okna dialogowe mogą stać się bardziej złożone z większej liczby formantów, unikatowe zestawienie formantów lub obu. W tych złożonych sytuacjach należy zapewnić odpowiednią przestrzeń między grupowaniami kontrolnymi, aby nadać użytkownikowi logiczny przepływ do analizy.

### <a name="utility-dialog-layout-examples"></a>Przykłady układu okna dialogowego narzędzia
 Wszystkie wymiary są wyrażone w pikselach.

 ![Odstępy dialogowe dla etykiet powyżej kontrolek](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Rysunek 08.01-a: Wskazówki dotyczące odstępów dla okien dialogowych narzędzi z etykietami powyżej kontrolek**

 ![Odstępy dialogowe dla etykiet po lewej stronie formantów](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Rysunek 08.01-b: Wskazówki dotyczące odstępów dla okien dialogowych narzędzi z etykietami po lewej stronie formantów**

### <a name="layout-details"></a>Szczegóły układu

#### <a name="margins"></a>Marginesy

- Wszystkie okna dialogowe powinny mieć obramowanie 12 pikseli wokół wszystkich krawędzi.

- Marginesy w ramce grupy powinny znajdować się 9 pikseli od krawędzi ramki.

- Marginesy w formancie karty powinny znajdować się 6 pikseli od krawędzi kontrolki karty.

#### <a name="command-buttons"></a>Przyciski poleceń

- Przyciski poleceń działają na ramce okna dialogowego, a nie na zawartości. Powinny one być umieszczone w prawym dolnym rogu i powinny mieć wystarczająco dużo zmiennej przestrzeni powyżej, aby ustawić przyciski wyraźnie oddzielone.

- Jeśli w oknie dialogowym znajdują się poziome przyciski, konfiguracja przycisku polecenia alternatywnego jest pionowym stosem w prawym górnym rogu. Zobacz [wewnętrzne przyciski poleceń](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) poniżej.

- Spacja po lewej stronie przycisków poleceń (lewy dolny/środek okna dialogowego) jest uważana za część "pasma" elementów sterujących obsługi okna dialogowego. Jedyną rzeczą, która powinna wtrącać się w tym miejscu jest łącze Pomocy, które jest istotne dla ogólnego zadania lub okna dialogowego.

- Przyciski poleceń powinny mieć rozmiar 75x23 pikseli.

- Przyciski poleceń powinny być oddalone od siebie o 6 pikseli.

  ![Podstawowe wyrównanie przycisków](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Rysunek 08.01-c: Podstawowe wyrównanie przycisków**

#### <a name="labels"></a>Etykiety

- Wyrównaj wszystkie etykiety do lewej.

- W przypadku etykiet, które znajdują się nad formantem, powinny one dokładnie wyrównać do lewej do formantu pod nim, a dolna część etykiety powinna znajdować się 5 pikseli powyżej górnej części drugiego formantu (na przykład pole kombi).

- W przypadku etykiet, które znajdują się po lewej stronie formantów, minimalna szerokość między etykietą a formantem wejściowym wynosi 10 pikseli. Dorozumiana druga kolumna powinna zostać ustanowiona w celu wyrównania pól tekstowych, pól kombi lub innych formantów.

- Etykiety są przypadkiem zdania, po którym następuje dwukropek. Zobacz [Styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Odległość między elementami sterującymi
 Steruje stosem rozsądnie. Nie ma żadnych bezwzględnych wytycznych dotyczących odstępów między formantami skumulowanymi. Szczelność między elementami sterującymi może się nieznacznie różnić w zależności od okna dialogowego. Zalecane odstępy to 20 pikseli dla par sterowania pionowego/etykiety i 9 pikseli dla par sterowania poziomego/etykiety. Minimalne odstępy kontrolne dla par poziomych to 6 pikseli.

 ![Zalecana odległość między elementami sterującymi](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Rysunek 08.01-d: Zalecenia dotyczące odległości między organami sterującymi**

#### <a name="control-indentation"></a>Wcięcie kontrolne
 Gdy formanty są zagnieżdżone, wyrównaj wewnętrzne formanty poziomo z lewą krawędzią formantu powyżej, zwykle etykietą.

 ![Wyrównanie zagnieżdżonego formantu](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Rysunek 08.01-e: Wyrównanie sterowania zagnieżdżonego**

#### <a name="control-width"></a>Szerokość sterowania
 Szerokość pola tekstowego lub innych podobnych formantów nie powinna być dłuższa niż średnie dane wejściowe dla pola. Przeciętne angielskie słowo to pięć znaków. Na przykład pole tekstowe, które wymaga długiej nazwy ścieżki, powinno być tak długo, jak pozwala na to układ poziomy, podczas gdy rozwijana dla nazw platform powinna mieć tylko długość, która pozwala na najdłuższy wpis.

#### <a name="helper-text"></a>Tekst pomocnika

- W oknie dialogowym można wyświetlić tekst pomocnika, który zawiera więcej informacji na temat celu okna dialogowego. To zazwyczaj siedzi na górze i może być 1-2 zdania.

- Długość linii powinna być wygodna szerokość dla użytkownika do analizy i odczytu. Średnie okno dialogowe nie powinno mieć więcej niż 550 pikseli szerokości.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Wewnętrzne przyciski poleceń
 W bardziej złożonych oknach dialogowych kontrola wewnętrzna może mieć własne powiązane przyciski, co może mieć wpływ na to, gdzie znajdują się przyciski zatwierdzania okna dialogowego.

- Użyj wyrównania pionowego (kolumny) przycisków wewnętrznych, gdy **przyciski OK**/**Anuluj** są ustawione poziomo w prawym dolnym rogu.

- Użyj wyrównania poziomego (wiersza) przycisków wewnętrznych, gdy **przyciski OK**/**Anuluj** są ustawione pionowo w prawym górnym rogu. Sytuacja ta jest mniej powszechna.

- Rozmiar przycisku wewnętrznego powinien być ukierunkowany na standardowy rozmiar przycisku 75x23 pikseli, odpowiadający rozmiarowi przycisków **OK**/**Anuluj,** jeśli to możliwe. Jeśli etykieta przycisku powoduje, że przycisk przekracza standardowy rozmiar przycisku, pozostałe przyciski w tym zestawie powinny być zgodne z tym szerszym rozmiarem.

  ![Przyciski Poziome OK i Anuluj](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Rysunek 08.01-f: Pionowe przyciski wewnętrzne z poziomym OK/Anuluj**

  ![Przyciski Pionowe OK i Anuluj](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Rysunek 08.01-g: Poziome przyciski wewnętrzne z pionowym OK/Anuluj**

#### <a name="browse-button"></a>[Przeglądaj...] Przycisk
 **[Przeglądaj...]** przyciski, które następują po polu tekstowym, powinny przeliterować "Przeglądaj..." w całości, w tym wielokropek. Jeśli miejsce jest ciasne lub na ekranie znajduje się wiele przycisków **[Przeglądaj...],** przycisk można zredukować do wielokropek.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Tematycznym układem dialogowym
 Tematykowe okna dialogowe w programie Visual Studio mają jaśniejszy wygląd i oferują więcej odstępów. Typografia zapewnia większy nacisk i zainteresowanie, oferując bardziej otwarte odstępy między wierszami oraz zmianę rozmiarów i wag czcionek. W miarę możliwości zmniejszono lub usunięto paski chromu i tytułu. Układ tych okien dialogowych powinien być zgodny z tym podstawowym wzorcem:

1. Tło okna dialogowego jest białe.

2. W kolorze szarym o średniej wartości znajduje się obramowanie reguły 1 piksela.

3. Tytuł okna dialogowego nie znajduje się już na pasku tytułu, ale zapewnia wizualne zainteresowanie i wyróżnienie w większym rozmiarze punktu. (Zobacz sekcję rozmiar czcionki w [stylu tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)).)

4. Etykiety w połączeniu z dodatkowym tekstem, takim jak opis, powinny być **czcionką Środowisko + Pogrubienie**.

5. Kolumny wewnętrzne są oddzielone regułą 1 pikseli w kolorze jasnoszarym.

6. Łącza domyślne nie mają podkreślenia. Stany myszy i naciśnięcia mają zmianę koloru oraz podkreślenie.

7. Przyciski zatwierdzania (takie jak **OK**/**Anuluj)** znajdują się w prawym dolnym rogu.

### <a name="themed-dialog-layout-examples"></a>Przykłady tematyzowania układu okna dialogowego
 ![Tematycznym układem dialogowym](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Rysunek 08.01-h: Okno dialogowe tematyce**

 ![Tematyce wymiary okna dialogowego](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Rysunek 08.01-i: Okno dialogowe tematyce — wymiary**

 ![Czcionki okna dialogowego tematykowego](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Rysunek 08.01-j: Okno dialogowe tematyce - Czcionki**

 ![Tematyce kolorów dialogowych](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Rysunek 08.01-k: Okno dialogowe tematyce - Kolory**

## <a name="see-also"></a>Zobacz też
- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Formanty (Windows)](/windows/desktop/uxguide/controls)
- [Okna dialogowe (Windows)](/windows/desktop/uxguide/win-dialog-box)
