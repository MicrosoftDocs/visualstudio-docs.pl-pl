---
title: Obrazy i ikony programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303198"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazy i ikony dla programu Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Użycie obrazu w programie Visual Studio
 Przed utworzeniem kompozycji należy rozważyć użycie ponad 1000 obrazów w [bibliotece obrazów programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy obrazów

- **Ikony**. Małe obrazy wyświetlane w poleceniach, hierarchiach, szablonach itd. Domyślny rozmiar ikony używany w programie Visual Studio to 16x16 PNG. Ikony tworzone przez usługę obrazów automatycznie generują format XAML dla obsługi hdpi.

    > [!NOTE]
    > Podczas gdy obrazy są używane w systemie menu, nie należy tworzyć ikony dla każdego polecenia. Zapoznaj się z [menu i polecenia dla programu Visual Studio,](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) aby zobaczyć, czy polecenie powinno uzyskać ikonę.

- **Miniatury.** Obrazy używane w obszarze podglądu okna dialogowego, takie jak okno dialogowe Nowy projekt.

- **Obrazy dialogowe.** Obrazy wyświetlane w oknach dialogowych lub kreatorach jako opisowe wskaźniki graficzne lub komunikaty. Używaj rzadko i tylko wtedy, gdy jest to konieczne, aby zilustrować trudną koncepcję lub zdobyć uwagę użytkownika (alert, ostrzeżenie).

- **Animacjami.** Używane w wskaźnikach postępu, paskach stanu i oknach dialogowych operacji.

- **Kursory.** Służy do wskazania, czy operacja jest dozwolona za pomocą myszy, gdzie obiekt może zostać upuszczony i tak dalej.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Projekt ikony

### <a name="overview"></a>Omówienie
 Visual Studio używa ikon w nowoczesnym stylu, które mają czystą geometrię i bilans 50/50 dodatnich/ujemnych (jasne/ciemne) i używają bezpośrednich, zrozumiałych metafor. Kluczowe punkty projektowania ikon skupiają się wokół jasności, uproszczenia i kontekstu.

- **Jasność: skup** się na podstawowej metaforze, która nadaje ikonie jej znaczenie i indywidualność.

- **Uproszczenie:** zmniejsz ikonę do jej podstawowego znaczenia - uzyskaj motyw za pomocą niezbędnych elementów i bez dodatków.

- **Kontekst:** należy wziąć pod uwagę wszystkie aspekty roli ikony podczas opracowywania koncepcji, co ma kluczowe znaczenie przy podejmowaniu decyzji, które elementy stanowią podstawową metaforę ikony.

  W liczba ikonach istnieje wiele punktów konstrukcyjnych, których należy unikać:

- Nie używaj ikon, które oznaczają elementy interfejsu użytkownika, chyba że jest to konieczne. Wybierz bardziej abstrakcyjne lub symboliczne podejście, gdy element interfejsu użytkownika nie jest ani wspólny, oczywisty, ani unikatowy.

- Nie używaj typowych elementów, takich jak dokumenty, foldery, strzałki i lupa. Takich elementów należy używać tylko wtedy, gdy jest to istotne dla znaczenia ikony. Na przykład lupa skierowana w prawo powinna wskazywać tylko wyszukiwanie, przeglądanie i znajdowanie.

- Chociaż niektóre starsze elementy ikony zachowują użycie perspektywy, nie należy tworzyć nowe ikony z perspektywy, chyba że element nie ma jasności bez niego.

- Nie wbuszaj zbyt wielu informacji w ikonę. Prosty obraz, który można łatwo rozpoznać lub nauczyć się jako rozpoznawalny symbol, jest o wiele bardziej przydatny niż zbyt złożony obraz. Ikona nie może opowiedzieć całej historii.

### <a name="icon-creation"></a>Tworzenie ikon

#### <a name="concept-development"></a>Opracowanie koncepcji
 Visual Studio ma w ramach interfejsu użytkownika szeroką gamę typów ikon. Należy dokładnie rozważyć typ ikony podczas tworzenia. Nie używaj niejasnych lub nietypowych obiektów interfejsu użytkownika dla elementów ikony. Wybierz symbol w tych przypadkach, na przykład z ikoną tagu inteligentnego. Należy zauważyć, że znaczenie abstrakcyjnego tagu po lewej stronie jest bardziej oczywiste niż niejasna wersja oparta na interfejsie użytkownika po prawej stronie:

|||
|-|-|
|**Prawidłowe wykorzystanie obrazów symbolicznych**|**Nieprawidłowe użycie obrazów symbolicznych**|
|![Ikona Popraw tag inteligentny](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nieprawidłowa ikona tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Istnieją przypadki, w których standardowe, łatwo rozpoznawalne elementy interfejsu użytkownika działają dobrze dla ikon. Dodaj okno jest jednym z takich przykładów:

|||
|-|-|
|**Popraw element interfejsu użytkownika w ikonie**|**Niepoprawny element interfejsu użytkownika w ikonie**|
|![Ikona Popraw okno dodawania](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Nieprawidłowa ikona Dodaj okno](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nie używaj dokumentu jako elementu podstawowego, chyba że jest to istotne dla znaczenia ikony. Bez elementu dokumentu na Dodaj dokument (poniżej) znaczenie zostanie utracone, natomiast z Odśwież element dokumentu jest niepotrzebne do komunikowania znaczenia.

|||
|-|-|
|**Prawidłowe użycie ikony dokumentu**|**Nieprawidłowe użycie ikony dokumentu**|
|![Ikona Popraw dokument](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Ikona Nieprawidłowy dokument](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Pojęcie "show" powinny być reprezentowane przez ikonę, która najlepiej ilustruje to, co jest wyświetlane, na przykład w przykładzie Pokaż wszystkie pliki. Metafora obiektywu może służyć do wskazania pojęcia "widok" w razie potrzeby, na przykład w widoku zasobów.

|||
|-|-|
|**"Pokaż"**|**"Widok"**|
|![Ikona Pokaż](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ikona Widoku](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Ikona lupy skierowana do prawej strony powinna reprezentować tylko wyszukiwanie, znajdowanie i przeglądanie. Wariant lewosztowy ze znakiem plus lub minus powinien reprezentować tylko powiększanie/pomniejszanie.

|||
|-|-|
|**"Szukaj"**|**"Zoom"**|
|![Ikona wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 W widokach drzewa nie należy używać zarówno ikony folderu, jak i modyfikatora. Jeśli jest dostępny, należy używać tylko modyfikatora.

|||
|-|-|
|**Prawidłowe ikony widoku drzewa**|**Nieprawidłowe ikony widoku drzewa**|
|![Popraw ikonę widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Popraw ikonę widoku drzewa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Nieprawidłowa ikona widoku drzewa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Nieprawidłowa ikona widoku drzewa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Szczegóły stylu

#### <a name="layout"></a>Układ
 Elementy stosu, jak pokazano dla standardowych ikon 16x16:

 ![Układ stosu dla ikon 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Układ stosu dla ikon 16x16

 Elementy powiadomień o stanie są lepiej używane jako ikony autonomiczne. Istnieją jednak konteksty, w których powiadomienie powinno być ułożone na elemencie podstawowym, na przykład z ikoną Zakończenie zadania:

 ![Autonomiczne powiadomienia w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Ikony powiadomień autonomicznych

 ![Ikona ukończenia zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ikona Zadania Ukończone

 Ikony projektu są zazwyczaj plikami .ico, które zawierają wiele rozmiarów. Większość ikon 16x16 zawiera te same elementy. Wersje 32x32 mają więcej szczegółów, w tym typ projektu, jeśli ma to zastosowanie.

 ![Ikony projektu w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ikony projektu biblioteki sterowania systemem Windows VB, 16x16 i 32x32

 Wyśrodkuj ikonę w ramce pikseli. Jeśli nie jest to możliwe, wyrównaj ikonę do góry i/lub po prawej stronie ramki.

 ![Ikona wyśrodkowany w ramce piksela](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ikona wyśrodkowany w ramce piksela

 ![Ikona wyrównana do prawego górnego rogu ramki pikseli](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ikona wyrównana do prawego górnego rogu ramki

 ![Ikona wyśrodkowany i wyrównany do górnej części ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ikona wyśrodkowany i wyrównany do górnej części ramki

 Aby osiągnąć idealne wyrównanie i równowagę, należy unikać zasłaniania elementu bazowego ikony za pomocą glifów akcji. Umieść glif w lewym górnym rogu elementu bazowego. Podczas dodawania dodatkowego elementu należy wziąć pod uwagę wyrównanie i równowagę ikony.

|||
|-|-|
|**Prawidłowe wyrównanie i wyważenie**|**Nieprawidłowe wyrównanie i równowaga**|
|![Popraw równowagę i wyrównanie ikon](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Nieprawidłowe balans i wyrównanie ikon](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Upewnij się, że parzystość rozmiaru dla ikon, które współużytkują elementy i są używane w zestawach. Należy zauważyć, że w niepoprawnym parowaniu okrąg i strzałka są przewymiarowane i nie pasują do siebie.

|||
|-|-|
|**Poprawna parzystość rozmiaru**|**Niepoprawna parzystość rozmiaru**|
|![Popraw rozmiar i parzystość ikony](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nieprawidłowy rozmiar i parzystość ikony](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Użyj spójnych obciążników liniowych i wizualnych. Oceń, jak ikona, którą budujesz, porównuje się z innymi ikonami za pomocą porównania obok siebie. Nigdy nie używaj całej ramki 16x16, używaj 15x15 lub mniejszej. Stosunek ujemny do dodatniego (ciemny do światła) powinien wynosić 50/50.

|||
|-|-|
|**Prawidłowy stosunek ujemny do dodatni**|**Niepoprawny stosunek ujemny do dodatni**|
|![Prawidłowa waga wizualna ikon &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Prawidłowa waga wizualna ikon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Prawidłowa waga wizualna ikon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nieprawidłowa masa wizualna ikon](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Użyj prostych, porównywalnych kształtów i uzupełniających się kątów, aby tworzyć elementy bez poświęcania integralności elementu. W miarę możliwości należy stosować kąty 45° lub 90°.

 ![Prawidłowe kąty ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektywa
 Utrzymuj ikonę w jasny i zrozumiały sposób. Używaj perspektywy i źródła światła tylko wtedy, gdy jest to konieczne. Chociaż należy unikać korzystania z perspektywy elementów ikony, niektóre elementy są nie do poznania bez niego. W takich przypadkach stylizowane perspektywy komunikuje jasność elementu.

 ![Perspektywa 3-punktowa](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspektywa 3-punktowa

 ![Perspektywa 1-punktowa](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspektywa 1-punktowa

 Większość elementów powinna być skierowana lub pod kątem w prawo:

 ![Ikony ustawione w prawo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Źródła światła należy używać tylko wtedy, gdy obiekt dodaje niezbędną przejrzystość.

|||
|-|-|
|**Prawidłowe źródło światła**|**Nieprawidłowe źródło światła**|
|![Prawidłowe źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nieprawidłowe źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Używaj konturów tylko w celu zwiększenia czytelności lub lepszego komunikowania metafory. Bilans ujemno-dodatni (ciemny światopomysł) powinien wynosić 50/50.

|||
|-|-|
|**Prawidłowe użycie konturów**|**Nieprawidłowe użycie konturów**|
|![Poprawne kontury](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Nieprawidłowe kontury](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Typy ikon
 **Ikony powłoki i paska poleceń** składają się z nie więcej niż trzech następujących elementów: jednej bazy, jednego modyfikatora, jednej akcji lub jednego stanu.

 ![Przykłady ikon powłoki i paska poleceń](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Przykłady ikon powłoki i paska poleceń

 Ikony **paska poleceń okna narzędzia** składają się z nie więcej niż trzech następujących elementów: jednej bazy, jednego modyfikatora, jednej akcji lub jednego stanu.

 ![Przykłady ikon paska poleceń okna narzędzia](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Przykłady ikon paska poleceń okna narzędzia

 **Ikony rozróżniacza widoku drzewa** składają się z nie więcej niż trzech następujących elementów: jednej bazy, jednego modyfikatora, jednej akcji lub jednego stanu.

 ![Przykłady ikon rozróżniacza widoku drzewa](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Przykłady ikon rozróżniacza widoku drzewa

 W następujących stanach istnieją oparte na stanie ikony **taksonomii wartości:** aktywne, aktywne wyłączone i nieaktywne wyłączone.

 ![Przykłady ikon taksonomii wartości opartej na stanie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Przykłady ikon taksonomii wartości opartej na stanie

 **Ikony IntelliSense** składają się z nie więcej niż trzech następujących elementów: jednej bazy, jednego modyfikatora i jednego stanu.

 ![Przykłady ikon IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Przykłady ikon IntelliSense

 **Małe (16x16)** ikony projektu powinny mieć nie więcej niż dwa elementy: jeden podstawowy i jeden modyfikator.

 ![Przykłady małych (16x16) ikon projektu](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 ikona projektu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 ikony projektu &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Przykłady małych (16x16) ikon projektu

 **Duże (32x32)** ikony projektu składają się z nie więcej niż czterech następujących elementów: jednej bazy, od jednego do dwóch modyfikatorów i jednej nakładki językowej.

 ![Przykłady dużych (32x32) ikon projektu](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Przykłady dużych (32x32) ikon projektu

### <a name="production-details"></a>Szczegóły produkcji
 Wszystkie nowe elementy interfejsu użytkownika powinny być tworzone przy użyciu programu Windows Presentation Foundation (WPF), a wszystkie nowe ikony dla WPF powinny być w formacie PNG 32-bitowego. 24-bitowy png jest starszy format, który nie obsługuje przezroczystości i dlatego nie jest zalecane dla ikon.

 Zapisz rozdzielczość na 96 DPI.

#### <a name="file-types"></a>Typy plików

- **32-bitowy PNG:** preferowany format ikon. Bezstratny format pliku kompresji danych, który może przechowywać pojedynczy obraz rastrowy (piksel). 32-bitowe pliki PNG obsługują przezroczystość kanału alfa, korekcję gamma i przeplot.

- **32-bitowy BMP:** dla formantów innych niż WPF. 32-bitowy BMP o nazwie XP lub high color to format obrazu RGB/A, obraz prawdziwego koloru z przezroczystością kanału alfa. Kanał alfa to warstwa przezroczystości oznaczona w programie Adobe Photoshop, która jest następnie zapisywana w mapie bitowej jako dodatkowy (czwarty) kanał kolorów. Czarne tło jest dodawane podczas produkcji kompozycji do wszystkich 32-bitowych plików BMP, aby zapewnić szybką wizualną wskazówkę dotyczącą głębi kolorów. To czarne tło reprezentuje obszar, który ma zostać zamaskowany w interfejsie użytkownika.

- **32-bitowa ICO:** dla ikon projektu i Dodaj element. Wszystkie pliki ICO są 32-bitowym kolorem true z przezroczystością kanału alfa (RGB/A). Ponieważ pliki ICO mogą przechowywać wiele rozmiarów i głębi kolorów, ikony vista są często w formacie ICO zawierającym rozmiary obrazów 16x16, 32x32, 48x48 i 256x256. Aby pliki ICO były poprawnie wyświetlane w Eksploratorze Windows, muszą być zapisywane do 24-bitowej i 8-bitowej głębi kolorów dla każdego rozmiaru obrazu.

- **XAML:** dla powierzchni projektowych i adornerów systemu Windows. Ikony XAML to pliki obrazów wektorowych, które obsługują skalowanie, obracanie, archiwizowanie i przezroczystość. Nie są one powszechne w programie Visual Studio dzisiaj, ale stają się coraz bardziej popularne ze względu na ich elastyczność.

- **Svg**

- **24-bitowy BMP:** dla paska poleceń programu Visual Studio. 24-bitowy format obrazu RGB w kolorze rzeczywistym jest konwencją ikon, która tworzy warstwę przezroczystości przy użyciu magenta (R=255, G=0, B=255) jako klucza koloru dla warstwy przezroczystości typu knock-out. W 24-bitowym bmp wszystkie powierzchnie karmazynowe są wyświetlane przy użyciu koloru tła.

- **24-bitowy GIF:** dla paska poleceń programu Visual Studio. Prawdziwie kolorowy format obrazu RGB, który obsługuje przezroczystość. Pliki GIF są często używane w kompozycji Kreatora i animacjach GIF.

### <a name="icon-construction"></a>Konstrukcja ikony
 Najmniejszy rozmiar ikony w programie Visual Studio to 16x16. Największy wspólny użytek to 32x32. Pamiętaj, aby podczas projektowania ikony nie wypełniać całej ramki 16x16, 24x24 lub 32x32. Czytelna, jednolita konstrukcja ikony jest niezbędna do rozpoznawania użytkownika. Podczas tworzenia ikon stosują się do następujących punktów.

- Ikony powinny być jasne, zrozumiałe i spójne.

- Lepiej jest użyć elementów powiadomień o stanie jako pojedynczych ikon i nie układać ich na wierzchu elementu bazowego ikony. W niektórych kontekstach interfejsu użytkownika może wymagać elementu stanu, które mają być sparowane z elementem podstawowym.

- Ikony projektu są zwykle plikami .ico, które zawierają kilka rozmiarów. Aktualizowane są tylko ikony 16x16, 24x24 i 32x32. Większość ikon 16x16 i 24x24 będzie zawierać te same elementy. Ikony 32x32 zawierają więcej szczegółów, w tym typ języka projektu, jeśli ma to zastosowanie.

- W przypadku ikon o wymiarach 32x32 elementy bazowe mają zazwyczaj 2-pikselową wagę linii. Do elementów szczegółowych można użyć 1- lub 2-pikselowej wagi linii. Użyj najlepszego osądu, aby określić, który jest bardziej odpowiedni.

- Mają co najmniej odstępy 1 pikseli między elementami dla ikon 16x16 i 24x24. W przypadku ikon o wymiarach 32x32 należy użyć odstępów 2-pikselowych między elementami oraz między modyfikatorem a elementem bazowym.

  ![Odstępy między elementami dla ikon o wymiarach 16x16, 24x24 i 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Odstępy między elementami dla ikon o wymiarach 16x16, 24x24 i 32x32

#### <a name="color-and-accessibility"></a>Kolor i dostępność
 Wskazówki dotyczące zgodności programu Visual Studio wymagają, aby wszystkie ikony w produkcie przeszły wymagania dotyczące ułatwień dostępu dla koloru i kontrastu. Osiąga się to poprzez odwrócenie ikon, a podczas projektowania, należy pamiętać, że będą one odwrócone programowo w produkcie.

 Aby uzyskać więcej informacji na temat używania kolorów w ikonach programu Visual Studio, zobacz [Używanie koloru w obrazach](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Korzystanie z kolorów na obrazach

### <a name="overview"></a>Omówienie
 Ikony w programie Visual Studio są przede wszystkim monochromatyczne. Kolor jest zarezerwowany do przekazywania konkretnych informacji, a nigdy do dekoracji. Kolor jest używany:

- , aby wskazać akcję

- , aby powiadomić użytkownika o powiadomieniu o stanie

- , aby wyznaczyć przynależność językową

- do rozróżniania elementów w ramach intellisense

### <a name="accessibility"></a>Ułatwienia dostępu
 Wskazówki dotyczące zgodności programu Visual Studio wymagają, aby wszystkie ikony zaewidencjonowane w produkcie przeszły wymagania dotyczące ułatwień dostępu dla kolorów i kontrastu. Kolory w palecie języków wizualnych zostały przetestowane i spełniają te wymagania.

#### <a name="color-inversion-for-dark-themes"></a>Odwrócenie kolorów dla ciemnych motywów
 Aby ikony były wyświetlane z poprawnym współczynnikiem kontrastu w ciemnym motywie programu Visual Studio, inwersja jest stosowana programowo. Kolory w tym przewodniku zostały wybrane częściowo tak, aby były poprawnie odwczone. Ogranicz użycie koloru do tej palety lub uzyskasz nieprzewidywalne wyniki po zastosowaniu inwersji.

 ![Przykłady ikon, których kolory zostały odwrócone](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Przykłady ikon, których kolory zostały odwrócone

### <a name="base-palette"></a>Paleta bazowa
 Wszystkie standardowe ikony zawierają trzy kolory podstawowe. Ikony nie zawierają gradientów ani cieni, z jednym lub dwoma wyjątkami dla ikon narzędzi 3D.

|Sposób użycia|Nazwa|Wartość (kompozycja Światło)|Próbkę|Przykład|
|-----------|----------|---------------------------|------------|-------------|
|Tło/ciemność|VS BG|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład palety bazowej](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Pierwszy plan/światło|VS FG|F0EFF1 / 240 239 241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Kontur|Vs wyjście|F6F6F6 / 246 246 246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oprócz kolorów bazowych każda ikona może zawierać jeden dodatkowy kolor z rozszerzonej palety.

### <a name="extended-palette"></a>Rozszerzona paleta

#### <a name="action-modifiers"></a>Modyfikatory akcji
 Poniższe cztery kolory wskazują typy akcji wymaganych przez modyfikatory akcji:

|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Dodatnie|VS Działanie Zielony|388A34 / 56 138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Ujemne|VS Akcja Czerwony|A1260D / 161,38,13|![Próbka A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS Działanie Niebieski|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Utwórz/Nowy|VS Akcja Pomarańczowy|C27D1A / 194 156,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Przykłady
 Zielony jest używany do modyfikatorów akcji pozytywnych, takich jak "Dodaj", "Uruchom", "Odtwórz" i "Sprawdź poprawność".

|||||
|-|-|-|-|
|![Ikona Uruchom](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Run|![Ikona Wykonywanie kwerendy](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Wykonanie kwerendy|![Ikona Odtwórz wszystkie kroki](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Zagraj we wszystkie kroki|![Ikona Dodaj formant](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Dodaj formant|

 Czerwony jest używany dla modyfikatorów akcji negatywnych, takich jak "Usuń", "Zatrzymaj", "Anuluj" i "Zamknij".

|||||
|-|-|-|-|
|![Ikona Usuń relację](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Usuwanie relacji|![Ikona Usuń kolumnę](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Usuń kolumnę|![Ikona Zatrzymaj kwerendę](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Zatrzymaj kwerendę|![Ikona Połączenie w trybie offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Połączenie w trybie offline|

 Niebieski jest stosowany do modyfikatorów akcji neutralnych najczęściej reprezentowanych jako strzałki, takie jak "Otwórz", "Następny", "Poprzedni", "Import" i "Eksport".

|||||
|-|-|-|-|
|![Przejdź do ikony pola](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Przejdź do pola|![&#45;sprawdzania wsadowego w ikonie](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Odprawa wsadowa|![Ikona edytora adresów](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Edytor adresów|![Ikona edytora skojarzenia](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Edytor skojarzeń|

 Ciemne złoto jest używane przede wszystkim do modyfikatora "Nowy".

|||||
|-|-|-|-|
|![Ikona nowego projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Nowy projekt|![Tworzenie nowej ikony wykresu](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Tworzenie nowego wykresu|![Nowa ikona testu jednostkowego](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Nowy test jednostkowy|![Ikona nowego elementu listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Nowy element listy|

#### <a name="special-cases"></a>Specjalne przypadki
 W szczególnych przypadkach modyfikator akcji kolorowych może być używany niezależnie jako ikona autonomiczna. Kolor używany dla ikony odzwierciedla akcje, z którymi jest skojarzona ikona. To użycie jest ograniczone do niewielkiego podzbioru ikon, w tym:

||||||
|-|-|-|-|-|
|![Ikona Uruchom](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Run|![Ikona Stop](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Stop|![Ikona Usuń](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Usuń|![Ikona zapisywania](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Zapisz|![Ikona nawigowania wstecz](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Nawiguj wstecz|

### <a name="code-hierarchy-palette"></a>Paleta hierarchii kodu

#### <a name="folder"></a>Folder

|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|Przykład|
|-----------|----------|--------------------------|------------|-------------|
|Foldery|Folder|DCB67A / 220 182 122|![Próbka DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona koloru folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Języki programu Visual Studio
 Każdy ze wspólnych języków lub platform dostępnych w programie Visual Studio ma skojarzony kolor. Kolory te są używane na ikonie podstawowej lub na modyfikatorach języka, które pojawiają się w prawym górnym rogu ikon złożonych.

|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Niebieski|0095D7 / 0,149,215|![Próbka 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Fioletowy|9B4F96 / 155 79 150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Zielony (VS Działanie Zielony)|388A34 / 56 138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Czerwony|BD1E2D / 189,30,45|![Próbka BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Fioletowy|672878 / 103,40,120|![Próbka 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Pomarańczowy|F16421 / 241 100,33|![Próbka F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Niebieski (VS Niebieski)|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Pomarańczowy|E04C06 / 224 76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Zielony|879636 / 135,150,54|![Próbka 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z modyfikatorami języka

|||||||
|-|-|-|-|-|-|
|![Ikona języka Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![Ikona&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![Ikona&#43;&#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Ikona języka JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Ikona języka Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Ikona programu ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Ikona typescript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Ikony IntelliSense używają ekskluzywnej palety kolorów. Kolory te są używane, aby pomóc użytkownikom szybko rozróżnić różne elementy na liście popup IntelliSense.

|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Klasa, Wydarzenie|VS Akcja Pomarańczowy|C27D1A / 194 125,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metoda rozszerzenia, metoda, moduł, delegat|VS Akcja Fioletowy|652D90 / 101,45,144|![Próbka 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Pole, Element wyliczenia, Makro, Struktura, Typ wartości Unii, Operator, Interfejs|VS Działanie Niebieski|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Obiekt|VS Działanie Zielony|388A34 / 56 138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Stała, Wyjątek, Element wyliczenia, Mapa, Element mapy, Obszar nazw, Szablon, Definicja typu|Tło (VS BG)|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Przykłady ikon IntelliSense

||||||
|-|-|-|-|-|
|![Ikona klasy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Klasa|![Ikona prywatnego wydarzenia IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Wydarzenie prywatne|![Ikona pełnomocnika programu IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Delegate|![Ikona znajomego metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Przyjaciel metody|![Ikona Pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Pole|
|![Ikona chronionego wyliczenia IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Chroniony element wyliczenia|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Obiekt|![Ikona szablonu intellisense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Szablon|![Ikona skrótu wyjątku IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Skrót wyjątku||

### <a name="notifications"></a>Powiadomienia
 Powiadomienia w programie Visual Studio są używane do wskazywania stanu. Paleta powiadomień używa następujących czterech kolorów, a także opcji wypełnienia na pierwszym planie w kolorze czarnym lub białym, aby zdefiniować powiadomienia z następującymi poziomami stanu.

|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|----------|--------------------------|------------|
|Status: neutralny|Powiadomienie niebieski (VS niebieski)|1BA1E2 / 27 161 226|![Próbka 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Status: pozytywny|Zielony powiadomień (VS Zielony)|339933 / 51,153,51|![Próbka 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Status: ujemny|Czerwony powiadomienie (VS Czerwony)|E51400 / 229 20,0|![Próbka E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Status: ostrzeżenie|Powiadomienie żółty (VS Pomarańczowy)|FFCC00 / 255 204,0|![Próbka FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Wypełnienie pierwszego planu|Powiadomienie czarny (czarny)|000000 / 0,0,0|![Próbka &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Wypełnienie pierwszego planu|Biały powiadomień (biały)|FFFFFF / 255 255 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Przykłady ikon powiadomień

|||||
|-|-|-|-|
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Alerty|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Ostrzeżenie|![Ikona Kompletny](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Complete|![Ikona Stop](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Stop|

### <a name="visual-studio-online"></a>Visual Studio Online
 Ogólnie rzecz biorąc Visual Studio Online składa się z funkcji hostowanych w przeglądarce. Kolor zmienia się w różnych środowiskach, ale styl pozostaje taki sam.

|Grupa|Sposób użycia|Nazwa|Wartość (wszystkie motywy)|Próbkę|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Tło|TFSO BG|656565/ 101, 101, 101|![Próbka 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Kontur|TFSO NA ZEWNĄTRZ|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monako|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normalne|F12 Grey_Primary|555555 / 85, 85, 85|![Próbka 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Aktywowane|F12 Blue_Hover|2279BF / 34 121 191|![Próbka 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Disabled (Wyłączony)|F12 LtGrey_Disabled|ABABAC / 171 171 172|![Swatch ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Najedź za tłem|Hover bg|D9EBF7 / 217,235,247|![Próbka D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Wciśnięty tło|Wciśnięty bg|B2D7F0 / 178 215 240|![Próbka B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Kontur|VS NA ZEWNĄTRZ|F6F6F6 / 246 246 246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Informacje|Informacje|00BCF2 / 0,188,242|![Próbka 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Ostrzeżenie|Ostrzeżenie|F28300 / 242 131,0|![Próbka F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Błąd / Wartość ujemna|Error_Negative|E81123 / 232 17,35|![Swatch E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Początek / Pozytywny|Start_Positive|009E49 / 0,158,73|![Próbka 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Typ przerwania|Typ przerwania|9B4F96 / 155 79 150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Oznacz zdarzenie|Oznacz zdarzenie|A51F00 / 165,31,0|![Próbka A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Oznaczyć użytkownika|Oznaczyć użytkownika|F16220 / 241,98,32|![Próbka F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Przykłady ikon usługi Visual Studio Online

|TFS Online||||
|----------------|-|-|-|
|![Ikona zespołu TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Zespół online|![Ikona informacji TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Informacje|![Ikona historii TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Historia|![Ikona gałęzi TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Odgałęzienie|

|Napa||||
|----------|-|-|-|
|![Ikona zawartości napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Zawartość|![Ikona poczty biurowej Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Poczta pakietu Office|![Ikona programu Napa SharePoint](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Ikona okienka zadań Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Okienko zadań|

|Monako||||
|------------|-|-|-|
|![Ikona plików Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Pliki|![Ikona aplikacji Monaco Git](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Ikona wyszukiwania w Monako](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Wyszukiwanie|![Ikona tekstu Monako](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Tekst|

|F12|||
|---------|-|-|
|![F12 ładna ikona kodu](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Ładny kod|![Ikona ostrzeżenia F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Ostrzeżenie|![Ikona emulacji F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Emulować|