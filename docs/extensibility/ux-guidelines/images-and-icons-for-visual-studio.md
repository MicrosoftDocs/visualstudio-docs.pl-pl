---
title: Obrazy i ikony dla programu Visual Studio | Microsoft Docs
description: Poznaj koncepcje projektowania używane do tworzenia obrazów i ikon dla programu Visual Studio.
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141e388e6877efe2b14c6f652b38b876bafe197f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069078"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazy i ikony dla programu Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Używanie obrazów w programie Visual Studio
 Przed utworzeniem kompozycji należy rozważyć użycie 1000 obrazów w [bibliotece obrazów programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy obrazów

- **Ikony**. Małe obrazy, które pojawiają się w poleceniach, hierarchiach, szablonach i tak dalej. Domyślny rozmiar ikony używany w programie Visual Studio to 16x16 PNG. Ikony tworzone przez usługę obrazu automatycznie generują format XAML na potrzeby obsługi HDPI.

    > [!NOTE]
    > Gdy obrazy są używane w systemie menu, nie należy tworzyć ikon dla każdego polecenia. Zapoznaj się z [menu i poleceniami dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) , aby sprawdzić, czy polecenie powinno uzyskać ikonę.

- **Miniaturk.** Obrazy używane w obszarze podglądu okna dialogowego, takie jak okno dialogowe Nowy projekt.

- **Obrazy okna dialogowego.** Obrazy, które pojawiają się w oknach dialogowych lub kreatorach, jako opisowa grafika lub wskaźniki komunikatów. Używaj rzadko i tylko wtedy, gdy jest to niezbędne do zilustrowania trudnej koncepcji lub uzyskania uwagi użytkownika (alert, ostrzeżenie).

- **Obrazy animowane.** Używany w wskaźnikach postępu, paskach stanu i oknach dialogowych operacji.

- **Mało.** Służy do wskazywania, czy operacja jest dozwolona przy użyciu myszy, gdzie obiekt może być porzucony i tak dalej.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Projektowanie ikon

### <a name="overview"></a>Omówienie
 Program Visual Studio używa ikon nowoczesnego stylu, które mają czyste elementy geometryczne i 50/50 bilanse pozytywne/negatywne (jasne/ciemne) i wykorzystują bezpośrednie, zrozumiałe metafory. Kluczowe ikony wskazujące na przejrzystość, uproszczenie i kontekst.

- **Przejrzystość:** koncentrowanie się na podstawowym metaphor, który zapewnia ikonę i jej znaczenie.

- **Uproszczenie:** Zmniejsz liczbę ikon do jej podstawy, aby uzyskać motyw w przypadku tylko niezbędnych elementów i nie Frills.

- **Kontekst:** należy wziąć pod uwagę wszystkie aspekty roli ikony podczas tworzenia koncepcji, które są decydujące podczas decydowania o tym, które elementy stanowią podstawowe metaphor ikon.

  W przypadku ikon istnieje kilka punktów projektowania, które można uniknąć:

- Nie używaj ikon wskazujących elementy interfejsu użytkownika, z wyjątkiem sytuacji, gdy jest to konieczne. Wybierz bardziej abstrakcyjną lub symboliczną metodę, gdy element interfejsu użytkownika nie jest powszechny, oczywisty ani unikatowy.

- Nie stosuj nadmiernych elementów wspólnych, takich jak dokumenty, foldery, strzałki i Lupa. Używaj takich elementów tylko wtedy, gdy są istotne dla znaczenia ikon. Na przykład szkło powiększające się z prawej strony powinno wskazywać tylko wyszukiwanie, przeglądanie i znajdowanie.

- Chociaż niektóre starsze elementy ikon utrzymują perspektywę, nie twórz nowych ikon z perspektywą, chyba że element nie ma przejrzystości.

- Nie Cram zbyt dużej ilości informacji na ikonę. Prosty obraz, który można łatwo rozpoznać lub poznać jako rozpoznawalny symbol, jest znacznie bardziej użyteczny niż nadmiernie złożona obraz. Ikona nie może informować o całym wątku.

### <a name="icon-creation"></a>Tworzenie ikony

#### <a name="concept-development"></a>Tworzenie koncepcji
 Program Visual Studio ma w swoim interfejsie użytkownika szeroką gamę typów ikon. Uważnie Rozważ użycie typu ikony podczas opracowywania. Nie używaj niejasnych lub nietypowych obiektów interfejsu użytkownika dla elementów ikon. W takich przypadkach należy wybrać symboliczne, takie jak ikona tagu inteligentnego. Należy zauważyć, że znaczenie taga abstract po lewej stronie jest bardziej oczywiste niż niejasny, wersja oparta na interfejsie użytkownika po prawej stronie:

|**Poprawne użycie obrazów symbolicznych**|**Nieprawidłowe użycie obrazów symbolicznych**|
|-|-|
|![Popraw ikonę tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nieprawidłowa ikona tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Istnieją wystąpienia, w których standardowe, łatwo rozpoznawalne elementy interfejsu użytkownika działają dobrze dla ikon. Dodaj okno jest jednym z takich przykładów:

|**Prawidłowy element interfejsu użytkownika w ikonie**|**Nieprawidłowy element UI w ikonie**|
|-|-|
|![Popraw ikonę okna dodawania](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Niepoprawna ikona dodawania okna](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nie używaj dokumentu jako elementu podstawowego, chyba że jest to istotne dla znaczenia ikon. Bez elementu dokumentu w dokumencie Dodawanie dokumentu (poniżej) znaczenie jest tracone, podczas gdy odświeżanie elementu dokumentu nie jest konieczne do przekazania znaczenia.

|**Poprawne użycie ikony dokumentu**|**Nieprawidłowe użycie ikony dokumentu**|
|-|-|
|![Ikona poprawnego dokumentu](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Niepoprawna ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Koncepcja "show" powinna być reprezentowana przez ikonę, która najlepiej ilustruje, co jest wyświetlane, na przykład z przykładem Pokaż wszystkie pliki. Metaphor obiektywu może służyć do wskazania koncepcji "widok", jeśli to konieczne, na przykład z przykładem Widok zasobów.

|**Wskazują**|**Widokiem**|
|-|-|
|![Pokaż ikonę](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ikona widoku](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Ikona lupy ze prawą stroną powinna reprezentować tylko wyszukiwanie, wyszukiwanie i przeglądanie. Wariant z lewej strony ze znakiem plus lub znakiem minus powinien reprezentować tylko powiększanie/powiększanie.

|**Wyszukiwania**|**Zmieniać**|
|-|-|
|![Ikona wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 W widokach drzewa nie należy używać zarówno ikony folderu, jak i modyfikatora. Jeśli jest dostępna, użyj tylko modyfikatora.

|**Popraw ikony widoku drzewa**|**Nieprawidłowe ikony widoku drzewa**|
|-|-|
|![Poprawna ikona widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![ikona widoku drzewa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Niepoprawna ikona widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![ikona widoku drzewa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Szczegóły stylu

#### <a name="layout"></a>Layout
 Elementy stosu, jak pokazano dla standardowych ikon 16x16:

 ![Stos układu dla ikon 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stos układu dla ikon 16x16

 Elementy powiadomień o stanie są lepiej używane jako ikony autonomiczne. Istnieją jednak konteksty, w których powiadomienie powinno być ułożone na podstawie elementu podstawowego, na przykład z ikoną ukończenie zadania:

 ![Powiadomienia autonomiczne w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Ikony powiadomień autonomicznych

 ![Ikona ukończenia zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ikona ukończenia zadania

 Ikony projektu są zwykle plikami ICO, które zawierają wiele rozmiarów. Większość ikon 16x16 zawiera te same elementy. Wersje 32x32 zawierają więcej szczegółów, w tym typ projektu, jeśli ma zastosowanie.

 ![Ikony projektu w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ikony projektu biblioteki formantów systemu Windows w języku VB, 16x16 i 32x32

 Wyśrodkuj ikonę w obrębie jej ramki pikseli. Jeśli to nie jest możliwe, Wyrównaj ikonę do góry i/lub prawej krawędzi ramki.

 ![Ikona wyśrodkowana w obrębie ramki pikseli](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ikona wyśrodkowana w obrębie ramki pikseli

 ![Ikona wyrównany do prawej górnej krawędzi ramki pikseli](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ikona wyrównany do prawej górnej krawędzi ramki

 ![Ikona wyśrodkowana i wyrównana do góry ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ikona wyśrodkowana i wyrównana do góry ramki

 Aby osiągnąć idealne wyrównanie i balans, unikaj zakłócania elementu ikony z glifami akcji. Umieść symbol u góry po lewej stronie elementu podstawowego. Podczas dodawania dodatkowego elementu należy wziąć pod uwagę wyrównanie i balans ikony.

|**Prawidłowe wyrównanie i balans**|**Nieprawidłowe wyrównanie i balans**|
|-|-|
|![Poprawne saldo i wyrównanie ikony](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Nieprawidłowe saldo i wyrównanie ikony](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Zapewnij parzystość rozmiaru ikon, które udostępniają elementy i są używane w zestawach. Należy zauważyć, że w niepoprawnej parowania okrąg i Strzałka są zbyt duże i nie pasują do siebie.

|**Popraw parzystość rozmiaru**|**Niepoprawna parzystość rozmiaru**|
|-|-|
|![Prawidłowy rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nieprawidłowy rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Użyj spójnych wag liniowych i wizualnych. Oceń, w jaki sposób kompilowana ikona porównuje z innymi ikonami przy użyciu porównania Side-by-side. Nigdy nie używaj całej ramki 16x16, użyj 15x15 lub mniejszej. Współczynnik negatyw-do-pozytywnego (ciemny w jasny) powinien wynosić 50/50.

|**Popraw współczynnik negatyw-do-dodatni**|**Nieprawidłowy stosunek negatywny do wartości dodatniej**|
|-|-|
|![Popraw wagę wizualną dla ikon &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Popraw wagę wizualną dla ikon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Popraw grubość wizualną dla ikon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nieprawidłowa grubość wizualizacji dla ikon](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Używaj prostych, porównywalnych kształtów i prostopadłych kątów do kompilowania elementów bez utraty integralności elementów. W miarę możliwości należy używać kątów 45 ° lub 90.

 ![Poprawne kąty ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektywa
 Pozostaw ikonę jasno i zrozumiałą. Używaj perspektyw i źródła światła tylko wtedy, gdy jest to konieczne. Chociaż należy unikać używania perspektywy elementów ikon, niektóre elementy nie są rozpoznawane. W takich przypadkach z stylizowaną perspektywą jest poinformowanie o przejrzystości elementu.

 ![perspektywa 3-punktowa](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />perspektywa 3-punktowa

 ![perspektywa 1 punktu](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />perspektywa 1 punktu

 Większość elementów powinna mieć wartość równą lub skierowaną do prawej:

 ![Ikony ukośnie w prawo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Używaj źródeł światła tylko w przypadku dodawania niezbędnych przejrzystości do obiektu.

|**Prawidłowe Źródło światła**|**Nieprawidłowe źródło światła**|
|-|-|
|![Poprawne źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nieprawidłowe źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Używaj konspektów tylko w celu zwiększenia czytelności lub lepszego komunikowania się z metaphor. Saldo ujemne-dodatnie (ciemne światła) powinno wynosić 50/50.

|**Poprawne użycie konspektów**|**Nieprawidłowe użycie konspektów**|
|-|-|
|![Popraw konspekty](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Nieprawidłowe konspekty](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 Ikony **powłoki i paska poleceń** składają się z nie więcej niż trzech z następujących elementów: jedna podstawowa, jeden modyfikator, jedna akcja lub jeden stan.

 ![Przykłady ikon powłoki i paska poleceń](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Przykłady ikon powłoki i paska poleceń

 Ikony **paska poleceń okna narzędzi** składają się z nie więcej niż trzech z następujących elementów: jeden Base, jeden modyfikator, jedną akcję lub jeden stan.

 ![Przykłady ikon paska poleceń okna narzędzi](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Przykłady ikon paska poleceń okna narzędzi

 Ikony programu modyfikującego **Widok drzewa** składają się z nie więcej niż trzech z następujących elementów: jedna podstawowa, jeden modyfikator, jedna akcja lub jeden stan.

 ![Przykłady ikon elementu uściślania widoku drzewa](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Przykłady ikon elementu uściślania widoku drzewa

 Ikony **taksonomii wartości oparte na stanie** istnieją w następujących stanach: aktywne, aktywne wyłączone i nieaktywne.

 ![Przykłady ikon taksonomii wartościowej opartej na stanie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Przykłady ikon taksonomii wartościowej opartej na stanie

 Ikony **IntelliSense** składają się z nie więcej niż trzech z następujących elementów: jeden Base, jeden modyfikator i jeden stan.

 ![Przykłady ikon IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Przykłady ikon IntelliSense

 **Małe (16x16) ikony projektu** nie mogą zawierać więcej niż dwóch elementów: jeden modyfikator podstawowy i jeden.

 ![Przykłady małych (16x16) ikon projektu](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 project &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![ikonie projektu 16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Przykłady małych (16x16) ikon projektu

 **Duże (32x32) ikony projektu** składają się z nie więcej niż czterech następujących elementów: jeden Base, jeden do dwóch modyfikatorów i jedną nakładkę języka.

 ![Przykłady dużych ikon projektu (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Przykłady dużych ikon projektu (32x32)

### <a name="production-details"></a>Szczegóły produkcyjne
 Wszystkie nowe elementy interfejsu użytkownika powinny być tworzone przy użyciu Windows Presentation Foundation (WPF), a wszystkie nowe ikony WPF powinny mieć format 32-bitowy. 24-bitowy PNG jest starszym formatem, który nie obsługuje przejrzystości i dlatego nie jest zalecany dla ikon.

 Zapisz rozwiązanie pod adresem 96 DPI.

#### <a name="file-types"></a>Typy plików

- **32-bitowy PNG:** preferowany format dla ikon. Bezstratny format pliku kompresji danych, który może przechowywać pojedynczy obraz rastrowy (piksel). 32-bitowe pliki PNG obsługują przezroczystość kanału alfa, korekcję gamma i przeplot.

- **32-bitowy BMP:** dla formantów innych niż WPF. O nazwie XP lub High Color, 32-bitowy BMP to format obrazu RGB/A, obraz True Color z przezroczystością kanału alfa. Kanał alfa jest warstwą przezroczystości wydaną w programie Adobe Photoshop, która jest następnie zapisywana w mapie bitowej jako dodatkowy (czwarty) kanał koloru. Czarne tło jest dodawane w środowisku produkcyjnym do wszystkich 32-bitowych plików BMP, aby zapewnić szybką wizualizację na temat głębi kolorów. To czarne tło reprezentuje obszar, który ma być maskowany w interfejsie użytkownika.

- **32-bit ICO:** w przypadku ikon projektu i dodania elementu. Wszystkie pliki ICO są 32-bitowym True Color z przezroczystością kanału alfa (RGB/A). Ponieważ pliki ICO mogą przechowywać wiele rozmiarów i głębi kolorów, ikony systemu Vista często są w formacie ICO zawierającym rozmiary obrazów 16x16, 32x32, 48x48 i 256x256. Aby można było wyświetlić ją prawidłowo w Eksploratorze Windows, należy zapisać pliki ICO z 24-bitową i 8-bitową głębią kolorów dla każdego rozmiaru obrazu.

- **XAML:** dla powierzchni projektowych i modułów definiowania układu systemu Windows. Ikony XAML są plikami obrazów opartymi na wektorach, które obsługują skalowanie, obracanie, wypełnianie i przezroczystość. Nie są one często używane w programie Visual Studio, ale stają się coraz bardziej popularne ze względu na ich elastyczność.

- **FORMACIE**

- **24-bitowy BMP:** dla paska poleceń programu Visual Studio. Format obrazu RGB True Color, 24-bitowy BMP jest konwencją ikon, która tworzy warstwę przezroczystości przy użyciu opcji amarantowy (R = 255, G = 0, B = 255) jako klucz koloru dla warstwy przezroczystości wycinania. W 24-bitowym BMP wszystkie powierzchnie są wyświetlane przy użyciu koloru tła.

- **24-bitowy GIF:** dla paska poleceń programu Visual Studio. Format obrazu RGB True Color, który obsługuje przezroczystość. Pliki GIF są często używane w grafikach kreatora i animacjach GIF.

### <a name="icon-construction"></a>Konstrukcja ikony
 Najmniejszy rozmiar ikony w programie Visual Studio to 16x16. Największe w powszechnym użyciu to 32x32. Pamiętaj, aby nie wypełnić całej ramki 16x16, 24x24 lub 32x32 podczas projektowania ikony. Czytelna, jednorodna konstrukcja Icon jest istotna dla rozpoznawania użytkownika. Podczas kompilowania ikon należy przestrzegać następujących zagadnień.

- Ikony powinny być jasne, zrozumiałe i spójne.

- Lepiej jest używać elementów powiadomień o stanie jako pojedynczych ikon, a nie do układania ich na podstawie elementu podstawowego ikony. W niektórych kontekstach interfejs użytkownika może wymagać, aby element status został sparowany z elementem podstawowym.

- Ikony projektu są zwykle plikami ICO, które zawierają kilka rozmiarów. Aktualizowane są tylko ikony 16x16, 24x24 i 32x32. Większość ikon 16x16 i 24x24 będzie zawierać te same elementy. Ikony 32x32 zawierają więcej szczegółów, w tym typ języka projektu, jeśli ma to zastosowanie.

- W przypadku ikon 32x32 elementy podstawowe mają zwykle 2-pikselową grubość linii. Do elementów szczegółów można używać wagi liniowej 1 lub 2 pikseli. Skorzystaj z najlepszych orzeczeń, aby określić, co jest bardziej odpowiednie.

- Należy wybrać co najmniej jeden piksel między elementami dla ikon 16x16 i 24x24. W przypadku ikon 32x32 Użyj odstępu dwóch pikseli między elementami i między modyfikatorem a elementem bazowym.

  ![Odstępy między elementami ikon o rozmiarze 16x16, 24x24 i 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Odstępy między elementami ikon o rozmiarze 16x16, 24x24 i 32x32

#### <a name="color-and-accessibility"></a>Kolor i ułatwienia dostępu
 Wskazówki dotyczące zgodności programu Visual Studio wymagają, aby wszystkie ikony w produkcie przeszły wymagania dotyczące ułatwień dostępu dla kolorów i kontrastu. Jest to możliwe dzięki wykorzystaniu ikony, a podczas projektowania należy pamiętać, że zostaną one programowo odwracane w produkcie.

 Aby uzyskać więcej informacji na temat używania koloru w ikonach programu Visual Studio, zobacz [using Color in images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Korzystanie z koloru w obrazach

### <a name="overview"></a>Omówienie
 Ikony w programie Visual Studio to przede wszystkim monochromatyczny. Kolor jest zarezerwowany do przekazywania określonych informacji i nigdy nie do dekoracji. Kolor jest używany:

- Aby wskazać akcję

- aby ostrzec użytkownika do powiadomienia o stanie

- Aby wyznaczyć przynależność do języka

- Aby rozróżnić elementy w funkcji IntelliSense

### <a name="accessibility"></a>Ułatwienia dostępu
 Wskazówki dotyczące zgodności programu Visual Studio wymagają, aby wszystkie ikony zaznaczone w produkcie przeszły wymagania dotyczące ułatwień dostępu dla kolorów i kontrastu. Kolory z palety języka wizualnego zostały przetestowane i spełniają te wymagania.

#### <a name="color-inversion-for-dark-themes"></a>Kolorowa wersja dla ciemnych motywów
 Aby ikony były wyświetlane z poprawnym wskaźnikiem kontrastu w ciemnym motywie programu Visual Studio, program jest stosowany programowo. Kolory w tym przewodniku zostały wybrane w części, dzięki czemu są one odwracane poprawnie. Ogranicz użycie koloru do tej palety, aby uzyskać nieprzewidywalne wyniki w przypadku zastosowania nieużywanej wersji.

 ![Przykłady ikon, dla których zostały odwrócone kolory](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 — 01_DarkThemeInversion")<br />Przykłady ikon, dla których zostały odwrócone kolory

### <a name="base-palette"></a>Paleta podstawowa
 Wszystkie standardowe ikony zawierają trzy kolory podstawowe. Ikony nie zawierają gradientów ani cieni z jednym lub dwoma wyjątkami dla ikon narzędzi 3W.

|Użycie|Nazwa|Wartość (motyw jasny)|Spowoduje|Przykład|
|-----------|----------|---------------------------|------------|-------------|
|Tło/ciemne|VS BG|424242/66, 66, 66|![Próbnik 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład palety podstawowej](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 — 02_BasePaletteExample")|
|Pierwszy plan/światło|VS FG|F0EFF1/240 239 241|![F0EFF1 próbki](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Kontur|A poza|F6F6F6/246 246 246|![F6F6F6 próbki](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oprócz kolorów podstawowych Każda ikona może zawierać jeden dodatkowy kolor z rozszerzonej palety.

### <a name="extended-palette"></a>Rozszerzona paleta

#### <a name="action-modifiers"></a>Modyfikatory akcji
 Cztery poniższe kolory wskazują typy akcji wymagane przez Modyfikatory akcji:

|Użycie|Nazwa|Wartość (wszystkie motywy)|Spowoduje|
|-----------|----------|--------------------------|------------|
|Dodatnie|VS — Zielona akcja|388A34/56138, 52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Ujemne|Czerwona akcja VS|A1260D/161, 38, 13|![A1260D próbki](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|Niebieska akcja VS|00539C/0, 83156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Utwórz/nowy|VS — akcja pomarańczowa|C27D1A/194156, 26|![C27D1A próbki](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Przykłady
 Zielony jest używany dla modyfikatorów akcji pozytywnych, takich jak "Add", "Run", "Play" i "Validate".

|Uruchom|Wykonaj zapytanie|Odtwórz wszystkie kroki|Dodaj kontrolkę|
|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 — 03_ActionModifierRun")|![Ikona wykonywania zapytania](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 — 04_ExecuteQuery")|![Ikona odtwarzania wszystkich kroków](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 — 05_PlayAllSteps")|![Dodaj ikonę kontrolki](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 — 06_AddControl")|

 Czerwony jest używany dla modyfikatorów akcji ujemnych, takich jak "Delete", "Stop" "Cancel" i "Close".

|Usuwanie relacji|Usuń kolumnę|Zatrzymaj zapytanie|Połączenie w trybie offline|
|-|-|-|-|
|![Ikona usuwania relacji](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 — 07_DeleteRelationship")|![Ikona usuwania kolumny](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 — 08_DeleteColumn")|![Ikona zatrzymania zapytania](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 — 09_StopQuery")|![Ikona połączenia w trybie offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 — 10_ConnectionOffline")|

 Niebieska jest stosowana do modyfikatorów akcji neutralnych najczęściej reprezentowanych jako strzałki, takich jak "Open", "dalej" "Previous", "Import" i "Export".

|Przejdź do pola|Check-In wsadowe|Edytor adresów|Edytor skojarzeń|
|-|-|-|-|
|![Ikona przejdź do pola](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 — 11_GoToField")|![&#45;sprawdzanie wsadowe w ikonie](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 — 12_BatchedCheckIn")|![Ikona edytora adresów](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 — 13_AddressEditor")|![Ikona edytora skojarzeń](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 — 14_AssociationEditor")|

 Ciemny złoty jest używany głównie dla modyfikatora "New".

|Nowy projekt|Utwórz nowy wykres|Nowy test jednostkowy|Nowy element listy|
|-|-|-|-|
|![Ikona nowego projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 — 15_NewProject")|![Utwórz nową ikonę grafu](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 — 16_CreateNewGraph")|![Ikona nowego testu jednostkowego](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 — 17_NewUnitTest")|![Ikona nowego elementu listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 — 18_NewListItem")|

#### <a name="special-cases"></a>Specjalne przypadki
 W szczególnych przypadkach można użyć kolorowego modyfikatora akcji niezależnie jako ikony autonomicznej. Kolor używany dla ikony odzwierciedla akcje, z którymi jest skojarzona ikona. To użycie jest ograniczone do małego podzbioru ikon, w tym:

|Uruchom|Stop|Usuń|Zapisz|Nawiguj wstecz|
|-|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 — 03_ActionModifierRun")|![Ikona zatrzymania — Solid czerwony kwadrat.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 — 19_Stop")|![Ikona usuwania](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 — 20_Delete")|![Ikona zapisywania](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 — 21_Save")|![Ikona nawigacji Wstecz](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 — 22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Paleta hierarchii kodu

#### <a name="folder"></a>Folder

|Użycie|Nazwa|Wartość (wszystkie motywy)|Spowoduje|Przykład|
|-----------|----------|--------------------------|------------|-------------|
|Foldery|Folder|DCB67A/220 182 122|![DCB67A próbki](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona koloru folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 — 23_FolderColor")|

#### <a name="visual-studio-languages"></a>Języki programu Visual Studio
 Każdy ze wspólnych języków lub platform dostępnych w programie Visual Studio ma skojarzony kolor. Te kolory są używane na ikonie podstawowej lub w modyfikatorach języka, które pojawiają się w prawym górnym rogu ikon złożonych.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Spowoduje|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095D7/0149 215|![0095D7 próbki](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP purpurowy|9B4F96/155, 79150|![9B4F96 próbki](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS (zielony) (VS Action zielony)|388A34/56138, 52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Czerwony kod CSS|BD1E2D/189, 30, 45|![BD1E2D próbki](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|ZR — purpurowy|672878/103, 40120|![Próbnik 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS — pomarańczowy|F16421/241100, 33|![F16421 próbki](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|Niebieska VB (VS Action Blue)|00539C/0, 83156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Wypomarańcze TS|E04C06/224, 76, 6|![E04C06 próbki](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Zielony z pr|879636/135150, 54|![Próbnik 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z modyfikatorami języka

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 — 25_VB")|![Ikona&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 — 26_CSharp")|![Ikona&#43;&#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 — 27_CPlusPlus")|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 — 28_FSharp")|![Ikona JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 — 29_JavaScript")|![Ikona języka Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 — 30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 — 31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 — 32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 — 33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 — 34_CSS")<br />CSS|![Ikona języka TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 — 35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 Ikony IntelliSense używają wyłącznej palety kolorów. Te kolory są używane do ułatwienia użytkownikom szybkiego rozróżniania między różnymi elementami na liście podręcznej IntelliSense.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Spowoduje|
|-----------|----------|--------------------------|------------|
|Klasa, zdarzenie|VS — akcja pomarańczowa|C27D1A/194125, 26|![C27D1A próbki](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metoda rozszerzenia, metoda, moduł, delegat|VS — akcja purpurowa|652D90/101, 45144|![652D90 próbki](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Pole, element Enum, makro, struktura, typ wartości Unii, operator, interfejs|Niebieska akcja VS|00539C/0, 83156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Obiekt|VS — Zielona akcja|388A34/56138, 52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Stała, wyjątek, element Enum, mapa, element mapy, przestrzeń nazw, szablon, definicja typu|Tło (VS BG)|424242/66, 66, 66|![Próbnik 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Przykłady ikon IntelliSense

|Klasa|Wydarzenie prywatne|Delegat|Metoda zaprzyjaźniona|Pole|
|-|-|-|-|-|
|![Ikona klasy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 — 36_IntelliSenseClass")|![Ikona prywatnego zdarzenia IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 — 37_IntelliSensePrivateEvent")|![Ikona delegata IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 — 38_IntelliSenseDelegate")|![Ikona zaprzyjaźnionej metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 — 39_IntelliSenseMethodFriend")|![Ikona pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 — 40_Field")|

|Chroniony element Enum|Obiekt|Template|Skrót wyjątku|
|-|-|-|-|
|![Ikona elementu Enum chronionego przez funkcję IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 — 41_IntelliSenseProtectedEnumItem")|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 — 42_IntelliSenseObject")|![Ikona szablonu IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 — 43_IntelliSenseTemplate")|![Ikona skrótu wyjątku IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 — 44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Powiadomienia
 Powiadomienia w programie Visual Studio służą do wskazania stanu. Paleta powiadomień używa następujących czterech kolorów, a także czarno-białych opcji wypełnienia na pierwszym planie, aby definiować powiadomienia o następujących poziomach stanu.

|Użycie|Nazwa|Wartość (wszystkie motywy)|Spowoduje|
|-----------|----------|--------------------------|------------|
|Stan: neutralna|Powiadomienie niebieskie (VS Blue)|1BA1E2/27 161 226|![1BA1E2 próbki](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stan: dodatnie|Powiadomienie zielony (VS zielony)|339933/51153, 51|![Próbnik 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stan: negatyw|Powiadomienie czerwone (VS Red)|E51400/229, 20, 0|![E51400 próbki](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stan: Ostrzeżenie|Powiadomienie żółte (VS pomarańczowy)|FFCC00/255204, 0|![FFCC00 próbki](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Wypełnienie pierwszego planu|Powiadomienie Black (czerń)|000000/0, 0, 0|![Próbkowanie &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Wypełnienie pierwszego planu|Powiadomienie białe (białe)|FFFFFF/255 255 255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Przykłady ikon powiadomień

|Alerty|Ostrzeżenie|Ukończ|Stop|
|-|-|-|-|
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 — 45_Alert")|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 — 48_Warning")|![Ikona ukończenia](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 — 46_Complete")|![Ikona zatrzymania — Solid czerwony okrąg z białym kwadratem w środku.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 — 47_Stop")|