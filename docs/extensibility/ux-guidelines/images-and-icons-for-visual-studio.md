---
title: Obrazy i ikony dla programu Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409251"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazy i ikony dla programu Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a>Używanie obrazów w programie Visual Studio
 Przed utworzeniem kompozycji należy rozważyć użycie 1000 obrazów w [bibliotece obrazów programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Typy obrazów

- **Ikony**. Małe obrazy, które pojawiają się w poleceń, hierarchii, szablonów i tak dalej. Domyślny rozmiar ikony używane w programie Visual Studio jest PNG 16 x 16. Automatycznie generowane przez usługę obraz ikony Generowanie formacie XAML obsługi HDPI.

    > [!NOTE]
    > Gdy obrazy są używane w systemie menu, nie należy tworzyć ikon dla każdego polecenia. Zapoznaj się z [menu i poleceniami dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) , aby sprawdzić, czy polecenie powinno uzyskać ikonę.

- **Miniaturk.** Obrazy używane w obszarze (wersja zapoznawcza) okno dialogowe, takich jak okna dialogowego Nowy projekt.

- **Obrazy okna dialogowego.** Obrazy, które są wyświetlane w oknach dialogowych lub kreatory, jako opisowy grafiki lub wskaźników wiadomości. Użyj rzadko i tylko wtedy, gdy jest to niezbędne do zilustrowanie koncepcji trudne lub uzyskania uwagi użytkownika (alertów, ostrzeżenie).

- **Obrazy animowane.** Używane w wskaźniki postępu, paski stanu oraz operacji w oknach dialogowych.

- **Mało.** Służy do wskazania, czy operacja jest dozwolona przy użyciu myszy, gdy obiekt mogą zostać odrzucone i tak dalej.

## <a name="BKMK_IconDesign"></a>Projektowanie ikon

### <a name="overview"></a>Omówienie
 Visual Studio używa współczesny styl ikony, które geometrii czyste i 50/50 saldo plus/minus (jasny/ciemny) i użyj metafory bezpośrednie i zrozumiałej. Ikona kluczowe znaczenie podczas projektowania Centrum punktów wokół uściślenia i uproszczenie i kontekstu.

- **Przejrzystość:** koncentrowanie się na podstawowym metaphor, który zapewnia ikonę i jej znaczenie.

- **Uproszczenie:** Zmniejsz liczbę ikon do jej podstawy, aby uzyskać motyw w przypadku tylko niezbędnych elementów i nie Frills.

- **Kontekst:** należy wziąć pod uwagę wszystkie aspekty roli ikony podczas tworzenia koncepcji, które są decydujące podczas decydowania o tym, które elementy stanowią podstawowe metaphor ikon.

  Za pomocą ikony istnieje kilka punktów zaprojektowanych w celu uniknięcia:

- Nie należy używać ikony, które oznaczają elementy interfejsu użytkownika, z wyjątkiem sytuacji, gdy jest to konieczne. Wybierz podejście bardziej abstrakcyjne lub symbolicznych, gdy element interfejsu użytkownika nie jest wspólnego, wyraźne, ani unikatowy.

- Nie nadużyciami wspólnych elementów, takich jak dokumenty, folderów, strzałki i ikonę lupy. Za pomocą tych elementów tylko wtedy, gdy jest to istotne znaczenie ikony. Na przykład szkła powiększającego skierowaną w prawo powinna być widoczna tylko wyszukiwanie, przeglądanie i znajdowanie.

- Mimo że niektóre elementy starsza wersja ikony Obsługa korzystanie z punktu widzenia, nie należy tworzyć nowe ikony z punktu widzenia, chyba że element nie posiada przejrzystości bez niego.

- Nie zwiększały zbyt dużej ilości informacji do ikony. Proste obrazu, który można łatwo rozpoznane lub rozpoznane jako symbol separatora rozpoznawalnych jest znacznie bardziej przydatne niż obraz zbyt skomplikowana. Ikona nie przekazuje wszystkich informacji.

### <a name="icon-creation"></a>Ikona tworzenia

#### <a name="concept-development"></a>Pojęcia programowania
 Visual Studio ma w jego interfejsie użytkownika szerokiej gamy typy ikon. Podczas tworzenia, zastanów się ikoną typu. Nie używaj niejasna lub rzadko obiektów interfejsu użytkownika dla elementów ikony. Zoptymalizowany pod kątem dla symbolicznych w takich przypadkach, takich jak ikoną tagu inteligentnego. Należy zwrócić uwagę na to, że znaczenie abstrakcyjne tagu po lewej stronie jest bardziej oczywisty niż wersja niejasne, oparty na interfejsie użytkownika po prawej stronie:

|||
|-|-|
|**Poprawne użycie obrazów symbolicznych**|**Nieprawidłowe użycie obrazów symbolicznych**|
|![Popraw ikonę tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Nieprawidłowa ikona tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Istnieją sytuacje, w których standardowe, łatwo rozpoznawalną elementy interfejsu użytkownika będą działać dobrze w przypadku ikony. Dodaj, że okno jest jednym z przykładów:

|||
|-|-|
|**Prawidłowy element interfejsu użytkownika w ikonie**|**Nieprawidłowy element UI w ikonie**|
|![Popraw ikonę okna dodawania](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Niepoprawna ikona dodawania okna](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Nie używaj dokumentu jako elementu podstawowego, chyba że jest to istotne znaczenie ikony. Bez dokumentu elementu Dodawanie dokumentu (patrz poniżej) znaczenie zostało utracone lub z odświeżaniem nie trzeba przekazywać znaczenie jest element dokumentu.

|||
|-|-|
|**Poprawne użycie ikony dokumentu**|**Nieprawidłowe użycie ikony dokumentu**|
|![Ikona poprawnego dokumentu](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Niepoprawna ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Pojęcie "Pokaż" powinna być reprezentowana przez ikonę, która najlepiej ilustruje, co jest pokazywane, takie jak w przykładzie Pokaż wszystkie pliki. Metafora obiektywu mogą służyć do wskazania koncepcji "view", jeśli to konieczne, takie jak w przykładzie widok zasobów.

|||
|-|-|
|**Wskazują**|**Widokiem**|
|![Pokaż ikonę](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Ikona widoku](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Skierowaną w prawo powiększanie ikonę szkła powinien reprezentują tylko wyszukiwania, wyszukiwania i przeglądania. Wariant skierowaną w lewo przy użyciu znaku plus lub minus powinien reprezentować tylko powiększanie / pomniejszyć.

|||
|-|-|
|**Wyszukiwania**|**Zmieniać**|
|![Ikona wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 W widokach drzewa nie używaj ikonę folderu i modyfikujący. Jeśli jest dostępna, należy użyć tylko modyfikator.

|||
|-|-|
|**Popraw ikony widoku drzewa**|**Nieprawidłowe ikony widoku drzewa**|
|![Ikona &#40;poprawnego widoku&#41; drzewa 1](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![poprawna ikona &#40;widoku drzewa 2&#41; ](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Nieprawidłowa ikona &#40;widoku drzewa 1&#41; ](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![nieprawidłowa ikona &#40;widoku drzewa 2&#41; ](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Szczegóły dotyczące stylu

#### <a name="layout"></a>Układ
 Elementy stosu pokazany dla standardowych ikon 16 x 16:

 ![Stos układu dla ikon 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Stos układu dla ikon 16x16

 Stan powiadomienia elementów, są lepiej używane jako ikony autonomicznych. Istnieją kontekstów, jednak, w których powiadomienie powinny być skumulowany elementu podstawowego, takie jak ikoną zadanie ukończone:

 ![Powiadomienia autonomiczne w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Ikony powiadomień autonomicznych

 ![Ikona ukończenia zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Ikona ukończenia zadania

 Ikony projektu zazwyczaj są to pliki .ico, które zawierają wiele rozmiarów. Większość ikony 16 x 16 zawierają te same elementy. Wersje 32 x 32 mają więcej szczegółów, w tym typem projektu, jeśli ma to zastosowanie.

 ![Ikony projektu w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Ikony projektu biblioteki formantów systemu Windows w języku VB, 16x16 i 32x32

 Wyśrodkuj ikonę wewnątrz ramki pikseli. Jeśli nie jest to możliwe, należy wyrównać ikonę u góry i/lub prawo do ramki.

 ![Ikona wyśrodkowana w obrębie ramki pikseli](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Ikona wyśrodkowana w obrębie ramki pikseli

 ![Ikona wyrównany do prawej górnej krawędzi ramki pikseli](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Ikona wyrównany do prawej górnej krawędzi ramki

 ![Ikona wyśrodkowana i wyrównana do góry ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ikona wyśrodkowana i wyrównana do góry ramki

 Uzyskanie idealne wyrównanie i saldo, należy unikać nie utrudnia działania generatora ikony elementu base przy użyciu akcji symbole. Umieść symbol w prawym górnym lewym rogu elementu podstawowego. Podczas dodawania dodatkowy element, należy wziąć pod uwagę wyrównanie i saldo ikony.

|||
|-|-|
|**Prawidłowe wyrównanie i balans**|**Nieprawidłowe wyrównanie i balans**|
|![Poprawne saldo i wyrównanie ikony](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Nieprawidłowe saldo i wyrównanie ikony](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Upewnij się, parzystości rozmiar ikon, elementy, które są używane w zestawach. Należy pamiętać, że w niepoprawne parowanie kółko i Strzałka są zbyt duże i nie są zgodne.

|||
|-|-|
|**Popraw parzystość rozmiaru**|**Niepoprawna parzystość rozmiaru**|
|![Prawidłowy rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Nieprawidłowy rozmiar ikony i parzystość](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Za pomocą spójnego linii i wagi visual. Należy ocenić, jak ikony, którą tworzysz porównuje z innymi ikonami przy użyciu porównania side-by-side. Nigdy nie używaj całe ramki 16 x 16, użyj 15 x 15 lub mniejsze. Ujemna — pozytywny stosunek (dark światła) powinna być 50/50.

|||
|-|-|
|**Popraw współczynnik negatyw-do-dodatni**|**Nieprawidłowy stosunek negatywny do wartości dodatniej**|
|![Popraw grubość wizualną dla &#40;ikon 1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Popraw grubość wizualną dla &#40;ikon 2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Popraw grubość wizualną dla &#40;ikon 3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Nieprawidłowa grubość wizualizacji dla ikon](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Do tworzenia elementów bez obniżania oczekiwanego poziomu integralności elementu, należy użyć prostego, porównywalnych kształty i dopełniający kąty. Jeśli jest to możliwe, należy użyć 45 stopni lub 90° kąty.

 ![Poprawne kąty ikon](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektywa
 Zachowaj ikonę czytelne i zrozumiałe. Za pomocą perspektywy i źródła światła, tylko wtedy, gdy jest to konieczne. Chociaż należy unikać ikony elementów przy użyciu perspektywy, niektóre elementy są nierozpoznawalną bez niego. W takich przypadkach stylizowane perspektywy komunikuje się w celu uściślenia elementu.

 ![perspektywa 3-punktowa](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />perspektywa 3-punktowa

 ![perspektywa 1 punktu](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />perspektywa 1 punktu

 Większość elementów powinna mieć wartość równą lub skierowaną do prawej:

 ![Ikony ukośnie w prawo](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Użyj źródła światła, tylko wtedy, gdy dodawanie przejrzystości niezbędne do obiektu.

|||
|-|-|
|**Prawidłowe Źródło światła**|**Nieprawidłowe źródło światła**|
|![Poprawne źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Nieprawidłowe źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Użyj wskazano, tylko w celu zwiększenia czytelności lub lepszej komunikacji metaphor. Wynik dodatni ujemna saldo (dark-light) powinna być 50/50.

|||
|-|-|
|**Poprawne użycie konspektów**|**Nieprawidłowe użycie konspektów**|
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

 ![Przykłady ikon IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Przykłady ikony IntelliSense

 **Małe (16x16) ikony projektu** nie mogą zawierać więcej niż dwóch elementów: jeden modyfikator podstawowy i jeden.

 ![Przykłady małych (16x16) ikon projektu](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 Project ikona &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 projektu ikona 3&#41; &#40;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Przykłady małych (16x16) ikon projektu

 **Duże (32x32) ikony projektu** składają się z nie więcej niż czterech następujących elementów: jeden Base, jeden do dwóch modyfikatorów i jedną nakładkę języka.

 ![Przykłady dużych ikon projektu (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Przykłady dużych ikon projektu (32x32)

### <a name="production-details"></a>Szczegółów dotyczących środowiska produkcyjnego
 Wszystkie nowe elementy interfejsu użytkownika powinny być tworzone przy użyciu Windows Presentation Foundation (WPF), a wszystkie nowe ikony WPF powinna mieć format PNG 32-bitowych. Format PNG 24-bitowego jest starszego formatu, który nie obsługuje przezroczystości i dlatego nie jest zalecana dla ikon.

 Zapisz rozdzielczości 96 DPI.

#### <a name="file-types"></a>Typy plików

- **32-bitowy PNG:** preferowany format dla ikon. Dane bezstratne kompresji formacie, który może przechowywać obraz rastrowych pojedynczego (w pikselach). 32-bitowe pliki PNG obsługują kanał alfa przezroczystości, korekcja gamma i przeplotu.

- **32-bitowy BMP:** dla formantów innych niż WPF. Jest określana skrótem XP lub trybie high color, 32-bitowych BMP jest ma format obrazu RGB/A obrazem true kolor z przezroczystością kanał alfa. Kanał alfa jest warstwą przejrzystości umieszczoną w programie Adobe Photoshop, który następnie jest zapisywany w obrębie mapy bitowej jako dodatkowe (czwarty) kanału koloru. Czarne tło jest dodawany podczas produkcji kompozycji do wszystkich plików BMP 32-bitowych, aby zapewnić szybkie wizualną o głębi kolorów. To czarne tło reprezentuje obszar maskowane się w interfejsie użytkownika.

- **32-bit ICO:** w przypadku ikon projektu i dodania elementu. Wszystkie pliki ICO są true kolor 32-bitowy z przezroczystością kanał alfa (RGB/A). Ponieważ pliki ICO można przechowywać wiele wielkości i głębi kolorów, Vista ikony są często w formacie ICO zawierające 16 x 16, 32 x 32, 48 x 48 i rozmiary obrazów 256 x 256. Aby można było wyświetlać się poprawnie w Eksploratorze Windows, pliki ICO musi być zapisane w celu liczby 24-bitowego i 8-bitowych kolorów dla każdego rozmiaru obrazu.

- **XAML:** dla powierzchni projektowych i modułów definiowania układu systemu Windows. Ikony XAML są plików obrazu opartego na wektorach, które obsługują skalowanie, obracanie, przesyłanie i przejrzystości. Nie są obecnie często używany w programie Visual Studio, ale stają się coraz bardziej popularne ze względu na ich elastyczność.

- **FORMACIE**

- **24-bitowy BMP:** dla paska poleceń programu Visual Studio. Format obrazu true kolor RGB BMP 24-bitowego jest Konwencji ikonę, która tworzy warstwę przezroczystość przy użyciu amarantowy (R = 255, G = 0, B = 255) jako klucza kolorów dla warstwy przezroczystości przeciwstukowe w poziomie. W BMP 24-bitowego wszystkich powierzchni magenta są wyświetlane na kolor tła.

- **24-bitowy GIF:** dla paska poleceń programu Visual Studio. True — kolor RGB obraz formacie, który obsługuje przezroczystość. Pliki GIF są często używane w Kreatorze kompozycji i animacji GIF.

### <a name="icon-construction"></a>Ikona tworzenia
 Najmniejszy rozmiar ikony w programie Visual Studio jest 16 x 16. Największy wspólne użycie jest 32 x 32. Należy pamiętać, nie w celu wypełnienia całe ramki 16 x 16, 24 x 24 lub 32 x 32 podczas projektowania ikony. Konstrukcja czytelny, jednolity ikona jest niezbędne do rozpoznawania użytkownika. Podczas kompilowania ikony, należy stosować się do następujących punktów.

- Ikony powinny być jasne, do zrozumienia i spójne.

- Zaleca się, użyj elementów powiadomień stanu jako pojedynczy ikony, a nie stosu je na górze ikonę elementu podstawowego. W niektórych kontekstach interfejsu użytkownika mogą wymagać elementu stanu, aby łączyć się z elementu podstawowego.

- Ikony projektu są zazwyczaj pliki .ico, które zawierają wiele rozmiarów. Trwa aktualizowanie tylko ikony 16 x 16, 24 x 24 oraz 32 × 32. Większość ikon 16 x 16 i 24 x 24 będzie zawierać te same elementy. Ikony 32 x 32 zawiera bardziej szczegółowe informacje, łącznie z typem języka projektu, jeśli ma to zastosowanie.

- Ikony 32 x 32 podstawowych elementów ma zazwyczaj grubość linii 2 pikseli. Grubość linii pikseli 1 lub 2 może służyć do szczegółów elementów. Zdrowym rozsądkiem najlepiej, aby określić, która jest bardziej odpowiednia.

- Ma co najmniej 1-pikselowe odstępy elementy dla 16 x 16 i 24 x 24 ikon. Ikony 32 x 32 można użyć w 2-pikselowe odstępy między elementami oraz między modyfikator i elementu podstawowego.

  ![Odstępy między elementami ikon o rozmiarze 16x16, 24x24 i 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Odstępy między elementami ikon o rozmiarze 16x16, 24x24 i 32x32

#### <a name="color-and-accessibility"></a>Kolor i ułatwienia dostępu
 Wytycznych dotyczących zgodności programu Visual Studio wymagają, że wszystkie ikony w produkcie przekazywać wymagania dotyczące ułatwień dostępu dla koloru i kontrast. Jest to realizowane poprzez odwrócenie ikonę, a podczas projektowania, należy pamiętać, że będą one można programowo odwrócony w produkcie.

 Aby uzyskać więcej informacji na temat używania koloru w ikonach programu Visual Studio, zobacz [using Color in images](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Korzystanie z koloru w obrazach

### <a name="overview"></a>Omówienie
 Ikony w programie Visual Studio są głównie monochromatyczny. Kolor jest zarezerwowana do przekazywania określonych informacji i nigdy nie dla dekoracji. Kolor jest używany:

- Aby wskazać akcję

- aby ostrzec użytkownika powiadomienia o stanie

- Aby wyznaczyć przynależności języka

- do odróżniania elementów w obrębie funkcji IntelliSense

### <a name="accessibility"></a>Ułatwienia dostępu
 Wytycznych dotyczących zgodności programu Visual Studio wymagają, że wszystkie ikony zaznaczone pole wyboru do produktu — dostęp próbny wymagania dotyczące ułatwień dostępu dla koloru i kontrast. Kolory z palety języka visual zostały przetestowane i spełniają te wymagania.

#### <a name="color-inversion-for-dark-themes"></a>Odwracanie kolorów dla motywów ciemny
 Aby można było wprowadzić ikony są wyświetlane razem ze współczynnik kontrastu poprawne motywu ciemny programu Visual Studio, odwrócenie jest stosowany programowo. Kolory, w tym przewodniku zostały wybrane w części, aby ich Odwróć poprawnie. Ograniczanie kolorów do tej palety, lub może dawać nieoczekiwane wyniki, po zastosowaniu odwrócenie.

 ![Przykłady ikon, dla których zostały odwrócone kolory](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 — 01_DarkThemeInversion")<br />Przykłady ikon, dla których zostały odwrócone kolory

### <a name="base-palette"></a>Paleta podstawowa
 Wszystkich standardowych ikon zawiera trzy kolory podstawowej. Ikony zawierają nie gradientach lub cienie, z co najmniej dwa wyjątki dla ikony narzędzia 3D.

|Sposób użycia|Name (Nazwa)|Wartość (motyw jasny)|Próbki|Przykład|
|-----------|----------|---------------------------|------------|-------------|
|Tło/ciemny|VS BG|424242 / 66,66,66|![Próbnik 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład palety podstawowej](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 — 02_BasePaletteExample")|
|Pierwszy plan/lekki|VS FG|F0EFF1 / 240,239,241|![F0EFF1 próbki](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Kontur|VS Out|F6F6F6 / 246,246,246|![F6F6F6 próbki](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Oprócz podstawowego kolory każda ikona może zawierać jeden dodatkowe kolor z palety rozszerzonej.

### <a name="extended-palette"></a>Rozszerzone palety

#### <a name="action-modifiers"></a>Modyfikatory akcji
 Cztery kolory poniżej wskazują typy akcji związanej z Modyfikatory akcji:

|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|
|-----------|----------|--------------------------|------------|
|Dodatnie|Zielony akcji programu VS|388A34 / 56,138,52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Ujemne|Czerwony akcji programu VS|A1260D / 161,38,13|![A1260D próbki](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Niezależny od|Niebieski akcji programu VS|00539C / 0,83,156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Utwórz nową|Pomarańczowy akcji programu VS|C27D1A / 194,156,26|![C27D1A próbki](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Przykłady
 Zielony jest używany dla modyfikatorów akcji pozytywnych, takich jak "Add", "Run", "Play" i "Validate".

|||||
|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 — 03_ActionModifierRun")<br />Uruchom polecenie|![Ikona wykonywania zapytania](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 — 04_ExecuteQuery")<br />Wykonaj zapytanie|![Ikona odtwarzania wszystkich kroków](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 — 05_PlayAllSteps")<br />Odtwórz wszystkie kroki|![Dodaj ikonę kontrolki](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 — 06_AddControl")<br />Dodaj kontrolkę|

 Czerwony jest używany dla modyfikatorów akcji ujemnych, takich jak "Delete", "Stop" "Cancel" i "Close".

|||||
|-|-|-|-|
|![Ikona usuwania relacji](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 — 07_DeleteRelationship")<br />Usuwanie relacji|![Ikona usuwania kolumny](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 — 08_DeleteColumn")<br />Usuń kolumnę|![Ikona zatrzymania zapytania](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 — 09_StopQuery")<br />Zatrzymaj zapytanie|![Ikona połączenia w trybie offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 — 10_ConnectionOffline")<br />Połączenie w trybie offline|

 Niebieska jest stosowana do modyfikatorów akcji neutralnych najczęściej reprezentowanych jako strzałki, takich jak "Open", "dalej" "Previous", "Import" i "Export".

|||||
|-|-|-|-|
|![Ikona przejdź do pola](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 — 11_GoToField")<br />Przejdź do pola|![Ikona ewidencjonowania&#45;wsadowego](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 — 12_BatchedCheckIn")<br />Wsadowe ewidencjonowanie|![Ikona edytora adresów](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 — 13_AddressEditor")<br />Edytor adresów|![Ikona edytora skojarzeń](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 — 14_AssociationEditor")<br />Edytor skojarzeń|

 Ciemny złoty jest używany głównie dla modyfikatora "New".

|||||
|-|-|-|-|
|![Ikona nowego projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 — 15_NewProject")<br />Nowy projekt|![Utwórz nową ikonę grafu](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 — 16_CreateNewGraph")<br />Utwórz nowy wykres|![Ikona nowego testu jednostkowego](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 — 17_NewUnitTest")<br />Nowy test jednostkowy|![Ikona nowego elementu listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 — 18_NewListItem")<br />Nowy element listy|

#### <a name="special-cases"></a>Specjalne przypadki
 W szczególnych przypadkach modyfikator kolorowe akcji może używać niezależnie jako ikona autonomicznych. Kolor ikony odzwierciedla akcje, które ikonę jest skojarzony. To użycie jest ograniczone do małego podzbioru ikony, w tym:

||||||
|-|-|-|-|-|
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 — 03_ActionModifierRun")<br />Uruchom polecenie|![Ikona zatrzymania](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 — 19_Stop")<br />Stop|![Ikona usuwania](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 — 20_Delete")<br />Usuń|![Ikona zapisywania](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 — 21_Save")<br />Zapisz|![Ikona nawigacji Wstecz](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 — 22_NavigateBack")<br />Nawiguj wstecz|

### <a name="code-hierarchy-palette"></a>Kod hierarchii palety

#### <a name="folder"></a>Folder

|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|Przykład|
|-----------|----------|--------------------------|------------|-------------|
|Foldery|Folder|DCB67A / 220,182,122|![DCB67A próbki](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona koloru folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 — 23_FolderColor")|

#### <a name="visual-studio-languages"></a>Języki Visual Studio
 Każda z typowych języków lub platform dostępne w programie Visual Studio ma kolor skojarzony. Te kolory na ikonie podstawowej lub nad modyfikatorami języka, które pojawiają się w prawym górnym rogu złożone ikony.

|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|Niebieski HTML WPF ASP|0095D 7 / 0,149,215|![0095D7 próbki](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Purpurowy CPP|9B4F96 / 155,79,150|![9B4F96 próbki](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|Zielony CS (zielony akcji programu VS)|388A34 / 56,138,52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Czerwony CSS|BD1E2D / 189,30,45|![BD1E2D próbki](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Purpurowy FS|672878 / 103,40,120|![Próbnik 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Pomarańczowy JS|F16421 / 241,100,33|![F16421 próbki](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|Niebieski VB (niebieski akcji programu VS)|00539C / 0,83,156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Pomarańczowy usług terminalowych|E04C06 / 224,76,6|![E04C06 próbki](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Zielony PY|879636 / 135,150,54|![Próbnik 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z modyfikatorów języka

|||||||
|-|-|-|-|-|-|
|![Ikona Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 — 25_VB")<br />VB|![Ikona&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 — 26_CSharp")<br />C#|![Ikona&#43; &#43; C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 — 27_CPlusPlus")<br />C++|![Ikona&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 — 28_FSharp")<br />F#|![Ikona JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 — 29_JavaScript")<br />JavaScript|![Ikona języka Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 — 30_Python")<br />Python|
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 — 31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 — 32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 — 33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 — 34_CSS")<br />CSS|![Ikona języka TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 — 35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Ikony IntelliSense Użyj palety kolorów wyłączności. Te kolory pomagają użytkownikom szybko odróżnić różne elementy na liście menu podręczne IntelliSense.

|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|
|-----------|----------|--------------------------|------------|
|Klasa zdarzenia|Pomarańczowy akcji programu VS|C27D1A / 194,125,26|![C27D1A próbki](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Metody rozszerzenia, delegat metody i modułu|Purpurowy akcji programu VS|652D 90 / 101,45,144|![652D90 próbki](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Pole elementu wartości wyliczeniowej, — makro, struktury, typ wartości Union, Operator, interfejs|Niebieski akcji programu VS|00539C / 0,83,156|![00539C próbki](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Obiekt|Zielony akcji programu VS|388A34 / 56,138,52|![388A34 próbki](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Stałe, wyjątków, elementu wartości wyliczeniowej, mapy, elementu mapy, Namespace, szablon, definicja typu|W tle (VS BG)|424242 / 66,66,66|![Próbnik 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Przykłady ikony IntelliSense

||||||
|-|-|-|-|-|
|![Ikona klasy IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 — 36_IntelliSenseClass")<br />Klasa|![Ikona prywatnego zdarzenia IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 — 37_IntelliSensePrivateEvent")<br />Wydarzenie prywatne|![Ikona delegata IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 — 38_IntelliSenseDelegate")<br />Delegate|![Ikona zaprzyjaźnionej metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 — 39_IntelliSenseMethodFriend")<br />Metoda zaprzyjaźniona|![Ikona pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 — 40_Field")<br />Pole|
|![Ikona elementu Enum chronionego przez funkcję IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 — 41_IntelliSenseProtectedEnumItem")<br />Chroniony element Enum|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 — 42_IntelliSenseObject")<br />Obiekt|![Ikona szablonu IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 — 43_IntelliSenseTemplate")<br />Szablon|![Ikona skrótu wyjątku IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 — 44_IntelliSenseExceptionShortcut")<br />Skrót wyjątku||

### <a name="notifications"></a>Powiadomienia
 Powiadomienia w programie Visual Studio są używane do wskazania stanu. Paleta powiadomień używa następujące cztery kolory, a także Opcje wypełnienia czarne lub białe pierwszego planu, w celu zdefiniowania powiadomień za pomocą następujących poziomów stanu.

|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|
|-----------|----------|--------------------------|------------|
|Stan: neutralny|Niebieski powiadomień (VS niebieski)|1BA1E2 / 27,161,226|![1BA1E2 próbki](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Stan: dodatnią|Zielony powiadomień (kolor zielony VS)|339933 / 51,153,51|![Próbnik 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Stan: ujemna|Powiadomienie Red (czerwony VS)|E51400 / 229,20,0|![E51400 próbki](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Stan: ostrzeżenie|Żółty powiadomień (kolor pomarańczowy VS)|FFCC00 / 255,204,0|![FFCC00 próbki](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Wypełnienie pierwszego planu|Powiadomienie czarny (czarny)|000000 / 0,0,0|![000000 &#35;próbki](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Wypełnienie pierwszego planu|Powiadomienie biały (biały)|FFFFFF / 255,255,255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Przykłady ikony powiadomień

|||||
|-|-|-|-|
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 — 45_Alert")<br />Alerty|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 — 48_Warning")<br />Ostrzeżenie|![Ikona ukończenia](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 — 46_Complete")<br />Complete|![Ikona zatrzymania](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 — 47_Stop")<br />Stop|

### <a name="visual-studio-online"></a>Visual Studio Online
 Ogólnie rzecz biorąc Visual Studio Online zawiera funkcje obsługiwane w przeglądarce. Kolor zmienia się w różnych środowiskach, ale styl pozostają bez zmian.

|Grupa|Sposób użycia|Name (Nazwa)|Wartości (wszystkie motywy)|Próbki|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Tło|TFSO BG|656565/ 101, 101, 101|![Próbnik 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Kontur|TFSO OUT|FFFFFF / 255, 255, 255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Narzędzia Napa|Tło|Biały|FFFFFF / 255, 255, 255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monaco|Tło|Biały|FFFFFF / 255, 255, 255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Tło|Biały|FFFFFF / 255, 255, 255|![FFFFFF próbki](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normalne|F12 Grey_Primary|555555 / 85, 85, 85|![Próbnik 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Po wskazaniu wskaźnikiem|F12 Blue_Hover|2279BF / 34,121,191|![2279BF próbki](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Disabled (Wyłączony)|F12 LtGrey_Disabled|ABABAC / 171,171,172|![ABABAC próbki](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Tło|Zatrzymaj wskaźnik myszy bg|D9EBF7 / 217,235,247|![D9EBF7 próbki](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Po naciśnięciu tła|Po naciśnięciu bg|B2D7F0 / 178,215,240|![B2D7F0 próbki](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Kontur|VS OUT|F6F6F6 / 246,246,246|![F6F6F6 próbki](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Informacje|Informacje|00BCF2 / 0,188,242|![00BCF2 próbki](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Ostrzeżenie|Ostrzeżenie|F28300 / 242,131,0|![F28300 próbki](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Błąd / ujemna|Error_Negative|E81123 / 232,17,35|![E81123 próbki](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Start / dodatnią|Start_Positive|009E49 / 0,158,73|![009E49 próbki](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Typ podziału|Typ podziału|9B4F96 / 155,79,150|![9B4F96 próbki](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Znacznik zdarzenia|Znacznik zdarzenia|A51F00 / 165,31,0|![A51F00 próbki](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Znacznik użytkownika|Znacznik użytkownika|F16220 / 241,98,32|![F16220 próbki](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Przykłady ikony programu Visual Studio Online

|TFS Online||||
|----------------|-|-|-|
|![Ikona zespołu usługi TFS online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 — 49_TFSOnlineTeam")<br />Zespół online|![Ikona informacji TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 — 50_TFSInformation")<br />Informacje|![Ikona historii TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 — 51_TFSHistory")<br />Historia|![Ikona gałęzi TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 — 52_TFSBranch")<br />Odgałęzienie|

|Narzędzia Napa||||
|----------|-|-|-|
|![Ikona zawartości Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 — 53_NapaContent")<br />Zawartość|![Ikona poczty Napa Office](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 — 54_NapaOfficeMail")<br />Poczta biurowa|![Ikona programu SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 — 55_NapaSharePoint")<br />Sharepoint|![Ikona okienka zadań Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 — 56_NapaTaskPane")<br />Okienko zadań|

|Monaco||||
|------------|-|-|-|
|![Ikona plików Monako](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 — 57_MonacoFiles")<br />Pliki|![Ikona usługi Git w Monako](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 — 58_MonacoGit")<br />Usługa Git|![Ikona wyszukiwania w Monako](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 — 59_MonacoSearch")<br />Wyszukiwanie|![Ikona tekstu Monako](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 — 60_MonacoText")<br />Tekst|

|F12|||
|---------|-|-|
|![Ikona klawisza F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 — 61_F12PrettyCode")<br />Kod całkiem|![Ikona ostrzeżenia o naciśnięciu klawisza F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 — 62_F12Warning")<br />Ostrzeżenie|![Ikona emulacji F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 — 63_F12Emulate")<br />Emulować|