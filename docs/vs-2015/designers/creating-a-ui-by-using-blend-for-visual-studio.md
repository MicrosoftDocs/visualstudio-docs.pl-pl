---
title: Tworzenie interfejsu użytkownika przy użyciu programu Blend
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a65f42dafca696bfa638964b825410b576d4845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544290"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Blend for Visual Studio ułatwia projektowanie aplikacji klasycznych dla systemu Windows opartych na języku XAML, w sieci Web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)i aplikacjach ze [sklepu Windows](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) . Zapewnia to takie samo podstawowe środowisko projektowe XAML jak program Visual Studio i dodaje projektantów wizualizacji do zaawansowanych zadań, takich jak animacje i zachowania.

 Ponieważ Blend for Visual Studio jest częścią programu Visual Studio, nie trzeba jej pobierać. Należy jednak wybrać go w Instalatorze programu Visual Studio, aby mógł zostać zainstalowany w systemie.

 Jeśli dopiero zaczynasz Blend for Visual Studio, poświęć chwilę na zapoznanie się z unikatowymi funkcjami obszaru roboczego. Ten temat obejmuje Krótki przewodnik.

> [!NOTE]
> Aby zapoznać się z udostępnionymi funkcjami projektu, takimi jak obszar kompozycji, okno konspektu dokumentu i okno urządzenia, zobacz [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **W tym temacie**:

- [Przewodnik po panelu Narzędzia](#Tools)

- [Przewodnik po panelu Składniki](#Assets)

- [Przewodnik po panelu Obiekty i oś czasu](#Objects)

- [Przewodnik po panelu Właściwości](#Properties)

## <a name="tour-of-the-tools-panel"></a><a name="Tools"></a> Przewodnik po panelu Narzędzia
 Panel **Narzędzia** w Blend for Visual Studio służy do tworzenia i modyfikowania obiektów w aplikacji. Obiekty są tworzone przez wybranie narzędzia i rysowanie w obszarze kompozycji za pomocą myszy.

 ![Panel narzędzi](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|Obraz|Typ narzędzia|Obraz|Typ narzędzia|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Narzędzia wyboru** Wybierz obiekty i ścieżki.<br /><br /> Użyj narzędzia **wybór bezpośredni** , aby zaznaczyć zagnieżdżone obiekty i segmenty ścieżki.|![Objaśnienie A](../designers/media/b5-label-a.png "b5_label_A")|**Narzędzia gradientowe i pędzle**|
|![](../designers/media/b1-2.png "B1_2")|**Narzędzia widoku** Dostosuj widok obszaru kompozycji, taki jak przesuwanie i powiększanie.|![Objaśnienie B](../designers/media/b5-label-b.png "b5_label_B")|**Narzędzia ścieżki**|
|![](../designers/media/b1-3.png "B1_3")|**Narzędzia pędzla** Pracuj z atrybutami wizualizacji obiektu, takimi jak Przekształcanie pędzla, malowanie obiektu lub wybieraniem atrybutów jednego obiektu, aby zastosować je do innego obiektu.|![Objaśnienie C](../designers/media/b5-label-c.png "b5_label_C")|**Narzędzia kształtu**|
|![](../designers/media/b1-4.png "B1_4")|**Narzędzia obiektów** Rysowanie najpopularniejszych obiektów w obszarze kompozycji, takich jak ścieżki, kształty, panele układu, tekst i kontrolki.|![Objaśnienie D](../designers/media/b5-label-d.png "b5_label_D")|**Panele układów**|
|![](../designers/media/b1-5.png "B1_5")|**Narzędzia zasobów** Dostęp do panelu **składniki** i wyświetlanie ostatnio używanego elementu zawartości z biblioteki.|![Objaśnienie E](../designers/media/b5-label-e.png "b5_label_E")|**Kontrolki tekstu**|
|||![Objaśnienie F](../designers/media/b5-label-f.png "b5_label_F")|**Typowe kontrolki**|

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [na pasku narzędzi](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a><a name="Assets"></a> Przewodnik po panelu Składniki
 Wszystkie kontrolki można znaleźć w panelu **składniki** , podobnie jak w przypadku **przybornika** w programie Visual Studio. Oprócz formantów znajdziesz wszystko, co można dodać do obszaru kompozycji w panelu **składniki** , w tym style, multimedia, zachowania i efekty.

 ![Panel składników zasobów](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|Obraz|Opis|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Pole wyszukiwania** Wpisz w polu **wyszukiwania** , aby odfiltrować listę zasobów.|
|![](../designers/media/b1-2.png "B1_2")|**Tryb siatki i tryb listy** Przełączanie między widokiem **siatki** a widokiem **listy** zasobów.|
|![](../designers/media/b1-3.png "B1_3")|**Kategorie zasobów** Kliknij kategorię lub podkategorię, aby wyświetlić listę zasobów w tej kategorii.|
|![](../designers/media/b1-4.png "B1_4")|**Style** Pokaż wszystkie style, które są zawarte w słowniku zasobów.|
|![](../designers/media/b1-5.png "B1_5")|**Opis** Wyświetl opis kategorii lub podkategorii wybranych zasobów.|

## <a name="tour-of-the-objects-and-timeline-panel"></a><a name="Objects"></a> Przewodnik po panelu Obiekty i oś czasu
 Ten panel służy do organizowania obiektów w obszarze kompozycji i, jeśli chcesz, animowania ich.

 ![Panel obiektów i osi czasu w trybie animacji](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|Obraz|Opis|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Widok obiektów** Wyświetlanie drzewa wizualnego dokumentu. Możesz przejść do szczegółów na różne poziomy szczegółowości. Możesz również dodać warstwy, aby dodatkowo organizować obiekty w obszarze kompozycji. Dzięki temu można zablokować i ukryć je jako grupę.|
|![](../designers/media/b1-2.png "B1_2")|**Wskaźnik trybu rekordu** Sprawdź, czy rejestrujesz zmiany właściwości na osi czasu.|
|![](../designers/media/b1-3.png "B1_3")|**Selektor scenorysu** Wyświetl listę utworzonych scenorysów.|
|![](../designers/media/b1-4.png "B1_4")|**Zamknij scenorys** Zamknij bieżący scenorys.|
|![](../designers/media/b1-5.png "B1_5")|**Opcje scenorysu** Tworzenie, duplikowanie, odwracanie, usuwanie, zmiana nazwy lub zamykanie scenorysu.|
|![](../designers/media/b1-6.png "B1_6")|**Kontrolki odtwarzania** Nawigowanie po osi czasu. Możesz również przeciągnąć głowicę odtwarzania, aby przechodź ( *lub*przewinąć) oś czasu.|
|![](../designers/media/b1-7.png "B1_7")|**Zwróć zakres do** Ustaw zakres wyświetlania obiektów z powrotem na poprzedni obiekt główny lub poprzedni zakres. Można to zrobić tylko w przypadku modyfikacji stylu lub szablonu.|
|![](../designers/media/b1-8.png "B1_8")|**Rejestrowanie klatki kluczowej** Zapisz migawkę właściwości wybranego obiektu w bieżącym punkcie w czasie.|
|![](../designers/media/b1-9.png "B1_9")|**Opcje przyciągania** Ustawianie przyciągania osi czasu, rozdzielczości przyciągania i wyłączania przyciągania osi czasu.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Pokaż/Ukryj**, **Zablokuj/Odblokuj** Pokaż lub Ukryj opcje widoczności i blokowania dla widoku obiekty.|
|![](../designers/media/b1-11.png "B1_11")|**Położenie głowicy odtwarzania na osi czasu** Pokaż bieżący czas (w milisekundach). Można również bezpośrednio wpisać wartości czasu w tym polu, aby przejść do określonego punktu w czasie. Precyzja zależy od rozdzielczości Snap ustawionej w **opcjach przyciągania**.|
|![](../designers/media/b1-12.png "B1_12")|**Głowica odtwarzania** Określ, który punkt w czasie ma być animacją. Przeciągając wskaźnik odtwarzania na osi czasu, można wyświetlić podgląd animacji.|
|![](../designers/media/b1-13.png "B1_13")|**Ramki kluczowe ustawione na osiach czasu** Zmień wartość właściwości w określonym punkcie w czasie.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Zmień kolejność obiektów** Ustaw kolejność wyświetlania obiektów. Kliknij ten przycisk, aby rozmieścić obiekty w widoku struktury według porządku osi Z (od przodu do tyłu) lub według kolejności znaczników (kolejność, w której są wyświetlane w widoku **XAML** ).|
|![](../designers/media/b1-15.png "B1_15")|**Powiększenie osi czasu** Ustaw rozdzielczość osi czasu dla powiększenia. Powiększanie pozwala bardziej szczegółowo edytować animację, a pomniejszenie przedstawia bardziej ogólny obraz zdarzeń w dłuższym okresie. Jeśli po powiększeniu nie można ustawić ramki kluczowej na żądanej pozycji w czasie, należy sprawdzić, czy ustawiono odpowiednio dużą rozdzielczość przyciągania.|
|![Objaśnienie 16](../designers/media/b5-label-16.png "b5_label_16")|**Obszar kompozycji osi czasu** Wyświetlaj oś czasu i przenoś ramki kluczowe, przeciągając je lub używając ich menu skrótów.|

## <a name="tour-of-the-properties-panel"></a><a name="Properties"></a> Przewodnik po panelu Właściwości
 Ten panel służy do wyświetlania i modyfikowania właściwości obiektu. Można je również ustawić bezpośrednio w obszarze kompozycji. W takim przypadku zmiany właściwości zostaną odzwierciedlone w panelu **Właściwości** .

 ![Panel właściwości](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategorie** Rozwijanie i zwijanie kategorii właściwości. Kliknij przycisk **Rozwiń** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") i **Zwiń** ![zwijanie](../designers/media/b5-collapse-button.png "b5_collapse_button") , aby pokazać lub ukryć szczegóły kategorii.

|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Nazwa i typ** Wyświetl ikonę, nazwę i typ zaznaczonego obiektu.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Rozmieść według** Rozmieść właściwości alfabetycznie według nazwy, źródła lub kategorii.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Właściwości pędzla** Ustaw właściwości wizualizacji dla pędzli, takich jak Pędzel wypełnienia, Pędzel obrysu i Pędzel pierwszego planu.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Edytor kolorów** Użyj dla pędzli pełnych kolorów i gradientów.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Selektor kolorów** Wybierz kolor.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Wióry kolorów** Wyświetl kolor początkowy, bieżący kolor i ostatni kolor                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Kroplomierze** Użyj koloru dowolnego elementu na ekranie. **Kroplomierz koloru** jest dostępny po wybraniu **pędzla pełnego koloru** . **Kroplomierz gradientu** jest dostępny po wybraniu **pędzla gradientu** . |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Właściwości i zdarzenia** Ustaw właściwości lub wybierz zdarzenia dla wybranego elementu.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Pole wyszukiwania** Wyszukaj właściwości. Filtruj właściwości, które są wyświetlane, wpisując w polu **wyszukiwania** .                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Karty edytora pędzla** Użyj, aby wybrać Edytor pędzla. Możesz wybrać **Brak pędzla**, **pełnego pędzla kolorów**, pędzla **gradientu**, **pędzla kafelków**lub **zasobu pędzla**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Zasoby koloru** Zastosuj dokładnie ten sam kolor do różnych właściwości. Karta **zasoby kolorów** zawiera **Zasoby lokalne** i **zasoby systemowe**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **Przestrzeń kolorów RGB** Zmodyfikuj kolor, dostosowując wartości dla edytorów liczb **R**,  **G**lub **B** (czerwony, zielony, niebieski).                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Kanał alfa** Zmodyfikuj wartość alfa przy użyciu edytora liczb obok **elementu**.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Konwertuj kolor na zasób** Konwertuj wybrany kolor na zasób koloru. Zasoby koloru są dostępne po kliknięciu karty zasoby koloru.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Wartość szesnastkowa** Wyświetl wartość szesnastkową wyświetlanego koloru.                                                                                 |
|                     ![Objaśnienie 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Suwak gradientu** Pojawia się tylko wtedy, gdy wybrano pędzel gradientu.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Pokaż właściwości zaawansowane** Wyświetlanie kategorii właściwości, które są rzadziej używane.                                                                      |

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Panel właściwości](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Zobacz też
 [Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [animowanie obiektów](../designers/animate-objects-in-xaml-designer.md) [rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md) [projektowanie XAML w Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
