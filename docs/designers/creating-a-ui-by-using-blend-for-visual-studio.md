---
title: Tworzenie interfejsu użytkownika — Blend for Visual Studio
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76743674ef4e92f2ad52be108c1dafb8d942676c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059869"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio

Program Blend for Visual Studio ułatwia projektowanie oparte na XAML Windows i aplikacji sieci Web. Zapewnia takie samo środowisko projektowania podstawowe XAML w co program Visual Studio i dodaje projektantów wizualnych dotyczące zaawansowanych zadań, takich jak animacjom i zachowaniom. Dla porównania między programami Blend i Visual Studio, zobacz [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Program Blend for Visual Studio jest składnikiem programu Visual Studio. Aby zainstalować program Blend, w **Instalatora programu Visual Studio** wybierają **programowania na platformę uniwersalną Windows** lub **programowanie aplikacji klasycznych dla platformy .NET** obciążenia. Oba te obciążenia obejmują program Blend for Visual Studio składnika.

![Składniki obciążenia platformy UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Składniki obciążenie programowanie aplikacji klasycznych dla platformy .NET](media/installer-dotnet-desktop.png)

Jeśli jesteś nowym użytkownikiem programu Blend for Visual Studio, Poświęć chwilę na zapoznanie się z unikatowych funkcji obszaru roboczego. W tym temacie przejmuje krótkiego przewodnika.

> [!NOTE]
> Aby poznasz funkcje projektu udostępnionego, takich jak obszaru kompozycji, **konspekt dokumentu** oknie i **urządzenia** okna, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Samouczek panelu Narzędzia

Możesz użyć **narzędzia** panel w programie Blend for Visual Studio do tworzenia i modyfikowania obiektów w aplikacji. Możesz utworzyć obiekty, wybierając narzędzie i rysowanie w obszarze kompozycji przy użyciu myszy.

![Panel narzędzi](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![Narzędzia wyboru](../designers/media/b1_1.png)|**Narzędzia wyboru** Zaznaczanie obiektów i ścieżki.<br /><br /> Użyj **Zaznaczanie bezpośrednie** narzędzie do wybierania obiektów zagnieżdżonych i segmentów ścieżki.|![Objaśnienie A](../designers/media/b5_label_a.png)|**Narzędzia gradientu i pędzla**|
|![Wyświetl narzędzia](../designers/media/b1_2.png)|**Wyświetl narzędzia** Dostosowywanie widoku obszaru kompozycji, takie jak przesuwać i powiększać.|![Objaśnienie B](../designers/media/b5_label_b.png)|**Ścieżka narzędzia**|
|![Pędzel](../designers/media/b1_3.png)|**Pędzel, narzędzia** pracy z visual atrybutów obiektu, takich jak Przekształcanie pędzla, malowanie obiektu lub wybierając atrybuty jednego obiektu, aby zastosować je do innego obiektu.|![Objaśnienie C](../designers/media/b5_label_c.png)|**Narzędzia kształtów**|
|![Obiekt narzędzia](../designers/media/b1_4.png)|**Obiekt narzędzia** Rysuj obiekty najczęściej w obszarze kompozycji, takich jak ścieżki, kształty, panele układów, tekstu i formanty.|![Objaśnienie D](../designers/media/b5_label_d.png)|**Panele układów**|
|![Narzędzia zasobów](../designers/media/b1_5.png)|**Narzędzia zasobów** dostępu **zasoby** panelu, i aby wyświetlić ostatnio używane zasobu z biblioteki.|![Objaśnienie E](../designers/media/b5_label_e.png)|**Kontrolek tekstu**|
|||![Objaśnienie F](../designers/media/b5_label_f.png)|**Formanty standardowe**|

**Obejrzyj krótki film wideo:** ![Konfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [narzędzi](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Samouczek panelu Zasoby

Możesz znaleźć wszystkie formanty w **zasoby** panelu, podobnie jak **przybornika** w programie Visual Studio. Oprócz formantów, znajdziesz wszystko, czego możesz dodać do Twojego obszaru roboczego w **zasoby** panelu, w tym stylów, multimediów, zachowań i efektów.

![Panel składników zasobów](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Pole wyszukiwania** wpisać **wyszukiwania** polu, aby filtrować listę zasobów.|
|![Tryb siatki i tryb listy](../designers/media/b1_2.png)|**Tryb siatki i tryb listy** przełączać się między **trybu siatki** widoku i **tryb listy** widoku zasobów.|
|![Kategorie zasobów](../designers/media/b1_3.png)|**Kategorie zasobów** kliknij kategorię lub podkategorię, aby wyświetlić listę zasobów w tej kategorii.|
|![Style](../designers/media/b1_4.png)|**Style** Pokaż wszystkie style, które są zawarte w słowniku zasobów.|
|![Opis](../designers/media/b1_5.png)|**Opis** Wyświetl opis wybranej kategorii lub podkategorii zasobów.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Przewodnik po przykładzie obiekty i oś czasu panelu

Użyj tego panelu do porządkowania obiektów w Twojego obszaru roboczego i, jeśli chcesz, aby animować je.

![Panel obiektów i osi czasu w trybie animacji](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Wyświetl obiekty](../designers/media/b1_1.png)|**Widok obiektów** przeglądać drzewo wizualne dokumentu. Przechodzić do różnych poziomów szczegółowości. Można również dodać warstwy w celu dokładniejszego porządkowania obiektów w obszarze kompozycji. W ten sposób można zablokować i je ukryć jako grupa.|
|![Wskaźnik trybu nagrywania](../designers/media/b1_2.png)|**Wskaźnik trybu nagrywania** Zobacz, czy rejestrowane zmiany właściwości na osi czasu.|
|![Selektor scenorysu](../designers/media/b1_3.png)|**Selektor scenorysu** wyświetlić listę scenorysy, które zostały utworzone.|
|![Zamknij scenorys](../designers/media/b1_4.png)|**Zamknij scenorys** zamknąć bieżący scenorysu.|
|![Opcje scenorysu](../designers/media/b1_5.png)|**Opcje scenorysu** odwrotna duplikatów, tworzenie, usuwanie, zmiana nazwy lub zamykanie scenorysu.|
|![Formanty odtwarzania](../designers/media/b1_6.png)|**Formanty odtwarzania** Nawiguj za pomocą osi czasu. Można również przeciągać wskaźnik odtwarzania w celu nawigowania (lub *czyszczenie*) osi czasu.|
|![Zwróć zakres do](../designers/media/b1_7.png)|**Zwróć zakres do** zakres widoku obiektów powrót do poprzedniego obiektu głównego lub poprzedniego zakresu. Można to zrobić tylko wtedy, gdy modyfikujesz stylu lub szablonu.|
|![Rekord klatki kluczowej](../designers/media/b1_8.png)|**Zarejestruj kluczową** Zapisz migawkę właściwości wybranego obiektu w bieżącym punkcie w czasie.|
|![Opcje przyciągania](../designers/media/b1_9.png)|**Opcje przyciągania** Ustaw przyciąganie do osi czasu, rozdzielczość przyciągania i wyłączyć przyciąganie do osi czasu.|
|![Odblokowanie blokady Ukryj show](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Pokaż/Ukryj**, **Zablokuj/Odblokuj** Pokaż lub Ukryj widoczności i blokowania opcje widoku obiektów.|
|![Pozycja wskaźnika odtwarzania na osi czasu](../designers/media/b1_11.png)|**Pozycja wskaźnika odtwarzania na osi czasu** wyświetlić bieżący czas w milisekundach. Można również bezpośrednio wpisać wartości czasu w tym polu, aby przejść do określonego punktu w czasie. Dokładność zależy od rozdzielczości przyciągania ustawionej w **opcje przyciągania**.|
|![Wskaźnik odtwarzania](../designers/media/b1_12.png)|**Wskaźnik odtwarzania** ustalić, w jakim punkcie czasu jest animacja. Przeciągając wskaźnik odtwarzania na osi czasu, można wyświetlić podgląd animacji.|
|![Ramki kluczowe ustawione na osiach czasu](../designers/media/b1_13.png)|**Ramki kluczowe ustawione na osiach czasu** Zmień wartość właściwości w określonym punkcie w czasie.|
|![Zmień kolejność obiektów](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Zmień kolejność obiektów** Ustaw kolejność wyświetlania obiektów. Kliknięcie tego przycisku pozwala rozmieścić obiekty w widoku struktury, według porządku osi Z (z przodu do tyłu) lub według kolejności znaczników (kolejności, w jakiej występują w **XAML** widoku).|
|![Powiększenie osi czasu](../designers/media/b1_15.png)|**Powiększenie osi czasu** Ustaw rozdzielczość powiększania osi czasu. Powiększanie pozwala bardziej szczegółowo edytować animację, a pomniejszenie przedstawia bardziej ogólny obraz zdarzeń w dłuższym okresie. Jeśli po powiększeniu nie można ustawić ramki kluczowej na żądanej pozycji w czasie, należy sprawdzić, czy ustawiono odpowiednio dużą rozdzielczość przyciągania.|
|![Objaśnienie 16](../designers/media/b5_label_16.png)|**Obszar kompozycji osi czasu** Wyświetl oś czasu i przesuwanie ramek kluczowych przez przeciąganie ich lub za pomocą menu skrótów.|

## <a name="tour-of-the-properties-panel"></a>Samouczek Panelu właściwości

Ten panel umożliwia wyświetlanie i modyfikowanie właściwości obiektu. Można również ustawić je bezpośrednio w obszarze kompozycji. Jeśli to zrobisz, zmiany właściwości zostaną odzwierciedlone w **właściwości** panelu.

![Panel właściwości](../designers/media/blend5_properties_panel.png)

**Kategorie** rozwijanie i zwijanie kategorie właściwości. Kliknij przycisk **rozwiń** ![rozwiń](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) i **Zwiń** ![Zwiń](../designers/media/b5_collapse_button.png) pokazać lub ukryć szczegóły kategorii.

|||
|-|-|
|![Nazwa i typ](../designers/media/b1_1.png)|**Nazwa i typ** wyświetlać ikony, nazwę i typ wybranego obiektu.|
|![Rozmieść według](../designers/media/b1_2.png)|**Rozmieść według** rozmieszczania właściwości alfabetycznie według nazwy, źródła lub kategorii.|
|![Właściwości pędzla](../designers/media/b1_3.png)|**Właściwości pędzla** Ustaw właściwości visual pędzle, takie jak Pędzel wypełnienia, obrysu pędzla i pędzla pierwszego planu.|
|![Edytor kolorów](../designers/media/b1_4.png)|**Edytor kolorów** jednolitego koloru i pędzle gradientów.|
|![Selektor kolorów](../designers/media/b1_5.png)|**Selektor kolorów** wybierz kolor.|
|![Kolor mikroukładami](../designers/media/b1_6.png)|**Kolor mikroukładami** wyświetlać kolor początkowy, bieżący kolor i ostatni kolor|
|![Kroplomierzy](../designers/media/b1_7.png)|**Kroplomierzy** Użyj kolor dowolnego elementu na ekranie. **Pipeta koloru** jest dostępna, gdy **pędzel pełnego koloru** jest zaznaczone. **Pipeta gradientu** jest dostępna, gdy **pędzla gradientu** jest zaznaczone.|
|![Właściwości i zdarzenia](../designers/media/b1_8.png)|**Właściwości i zdarzenia** Ustaw właściwości lub wybrać zdarzenia dla wybranego elementu.|
|![Pole wyszukiwania](../designers/media/b1_9.png)|**Pole wyszukiwania** wyszukiwać właściwości. Filtrowanie właściwości, które są wyświetlane, wpisując w polach **wyszukiwania** pole.|
|![Pędzel Edytor karty](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Pędzel, Edytor karty** wybierz edytor pędzla. Możesz wybrać **Brak pędzla**, **pędzel pełnego koloru**, **pędzla gradientu**, **pędzla kafelków**, lub **pędzla zasobów**.|
|![Zasób koloru](../designers/media/b1_11.png)|**Zasoby koloru** dotyczą dokładnie ten sam kolor inne właściwości. **Zasoby koloru** karta zawiera **zasoby lokalne** i **zasobów systemowych**.|
|![Przestrzeń kolorów RGB](../designers/media/b1_12.png)|**Przestrzeń kolorów RGB** modyfikacji koloru, dopasowując wartości **R**, **G**, lub **B** (czerwony, zielony, niebieski) edytory liczb.|
|![Kanał alfa](../designers/media/b1_13.png)|**Kanał alfa** zmodyfikuj wartość alfa przy użyciu numeru edytora obok **A**.|
|![Konwertuj kolor na zasób](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Konwertuj kolor na zasób** Konwertuj wybrany kolor na zasób koloru. Zasoby koloru są dostępne po kliknięciu na karcie Zasoby kolorów.|
|![](../designers/media/b1_15.png)|**Wartość szesnastkowa** wyświetlić wartość szesnastkową kolor wyświetlany.|
|![Objaśnienie 16](../designers/media/b5_label_16.png)|**Suwak gradientu** pojawia się tylko wtedy, gdy wybrano pędzla gradientu.|
|![Pokaż zaawansowane właściwości](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Pokaż zaawansowane właściwości** kategorii właściwości, które są rzadko używane.|

**Obejrzyj krótki film wideo:** ![Konfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [panelu właściwości](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Zobacz także

- [Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)
- [Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)
- [Projektowanie XAML w programach Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)
