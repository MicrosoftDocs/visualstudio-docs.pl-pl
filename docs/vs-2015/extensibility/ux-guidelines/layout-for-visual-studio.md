---
title: Układ
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d38a1e984f5705c52d8c6b310ead7a522f4ecb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753748"
---
# <a name="layout-for-visual-studio"></a>Układ dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Większość okien dialogowych programu Visual Studio jest [układ okna dialogowego narzędzia](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), które są unthemed okien dialogowych standardzie postępuj zgodnie z [zasad układu okna dialogowego pulpitu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx). Przemieszcza się w programie Visual Studio można odświeżyć jego interfejsie użytkownika, niektóre ważniejszej okien dialogowych mają nowy projekt, który ustanawia je jak definiowanie produktu środowiska. Te [układ okna dialogowego motywem](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ma wygląd kompozycji.

##  <a name="BKMK_UtilityDialogLayout"></a> Układ okna dialogowego narzędzia

-   Wszystkie kontrolki w oknie dialogowym narzędzia należy rozpoczynają się od góry/do lewej i przepływu w dół.

-   Nigdy nie środka kontrolki w oknie dialogowym w celu wypełnienia obszaru dużych.

-   Czcionka środowiska na użytek cały tekst okna dialogowego. Podczas pisania visual specyfikacji, należy określić czcionka środowiska zamiast zaznaczania określonej czcionki i rozmiar. Zobacz [czcionka środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

-   Umożliwia obsługę celem jakości w craftsmanship w odstępy spójną kontrolę i położenia.

-   Okna dialogowe może stać się bardziej złożone z większej liczby kontrolek i/lub unikatowe zestawienie kontrolki. W tych złożonych sytuacjach na odpowiednia ilość miejsca między kontroli grupowania, aby przyznać użytkownikowi przepływ logiczny można przeanalizować.

### <a name="utility-dialog-layout-examples"></a>Przykłady układu okna dialogowego narzędzia
 Wszystkie wymiary są wyrażane jako pikseli.

 ![Okno dialogowe odstępy dla etykiety powyżej kontrolki](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801 a_UtilitySpacingAbove")

 **Rysunek 08.01-o: Wytyczne odstępy w oknach dialogowych narzędzia, za pomocą etykiet powyżej formantów**

 ![Okno dialogowe odstępy dla etykiety z lewej strony kontrolki](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801 b_UtilitySpacingLeft")

 **Rysunek 08.01-b: Wytyczne odstępy w oknach dialogowych narzędzia, za pomocą etykiety z lewej strony kontrolki**

### <a name="layout-details"></a>Szczegóły układu

#### <a name="margins"></a>Marginesy

-   Wszystkie okna dialogowe powinny mieć 12-pikselowe obramowanie wokół krawędzi wszystkich.

-   Marginesy w ramce grupy powinna być 9 pikseli od krawędzi ramki.

-   Marginesy w kontrolce karty powinny być 6 pikseli z krawędzią formantu karty.

#### <a name="command-buttons"></a>Przyciski poleceń

- Przyciski poleceń działają na ramki okna dialogowego, a nie na zawartość. One będzie umieszczona w dolnej prawej i powinien mieć wystarczającej ilości miejsca zmiennej powyżej, aby ustawić wyraźnie oddzielne przycisków.

- W przypadku przyciski poziome, które działają w obrębie okna dialogowego konfiguracji przycisku polecenia jest pionowy stos w prawym górnym rogu. Zobacz [przycisków poleceń posługiwanie się nimi](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) poniżej.

- Miejsce na lewo od przycisków poleceń (niższe po lewej stronie/środka okna dialogowego) jest uważany za część "poza pasmem" formantów operacji okna dialogowego. Jedyną czynnością, który powinna mającym w tym miejscu jest łącza pomocy, która jest odpowiednia dla całego zadania lub okna dialogowego.

- Przyciski poleceń powinny być 75 x 23 pikseli.

- Przyciski poleceń powinna być 6 pikseli od siebie.

  ![Wyrównanie podstawowe przycisku](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801 c_ButtonAlign")

  **Rysunek 08.01 — c: Wyrównanie podstawowe przycisku**

#### <a name="labels"></a>Etykiety

-   Wyrównaj do lewej wszystkie etykiety.

-   Dla etykiet, które znajdują się powyżej kontrolki one powinien wyrównuj do lewej dokładnie kontrolką poniżej i dolnej części etykieta powinna być 5 pikseli powyżej górnej części innego formantu (na przykład pole kombi).

-   Dla etykiet, które znajdują się na lewo od formantów minimalna szerokość pomiędzy etykietą i kontrolki wprowadzania jest 10 pikseli. Powinno zostać ustanowione dorozumianych drugiej kolumny do wyrównywania pola tekstowe, pola kombi lub innych kontrolek.

-   Etykiety liter i są z dwukropkiem. Zobacz [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Odległość między kontrolkami
 Stos jest kontrolki. Nie ma żadnych bezwzględne wytyczne dotyczące odstępów między formantami skumulowany. Szczelność między kontrolkami mogą się nieco różnić między okien dialogowych. Zalecane jest 20 pikseli dla par pionowych formant/etykiety i 9 pikseli dla par pozioma kontrolka/etykiety. Odstępy minimalne kontroli dla par poziomy to 6 pikseli.

 ![Zalecane odległość między kontrolkami](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801 d_ControlDistance")

 **Rysunek 08.01 — d: Zalecenia dotyczące odległość między kontrolkami**

#### <a name="control-indentation"></a>Wcięcie kontroli
 Gdy są zagnieżdżone formanty, wyrównać wewnętrzny kontrolki w poziomie z lewą krawędzią kontrolki powyżej, zwykle etykiety.

 ![Zagnieżdżone kontroli nad położeniem](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801 e_ControlAlign")

 **Rysunek 08.01 — e: Wyrównanie zagnieżdżony formant**

#### <a name="control-width"></a>Szerokość formantu
 Szerokość pola tekstowego lub innych podobnych kontrolek, należy nie dłuższą niż średnia dane wejściowe dla pola. Średnia słowa angielskiego jest pięć znaków. Na przykład pola tekstowego, który wymaga długiej nazwy powinna być tak długo, jak w układzie poziomym pozwala, podczas gdy listy rozwijanej dla nazw platform powinny być tylko długości, która pozwala na zapis najdłuższy.

#### <a name="helper-text"></a>Tekst pomocy

-   Okno dialogowe można wyświetlić tekst pomocy, który zawiera więcej informacji o przeznaczeniu okna dialogowego. To zwykle znajduje się u góry i może być zdania 1-2.

-   Długość wiersza powinna być dobrze szerokości dla użytkownika przeanalizować i odczytać. Średnie okna dialogowego powinna być co najwyżej 550 pikseli szerokości.

####  <a name="BKMK_InteriorCommandButtons"></a> Przyciski poleceń posługiwanie się nimi
 W oknach dialogowych bardziej złożone wewnętrznej kontroli może być własną powiązane przycisków, które mogą mieć wpływ na, gdzie znajdują się okno dialogowe zatwierdzenia przycisków.

- Wyrównanie w pionie (kolumna) wnętrza przyciski, gdy użycie **OK**/**anulować** w poziomie są ukierunkowane w prawym dolnym rogu.

- Wyrównanie w poziomie (wiersz) wnętrza przyciski, gdy użycie **OK**/**anulować** w pionie są ukierunkowane w prawym górnym rogu. Ta sytuacja jest rzadziej używane.

- Rozmiar przycisku posługiwanie się nimi powinien dotyczyć rozmiar przycisk standardowy, 75 x 23 pikseli, dopasowywanie rozmiaru **OK**/**anulować** przyciski, gdy jest to możliwe. Jeśli etykieta przycisku sprawia, że przycisk przekracza rozmiar przycisk standardowy, inne przyciski, w tym zestawie należy wyrównać za pomocą tego rozmiaru szersze.

  ![Przyciski poziome OK i Anuluj](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801 f_HorizOKCan")

  **Rysunek 08.01-f: Pionowe przyciski posługiwanie się nimi za pomocą polecenia poziomy OK/Anuluj**

  ![Przyciski pionowy OK i Anuluj](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801 g_VertOKCan")

  **Rysunek 08.01-g: Posługiwanie się nimi przyciski poziome za pomocą polecenia pionowy OK/Anuluj**

#### <a name="browse-button"></a>[Przeglądaj …] przycisk
 **[Przeglądaj …]**  przycisków poniżej pola tekstowego powinien zawierają bardziej "Przeglądaj..." w całości, w tym wielokropka. Jeśli ilość miejsca jest ścisła lub dostępnych jest wiele **[Przeglądaj …]**  przyciski na ekranie przycisku można zmniejszyć do właśnie wielokropka.

##  <a name="BKMK_ThemedDialogLayout"></a> Układ okna dialogowego motywów
 Motywem okien dialogowych w programie Visual Studio mają jaśniejszy wygląd i oferują więcej biały. Typografia zapewnia więcej wyróżnienia i zainteresowań, oferując bardziej otwarty i ustawić odmianą rozmiary czcionek i wagi. Jeśli to możliwe, chrome i paska tytułu zostały obniżone lub usunięte. Układ tych okien dialogowych należy stosować tego podstawowego wzorca:

1.  Tło okna dialogowego jest białe.

2.  Istnieje reguła 1-pikselowe obramowanie kolorem szarym wartości średniej.

3.  Tytuł okna dialogowego nie jest już znajduje się w pasku tytułu, ale zapewnia wizualnego zainteresowania i wyróżnić w punkcie o większym rozmiarze. (Zobacz sekcję rozmiar czcionki w [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4.  Dzięki połączeniu z usługami dodatkowe tekstu, na przykład opis etykiety powinny być **czcionka środowiska + Bold**.

5.  Posługiwanie się nimi kolumny są rozdzielane przez regułę 1-pikselowe w kolorze szarym światła.

6.  Domyślne łącza mają nie znaku podkreślenia. Ustaw kursor po naciśnięciu stany się zmiana koloru oraz podkreślenia.

7.  Zatwierdź przycisków (takich jak **OK**/**anulować**) znajdują się w prawym dolnym rogu.

### <a name="themed-dialog-layout-examples"></a>Przykłady układu okna dialogowego motywów
 ![Układ okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801 h_ThemedDialog")

 **Rysunek 08.01-h: Okno dialogowe motywów**

 ![Wymiary okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801 i_ThemedDialogDimensions")

 **Rysunek 08.01-i: Okno dialogowe motywem — wymiarów**

 ![Czcionki okna dialogowego motywem](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801 j_ThemedDialogFonts")

 **Rysunek 08.01-j: Okno dialogowe motywem — czcionek**

 ![Okno motywem kolorów](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801 k_ThemedDialogColors")

 **Rysunek 08.01-k: Okno dialogowe motywem — kolory**

## <a name="see-also"></a>Zobacz też
 [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md) [formantów (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) [okien dialogowych (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)
