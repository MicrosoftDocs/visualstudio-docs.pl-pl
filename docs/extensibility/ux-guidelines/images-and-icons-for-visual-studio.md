---
title: Obrazy i ikony dla Visual Studio | Microsoft Docs
description: Poznaj pojęcia związane z projektowaniem używane do tworzenia obrazów i ikon dla Visual Studio.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36b77dc79574b1741c8feaded65104810e58c2fb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898795"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazy i ikony dla programu Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Użycie obrazu w Visual Studio
 Przed utworzeniem grafiki rozważ użycie ponad 1000 obrazów w bibliotece obrazów Visual Studio [obrazów.](https://www.microsoft.com/download/details.aspx?id=35825)

### <a name="types-of-images"></a>Typy obrazów

- **Ikony**. Małe obrazy wyświetlane w poleceniach, hierarchiach, szablonach itp. Domyślny rozmiar ikony używany w Visual Studio png 16 x 16. Ikony generowane przez usługę obrazów automatycznie generują format XAML dla obsługi hdpi.

    > [!NOTE]
    > Chociaż obrazy są używane w systemie menu, nie należy tworzyć ikony dla każdego polecenia. Zapoznaj [się z menu i poleceniami Visual Studio,](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) aby sprawdzić, czy polecenie powinno otrzymać ikonę.

- **Miniatury.** Obrazy używane w obszarze podglądu okna dialogowego, na przykład w oknie dialogowym Nowy projekt.

- **Obrazy okien dialogowych.** Obrazy, które są wyświetlane w oknach dialogowych lub kreatorach, jako opisowa grafika lub wskaźniki komunikatów. Używaj rzadko i tylko wtedy, gdy jest to konieczne, aby zilustrować trudną koncepcję lub zwrócić uwagę użytkownika (alert, ostrzeżenie).

- **Animacjami.** Używane wskaźniki w toku, paski stanu i okna dialogowe operacji.

- **Kursory.** Służy do wskazywania, czy operacja jest dozwolona przy użyciu myszy, gdzie obiekt może zostać porzucony i tak dalej.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Projekt ikony

### <a name="overview"></a>Omówienie
 Visual Studio korzysta z ikon nowoczesnego stylu, które mają czystą geometrię i równowagi 50/50 wartości dodatnich/ujemnych (jasny/ciemny) i używają bezpośrednich, zrozumiałych metafor. Kluczowe punkty projektowe ikon są nakierowyne na przejrzystość, uproszczenie i kontekst.

- **Przejrzystość:** skoncentruj się na podstawowym metaforze, który nadaje ikonie znaczenie i indywidualność.

- **Uproszczenie:** zmniejsz ikonę do podstawowego znaczenia — pobierz motyw z tylko niezbędnymi elementami i bez dodatków.

- **Kontekst:** podczas opracowywania koncepcji należy wziąć pod uwagę wszystkie aspekty roli ikony, co ma kluczowe znaczenie podczas podejmowania decyzji o tym, które elementy stanowią podstawowy metaforę ikony.

  W przypadku ikon istnieje wiele punktów projektowych, których należy unikać:

- Nie używaj ikon, które oznaczają elementy interfejsu użytkownika, z wyjątkiem sytuacji, gdy jest to konieczne. Wybierz bardziej abstrakcyjne lub symboliczne podejście, gdy element interfejsu użytkownika nie jest wspólny, oczywisty ani unikatowy.

- Nie należy nadążać za pomocą typowych elementów, takich jak dokumenty, foldery, strzałki i lupa. Takich elementów należy używać tylko wtedy, gdy są niezbędne do znaczenia ikony. Na przykład lupa po prawej stronie powinna wskazywać tylko pola Wyszukaj, Przeglądaj i Znajdź.

- Mimo że niektóre starsze elementy ikon korzystają z perspektywy, nie należy tworzyć nowych ikon z perspektywą, chyba że element nie ma przejrzystości bez niego.

- Nie dopłacaj zbyt wielu informacji do ikony. Prosty obraz, który można łatwo rozpoznać lub nauczyć jako rozpoznawalny symbol, jest znacznie bardziej przydatny niż zbyt złożony obraz. Ikona nie może opowiedzieć całej historii.

### <a name="icon-creation"></a>Tworzenie ikon

#### <a name="concept-development"></a>Opracowywanie koncepcji
 Visual Studio ma w swoim interfejsie użytkownika szeroką gamę typów ikon. Podczas opracowywania starannie rozważ typ ikony. Nie używaj niejasnych lub nietypowych obiektów interfejsu użytkownika dla elementów ikony. W takich przypadkach wybierz symbol symboliczny, na przykład ikonę tagu inteligentnego. Należy pamiętać, że znaczenie tagu abstrakcyjnego po lewej stronie jest bardziej oczywiste niż niejasna, oparta na interfejsie użytkownika wersja po prawej stronie:

|**Poprawne użycie obrazów symbolicznych**|**Nieprawidłowe użycie obrazów symbolicznych**|
|-|-|
|![Poprawianie ikony tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nieprawidłowa ikona tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Istnieją wystąpienia, w których standardowe, łatwo rozpoznawalne elementy interfejsu użytkownika dobrze działają w przypadku ikon. Dodaj okno jest jednym z takich przykładów:

|**Poprawianie elementu interfejsu użytkownika w ikonie**|**Nieprawidłowy element interfejsu użytkownika w ikonie**|
|-|-|
|![Poprawna ikona Dodaj okno](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Nieprawidłowa ikona dodawania okna](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nie należy używać dokumentu jako elementu podstawowego, chyba że jest to niezbędne do znaczenia ikony. Bez elementu dokumentu w oknie Dodawanie dokumentu (poniżej) znaczenie jest utracone, natomiast w przypadku odświeżania element dokumentu nie jest zbędny do przekazywania znaczenia.

|**Poprawne użycie ikony dokumentu**|**Nieprawidłowe użycie ikony dokumentu**|
|-|-|
|![Ikona Popraw dokument](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Nieprawidłowa ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Pojęcie "pokaż" powinno być reprezentowane przez ikonę, która najlepiej ilustruje to, co jest wyświetlane, na przykład w przykładzie Pokaż wszystkie pliki. Metafora obiektywu może służyć do wskazania koncepcji "widoku", jeśli jest to konieczne, na przykład w Widok zasobów przykładzie.

|**"Pokaż"**|**"Wyświetl"**|
|-|-|
|![Ikona Pokaż](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ikona Wyświetl](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Ikona lupy po prawej stronie powinna reprezentować tylko pola Wyszukaj, Znajdź i Przeglądaj. Wariant po lewej stronie ze znakiem plus lub minusem powinien reprezentować tylko powiększanie/pomniejszanie.

|**"Wyszukaj"**|**"Zoom"**|
|-|-|
|![Ikona wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 W widokach drzewa nie należy używać ikony folderu ani modyfikatora. Jeśli jest dostępna, należy używać tylko modyfikatora .

|**Poprawne ikony widoku drzewa**|**Nieprawidłowe ikony widoku drzewa**|
|-|-|
|![Poprawna ikona widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Prawidłowy widok drzewa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Niepoprawna ikona widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") niepoprawna ikona widoku drzewa ![&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Szczegóły stylu

#### <a name="layout"></a>Layout
 Elementy stosu, jak pokazano w przypadku standardowych ikon 16x16:

 ![Stos układu dla ikon 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stos układu dla ikon 16x16

 Elementy powiadomień o stanie są lepiej używane jako ikony autonomiczne. Istnieją jednak konteksty, w których powiadomienie powinno być skumulowane na elemencie bazowym, na przykład za pomocą ikony Ukończenie zadania:

 ![Powiadomienia autonomiczne w Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Ikony powiadomień autonomicznych

 ![Ikona ukończenia zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ikona Ukończenie zadania

 Ikony projektu to zazwyczaj pliki ico, które zawierają wiele rozmiarów. Większość ikon 16 x 16 zawiera te same elementy. Wersje 32x32 mają więcej szczegółów, w tym typ projektu, jeśli ma to zastosowanie.

 ![Ikony projektu w Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ikony projektu biblioteki kontrolek systemu Windows VB, 16x16 i 32x32

 Wyśrodkuj ikonę w ramce pikseli. Jeśli nie jest to możliwe, wyrównaj ikonę do góry i/lub z prawej strony ramki.

 ![Ikona wyśrodkowana w ramce pikseli](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ikona wyśrodkowana w ramce pikseli

 ![Ikona wyrównana do prawej górnej części ramki pikseli](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ikona wyrównana do prawej górnej części ramki

 ![Ikona wyśrodkowana i wyrównana do górnej części ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ikona wyśrodkowana i wyrównana do góry ramki

 Aby uzyskać idealne wyrównanie i równowagę, unikaj zawłaszania elementu podstawowego ikony za pomocą glifów akcji. Umieść glif w lewym górnym rogu elementu podstawowego. Podczas dodawania dodatkowego elementu należy wziąć pod uwagę wyrównanie i równowagę ikony.

|**Poprawianie wyrównania i równoważenia**|**Niepoprawne wyrównanie i równoważenie**|
|-|-|
|![Poprawianie równowagi i wyrównania ikon](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Niepoprawne równoważenie i wyrównywanie ikon](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Zapewnij parzystość rozmiaru ikon, które współużytkują elementy i są używane w zestawach. Zwróć uwagę, że w przypadku nieprawidłowego parowania okrąg i strzałka są przesłonione i nie są zgodne.

|**Poprawna parzystość rozmiaru**|**Niepoprawna parzystość rozmiaru**|
|-|-|
|![Popraw rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nieprawidłowy rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Używaj spójnych wag linii i wizualizacji. Oceń, w jaki sposób skaluj ikony, które chcesz budować, w porównaniu z innymi ikonami, korzystając z porównania obok siebie. Nigdy nie używaj całej ramki 16 x 16, używaj ramek 15x15 lub mniejszych. Stosunek wartości ujemnej do dodatniej (ciemnej do jasnej) powinien być 50/50.

|**Poprawianie współczynnika wartości ujemnych do dodatnich**|**Niepoprawny współczynnik ujemny do dodatni**|
|-|-|
|![Popraw wagę wizualizacji dla ikon &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Popraw wagę wizualizacji dla ikon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Popraw wagę wizualizacji dla ikon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nieprawidłowa waga wizualizacji dla ikon](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Używaj prostych, porównywalnych kształtów i uzupełniających kątów, aby tworzyć elementy bez poświęcania integralności elementów. Jeśli to możliwe, używaj kątów 45° lub 90°.

 ![Poprawne kąty ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektywa
 Zachowaj czytelną i zrozumiałą ikonę. Używaj perspektywy i źródła światła tylko wtedy, gdy jest to konieczne. Mimo że należy unikać korzystania z perspektywy elementów ikon, niektóre elementy są nierozpoznawalne bez niego. W takich przypadkach stylizowana perspektywa komunikuje przejrzystość elementu.

 ![Perspektywa na 3 punkty](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspektywa na 3 punkty

 ![Perspektywa na 1 punkt](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspektywa na 1 punkt

 Większość elementów powinna być skierowana do strony lub pod kątem prawej strony:

 ![Ikony pod kątem po prawej stronie](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Źródeł jasnych należy używać tylko w przypadku dodawania niezbędnej przejrzystości do obiektu.

|**Poprawne źródło światła**|**Nieprawidłowe źródło światła**|
|-|-|
|![Poprawianie źródeł światła dla ikon](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nieprawidłowe źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Używaj konturów tylko w celu zwiększenia czytelności lub lepszego komunikowania metafory. Wynik ujemny (ciemne światło) powinien mieć wartość 50/50.

|**Poprawne użycie konspektu**|**Niepoprawne użycie konspektu**|
|-|-|
|![Prawidłowe kontury](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Nieprawidłowe kontury](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 **Ikony powłoki i paska** poleceń składają się z nie więcej niż trzech z następujących elementów: jeden podstawowy, jeden modyfikator, jedna akcja lub jeden stan.

 ![Przykłady ikon powłoki i paska poleceń](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Przykłady ikon powłoki i paska poleceń

 **Ikony paska poleceń okna** narzędzi składają się z nie więcej niż trzech z następujących elementów: jeden podstawowy, jeden modyfikator, jedna akcja lub jeden stan.

 ![Przykłady ikon paska poleceń okna narzędzi](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Przykłady ikon paska poleceń okna narzędzi

 **Ikony ujmujące** widok drzewa składają się z nie więcej niż trzech z następujących elementów: jeden podstawowy, jeden modyfikator, jedna akcja lub jeden stan.

 ![Przykłady ikon ujmujących widok drzewa](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Przykłady ikon ujmujących widok drzewa

 **Ikony taksonomii** wartości opartej na stanie istnieją w następujących stanach: aktywne, aktywne wyłączone i nieaktywne wyłączone.

 ![Przykłady ikon taksonomii wartości opartej na stanie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Przykłady ikon taksonomii wartości opartej na stanie

 **Ikony IntelliSense** składają się z nie więcej niż trzech z następujących elementów: jeden podstawowy, jeden modyfikator i jeden stan.

 ![Przykłady ikon IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Przykłady ikon IntelliSense

 **Ikony małych projektów (16x16)** powinny mieć nie więcej niż dwa elementy: jeden podstawowy i jeden modyfikator.

 Przykłady ikon małego ![projektu (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ikona projektu &#40;2&#41;![16x16](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3") &#40;3&#41;<br />Przykłady małych ikon projektów (16x16)

 **Ikony dużych projektów (32 x 32)** składają się z nie więcej niż czterech z następujących elementów: jednej podstawy, modyfikatorów od jednego do dwóch i jednej nakładki języka.

 ![Przykłady ikon dużego projektu (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Przykłady ikon dużego projektu (32x32)

### <a name="production-details"></a>Szczegóły produkcji
 Wszystkie nowe elementy interfejsu użytkownika powinny być tworzone przy użyciu Windows Presentation Foundation (WPF), a wszystkie nowe ikony dla WPF powinny być w 32-bitowym formacie PNG. 24-bitowy format PNG to starszy format, który nie obsługuje przezroczystości i dlatego nie jest zalecany w przypadku ikon.

 Zapisz rozdzielczość przy rozdzielczości 96 DPI.

#### <a name="file-types"></a>Typy plików

- **32-bitowy format PNG:** preferowany format ikon. Format pliku kompresji danych bez utraty, który może przechowywać pojedynczy obraz rastrowy (pikseli). 32-bitowe pliki PNG obsługują przezroczystość kanału alfa, korektę gamma i przeplot.

- **32-bitowy BMP: dla** kontrolek innych niż WPF. 32-bitowy BMP, nazywany również XP lub wysokim kolorem, to format obrazu RGB/A, obraz o true kolorze z przezroczystością kanału alfa. Kanał alfa to warstwa przezroczystości wyznaczona w programie Adobe Adobe Funkcji, która jest następnie zapisywana w obrębie mapy bitowej jako dodatkowy (czwarty) kanał kolorów. Czarne tło jest dodawane podczas produkcji kompozycji do wszystkich 32-bitowych plików BMP, aby zapewnić szybką wizualizację podejdź do głębokości koloru. To czarne tło reprezentuje obszar, który ma być zamaskowany w interfejsie użytkownika.

- **32-bitowe ICO: dla** ikon Projektu i Dodaj element. Wszystkie pliki ICO mają 32-bitowy kolor z przezroczystością kanału alfa (RGB/A). Ponieważ pliki ICO mogą przechowywać wiele rozmiarów i głębokości kolorów, ikony systemu Vista są często w formacie ICO zawierającym rozmiary obrazów 16x16, 32x32, 48x48 i 256x256. Aby pliki ICO Eksplorator Windows prawidłowo wyświetlane w poszczególnych plikach, muszą być zapisywane do 24-bitowej i 8-bitowej głębokości kolorów dla każdego rozmiaru obrazu.

- **XAML: dla** powierzchni projektowych i funkcji definiowania układów systemu Windows. Ikony XAML to oparte na wektorach pliki obrazów, które obsługują skalowanie, rotację, wypełnianie i przezroczystość. Obecnie nie są one często Visual Studio, ale stają się bardziej popularne ze względu na elastyczność.

- **Svg**

- **24-bitowy BMP:** dla Visual Studio wiersza polecenia. Format obrazu RGB o true kolorze, 24-bitowy format BMP, to konwencja ikon tworząca warstwę przezroczystości przy użyciu magenta (R=255, G=0, B=255) jako klucza koloru dla warstwy przezroczystości typu knock-out. W 24-bitowym BMP wszystkie powierzchnie magenta są wyświetlane przy użyciu koloru tła.

- **24-bitowy plik GIF:** dla Visual Studio paska poleceń. Format obrazu RGB o true kolorze, który obsługuje przezroczystość. Pliki GIF są często używane w pracach kreatora i animacjach GIF.

### <a name="icon-construction"></a>Konstrukcja ikony
 Najmniejszy rozmiar ikony w Visual Studio to 16x16. Największy w powszechnym użyciu to 32x32. Pamiętaj, aby nie wypełniać całej ramki 16x16, 24x24 lub 32x32 podczas projektowania ikony. Czytelna, ujednolicona konstrukcja ikon jest niezbędna do rozpoznawania użytkowników. Podczas tworzenia ikon należy stosować się do następujących punktów.

- Ikony powinny być jasne, zrozumiałe i spójne.

- Lepiej jest używać elementów powiadomień o stanie jako pojedynczych ikon, a nie stosuć ich na elemencie bazowym ikony. W niektórych kontekstach interfejs użytkownika może wymagać sparowania elementu status z elementem bazowym.

- Ikony projektu to zazwyczaj pliki .ico, które zawierają kilka rozmiarów. Aktualizowane są tylko ikony 16x16, 24x24 i 32x32. Większość ikon 16x16 i 24x24 będzie zawierać te same elementy. Ikony 32x32 zawierają więcej szczegółów, w tym typ języka projektu, jeśli ma to zastosowanie.

- W przypadku ikon 32 x 32 elementy podstawowe mają zazwyczaj wagę linii 2 pikseli. Do elementów szczegółowych można użyć wagi linii 1 lub 2 pikseli. Użyj swojej najlepszej oceny, aby określić, która z nich jest bardziej odpowiednia.

- Odstępy co najmniej 1 pikseli między elementami dla ikon 16x16 i 24x24. W przypadku ikon 32 x 32 użyj odstępów 2 pikseli między elementami oraz między modyfikatorem a elementem bazowym.

  ![Odstępy między elementami dla ikon o rozmiarach 16x16, 24x24 i 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Odstępy między elementami dla ikon o rozmiarach 16x16, 24x24 i 32x32

#### <a name="color-and-accessibility"></a>Kolor i ułatwienia dostępu
 Visual Studio zgodności wymagają, aby wszystkie ikony w produkcie spełniały wymagania dotyczące ułatwień dostępu dla koloru i kontrastu. Jest to osiągane przez odwrócenie ikony, a podczas projektowania należy pamiętać, że zostaną one odwrócone programowo w produkcie.

 Aby uzyskać więcej informacji na temat używania koloru w Visual Studio, zobacz Using color in images (Używanie [koloru na obrazach).](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Używanie koloru na obrazach

### <a name="overview"></a>Omówienie
 Ikony w Visual Studio są głównie monochromatyczne. Kolor jest zarezerwowany do przekazywania określonych informacji i nigdy do dekorowania. Używany kolor:

- aby wskazać akcję

- aby zaalarmować użytkownika o powiadomieniu o stanie

- aby wyznaczyć przynależność do języka

- aby rozróżnić elementy w funkcji IntelliSense

### <a name="accessibility"></a>Ułatwienia dostępu
 Visual Studio zgodności wymagają, aby wszystkie ikony zaewidencjonowane w produkcie spełniały wymagania dotyczące ułatwień dostępu dla koloru i kontrastu. Kolory na palecie języków wizualizacji zostały przetestowane i spełniają te wymagania.

#### <a name="color-inversion-for-dark-themes"></a>Odwrócenie kolorów dla motywów ciemnych
 Aby ikony były wyświetlane z poprawnym współczynnikiem kontrastu w Visual Studio motywie ciemnym, inwersja jest stosowana programowo. Kolory w tym przewodniku zostały wybrane częściowo, aby zostały prawidłowo odwrócone. Ogranicz użycie koloru do tej palety. W przypadku zastosowania odwrócenia otrzymasz nieprzewidywalne wyniki.

 ![Przykłady ikon, które miały odwrócone kolory](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Przykłady ikon, które miały odwrócone kolory

### <a name="base-palette"></a>Paleta podstawowa
 Wszystkie ikony standardowe zawierają trzy kolory podstawowe. Ikony nie zawierają gradientów ani cieni, z jednym lub dwoma wyjątkami dla ikon narzędzi 3D.

|Użycie|Nazwa|Wartość (motyw jasny)|Próbkę|Przykład|
|-----------|----------|---------------------------|------------|-------------|
|Tło/ciemny|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład palety podstawowej](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Pierwszy plan/światło|VS FG|F0EFF1 / 240 239 241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Kontur|VS Out|F6F6F6 / 246 246 246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oprócz kolorów podstawowych każda ikona może zawierać jeden dodatkowy kolor z rozszerzonej palety.

### <a name="extended-palette"></a>Paleta rozszerzona

#### <a name="action-modifiers"></a>Modyfikatory akcji
 Cztery kolory poniżej wskazują typy akcji wymaganych przez modyfikatory akcji:

|Użycie|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Dodatnie|VS Action Green|388A34 / 56 138 52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Ujemne|VS Action Red|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS Action Blue|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Tworzenie/nowy|VS Action Orange|C27D1A / 194 156 26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Przykłady
 Kolor zielony jest używany w przypadku modyfikatorów akcji pozytywnych, takich jak "Dodaj", "Uruchom", "Odtąd" i "Weryfikuj".

|Uruchom|Wykonywanie zapytania|Odtwarzanie wszystkich kroków|Dodawanie kontrolki|
|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Ikona Wykonywania zapytania](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Ikona Odtwarzania wszystkich kroków](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Ikona dodawania kontrolki](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Kolor czerwony jest używany w przypadku modyfikatorów akcji negatywnych, takich jak "Usuń", "Zatrzymaj", "Anuluj" i "Zamknij".

|Usuwanie relacji|Usuwanie kolumny|Zatrzymywanie zapytania|Połączenie w trybie offline|
|-|-|-|-|
|![Ikona Usuwania relacji](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Ikona usuń kolumnę](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Ikona zatrzymania zapytania](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Ikona połączenia w trybie offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Niebieski jest stosowany do modyfikatorów akcji neutralnych najczęściej reprezentowanych jako strzałki, takie jak "Otwórz", "Dalej", "Wstecz", "Import" i "Eksportuj".

|Przejdź do pola|Przetwarzanie wsadowe Check-In|Edytor adresów|Edytor skojarzenia|
|-|-|-|-|
|![Ikona Przejdź do pola](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Wsadowe sprawdzanie&#45;w ikonie](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Ikona edytora adresów](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Ikona edytora skojarzenia](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Ciemny złoty jest używany głównie w przypadku modyfikatora "Nowy".

|Nowy projekt|Tworzenie nowego grafu|Nowy test jednostkowy|Nowy element listy|
|-|-|-|-|
|![Ikona nowego projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Ikona Tworzenia nowego grafu](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Ikona nowego testu jednostkowego](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Ikona nowego elementu listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Specjalne przypadki
 W szczególnych przypadkach kolorowy modyfikator akcji może być używany niezależnie jako ikona autonomiczna. Kolor używany dla ikony odzwierciedla akcje, z których jest skojarzona ikona. To zastosowanie jest ograniczone do niewielkiego podzestawu ikon, w tym:

|Uruchom|Stop|Usuń|Zapisz|Nawiguj wstecz|
|-|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Ikona zatrzymania — pełny czerwony kwadrat.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Ikona usuwania](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Ikona zapisywania](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Ikona nawigowania wstecz](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Paleta hierarchii kodu

#### <a name="folder"></a>Folder

|Użycie|Nazwa|Wartość (wszystkie motywy)|Próbkę|Przykład|
|-----------|----------|--------------------------|------------|-------------|
|Foldery|Folder|DCB67A / 220,182,122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona koloru folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio języków
 Każdy z typowych języków lub platform dostępnych w Visual Studio ma skojarzony kolor. Te kolory są używane na ikonie podstawowej lub w modyfikatorach języka, które pojawiają się w prawym górnym rogu ikon złożonych.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095D7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Purple|9B4F96 / 155 79 150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56 138 52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|KOLOR CZERWONY CSS|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Purple|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Swatch F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (VS Action Blue)|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224 76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z modyfikatorami języka

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![Ikona&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![Ikona&#43;&#43; języka C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![Ikona języka JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Ikona języka Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Ikona języka TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 Ikony funkcji IntelliSense używają wyłącznej palety kolorów. Te kolory ułatwiają użytkownikom szybkie rozróżnienie różnych elementów na liście podręcznej funkcji IntelliSense.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Klasa, zdarzenie|VS Action Orange|C27D1A / 194 125 26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Extension, Method, Module, Delegate|VS Action Purple|652D90 / 101 45 144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Field, Enum Item, Macro, Structure, Union Value Type, Operator, Interface|VS Action Blue|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Obiekt|VS Action Green|388A34 / 56 138 52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Stała, Wyjątek, Element wyli tylko, Mapa, Element mapy, Przestrzeń nazw, Szablon, Definicja typu|Tło (VS BG)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Przykłady ikon IntelliSense

|Klasa|Wydarzenie prywatne|Delegat|Znajomy metody|Pole|
|-|-|-|-|-|
|![Ikona klasy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Ikona prywatnego zdarzenia funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Ikona delegata funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Ikona znajoma metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Ikona pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Chroniony element wyli|Obiekt|Template|Skrót do wyjątku|
|-|-|-|-|
|![Ikona chronionego elementu wy enum funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Ikona szablonu funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Ikona skrótu wyjątku funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Powiadomienia
 Powiadomienia w Visual Studio są używane do wskazywania stanu. Paleta powiadomień używa następujących czterech kolorów, a także opcji wypełnienia czarnego lub białego pierwszego planu do definiowania powiadomień z następującymi poziomami stanu.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Stan: neutral|Notification Blue (VS Blue)|1BA1E2 / 27 161 226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stan: dodatni|Zielony komunikat powiadomienia (VS Green)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stan: ujemny|Powiadomienie w kolorze czerwonym (VS Red)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stan: ostrzeżenie|Powiadomienie żółty (VS Orange)|FFCC00 / 255 204,0|![Swatch FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Wypełnienie pierwszego planu|Powiadomienie czarne (czarne)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Wypełnienie pierwszego planu|Powiadomienie białe (białe)|FFFFFF / 255 255 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Przykłady ikon powiadomień

|Alerty|Ostrzeżenie|Ukończ|Stop|
|-|-|-|-|
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Ikona Ukończenie](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Ikona zatrzymania — pełne czerwone kółko z białym kwadratem w środku.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|