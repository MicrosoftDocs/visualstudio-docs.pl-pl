---
title: Historia pikseli grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e0302e4b245a4fbf94d0eb49850101c404cd8a2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479958"
---
# <a name="graphics-pixel-history"></a>Historia pikseli grafiki
Okno Historia pikseli grafiki w analizatora grafiki programu Visual Studio pomaga w zrozumieniu wpływ pikseli określone przez zdarzenia Direct3D, jakie występują podczas ramka gry lub aplikacji.  
  
 To okno Historia pikseli:  
  
 ![Piksel z trzech zdarzeń Direct3D w jego historii. ](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Opis okno Historia pikseli  
 Korzystając z historii pikseli, można analizować wpływ piksel określonego obiektu docelowego renderowania Direct3D zdarzeń w ramce. Problem z renderowaniem do określonego zdarzenia Direct3D, nawet jeśli kolejne zdarzenia można wyznaczyć — albo pierwotnych kolejnych w tym samym zdarzeniu — zmienić kolor końcowy pikseli w dalszym ciągu. Na przykład piksel może być renderowane niepoprawnie i następnie zasłonięty przez inny, półprzezroczyste pikseli, aby ich kolorów są mieszane razem w obiektu. Tego rodzaju problem jest trudna do diagnozowania, jeśli masz tylko zawartość końcowego obiektu docelowego renderowania prowadzące.  
  
 Okno Historia pikseli Wyświetla całą historię piksel w trakcie zaznaczonej ramki. **Końcowego buforu ramki** w górnej części okna wyświetla kolor, który jest zapisywany do obiektu na końcu ramki, oraz dodatkowe informacje na temat pikseli, takie jak jego ekranu i ramki, która pochodzi z współrzędne. Ten obszar zawiera także **renderowania alfa** pole wyboru. Gdy to pole wyboru jest zaznaczone, **końcowego buforu ramki** pośredniego koloru wartości koloru i są wyświetlane z przezroczystość za pośrednictwem wzorzec szachownicy. Jeśli pole wyboru jest wyczyszczone, wartości kolorów kanału alfa jest ignorowana.  
  
 W dolnej części okna Wyświetla zdarzenia, które ma wpływ na kolor pikseli, wraz z możliwością **początkowej** i **końcowego** pseudo-zdarzenia, które reprezentują wartości początkowe i końcowe kolorów piksel w obiektu. Wartość początkowa kolor jest określany przez pierwsze zdarzenie, które zmienić kolor piksela (zazwyczaj `Clear` zdarzeń). Piksel w zawsze znajdują się te dwa pseudo-zdarzenia swoją historię nawet wtedy, gdy nie inne zdarzenia, których to dotyczy on. Jeśli inne zdarzenia wypróbowana wpływają na piksel, zostaną one wyświetlone między **początkowej** i **końcowego** zdarzenia. Zdarzenia można rozszerzyć, aby wyświetlić jego szczegóły. Proste zdarzeń takimi jak wyczyścić docelowego renderowania zdarzenia, które powoduje tylko wartości koloru. Bardziej złożone zdarzenia, takie jak wywołania rysowania Wygeneruj jeden lub więcej podstawowych, które mogą przyczynić się do kolor piksela.  
  
 Elementy podstawowe rysowanych przez zdarzenie są identyfikowane według typu pierwotnego i indeksu, wraz z łączną liczbę pierwotnych dla obiekt. Na przykład identyfikator, takich jak **trójkąt (1456) (6214)** oznacza, że element pierwotny odpowiada 1456th trójkąt w obiekcie, który składa się z 6214 trójkąty. Z lewej strony każdego pierwotny identyfikator jest ikonę, która zawiera podsumowanie wpływ, jaki element pierwotny, które miał na piksel. Elementy podstawowe, które mają wpływ na kolor pikseli są reprezentowane przez zaokrąglony prostokąt, który zostanie wypełniony kolorem wynik. Elementy podstawowe, które są wykluczone z mające wpływ na kolor pikseli są reprezentowane przez ikony, które wskazać, że piksel został wykluczony. Te ikony są opisane w sekcji [pierwotnych wykluczeń](#exclusion) dalszej części tego artykułu.  
  
 Można rozwinąć każdego pierwotnych, aby sprawdzić, jak dane wyjściowe programu do cieniowania pikseli zostało scalone z istniejącego koloru pikseli dostarczyło wyniku kolor. W tym miejscu można również przejrzeć lub debugowania kodu programu do cieniowania pikseli skojarzoną z typów pierwotnych i można rozwinąć węzła programu do cieniowania wierzchołków do sprawdzenia danych wejściowych programu do cieniowania wierzchołków.  
  
###  <a name="exclusion"></a> Pierwotne wykluczeń  
 Jeśli podstawowy został wykluczony z wpływających na kolor pikseli, wykluczenia może wystąpić z różnych przyczyn. Przyczyna każdy jest reprezentowany przez ikonę, która jest opisane w poniższej tabeli:  
  
|Ikona|Przyczynę wykluczenia|  
|----------|--------------------------|  
|![Ikona Błąd testu głębokość. ](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Piksel został wykluczony, ponieważ nie test głębi.|  
|![Ikona Błąd test przycinania. ](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Piksel został wykluczony, ponieważ nie test przycinania.|  
|![Ikona Błąd test wzornika. ](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Piksel został wykluczony, ponieważ test wzornika nie.|  
  
### <a name="draw-call-exclusion"></a>Wyłączenie wywołanie rysowania  
 W przypadku wszystkich elementów podstawowych do rysowania wywołania są wykluczone z wpływających na obiektu docelowego renderowania, ponieważ się one zakończyć niepowodzeniem testu, nie można rozwijać wywołanie rysowania i ikonę, która odpowiada przyczynę wykluczenia jest wyświetlany obok niej. Powody wykluczenia wywołanie rysowania przypominać powody wykluczenia pierwotnych, a ich ikony są podobne.  
  
### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania  
 Możesz sprawdzić i debugowania kodu dla wierzchołków, powłoki, domeny, programów do cieniowania geometrycznego i pikseli za pomocą formantów poniżej podstawowego, który został skojarzony z programu do cieniowania.  
  
##### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy programu do cieniowania  
  
1.  W **Historia pikseli grafiki** okna, zlokalizuj wywołanie rysowania, który odpowiada programu do cieniowania chcesz zbadać i rozwiń go.  
  
2.  W obszarze rysowania wywołanie tylko rozwinięty, wybierz podstawowy demonstrujący problem, który chcesz i rozwiń go.  
  
3.  W obszarze pierwotnych interesuje Cię, kliknij link tytuł programu do cieniowania — na przykład, kliknij link **obj:30 programu do cieniowania wierzchołków** Aby wyświetlić kod źródłowy programu do cieniowania wierzchołków.  
  
    > [!TIP]
    >  Liczba obiektów **obj:30**, identyfikuje to cieniowanie w interfejsie analizatora grafiki przykład w oknie etapy tabeli i potoku obiektu.  
  
##### <a name="to-debug-a-shader"></a>Do debugowania cieniowania  
  
1.  W **Historia pikseli grafiki** okna, zlokalizuj wywołanie rysowania, który odpowiada programu do cieniowania chcesz zbadać i rozwiń go.  
  
2.  Następnie, w obszarze wywołanie rysowania właśnie rozwiniętej, wybierz podstawowy demonstrujący problem interesuje i rozwiń go.  
  
3.  W obszarze pierwotnych interesuje Cię, wybierz **Rozpocznij debugowanie**. Ten punkt wejścia do wartości domyślnych debuger HLSL dla pierwszego wywołania funkcji programu do cieniowania dla odpowiednich typów pierwotnych, oznacza to, pierwszy pikseli lub wierzchołek jest przetwarzany przez programu do cieniowania. Istnieje tylko jeden piksel skojarzone z pierwotnego, ale więcej niż jednego wywołania programu do cieniowania wierzchołków linii i trójkąty.  
  
     Aby debugować wywołania programu do cieniowania wierzchołków określonego wierzchołka, rozwiń łącze tytuł VertexShader i Znajdź wierzchołka interesuje Cię, następnie wybierz polecenie **Rozpocznij debugowanie** obok niej.  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby poznać zdarzeń grafiki w historii pikseli, może być konieczne informacje dotyczące stanu urządzenia w czasie zdarzenia lub obiekty Direct3D, do których odwołuje się zdarzenie. Dla każdego zdarzenia w historii pikseli **Historia pikseli grafiki** zawiera łącza do urządzenia aktualnymi stanu i do powiązanych obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)