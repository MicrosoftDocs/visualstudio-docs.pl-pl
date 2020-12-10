---
title: Grafika — historia pikseli | Microsoft Docs
description: Rozwiązywanie problemów z renderowaniem przez Wyświetlanie historii określonego piksela. Historia pikseli grafiki pokazuje efekty zdarzeń Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b12264c610d291ff49be0524663141a59082e9e
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995307"
---
# <a name="graphics-pixel-history"></a>Historia pikseli grafiki
Okno Historia pikseli grafiki w analizator grafiki programu Visual Studio pomaga zrozumieć, w jaki sposób zdarzenia programu Direct3D występują na określonym pikselu, które wystąpiły w ramach gry lub aplikacji.

 Jest to okno historii pikseli:

 ![Piksel z trzema zdarzeniami Direct3D w swojej historii.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Zrozumienie okna historii pikseli
 Za pomocą historii pikseli można analizować, w jaki sposób zdarzenia Direct3D mają wpływ na określony piksel obiektu docelowego renderowania. Możesz wskazać problem z renderowaniem w konkretnym zdarzeniu Direct3D, nawet gdy kolejne zdarzenia — lub kolejne elementy podstawowe w tym samym zdarzeniu — Kontynuuj zmianę końcowej wartości koloru piksela. Na przykład piksel może być niepoprawnie renderowany, a następnie zasłonięty przez inny, półprzezroczysty piksel, tak aby ich kolory zostały zmieszane w bufor ramki. Ten rodzaj problemu może być trudny do zdiagnozowania, jeśli masz tylko ostateczną zawartość elementu docelowego renderowania, aby Ci pomóc.

 W oknie Historia pikseli zostanie wyświetlona kompletna Historia pikseli w ramach kursu wybranej ramki. **Ostatni bufor ramki** w górnej części okna wyświetla kolor, który jest zapisywana w bufor ramki na końcu ramki, wraz z dodatkowymi informacjami o pikselach, takimi jak klatka, z której pochodzi i współrzędne ekranu. Ten obszar zawiera również pole wyboru **Renderuj alfa** . Gdy to pole wyboru jest zaznaczone, kolor **buforu ramki końcowej** i pośrednich wartości koloru są wyświetlane z przezroczystością na wzorcu szachownicy. Jeśli pole wyboru jest wyczyszczone, kanał alfa wartości koloru jest ignorowany.

 W dolnej części okna są wyświetlane zdarzenia, które miały wpływ na kolor piksela oraz **początkowe** i **końcowe** pseudo zdarzeń, które reprezentują początkowe i końcowe wartości koloru piksela w bufor ramki. Początkowa wartość koloru jest określana przez pierwsze zdarzenie, które zmieniło kolor piksela (zazwyczaj jest to `Clear` zdarzenie). Piksel zawsze mają te dwa pseudo zdarzeń w swojej historii, nawet jeśli nie ma żadnych innych zdarzeń. Gdy inne zdarzenia mają wpływ na piksel, są wyświetlane między zdarzeniami **początkowymi** i **końcowymi** . Zdarzenia mogą być rozwinięte, aby pokazać ich szczegóły. W przypadku prostych zdarzeń, takich jak te, które wyczyścili obiekt docelowy renderowania, efekt zdarzenia jest tylko wartością koloru. Bardziej złożone zdarzenia, takie jak wywołania rysowania, generują co najmniej jeden element pierwotny, który może współtworzyć kolor piksela.

 Elementy pierwotne, które były rysowane przez zdarzenie, są identyfikowane przez ich typ pierwotny i indeks oraz łączną liczbę pierwotną dla obiektu. Na przykład, identyfikator, taki jak **Trójkąt (1456) z (6214)** oznacza, że pierwotna odnosi się do trójkąta 1456th w obiekcie, który składa się z 6214 trójkąty. Po lewej stronie każdego identyfikatora pierwotnego jest ikona, która podsumowuje efekt pierwotny w pikselach. Elementy pierwotne, które wpływają na kolor pikseli, są reprezentowane przez zaokrąglony prostokąt, który jest wypełniony kolorem wynikowym. Elementy pierwotne, które są wykluczone z mają wpływ na kolor pikseli, są reprezentowane przez ikony wskazujące przyczynę wykluczenia piksela. Te ikony są opisane w sekcji [pierwotne wykluczenie](#exclusion) w dalszej części tego artykułu.

 Można rozwinąć każdy element pierwotny, aby określić, jak dane wyjściowe programu do cieniowania pikseli zostały scalone z istniejącym kolorem pikseli w celu uzyskania koloru wynikowego. W tym miejscu można również przeanalizować lub debugować kod programu do cieniowania pikseli skojarzony z elementem pierwotnym, a następnie można rozwinąć węzeł cieniowania wierzchołków, aby przeanalizować dane wejściowe programu do cieniowania wierzchołków.

### <a name="primitive-exclusion"></a><a name="exclusion"></a> Wykluczenia pierwotne
 Jeśli element pierwotny jest wykluczony z wpływu na kolor pikseli, wykluczenie może wystąpić z różnych powodów. Każdy powód jest reprezentowany przez ikonę, która jest opisana w tej tabeli:

|Ikona|Przyczyna wykluczenia|
|----------|--------------------------|
|![Ikona niepowodzenia testu głębokości.](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Piksel został wykluczony, ponieważ test głębokości został zakończony niepowodzeniem.|
|![Ikona niepowodzenia testu podbiegu.](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Piksel został wykluczony, ponieważ test przycinania został zakończony niepowodzeniem.|
|![Ikona niepowodzenia testu wzornika.](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Piksel został wykluczony, ponieważ test wzornika został zakończony niepowodzeniem.|

### <a name="draw-call-exclusion"></a>Wykluczanie wywołania rysowania
 Jeśli wszystkie elementy podstawowe w wywołaniu rysowania są wykluczone z wpływu na obiekt docelowy renderowania, ponieważ kończą się niepowodzeniem testu, wywołanie rysowania nie może być rozwinięte, a ikona odpowiadająca przyczynie wykluczenia jest wyświetlana obok niej. Przyczyny wykluczenia z połączeń rysowania są podobne do przyczyn wykluczenia pierwotnego, a ich ikony są podobne.

### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania
 Można przeanalizować i debugować kod dla wierzchołków, kadłuba, domeny, geometrii i cieniowania pikseli przy użyciu kontrolek poniżej elementu podstawowego, który jest skojarzony z cieniem.

##### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy programu do cieniowania

1. W oknie **Historia pikseli grafiki** zlokalizuj wywołanie rysowania odpowiadające programowi cieniującego, który ma zostać sprawdzony i rozwinięty.

2. W obszarze właśnie rozwinięte wywołanie rysowania wybierz element podstawowy, który pokazuje problem, który Cię interesuje, i rozwiń go.

3. W obszarze pierwotny, który Cię interesuje, postępuj zgodnie z linkiem do tytułu modułu cieniującego — na przykład postępuj zgodnie z tym, aby wyświetlić kod źródłowy programu **do cieniowania** wierzchołka.

    > [!TIP]
    > Numer obiektu, **obj: 30**, identyfikuje ten program do cieniowania w interfejsie analizatora grafiki, na przykład w oknie tabela obiektów i etapy potoku.

##### <a name="to-debug-a-shader"></a>Aby debugować cieniowanie

1. W oknie **Historia pikseli grafiki** zlokalizuj wywołanie rysowania odpowiadające programowi cieniującego, który ma zostać sprawdzony i rozwinięty.

2. Następnie w obszarze dokładnie rozwinięte wywołanie rysowania wybierz element podstawowy, który pokazuje problem, który Cię interesuje, i rozwiń go.

3. W obszarze pierwotny interes wybierz pozycję **Rozpocznij debugowanie**. Ten punkt wejścia do debugera HLSL domyślnie określa pierwsze wywołanie cieniowania dla odpowiadającego elementu pierwotnego — czyli pierwszy piksel lub wierzchołek przetworzony przez program do cieniowania. Istnieje tylko jeden piksel skojarzony z elementem pierwotnym, ale istnieje więcej niż jedno wywołanie programu do cieniowania wierzchołka dla linii i trójkątów.

     Aby debugować wywołanie programu do cieniowania wierzchołków dla określonego wierzchołka, rozwiń link tytułu VertexShader i Znajdź interesujący Cię wierzchołek, a następnie wybierz **Rozpocznij debugowanie** obok niego.

### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych
 Aby zrozumieć zdarzenia grafiki w historii pikseli, może być konieczne informacje o stanie urządzenia w momencie zdarzenia lub o obiektach Direct3D, do których odwołuje się zdarzenie. Dla każdego zdarzenia w historii pikseli, **Historia pikseli grafiki** zawiera linki do stanu bieżącego urządzenia i pokrewnych obiektów.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)
- [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)