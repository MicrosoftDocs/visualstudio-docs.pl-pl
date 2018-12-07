---
title: Tworzenie interfejsu użytkownika przy użyciu programu Blend
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f77fba9ed184d5def85aa7ca260b7c552dddbfd1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054544"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Blend for Visual Studio ułatwia projektowanie oparte na XAML Windows pulpitu, sieci web, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx), i [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) aplikacji. Zapewnia takie samo środowisko projektowania podstawowe XAML w co program Visual Studio i dodaje projektantów wizualnych dotyczące zaawansowanych zadań, takich jak animacjom i zachowaniom.

 Ponieważ program Blend for Visual Studio jest dostarczany jako część pakietu Visual Studio, nie trzeba go pobrać. Potrzebny ją wybrać w Instalatorze programu Visual Studio dla niego, można zainstalować w systemie.

 Jeśli jesteś nowym użytkownikiem programu Blend for Visual Studio, Poświęć chwilę na zapoznanie się z unikatowych funkcji obszaru roboczego. W tym temacie przejmuje krótkiego przewodnika.

> [!NOTE]
>  Aby poznasz funkcje projektu udostępnionego, takie jak obszaru kompozycji, okno konspektu dokumentu i okno urządzenia, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **W tym temacie**:

-   [Samouczek panelu Narzędzia](#Tools)

-   [Samouczek panelu Zasoby](#Assets)

-   [Przewodnik po przykładzie obiekty i oś czasu panelu](#Objects)

-   [Samouczek Panelu właściwości](#Properties)

##  <a name="Tools"></a> Samouczek panelu Narzędzia
 Możesz użyć **narzędzia** panel w programie Blend for Visual Studio do tworzenia i modyfikowania obiektów w aplikacji. Możesz utworzyć obiekty, wybierając narzędzie i rysowanie w obszarze kompozycji przy użyciu myszy.

 ![Panel narzędzi](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Narzędzia wyboru** Zaznaczanie obiektów i ścieżki.<br /><br /> Użyj **Zaznaczanie bezpośrednie** narzędzie do wybierania obiektów zagnieżdżonych i segmentów ścieżki.|![Objaśnienie A](../designers/media/b5-label-a.png "b5_label_A")|**Narzędzia gradientu i pędzla**|
|![](../designers/media/b1-2.png "B1_2")|**Wyświetl narzędzia** Dostosowywanie widoku obszaru kompozycji, takie jak przesuwać i powiększać.|![Objaśnienie B](../designers/media/b5-label-b.png "b5_label_B")|**Ścieżka narzędzia**|
|![](../designers/media/b1-3.png "B1_3")|**Pędzel, narzędzia** pracy z visual atrybutów obiektu, takich jak Przekształcanie pędzla, malowanie obiektu lub wybierając atrybuty jednego obiektu, aby zastosować je do innego obiektu.|![Objaśnienie C](../designers/media/b5-label-c.png "b5_label_C")|**Narzędzia kształtów**|
|![](../designers/media/b1-4.png "B1_4")|**Obiekt narzędzia** Rysuj obiekty najczęściej w obszarze kompozycji, takich jak ścieżki, kształty, panele układów, tekstu i formanty.|![Objaśnienie D](../designers/media/b5-label-d.png "b5_label_D")|**Panele układów**|
|![](../designers/media/b1-5.png "B1_5")|**Narzędzia zasobów** dostępu **zasoby** panelu, i aby wyświetlić ostatnio używane zasobu z biblioteki.|![Objaśnienie E](../designers/media/b5-label-e.png "b5_label_E")|**Kontrolek tekstu**|
|||![Objaśnienie F](../designers/media/b5-label-f.png "b5_label_F")|**Formanty standardowe**|

 **Obejrzyj krótki film wideo:** ![Konfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [narzędzi](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

##  <a name="Assets"></a> Samouczek panelu Zasoby
 Możesz znaleźć wszystkie formanty w **zasoby** panelu, podobnie jak **przybornika** w programie Visual Studio. Oprócz formantów, znajdziesz wszystko, czego możesz dodać do Twojego obszaru roboczego w **zasoby** panelu, w tym stylów, multimediów, zachowań i efektów.

 ![Panel zasobów](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Pole wyszukiwania** wpisać **wyszukiwania** polu, aby filtrować listę zasobów.|
|![](../designers/media/b1-2.png "B1_2")|**Tryb siatki i tryb listy** przełączać się między **trybu siatki** widoku i **tryb listy** widoku zasobów.|
|![](../designers/media/b1-3.png "B1_3")|**Kategorie zasobów** kliknij kategorię lub podkategorię, aby wyświetlić listę zasobów w tej kategorii.|
|![](../designers/media/b1-4.png "B1_4")|**Style** Pokaż wszystkie style, które są zawarte w słowniku zasobów.|
|![](../designers/media/b1-5.png "B1_5")|**Opis** Wyświetl opis wybranej kategorii lub podkategorii zasobów.|

##  <a name="Objects"></a> Przewodnik po przykładzie obiekty i oś czasu panelu
 Użyj tego panelu do porządkowania obiektów w Twojego obszaru roboczego i, jeśli chcesz, aby animować je.

 ![Panel obiektów i osi czasu w trybie animacji](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Widok obiektów** przeglądać drzewo wizualne dokumentu. Przechodzić do różnych poziomów szczegółowości. Można również dodać warstwy w celu dokładniejszego porządkowania obiektów w obszarze kompozycji. W ten sposób można zablokować i je ukryć jako grupa.|
|![](../designers/media/b1-2.png "B1_2")|**Wskaźnik trybu nagrywania** Zobacz, czy rejestrowane zmiany właściwości na osi czasu.|
|![](../designers/media/b1-3.png "B1_3")|**Selektor scenorysu** wyświetlić listę scenorysy, które zostały utworzone.|
|![](../designers/media/b1-4.png "B1_4")|**Zamknij scenorys** zamknąć bieżący scenorysu.|
|![](../designers/media/b1-5.png "B1_5")|**Opcje scenorysu** odwrotna duplikatów, tworzenie, usuwanie, zmiana nazwy lub zamykanie scenorysu.|
|![](../designers/media/b1-6.png "B1_6")|**Formanty odtwarzania** Nawiguj za pomocą osi czasu. Można również przeciągać wskaźnik odtwarzania w celu nawigowania (lub *czyszczenie*) osi czasu.|
|![](../designers/media/b1-7.png "B1_7")|**Zwróć zakres do** zakres widoku obiektów powrót do poprzedniego obiektu głównego lub poprzedniego zakresu. Można to zrobić tylko wtedy, gdy modyfikujesz stylu lub szablonu.|
|![](../designers/media/b1-8.png "B1_8")|**Zarejestruj kluczową** Zapisz migawkę właściwości wybranego obiektu w bieżącym punkcie w czasie.|
|![](../designers/media/b1-9.png "B1_9")|**Opcje przyciągania** Ustaw przyciąganie do osi czasu, rozdzielczość przyciągania i wyłączyć przyciąganie do osi czasu.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pokaż/Ukryj**, **Zablokuj/Odblokuj** Pokaż lub Ukryj widoczności i blokowania opcje widoku obiektów.|
|![](../designers/media/b1-11.png "B1_11")|**Pozycja wskaźnika odtwarzania na osi czasu** wyświetlić bieżący czas w milisekundach. Można również bezpośrednio wpisać wartości czasu w tym polu, aby przejść do określonego punktu w czasie. Dokładność zależy od rozdzielczości przyciągania ustawionej w **opcje przyciągania**.|
|![](../designers/media/b1-12.png "B1_12")|**Wskaźnik odtwarzania** ustalić, w jakim punkcie czasu jest animacja. Przeciągając wskaźnik odtwarzania na osi czasu, można wyświetlić podgląd animacji.|
|![](../designers/media/b1-13.png "B1_13")|**Ramki kluczowe ustawione na osiach czasu** Zmień wartość właściwości w określonym punkcie w czasie.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Zmień kolejność obiektów** Ustaw kolejność wyświetlania obiektów. Kliknięcie tego przycisku pozwala rozmieścić obiekty w widoku struktury, według porządku osi Z (z przodu do tyłu) lub według kolejności znaczników (kolejności, w jakiej występują w **XAML** widoku).|
|![](../designers/media/b1-15.png "B1_15")|**Powiększenie osi czasu** Ustaw rozdzielczość powiększania osi czasu. Powiększanie pozwala bardziej szczegółowo edytować animację, a pomniejszenie przedstawia bardziej ogólny obraz zdarzeń w dłuższym okresie. Jeśli po powiększeniu nie można ustawić ramki kluczowej na żądanej pozycji w czasie, należy sprawdzić, czy ustawiono odpowiednio dużą rozdzielczość przyciągania.|
|![Objaśnienie 16](../designers/media/b5-label-16.png "b5_label_16")|**Obszar kompozycji osi czasu** Wyświetl oś czasu i przesuwanie ramek kluczowych przez przeciąganie ich lub za pomocą menu skrótów.|

##  <a name="Properties"></a> Samouczek Panelu właściwości
 Ten panel umożliwia wyświetlanie i modyfikowanie właściwości obiektu. Można również ustawić je bezpośrednio w obszarze kompozycji. Jeśli to zrobisz, zmiany właściwości zostaną odzwierciedlone w **właściwości** panelu.

 ![Panel właściwości](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategorie** rozwijanie i zwijanie kategorie właściwości. Kliknij przycisk **rozwiń** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") i **Zwiń** ![Zwiń](../designers/media/b5-collapse-button.png "b5_collapse_button") pokazać lub ukryć szczegóły kategorii.


|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Nazwa i typ** wyświetlać ikony, nazwę i typ wybranego obiektu.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Rozmieść według** rozmieszczania właściwości alfabetycznie według nazwy, źródła lub kategorii.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Właściwości pędzla** Ustaw właściwości visual pędzle, takie jak Pędzel wypełnienia, obrysu pędzla i pędzla pierwszego planu.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Edytor kolorów** jednolitego koloru i pędzle gradientów.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Selektor kolorów** wybierz kolor.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Kolor mikroukładami** wyświetlać kolor początkowy, bieżący kolor i ostatni kolor                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Kroplomierzy** Użyj kolor dowolnego elementu na ekranie. **Pipeta koloru** jest dostępna, gdy **pędzel pełnego koloru** jest zaznaczone. **Pipeta gradientu** jest dostępna, gdy **pędzla gradientu** jest zaznaczone. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Właściwości i zdarzenia** Ustaw właściwości lub wybrać zdarzenia dla wybranego elementu.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Pole wyszukiwania** wyszukiwać właściwości. Filtrowanie właściwości, które są wyświetlane, wpisując w polach **wyszukiwania** pole.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Pędzel, Edytor karty** wybierz edytor pędzla. Możesz wybrać **Brak pędzla**, **pędzel pełnego koloru**, **pędzla gradientu**, **pędzla kafelków**, lub **pędzla zasobów**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Zasoby koloru** dotyczą dokładnie ten sam kolor inne właściwości. **Zasoby koloru** karta zawiera **zasoby lokalne** i **zasobów systemowych**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **Przestrzeń kolorów RGB** modyfikacji koloru, dopasowując wartości **R**, **G**, lub **B** (czerwony, zielony, niebieski) edytory liczb.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Kanał alfa** zmodyfikuj wartość alfa przy użyciu numeru edytora obok **A**.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Konwertuj kolor na zasób** Konwertuj wybrany kolor na zasób koloru. Zasoby koloru są dostępne po kliknięciu na karcie Zasoby kolorów.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Wartość szesnastkowa** wyświetlić wartość szesnastkową kolor wyświetlany.                                                                                 |
|                     ![Objaśnienie 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Suwak gradientu** pojawia się tylko wtedy, gdy wybrano pędzla gradientu.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Pokaż zaawansowane właściwości** kategorii właściwości, które są rzadko używane.                                                                      |

 **Obejrzyj krótki film wideo:** ![Konfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [panelu właściwości](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Zobacz też
 [Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md) [Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md) [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
