---
title: Historia pikseli grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20b33c987cf7e2b1ab57160b4f4917246d9030b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733173"
---
# <a name="graphics-pixel-history"></a>Historia pikseli grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno Historia pikseli grafiki w analizatora grafiki programu Visual Studio pomaga zrozumieć wpływ piksela określone przez zdarzenia Direct3D występujących podczas ramki grach i aplikacjach.  
  
 Jest to okno Historia pikseli:  
  
 ![Piksel z trzech zdarzenia Direct3D w jego historię. ](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Opis w oknie Historia pikseli  
 Korzystając z historii pikseli, można analizować, piksel określonego obiektu docelowego renderowania wpływu zdarzenia Direct3D horyzoncie. Można wyznaczyć z problemem renderowania do określonego zdarzenia Direct3D, nawet jeśli jest to kolejne zdarzenia — lub kolejnych elementów podstawowych, w tym samym zdarzeniu — ulegają zmianie wartości ostateczny koloru piksela. Na przykład jeden piksel może niepoprawnie renderowany i następnie zasłonięte przez inną, półprzezroczyste pikseli, aby ich kolorów są mieszane ze sobą w bufor ramki. Tego rodzaju problemy będą trudne do zdiagnozowania, jeśli masz tylko zawartość końcowego obiektu docelowego renderowania przeprowadzenie Cię.  
  
 W oknie historii pikseli wyświetlane pełnej historii pikseli w miarę upływu zaznaczonej klatki. **Końcowego buforu ramki** u góry okna wyświetla kolor, który jest zapisywany bufor ramki na końcu ramki, oraz dodatkowe informacje na temat pikseli, takie jak jego ekranu i ramkę, która pochodzi z współrzędne. Ten obszar zawiera również **Renderuj alfa** pole wyboru. Gdy to pole wyboru jest zaznaczone, **końcowego buforu ramki** koloru i wartości pośrednich kolorów są wyświetlane z przezroczystością na wzorzec szachownicy. Jeśli pole wyboru jest wyczyszczone, kanał alfa, wartości kolorów jest ignorowana.  
  
 W dolnej części okna Wyświetla zdarzenia, które mieli Państwo możliwość wpływają na kolor piksela, wraz z **początkowej** i **końcowego** pseudo-zdarzenia, które reprezentują wartości początkowe i końcowe kolorów piksel w bufor ramki. Początkowa wartość koloru jest określana przez pierwsze zdarzenie, która się zmieniła kolor piksela (zazwyczaj `Clear` zdarzeń). Piksel w zawsze znajdują się te dwa pseudo-zdarzenia jego historię nawet wtedy, gdy żadne inne zdarzenia, wpływ na jej. Jeśli inne zdarzenia mieli Państwo możliwość wpływają na piksel, zostaną one wyświetlone między **początkowej** i **końcowego** zdarzenia. Zdarzenia można rozszerzyć, aby wyświetlić jego szczegóły. Proste zdarzeń, takich jak te, które czyszczą docelowego renderowania zdarzenia powoduje po prostu wartość koloru. Bardziej złożone zdarzenia, takie jak wywołania rysowania Wygeneruj jeden lub więcej elementów podstawowych, które mogą przyczynić się do koloru piksela.  
  
 Elementy podstawowe rysowanych przez zdarzenie są identyfikowane przez ich typ pierwotny i indeks, wraz z całkowitą liczbą pierwotnego obiektu. Na przykład identyfikator, takie jak **trójkąt (1456) (6214)** oznacza, że element pierwotny odpowiada 1456th trójkąta w obiekcie, który składa się z 6214 trójkąty. Po lewej stronie każdej pierwotny identyfikator znajduje się ikona, który podsumowuje wpływ, jaki element pierwotny miał na piksel. Elementy podstawowe, które wpływają na kolor piksela są reprezentowane przez zaokrąglony prostokąt, który zostanie wypełniony kolorem wynik. Elementy podstawowe, które są wykluczone z mające wpływ na kolor piksela są reprezentowane przez ikony wskazujące przyczynę, piksel został wykluczony. Te ikony są opisane w sekcji [pierwotnych wykluczeń](../debugger/graphics-pixel-history.md#exclusion) w dalszej części tego artykułu.  
  
 Można rozwinąć każdego podstawowego, aby sprawdzić, jak dane wyjściowe programu do cieniowania pikseli została scalona z istniejących kolor piksela, aby otrzymać kolor wyniku. W tym miejscu można zbadać lub debugowanie kodu programu do cieniowania pikseli, która jest skojarzona z podstawowego i można rozwinąć węzła programu do cieniowania wierzchołków do zbadania cieniowania wierzchołków, danych wejściowych.  
  
###  <a name="exclusion"></a> Pierwotny wykluczeń  
 Jeśli podstawowy jest wykluczony z wpływu na kolor piksela, wyłączenie może wystąpić z różnych powodów. Każdy powód jest reprezentowany przez ikonę która jest opisane w poniższej tabeli:  
  
|Ikona|Przyczynę wyłączenia|  
|----------|--------------------------|  
|![Ikona niepowodzenia testu głębi. ](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|Piksel został wykluczony, ponieważ nie powiodło się test głębi.|  
|![Ikona niepowodzenia testu przycinania. ](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|Piksel został wykluczony, ponieważ test przycinania został zakończony niepowodzeniem.|  
|![Ikona błędu test wzornika. ](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|Piksel został wykluczony, ponieważ test wzornika zakończone niepowodzeniem.|  
  
### <a name="draw-call-exclusion"></a>Wykluczenie wywołania rysowania  
 Jeśli wywołanie wszystkich elementów podstawowych do rysowania są wykluczane z wpływu na obiektu docelowego renderowania, ponieważ one zakończyć niepowodzeniem test, a następnie wywołania rysowania, nie można rozwijać i ikonę która odpowiada z przyczyn wyłączenia jest wyświetlany obok niej. Powody wykluczenia wywołanie rysowania przypominają powody wykluczenia pierwotnych, a ich ikony są podobne.  
  
### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania  
 Można zbadać i debugowania kodu dla wierzchołków, kadłuba, domeny, programów do cieniowania geometrii i piksela za pomocą kontrolek poniżej podstawowego, który jest skojarzony z modułem cieniującym.  
  
##### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy modułu cieniującego  
  
1.  W **Historia pikseli grafiki** oknie Znajdź wywołania rysowania, która odnosi się do programu do cieniowania chcesz zbadać i rozwiń go.  
  
2.  W obszarze rysowania Zadzwonimy do Ciebie po prostu rozwinięte, wybierz podstawowy, który demonstruje problem, który chcesz wziąć i rozwiń go.  
  
3.  W obszarze podstawowego interesuje Cię, skorzystaj z linku tytuł programu do cieniowania — na przykład, kliknij link **obj:30 program do cieniowania wierzchołków** Aby wyświetlić kod źródłowy modułu cieniującego wierzchołek.  
  
    > [!TIP]
    >  Liczba obiektów **obj:30**, identyfikuje ten program do cieniowania w całym interfejsu analizatora grafiki przykład w oknie etapy potoku i tabela obiektu.  
  
##### <a name="to-debug-a-shader"></a>Do debugowania cieniowania  
  
1.  W **Historia pikseli grafiki** oknie Znajdź wywołania rysowania, która odnosi się do programu do cieniowania chcesz zbadać i rozwiń go.  
  
2.  Następnie w obszarze wywołanie rysowania właśnie rozwiniętej, wybierz podstawowy, który pokazuje problem interesuje i rozwiń go.  
  
3.  W obszarze podstawowego interesuje Cię, wybierz opcję **Rozpocznij debugowanie**. Ten punkt wejścia do wartości domyślnych debugera HLSL pierwszego wywołania modułu cieniującego dla odpowiedniego podstawowego — czyli pierwszej pikseli lub wierzchołek, który jest przetwarzany przez programu do cieniowania. Istnieje tylko jeden piksel, skojarzony element pierwotny, ale ma więcej niż jednego wywołania programu do cieniowania wierzchołków linii i trójkąty.  
  
     Aby debugować wywołania programu do cieniowania wierzchołków dla określonego wierzchołka, rozwiń link tytułu VertexShader i Znajdź wierzchołka interesuje Cię, następnie wybierz **Rozpocznij debugowanie** obok niej.  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby poznać zdarzenia grafiki w historii pikseli, może być konieczne informacje dotyczące stanu urządzenia w czasie zdarzenia lub obiekty Direct3D, które są przywoływane przez zdarzenie. Dla każdego zdarzenia w historii pikseli **Historia pikseli grafiki** zawiera łącza do urządzenia obowiązywały stanu i do powiązanych obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Brak obiektów spowodowany stanem urządzenia](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



