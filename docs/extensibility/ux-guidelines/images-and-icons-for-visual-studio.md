---
title: Obrazy i ikony dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a49445445388a6db0e6dae9c09b50137c04c4ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954127"
---
# <a name="images-and-icons-for-visual-studio"></a>Obrazy i ikony dla programu Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a> Użyj obrazu w programie Visual Studio  
 Przed utworzeniem kompozycji, należy wziąć pod uwagę podejmowanie użycie obrazów ponad 1000 w [Visual Studio Image Library](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Typy obrazów  
  
-   **Ikony**. Małe obrazy, które pojawiają się w poleceń, hierarchii, szablonów i tak dalej. Domyślny rozmiar ikony używane w programie Visual Studio jest PNG 16 x 16. Automatycznie generowane przez usługę obraz ikony Generowanie formacie XAML obsługi HDPI.  
  
     **UWAGA:** Gdy obrazy są używane w systemie menu, nie należy tworzyć ikony dla każdego polecenia. Zapoznaj się z [menu i poleceń dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) aby zobaczyć, czy polecenie powinna pojawić się ikony.  
  
-   **Miniatury.** Obrazy używane w obszarze (wersja zapoznawcza) okno dialogowe, takich jak okna dialogowego Nowy projekt.  
  
-   **Okno dialogowe obrazów.** Obrazy, które są wyświetlane w oknach dialogowych lub kreatory, jako opisowy grafiki lub wskaźników wiadomości. Użyj rzadko i tylko wtedy, gdy jest to niezbędne do zilustrowanie koncepcji trudne lub uzyskania uwagi użytkownika (alertów, ostrzeżenie).  
  
-   **Obrazy animowany.** Używane w wskaźniki postępu, paski stanu oraz operacji w oknach dialogowych.  
  
-   **Kursory.** Służy do wskazania, czy operacja jest dozwolona przy użyciu myszy, gdy obiekt mogą zostać odrzucone i tak dalej.  
  
##  <a name="BKMK_IconDesign"></a> Ikony projektu  
  
### <a name="overview"></a>Omówienie  
 Visual Studio używa współczesny styl ikony, które geometrii czyste i 50/50 saldo plus/minus (jasny/ciemny) i użyj metafory bezpośrednie i zrozumiałej. Ikona kluczowe znaczenie podczas projektowania Centrum punktów wokół uściślenia i uproszczenie i kontekstu.  
  
- **W celu uściślenia:** skupić się na podstawowych metaphor, zapewniająca ikony jego znaczenie i indywidualizm.  
  
- **Uproszczenie:** zmniejszyć ikonę jego znaczenie core — Pobierz motyw tylko niezbędne elementy i nie frills.  
  
- **Kontekst:** należy wziąć pod uwagę wszystkie aspekty ról ikonę podczas tworzenia koncepcji, który jest kluczowy podczas podczas podejmowania decyzji o elementy, które stanowią metaphor core ikony.  
  
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
|**Prawidłowe użycie obrazów symboliczne**|**Niepoprawne użycie obrazów symboliczne**|  
|![Ikony jest poprawna tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![Nieprawidłowa ikona tagu inteligentnego](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 Istnieją sytuacje, w których standardowe, łatwo rozpoznawalną elementy interfejsu użytkownika będą działać dobrze w przypadku ikony. Dodaj, że okno jest jednym z przykładów:  
  
|||  
|-|-|  
|**Poprawny element interfejsu użytkownika w ikony**|**Nieprawidłowy element interfejsu użytkownika w ikony**|  
|![Poprawne ikona okno Dodawanie](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![Nieprawidłowa ikona okno Dodawanie](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 Nie używaj dokumentu jako elementu podstawowego, chyba że jest to istotne znaczenie ikony. Bez dokumentu elementu Dodawanie dokumentu (patrz poniżej) znaczenie zostało utracone lub z odświeżaniem nie trzeba przekazywać znaczenie jest element dokumentu.  
  
|||  
|-|-|  
|**Prawidłowe użycie ikony dokumentu**|**Niepoprawne użycie ikony dokumentu**|  
|![Ikony dokumentu jest poprawna](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Nieprawidłowa ikona dokumentu](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 Pojęcie "Pokaż" powinna być reprezentowana przez ikonę, która najlepiej ilustruje, co jest pokazywane, takie jak w przykładzie Pokaż wszystkie pliki. Metafora obiektywu mogą służyć do wskazania koncepcji "view", jeśli to konieczne, takie jak w przykładzie widok zasobów.  
  
|||  
|-|-|  
|**"Show"**|**"View"**|  
|![Pokaż ikonę](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![Ikona widoku](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|  
  
 Skierowaną w prawo powiększanie ikonę szkła powinien reprezentują tylko wyszukiwania, wyszukiwania i przeglądania. Wariant skierowaną w lewo przy użyciu znaku plus lub minus powinien reprezentować tylko powiększanie / pomniejszyć.  
  
|||  
|-|-|  
|**"Wyszukaj"**|**"Powiększ"**|  
|![Ikony wyszukiwania](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![Ikona powiększenia](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|  
  
 W widokach drzewa nie używaj ikonę folderu i modyfikujący. Jeśli jest dostępna, należy użyć tylko modyfikator.  
  
|||  
|-|-|  
|**Ikony poprawne drzewa**|**Nieprawidłowe drzewo ikony**|  
|![Ikona widoku drzewa poprawne &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![ikonę Widok drzewa poprawne &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Ikona widoku drzewa nieprawidłowa &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![ikonę Widok drzewa nieprawidłowa &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_ TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Szczegóły dotyczące stylu  
  
#### <a name="layout"></a>Układ  
 Elementy stosu pokazany dla standardowych ikon 16 x 16:  
  
 ![Układ stosu 16 x 16 ikon](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />Układ stosu dla ikon 16 x 16
  
 Stan powiadomienia elementów, są lepiej używane jako ikony autonomicznych. Istnieją kontekstów, jednak, w których powiadomienie powinny być skumulowany elementu podstawowego, takie jak ikoną zadanie ukończone:  
  
 ![Autonomiczny powiadomień w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />Ikony powiadomień autonomiczny
  
 ![Ikona zakończonego zadania](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />Ikona zakończonego zadania
  
 Ikony projektu zazwyczaj są to pliki .ico, które zawierają wiele rozmiarów. Większość ikony 16 x 16 zawierają te same elementy. Wersje 32 x 32 mają więcej szczegółów, w tym typem projektu, jeśli ma to zastosowanie.  
  
 ![Projekt ikony w programie Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />Projekt Biblioteka formantów Windows VB ikony, 16 x 16 i 32 x 32 
  
 Wyśrodkuj ikonę wewnątrz ramki pikseli. Jeśli nie jest to możliwe, należy wyrównać ikonę u góry i/lub prawo do ramki.  
  
 ![Ikona wyśrodkowana wewnątrz ramki pikseli](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />Ikona wyśrodkowana wewnątrz ramki pikseli
  
 ![Wyrównywana ikonę w prawym górnym rogu ramki pikseli](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />Ikona wyrównanym do górnej rogu ramki
  
 ![Ikona, a ich tematyka i wyrównane do górnej ramki pikseli](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />Ikona, a ich tematyka i wyrównanym do górnej ramki
  
 Uzyskanie idealne wyrównanie i saldo, należy unikać nie utrudnia działania generatora ikony elementu base przy użyciu akcji symbole. Umieść symbol w prawym górnym lewym rogu elementu podstawowego. Podczas dodawania dodatkowy element, należy wziąć pod uwagę wyrównanie i saldo ikony.  
  
|||  
|-|-|  
|**Wyrównanie poprawne i saldo**|**Nieprawidłowe wyrównanie i saldo**|  
|![Popraw ikonę informacji o saldach i wyrównanie](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Nieprawidłowa ikona informacji o saldach i wyrównanie](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 Upewnij się, parzystości rozmiar ikon, elementy, które są używane w zestawach. Należy pamiętać, że w niepoprawne parowanie kółko i Strzałka są zbyt duże i nie są zgodne.  
  
|||  
|-|-|  
|**Niepoprawny rozmiar parzystości**|**Niepoprawny rozmiar parzystości**|  
|![Popraw rozmiar ikon i parzystości](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Rozmiar ikony niepoprawne i parzystości](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 Za pomocą spójnego linii i wagi visual. Należy ocenić, jak ikony, którą tworzysz porównuje z innymi ikonami przy użyciu porównania side-by-side. Nigdy nie używaj całe ramki 16 x 16, użyj 15 x 15 lub mniejsze. Ujemna — pozytywny stosunek (dark światła) powinna być 50/50.  
  
|||  
|-|-|  
|**Poprawny wskaźnik ujemna — pozytywny**|**Niepoprawne współczynnik ujemna — pozytywny**|  
|![Popraw visual wagi ikon &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Popraw visual wagi ikon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Popraw visual wagi ikon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Nieprawidłowa waga visual ikon](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 Do tworzenia elementów bez obniżania oczekiwanego poziomu integralności elementu, należy użyć prostego, porównywalnych kształty i dopełniający kąty. Jeśli jest to możliwe, należy użyć 45 stopni lub 90° kąty.  
  
 ![Popraw kąty ikonę](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspektywa  
 Zachowaj ikonę czytelne i zrozumiałe. Za pomocą perspektywy i źródła światła, tylko wtedy, gdy jest to konieczne. Chociaż należy unikać ikony elementów przy użyciu perspektywy, niektóre elementy są nierozpoznawalną bez niego. W takich przypadkach stylizowane perspektywy komunikuje się w celu uściślenia elementu.  
  
 ![perspektywy punktu 3](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />perspektywy punktu 3
  
 ![1 punkt perspektywy](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />perspektywy punktu 1
  
 Większość elementów powinny miała dostęp do lub pod kątem po prawej stronie:  
  
 ![Ikony bezpośrednio pod kątem](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")  
  
 Użyj źródła światła, tylko wtedy, gdy dodawanie przejrzystości niezbędne do obiektu.  
  
|||  
|-|-|  
|**Prawidłowe źródło światła**|**Nieprawidłowe źródło światła**|  
|![Popraw źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Niepoprawne źródła światła dla ikon](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 Użyj wskazano, tylko w celu zwiększenia czytelności lub lepszej komunikacji metaphor. Wynik dodatni ujemna saldo (dark-light) powinna być 50/50.  
  
|||  
|-|-|  
|**Prawidłowe użycie konspekty**|**Niepoprawne użycie konspekty**|  
|![Popraw opisanych](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![Niepoprawne opisanych](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Typy ikon  
 **Skorupach i polecenia paska** ikony składają się z nie więcej niż trzech z następujących elementów: base jednego, jeden modyfikator, jedną akcję lub jeden stan.  
  
 ![Przykłady skorupach i polecenia paska ikony](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />Przykłady skorupach i polecenia paska ikon
  
 **Pasek poleceń okna narzędzia** ikony składają się z nie więcej niż trzech z następujących elementów: base jednego, jeden modyfikator, jedną akcję lub jeden stan.  
  
 ![Przykładowe okno narzędzia polecenia pasek ikon](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />Przykłady ikony paska poleceń okna narzędzi
  
 **Disambiguator widok drzewa** ikony składają się z nie więcej niż trzech z następujących elementów: base jednego, jeden modyfikator, jedną akcję lub jeden stan.  
  
 ![Przykłady drzewa widoku ikon disambiguator](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />Przykłady drzewa widoku disambiguator ikon
  
 **Wartość oparte na stanie taksonomii** ikony istnieje w jednym z następujących stanów: aktywne, aktywna, wyłączona i nieaktywne wyłączone.  
  
 ![Przykłady oparte na stanie wartość taksonomii ikony](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />Przykłady oparte na stanie wartość taksonomii ikon
  
 **Funkcja IntelliSense** ikony składają się z nie więcej niż trzech z następujących elementów: base jednego, jeden modyfikator i jeden stan.  
  
 ![Przykłady ikony IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />Przykłady ikony IntelliSense
  
 **Małe (16 x 16 pikseli) projektu** ikon powinna mieć nie więcej niż dwa elementy: podstawowe jednego i jeden modyfikator.  
  
 ![Przykłady małe (16 x 16 pikseli) projektu ikony](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![ikona 16 x 16 projektu &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![ikona 16 x 16 projektu &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />Przykłady małe ikony projektu (16 x 16)
  
 **Duży projekt (32 x 32)** ikony składają się z nie więcej niż cztery następujące elementy: jeden podstawowy, Modyfikatory jednej do dwóch i nakładki w jednym języku.  
  
 ![Przykłady dużych (32 x 32) projektu ikony](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />Przykłady duże ikony projektu (32 x 32)
  
### <a name="production-details"></a>Szczegółów dotyczących środowiska produkcyjnego  
 Wszystkie nowe elementy interfejsu użytkownika powinny być tworzone przy użyciu Windows Presentation Foundation (WPF), a wszystkie nowe ikony WPF powinna mieć format PNG 32-bitowych. Format PNG 24-bitowego jest starszego formatu, który nie obsługuje przezroczystości i dlatego nie jest zalecana dla ikon.  
  
 Zapisz rozdzielczości 96 DPI.  
  
#### <a name="file-types"></a>Typy plików  
  
-   **32-bitowych PNG:** preferowanym formacie ikon. Dane bezstratne kompresji formacie, który może przechowywać obraz rastrowych pojedynczego (w pikselach). 32-bitowe pliki PNG obsługują kanał alfa przezroczystości, korekcja gamma i przeplotu.  
  
-   **BMP 32-bitowe:** WPF innych kontrolek. Jest określana skrótem XP lub trybie high color, 32-bitowych BMP jest ma format obrazu RGB/A obrazem true kolor z przezroczystością kanał alfa. Kanał alfa jest warstwą przejrzystości umieszczoną w programie Adobe Photoshop, który następnie jest zapisywany w obrębie mapy bitowej jako dodatkowe (czwarty) kanału koloru. Czarne tło jest dodawany podczas produkcji kompozycji do wszystkich plików BMP 32-bitowych, aby zapewnić szybkie wizualną o głębi kolorów. To czarne tło reprezentuje obszar maskowane się w interfejsie użytkownika.  
  
-   **ICO 32-bitowe:** ikony projektu i Dodaj element. Wszystkie pliki ICO są true kolor 32-bitowy z przezroczystością kanał alfa (RGB/A). Ponieważ pliki ICO można przechowywać wiele wielkości i głębi kolorów, Vista ikony są często w formacie ICO zawierające 16 x 16, 32 x 32, 48 x 48 i rozmiary obrazów 256 x 256. Aby można było wyświetlać się poprawnie w Eksploratorze Windows, pliki ICO musi być zapisane w celu liczby 24-bitowego i 8-bitowych kolorów dla każdego rozmiaru obrazu.  
  
-   **XAML:** powierzchni projektowania i definiowania Windows. Ikony XAML są plików obrazu opartego na wektorach, które obsługują skalowanie, obracanie, przesyłanie i przejrzystości. Nie są obecnie często używany w programie Visual Studio, ale stają się coraz bardziej popularne ze względu na ich elastyczność.  
  
-   **SVG**  
  
-   **BMP 24-bitowego:** dla paska poleceń programu Visual Studio. Format obrazu true kolor RGB BMP 24-bitowego jest Konwencji ikonę, która tworzy warstwę przezroczystość przy użyciu amarantowy (R = 255, G = 0, B = 255) jako klucza kolorów dla warstwy przezroczystości przeciwstukowe w poziomie. W BMP 24-bitowego wszystkich powierzchni magenta są wyświetlane na kolor tła.  
  
-   **Obraz GIF 24-bitowego:** dla paska poleceń programu Visual Studio. True — kolor RGB obraz formacie, który obsługuje przezroczystość. Pliki GIF są często używane w Kreatorze kompozycji i animacji GIF.  
  
### <a name="icon-construction"></a>Ikona tworzenia  
 Najmniejszy rozmiar ikony w programie Visual Studio jest 16 x 16. Największy wspólne użycie jest 32 x 32. Należy pamiętać, nie w celu wypełnienia całe ramki 16 x 16, 24 x 24 lub 32 x 32 podczas projektowania ikony. Konstrukcja czytelny, jednolity ikona jest niezbędne do rozpoznawania użytkownika. Podczas kompilowania ikony, należy stosować się do następujących punktów.  
  
- Ikony powinny być jasne, do zrozumienia i spójne.  
  
- Zaleca się, użyj elementów powiadomień stanu jako pojedynczy ikony, a nie stosu je na górze ikonę elementu podstawowego. W niektórych kontekstach interfejsu użytkownika mogą wymagać elementu stanu, aby łączyć się z elementu podstawowego.  
  
- Ikony projektu są zazwyczaj pliki .ico, które zawierają wiele rozmiarów. Trwa aktualizowanie tylko ikony 16 x 16, 24 x 24 oraz 32 × 32. Większość ikon 16 x 16 i 24 x 24 będzie zawierać te same elementy. Ikony 32 x 32 zawiera bardziej szczegółowe informacje, łącznie z typem języka projektu, jeśli ma to zastosowanie.  
  
- Ikony 32 x 32 podstawowych elementów ma zazwyczaj grubość linii 2 pikseli. Grubość linii pikseli 1 lub 2 może służyć do szczegółów elementów. Zdrowym rozsądkiem najlepiej, aby określić, która jest bardziej odpowiednia.  
  
- Ma co najmniej 1-pikselowe odstępy elementy dla 16 x 16 i 24 x 24 ikon. Ikony 32 x 32 można użyć w 2-pikselowe odstępy między elementami oraz między modyfikator i elementu podstawowego.  
  
  ![Element odstępów dla ikon o rozmiarze 16 x 16, 24 x 24 oraz 32 × 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />Odstępy dla ikon o rozmiarze 16 x 16, 24 x 24 oraz 32 × 32
  
#### <a name="color-and-accessibility"></a>Kolor i ułatwienia dostępu  
 Wytycznych dotyczących zgodności programu Visual Studio wymagają, że wszystkie ikony w produkcie przekazywać wymagania dotyczące ułatwień dostępu dla koloru i kontrast. Jest to realizowane poprzez odwrócenie ikonę, a podczas projektowania, należy pamiętać, że będą one można programowo odwrócony w produkcie.  
  
 Aby uzyskać więcej informacji na temat używania kolorów w ikony programu Visual Studio, zobacz [przy użyciu koloru na obrazach](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a> Przy użyciu koloru na obrazach  
  
### <a name="overview"></a>Omówienie  
 Ikony w programie Visual Studio są głównie monochromatyczny. Kolor jest zarezerwowana do przekazywania określonych informacji i nigdy nie dla dekoracji. Kolor jest używany:  
  
-   Aby wskazać akcję  
  
-   aby ostrzec użytkownika powiadomienia o stanie  
  
-   Aby wyznaczyć przynależności języka  
  
-   do odróżniania elementów w obrębie funkcji IntelliSense  
  
### <a name="accessibility"></a>Ułatwienia dostępu  
 Wytycznych dotyczących zgodności programu Visual Studio wymagają, że wszystkie ikony zaznaczone pole wyboru do produktu — dostęp próbny wymagania dotyczące ułatwień dostępu dla koloru i kontrast. Kolory z palety języka visual zostały przetestowane i spełniają te wymagania.  
  
#### <a name="color-inversion-for-dark-themes"></a>Odwracanie kolorów dla motywów ciemny  
 Aby można było wprowadzić ikony są wyświetlane razem ze współczynnik kontrastu poprawne motywu ciemny programu Visual Studio, odwrócenie jest stosowany programowo. Kolory, w tym przewodniku zostały wybrane w części, aby ich Odwróć poprawnie. Ograniczanie kolorów do tej palety, lub może dawać nieoczekiwane wyniki, po zastosowaniu odwrócenie.  
  
 ![Przykłady ikon, które były ich kolorów, odwrócony](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />Przykłady ikon, które były ich kolorów, odwrócony
  
### <a name="base-palette"></a>Paleta podstawowa  
 Wszystkich standardowych ikon zawiera trzy kolory podstawowej. Ikony zawierają nie gradientach lub cienie, z co najmniej dwa wyjątki dla ikony narzędzia 3D.  
  
|Użycie|Nazwa|Wartość (motyw jasny)|Próbki|Przykład|  
|-----------|----------|---------------------------|------------|-------------|  
|Tło/ciemny|VS BG|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Przykład Paleta podstawowa](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|  
|Pierwszy plan/lekki|VS FG|F0EFF1 / 240,239,241|![Próbka F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Kontur|VS Out|F6F6F6 / 246,246,246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Oprócz podstawowego kolory każda ikona może zawierać jeden dodatkowe kolor z palety rozszerzonej.  
  
### <a name="extended-palette"></a>Rozszerzone palety  
  
#### <a name="action-modifiers"></a>Modyfikatory akcji  
 Cztery kolory poniżej wskazują typy akcji związanej z Modyfikatory akcji:  
  
|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Dodatnie|Zielony akcji programu VS|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Ujemne|Czerwony akcji programu VS|A1260D / 161,38,13|![Próbka A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Niezależny od|Niebieski akcji programu VS|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Utwórz nową|Pomarańczowy akcji programu VS|C27D1A / 194,156,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Przykłady  
 Kolor zielony jest używana do Modyfikatory dodatnią akcji, takich jak "Add", "Uruchom," "Play" i "Weryfikuj".  
  
|||||  
|-|-|-|-|  
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Uruchom|![Wykonywanie zapytania ikonę](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />Wykonywanie zapytania|![Odtwórz wszystkie ikony procedury](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />Odtwórz wszystkie kroki|![Dodawać ikonę kontroli](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />Dodaj kontrolkę|  
  
 Czerwony służy do Modyfikatory ujemna akcji, takich jak "Delete", "Stop", "Anuluj" i "Zamknąć".  
  
|||||  
|-|-|-|-|  
|![Usuń ikonę relacji](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />Usuwanie relacji|![Usuń ikonę kolumnowego](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />Usuń kolumnę|![Ikona zapytania stop](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />Zatrzymaj zapytanie|![Ikona trybu offline połączenia](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />Połączenia w trybie Offline|  
  
 Niebieski jest stosowany do akcji neutralne Modyfikatory najczęściej reprezentowane jako strzałki, takie jak "Otwarte," "Dalej", "Wstecz", "Importuj" i "Eksportuj".  
  
|||||  
|-|-|-|-|  
|![Przejdź do ikony pole](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />Przejdź do pola|![Wsadowe wyboru&#45;ikona](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />Wsadowej operacji ewidencjonowania|![Ikona Edytor adresów](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />Edytor adresów|![Ikona Edytor skojarzeń](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />Edytor skojarzeń|  
  
 Ciemny gold jest używany głównie dla modyfikator "New".  
  
|||||  
|-|-|-|-|  
|![Nowa ikona projektu](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 15_NewProject")<br />Nowy projekt|![Utwórz nową ikonę wykres](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />Utwórz nowy wykres|![Nowa ikona testów jednostkowych](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />Nowy Test jednostkowy|![Ikona nowego elementu listy](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />Nowy element listy|  
  
#### <a name="special-cases"></a>Specjalne przypadki  
 W szczególnych przypadkach modyfikator kolorowe akcji może używać niezależnie jako ikona autonomicznych. Kolor ikony odzwierciedla akcje, które ikonę jest skojarzony. To użycie jest ograniczone do małego podzbioru ikony, w tym:  
  
||||||  
|-|-|-|-|-|  
|![Ikona uruchamiania](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Uruchom|![Ikona stop](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />Zatrzymywanie|![Ikona usuwania](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />Usuwanie|![Ikona zapisu](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />Zapisanie|![Przejdź wstecz ikonę](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />Nawiguj wstecz|  
  
### <a name="code-hierarchy-palette"></a>Kod hierarchii palety  
  
#### <a name="folder"></a>Folder  
  
|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|Przykład|  
|-----------|----------|--------------------------|------------|-------------|  
|Foldery|Folder|DCB67A / 220,182,122|![Próbka DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ikona kolor folderu](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Języki Visual Studio  
 Każda z typowych języków lub platform dostępne w programie Visual Studio ma kolor skojarzony. Te kolory na ikonie podstawowej lub nad modyfikatorami języka, które pojawiają się w prawym górnym rogu złożone ikony.  
  
|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|Niebieski HTML WPF ASP|0095D 7 / 0,149,215|![Próbka 0095 D 7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|Purpurowy CPP|9B4F96 / 155,79,150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|Zielony CS (zielony akcji programu VS)|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Czerwony CSS|BD1E2D / 189,30,45|![Próbka BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|Purpurowy FS|672878 / 103,40,120|![Próbka 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|Pomarańczowy JS|F16421 / 241,100,33|![Próbka F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|Niebieski VB (niebieski akcji programu VS)|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Pomarańczowy usług terminalowych|E04C06 / 224,76,6|![Próbka E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|Zielony PY|879636 / 135,150,54|![Próbka 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Przykłady ikon z modyfikatorów języka  
  
|||||||  
|-|-|-|-|-|-|  
|![Ikona języka Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C&#35; icon](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43;&#43; icon](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; ikonę](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![Ikona JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Ikona Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|  
|![Ikona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![Ikona WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![Ikona ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 33_ASP")<br />ASP|![Ikona CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 34_CSS")<br />CSS|![Ikona TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 Ikony IntelliSense Użyj palety kolorów wyłączności. Te kolory pomagają użytkownikom szybko odróżnić różne elementy na liście menu podręczne IntelliSense.  
  
|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Klasa zdarzenia|Pomarańczowy akcji programu VS|C27D1A / 194,125,26|![Próbka C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Metody rozszerzenia, delegat metody i modułu|Purpurowy akcji programu VS|652D 90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Pole elementu wartości wyliczeniowej, — makro, struktury, typ wartości Union, Operator, interfejs|Niebieski akcji programu VS|00539C / 0,83,156|![Próbka 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Obiekt|Zielony akcji programu VS|388A34 / 56,138,52|![Próbka 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Stałe, wyjątków, elementu wartości wyliczeniowej, mapy, elementu mapy, Namespace, szablon, definicja typu|W tle (VS BG)|424242 / 66,66,66|![Próbka 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Przykłady ikony IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Ikona Klasa IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />Class|![Ikona Zdarzenie prywatne IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />Zdarzenie prywatne|![Ikona delegata funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />Delegate|![Ikona friend metody IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />Friend — metoda|![Ikona pola](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />Pole|  
|![IntelliSense chronione ikona elementu wyliczenia](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />Chroniony element typu wyliczeniowego|![Ikona obiektu IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Obiekt|![Ikona szablonu funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />Szablon|![Ikona skrótu wyjątek funkcji IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />Skrót wyjątku||  
  
### <a name="notifications"></a>Powiadomienia  
 Powiadomienia w programie Visual Studio są używane do wskazania stanu. Paleta powiadomień używa następujące cztery kolory, a także Opcje wypełnienia czarne lub białe pierwszego planu, w celu zdefiniowania powiadomień za pomocą następujących poziomów stanu.  
  
|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|  
|-----------|----------|--------------------------|------------|  
|Stan: neutralny|Niebieski powiadomień (VS niebieski)|1BA1E2 / 27,161,226|![Próbka 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Stan: dodatnią|Zielony powiadomień (kolor zielony VS)|339933 / 51,153,51|![Próbka 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Stan: ujemna|Powiadomienie Red (czerwony VS)|E51400 / 229,20,0|![Próbka E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Stan: ostrzeżenie|Żółty powiadomień (kolor pomarańczowy VS)|FFCC00 / 255,204,0|![Próbka FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Wypełnienie pierwszego planu|Powiadomienie czarny (czarny)|000000 / 0,0,0|![Próbka &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Wypełnienie pierwszego planu|Powiadomienie biały (biały)|FFFFFF / 255,255,255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Przykłady ikony powiadomień  
  
|||||  
|-|-|-|-|  
|![Ikona alertu](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />Alerty|![Ikona ostrzeżenia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />Ostrzeżenie|![Ikona zakończonego](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />Wykonaj|![Ikona stop](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />Zatrzymywanie|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Ogólnie rzecz biorąc Visual Studio Online zawiera funkcje obsługiwane w przeglądarce. Kolor zmienia się w różnych środowiskach, ale styl pozostają bez zmian.  
  
|Grupa|Użycie|Nazwa|Wartości (wszystkie motywy)|Próbki|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Tło|TFSO BG|656565/ 101, 101, 101|![Próbka 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Kontur|TFSO OUT|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Narzędzia Napa|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Tło|Biały|FFFFFF / 255, 255, 255|![Próbka FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normalny|F12 Grey_Primary|555555 / 85, 85, 85|![Próbka 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Po wskazaniu wskaźnikiem|F12 Blue_Hover|2279BF / 34,121,191|![Próbka 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Wyłączone|F12 LtGrey_Disabled|ABABAC / 171,171,172|![Próbka ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Tło|Zatrzymaj wskaźnik myszy bg|D9EBF7 / 217,235,247|![Próbka D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Po naciśnięciu tła|Po naciśnięciu bg|B2D7F0 / 178,215,240|![Próbka B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Kontur|VS OUT|F6F6F6 / 246,246,246|![Próbka F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Informacje|Informacje|00BCF2 / 0,188,242|![Próbka 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Ostrzeżenie|Ostrzeżenie|F28300 / 242,131,0|![Próbka F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Błąd / ujemna|Error_Negative|E81123 / 232,17,35|![Próbka E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Start / dodatnią|Start_Positive|009E49 / 0,158,73|![Próbka 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Typ podziału|Typ podziału|9B4F96 / 155,79,150|![Próbka 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Znacznik zdarzenia|Znacznik zdarzenia|A51F00 / 165,31,0|![Próbka A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Znacznik użytkownika|Znacznik użytkownika|F16220 / 241,98,32|![Próbka F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Przykłady ikony programu Visual Studio Online  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Ikona zespołu TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />Zespołu online|![Ikona informacji TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />Informacje|![Ikona historii TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 51_TFSHistory")<br />Historia|![Ikona gałęzi TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />Odgałęzienie|  
  
|Narzędzia Napa||||  
|----------|-|-|-|  
|![Napa content icon](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Zawartość|![Ikona poczty office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Poczta pakietu Office|![Ikona programu SharePoint narzędzia Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />Program SharePoint|![Ikona w okienku zadań Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />Okienka zadań|  
  
|Monaco||||  
|------------|-|-|-|  
|![Ikona pliki Monako](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />Pliki|![Ikona Git Monako](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![Ikony wyszukiwania Monako](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />Wyszukaj|![Ikona tekstu Monako](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />Tekst|  
  
|F12|||  
|---------|-|-|  
|![Ikona kodu pretty F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />Łatwa kodu|![Ikona ostrzeżenia F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />Ostrzeżenie|![Ikona emulować F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />Emuluj|