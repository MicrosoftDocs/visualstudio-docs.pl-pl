---
title: Układ dla Visual Studio | Microsoft Docs
description: Dowiedz się więcej o układzie Visual Studio dialogowych, w tym nieuznanych okien dialogowych i nowych okien dialogowych o wyglądzie z tematami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e52b7b3fd620080b73e8d3de80672003ecb8fcf7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900534"
---
# <a name="layout-for-visual-studio"></a>Układ dla programu Visual Studio
Większość standardowych okien dialogowych Visual Studio układ okna dialogowego narzędzia [,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)które są niezauważanych okien dialogowych, które są zgodne ze standardowymi zasadami układu okna dialogowego programu [Windows Desktop.](/windows/desktop/uxguide/win-dialog-box) W Visual Studio odświeżenia interfejsu użytkownika niektóre z bardziej znaczących okien dialogowych mają nowy projekt, który ustanawia je jako środowisko definiowania produktu. Układ [okna dialogowego z tematami](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ma wygląd z tematami.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Układ okna dialogowego narzędzia

- Wszystkie kontrolki w oknie dialogowym narzędzia powinny rozpoczynać się od lewego górnego rogu i przepływać w dół.

- Nigdy nie wyśrodkuj kontrolek w oknie dialogowym, aby wypełnić duży obszar.

- Użyj czcionki środowiska dla całego tekstu okna dialogowego. Podczas pisania specyfikacji wizualizacji określ czcionkę środowiska zamiast wybierać określoną czcionkę i rozmiar. Zobacz [czcionkę środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Używaj spójnych odstępów kontrolek i umieszczania, aby wspierać cel jakości w kontroli.

- Okna dialogowe mogą stać się bardziej złożone z większej liczby kontrolek, unikatowej jukstapozycji kontrolek lub obu tych elementów. W takich złożonych sytuacjach należy zapewnić użytkownikowi odpowiednią przestrzeń między grupowaniami sterującymi, aby umożliwić użytkownikowi analizę przepływu logicznego.

### <a name="utility-dialog-layout-examples"></a>Przykłady układu okna dialogowego narzędzia
 Wszystkie wymiary są wyrażone jako piksele.

 ![Odstępy w oknach dialogowych dla etykiet powyżej kontrolek](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Rysunek 08.01-a: Wytyczne dotyczące odstępów w oknach dialogowych narzędzi z etykietami powyżej kontrolek**

 ![Odstępy w oknach dialogowych dla etykiet po lewej stronie kontrolek](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Rysunek 08.01-b: Wytyczne dotyczące odstępów w oknach dialogowych narzędzi z etykietami po lewej stronie kontrolek**

### <a name="layout-details"></a>Szczegóły układu

#### <a name="margins"></a>Marginesy

- Wszystkie okna dialogowe powinny mieć obramowanie 12 pikseli wokół wszystkich krawędzi.

- Marginesy w ramce grupy powinny być 9 pikseli od krawędzi ramki.

- Marginesy w kontrolce karty powinny być 6 pikseli od krawędzi kontrolki karty.

#### <a name="command-buttons"></a>Przyciski poleceń

- Przyciski poleceń działają na ramce okna dialogowego, a nie na zawartości. Powinny one być umieszczone w prawym dolnym rogu i powinny mieć wystarczającą ilość miejsca na zmienne powyżej, aby ustawić przyciski oddzielnie.

- Jeśli istnieją przyciski poziome, które działają w oknie dialogowym, konfiguracja alternatywnego przycisku polecenia jest stosem pionowym w prawym górnym rogu. Zobacz [Przyciski poleceń wewnętrznych](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) poniżej.

- Miejsce po lewej stronie przycisków poleceń (lewa dolna/środkowa część okna dialogowego) jest traktowane jako część "pasma" kontrolek operacji okna dialogowego. Jedyną rzeczą, która powinna intruzem w tej przestrzeni, jest link Pomoc, który ma zastosowanie do ogólnego zadania lub okna dialogowego.

- Przyciski poleceń powinny mieć 75 x 23 piksele.

- Przyciski poleceń powinny być od siebie 6 pikseli.

  ![Podstawowe wyrównywanie przycisków](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Rysunek 08.01-c: Podstawowe wyrównywanie przycisków**

#### <a name="labels"></a>Etykiety

- Wyrównaj wszystkie etykiety do lewej.

- W przypadku etykiet, które znajdują się nad kontrolką, powinny być dokładnie wyrównane do lewej, a dolna część etykiety powinna być 5 pikseli nad górną krawędzią drugiej kontrolki (na przykład pole kombi).

- W przypadku etykiet, które są na lewo od kontrolek, minimalna szerokość między etykietą a kontrolką wejściową wynosi 10 pikseli. Należy ustalić dorozumianą drugą kolumnę w celu wyrównania pól tekstowych, pól kombi lub innych kontrolek.

- Etykiety są literami zdań i po nich następuje dwukropek. Zobacz [Styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Odległość między kontrolkami
 Względnie stosuj kontrolki. Nie ma bezwzględnych wytycznych dla odstępów między skumulowanymi kontrolkami. Bliskość między kontrolkami może się nieznacznie różnić między oknami dialogowymi. Zalecane odstępy to 20 pikseli dla par kontrolki pionowej/etykiety i 9 pikseli dla poziomych par kontrolek/etykiet. Minimalny odstęp kontrolki dla par poziomych wynosi 6 pikseli.

 ![Zalecana odległość między kontrolkami](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Rysunek 08.01-d: Zalecenia dotyczące odległości między kontrolkami**

#### <a name="control-indentation"></a>Wcięcie kontrolek
 Gdy kontrolki są zagnieżdżone, wyrównaj kontrolki wewnętrzne w poziomie do lewej krawędzi kontrolki powyżej, zazwyczaj etykiety.

 ![Wyrównanie zagnieżdżonych kontrolek](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Rysunek 08.01-e: Zagnieżdżone wyrównywanie kontrolek**

#### <a name="control-width"></a>Szerokość kontrolki
 Szerokość pola tekstowego lub innych podobnych kontrolek nie powinna być większa niż średnia wartość wejściowa dla pola. Średnia wartość w języku angielskim to pięć znaków. Na przykład pole tekstowe, które wymaga długiej nazwy ścieżki, powinno być tak długie, jak pozwala na to układ poziomy, a lista rozwijana nazw platform powinna mieć tylko długość, która umożliwia najdłuższe wprowadzanie.

#### <a name="helper-text"></a>Tekst pomocnika

- Okno dialogowe może wyświetlać tekst pomocnika, który zawiera więcej informacji na temat przeznaczenia okna dialogowego. Zwykle znajduje się u góry i może to być od 1 do 2 zdań.

- Długość linii powinna być wygodną szerokością do analizowania i odczytywania przez użytkownika. Średnie okno dialogowe nie powinno mieć więcej niż 550 pikseli szerokości.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Wewnętrzne przyciski poleceń
 W bardziej złożonych oknach dialogowych kontrolka wewnętrzna może mieć własne powiązane przyciski, które mogą mieć wpływ na miejsce, w którym znajdują się przyciski zatwierdzania okna dialogowego.

- Użyj wyrównania w pionie (kolumny) wewnętrznych przycisków, gdy przycisk **OK** Anuluj jest w orientacji poziomej /  w prawym dolnym rogu.

- Użyj wyrównania w poziomie (wiersza) wewnętrznych przycisków, gdy przycisk **OK** Anuluj jest wyrównany w pionie /  w prawym górnym rogu. Ta sytuacja jest mniej powszechna.

- Rozmiar przycisku wewnętrznego powinien być zgodny ze standardowym rozmiarem przycisku 75x23 pikseli, zgodnym z rozmiarem przycisków **OK** / **Anuluj,** jeśli jest to możliwe. Jeśli etykieta przycisku sprawia, że rozmiar przycisku przekracza standardowy rozmiar przycisku, inne przyciski w tym zestawie powinny być wyrównane do tego szerszego rozmiaru.

  ![Poziome przyciski OK i Anuluj](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Ilustracja 08.01-f: Pionowe wewnętrzne przyciski z poziomym ok/anulowaniem**

  ![Pionowe przyciski OK i Anuluj](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Ilustracja 08.01-g: Poziome wewnętrzne przyciski z pionowym ok/anulowaniem**

#### <a name="browse-button"></a>[Przeglądaj...] Przycisk
 **[Przeglądaj...]** Przyciski, które podążają za polem tekstowym, powinny mieć tekst "Przeglądaj..." w całości, w tym wielokropek. Jeśli miejsce jest ciasne lub na ekranie znajduje się wiele przycisków **[Browse...],** można go zmniejszyć tylko do wielokropka.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Układ okna dialogowego z tematami
 Okna dialogowe z Visual Studio mają jaśniejszy wygląd i oferują więcej białych miejsc. Typografia zapewnia większy nacisk i większe zainteresowanie, oferując więcej otwartych odstępów między wierszami oraz odmianę rozmiarów i wag czcionek. Tam, gdzie to możliwe, paski chrome i tytułu zostały ograniczone lub usunięte. Układ tych okien dialogowych powinien być zgodne z tym podstawowym wzorcem:

1. Tło okna dialogowego jest białe.

2. W szarym środku wartości znajduje się obramowanie reguły 1 piksela.

3. Tytuł okna dialogowego nie znajduje się już na pasku tytułu, ale zapewnia wizualne zainteresowanie i wyróżnienie większym rozmiarem punktu. (Zobacz sekcję rozmiar czcionki w [sekcji Styl tekstu).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Etykiety połączone z dodatkowymi tekstami, takimi jak opis, powinny mieć **etykietę Czcionka środowiska + Pogrubienie**.

5. Wewnętrzne kolumny są oddzielone regułą o rozmiarze 1 piksela w kolorze jasnoszarym.

6. Linki domyślne nie mają podkreślenia. Stany najechanie kursorem i naciśniętym kursorem mają zmianę koloru i znak podkreślenia.

7. Przyciski zatwierdzania (takie **jak OK** / **Anuluj)** znajdują się w prawym dolnym rogu.

### <a name="themed-dialog-layout-examples"></a>Przykłady układu okna dialogowego z tematami
 ![Układ okna dialogowego z tematami](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Rysunek 08.01-h: Okno dialogowe z tematami**

 ![Wymiary okna dialogowego z tematami](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Rysunek 08.01-i: Okno dialogowe z tematami — wymiary**

 ![Czcionki okna dialogowego z motywami](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Rysunek 08.01-j: Okno dialogowe z motywami — czcionki**

 ![Kolory okna dialogowego z tematami](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Rysunek 08.01-k: Okno dialogowe z tematami — kolory**

## <a name="see-also"></a>Zobacz też
- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Kontrolki (Windows)](/windows/desktop/uxguide/controls)
- [Okna dialogowe (Windows)](/windows/desktop/uxguide/win-dialog-box)
