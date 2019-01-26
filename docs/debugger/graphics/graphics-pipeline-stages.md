---
title: Etapy potoku grafiki | Dokumentacja firmy Microsoft
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e54f3e485425b90a8ff0b6b0dbbca63d02574dc8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940248"
---
# <a name="graphics-pipeline-stages"></a>Etapy potoku grafiki
W oknie etapy potoku grafiki pomaga zrozumieć, jak wywołanie rysowania poszczególnych jest przekształcana w każdym etapie potoku grafiki Direct3D.  
  
 Jest to w oknie etapy potoku:  
  
 ![Obiekt 3D przechodzi przez kolejne etapy potoku.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Opis w oknie etapy potoku grafiki  
 W oknie etapy potoku wizualizuje wynik każdego etapu potoku grafiki oddzielnie dla każdego wywołania rysowania. Zazwyczaj wyniki etapów w trakcie wykonywania potoku są ukryte, co utrudnia powiedzieć, którym jest uruchomiony z problemem renderowania. Dzięki wizualizowaniu osobno każdy z etapów, w oknie etapy potoku można łatwo zobaczyć, gdzie rozpoczyna się problem — na przykład, można łatwo zobaczyć, kiedy etapu programu do cieniowania wierzchołków nieoczekiwanie powoduje, że obiektu do narysowania ekranem.  
  
 Po zidentyfikowaniu etapu, w której występuje ten problem, można użyć innych narzędzi Analizator grafiki do sprawdzenia, jak interpretować lub przekształcone dane. Problemy z renderowaniem, które pojawiają się na etapy potoku są często deskryptory format powiązane niepoprawne wierzchołka, programy pracowały programu do cieniowania lub nieprawidłowo stanu.  
  
### <a name="links-to-related-graphics-objects"></a>Linki do powiązanych grafikach obiektów  
 Aby ustalić, dlaczego wywołanie rysowania wchodzi w interakcje w sposób przy użyciu potoku grafiki potrzebna jest czasami dodatkowy kontekst. Aby ułatwić znajdowanie ten dodatkowy kontekst, łącza okna etapy potoku grafiki, aby jeden lub więcej obiektów, które zapewniają dodatkowy kontekst związane z tym, co się dzieje w potoku grafiki.  
  
- W Direct3D 12 ten obiekt jest zwykle listę poleceń.  
  
- W interfejsie Direct3D 11 ten obiekt jest zwykle kontekstu urządzenia grafiki.  
  
  Te linki stanowią część bieżącego podpis zdarzenia grafiki, który znajduje się w lewym górnym rogu okna etapy potoku grafiki. Wykonaj jedną z poniższych linków, aby sprawdzić szczegółowe informacje o obiekcie.  
  
### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania  
 Można zbadać i debugowania kodu dla wierzchołków, kadłuba, domeny, programów do cieniowania geometrii i piksela za pomocą kontrolek na dole ich odpowiednich etapów w oknie etapy potoku.  
  
#### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy modułu cieniującego  
  
-   W **etapy potoku grafiki** oknie Znajdź etapu programu do cieniowania, który odnosi się do programu do cieniowania do sprawdzenia. Następnie poniżej obrazu podglądu wykonaj link tytułu etapu programu do cieniowania — na przykład, kliknij link **obj:30 program do cieniowania wierzchołków** Aby wyświetlić kod źródłowy modułu cieniującego wierzchołek.  
  
    > [!TIP]
    >  Liczba obiektów **obj:30**, identyfikuje ten program do cieniowania w całym interfejsu analizatora grafiki przykład w oknie historii tabeli i piksela obiektu.  
  
#### <a name="to-debug-a-shader"></a>Do debugowania cieniowania  
  
-   W **etapy potoku grafiki** oknie Znajdź etapu programu do cieniowania, który odnosi się do programu do cieniowania chcesz debugować. Następnie poniżej obrazu (wersja zapoznawcza) wybierz **Rozpocznij debugowanie**. Ten punkt wejścia do debugera HLSL ustawienia domyślne pierwsze wywołanie modułu cieniującego dla odpowiedniego etapu, czyli pierwszy pikseli, wierzchołków lub podstawowego, który jest przetwarzany przez moduł cieniujący podczas tego wywołania rysowania. Wywołania tego programu do cieniowania pikseli lub wierzchołka jest możliwy za pośrednictwem **Historia pikseli grafiki**.  
  
### <a name="the-pipeline-stages"></a>Etapy potoku  
 W oknie etapy potoku wizualizuje tylko etapy potoku, które były aktywne podczas wywołania rysowania. Każdy etap potoku grafiki przekształca dane wejściowe z poprzedniego etapu i przekazuje jego wynik do kolejnego etapu. Podczas pierwszego etapu — asemblera wejściowego — indeks i wierzchołka dane z aplikacji jako dane wejściowe; ostatni etap — scalanie danych wyjściowych — łączy w sobie nowo renderowane pikseli wraz z bieżącą zawartość obiektu lub obiekt docelowy renderowania jako dane wyjściowe, aby wygenerować ostateczny obraz zostanie wyświetlony na ekranie.  
  
> [!NOTE]
>  Obliczających programów cieniujących nie są obsługiwane w **etapy potoku grafiki** okna.  
  
 **Asembler wejściowy**  
 Asembler dane wejściowe odczytuje dane indeksu i wierzchołka, określony przez aplikację i składa się ona do sprzętu graficznego.  
  
 W oknie etapy potoku wyjściowy asemblera dane wejściowe są wizualizowane jako model szkielet. Aby Przyjrzyj się bliżej wynik, wybierz pozycję **asemblera dane wejściowe** w **etapy potoku grafiki** przeglądać zmontowanych wierzchołków w pełnej 3D za pomocą edytora modelu.  
  
> [!NOTE]
>  Jeśli `POSITION` semantycznego nie jest obecny w danych wyjściowych asemblera wejściowego, a następnie będą wyświetlane żadne informacje w **asemblera wejściowego** etapu.  
  
 **Program do cieniowania wierzchołków**  
 Etapu programu do cieniowania wierzchołków przetwarza wierzchołków, zwykle wykonywanie operacji, takich jak przekształcenie, powłoka i oświetlenia. Programów do cieniowania wierzchołków utworzyć taką samą liczbę wierzchołków, których one przyjmuje jako dane wejściowe.  
  
 W oknie etapy potoku dane wyjściowe programu do cieniowania wierzchołków są wizualizowane jako obraz szkielet. Aby Przyjrzyj się bliżej wynik, wybierz pozycję **program do cieniowania wierzchołków** w **etapy potoku grafiki** systemu windows, aby wyświetlić przetworzonych wierzchołków w edytorze obrazu.  
  
> [!NOTE]
>  Jeśli `POSITION` lub `SV_POSITION` semantyki nie są obecne w danych wyjściowych programu do cieniowania wierzchołków, a następnie będą wyświetlane żadne informacje w **program do cieniowania wierzchołków** etapu.  
  
 **Moduł cieniujący kadłuba** (Direct3D 11 i Direct3D 12 tylko)  
 Procesy etapu programu do cieniowania powłoki kontrolować punkty, które definiują powierzchni niskiego rzędu, takich jak linii, trójkąt lub cztery. Jako dane wyjściowe generuje poprawki geometrii wyższego rzędu i stałe poprawki, które są przekazywane do etapu tworzenia mozaiki stałej funkcji.  
  
 Etapu programu do cieniowania powłoki nie są wizualizowane w oknie etapy potoku.  
  
 **Etap tessellator** (Direct3D 11 i Direct3D 12 tylko)  
 Na etapie tessellator jest jednostka sprzętu fixed — funkcja (nieprzewidywalnych), który wstępnie przetwarza domeny reprezentowany przez dane wyjściowe programu do cieniowania powłoki. Jako dane wyjściowe, tworzy wzorzec próbkowania, domeny i zestawu mniejszych elementów podstawowych — punkty, linii, trójkąty — połączone z tych przykładów.  
  
 Na etapie tessellator nie są wizualizowane w oknie etapy potoku.  
  
 **Program do cieniowania domeny** (Direct3D 11 i Direct3D 12 tylko)  
 Etapu programu do cieniowania domeny przetwarza geometrii wyższego rzędu poprawki z moduł cieniujący kadłuba współczynniki mozaikowania razem z etapu tworzenia mozaiki. Mozaikowania, które czynniki mogą być tessellator czynniki wejściowe także dane wyjściowe czynników. Jako dane wyjściowe jest ona obliczana położenie wierzchołka punkcie poprawki dane wyjściowe, zgodnie z czynniki tessellator.  
  
 Etapu programu do cieniowania domeny nie są wizualizowane w oknie etapy potoku.  
  
 **Program do cieniowania geometrii**  
 Etapu programu do cieniowania geometrii przetwarza całego podstawowych — punkty, linie lub trójkąty — wraz z danymi wierzchołek opcjonalne dla krawędzi sąsiadujących elementów podstawowych. Inaczej niż w przypadku programów do cieniowania wierzchołków programów do cieniowania geometrii może wygenerować więcej lub mniej elementów podstawowych nie przyjmują jako dane wejściowe.  
  
 W oknie etapy potoku dane wyjściowe programu do cieniowania geometrii są wizualizowane jako obraz szkielet. Aby Przyjrzyj się bliżej wynik, wybierz pozycję **cieniowania geometrycznego** w **etapy potoku grafiki** okna, aby wyświetlić w edytorze obrazu przetworzonej podstawowych.  
  
 **Stream dane wyjściowe etapu**  
 Na etapie dane wyjściowe strumienia może przechwytywać przekształcone w nim elementów podstawowych, przed rasteryzacji i zapisanie ich do pamięci. stamtąd dane mogą być ponownie skierowany jako dane wejściowe do wcześniejszych etapach potoku grafiki lub odczytywane przez procesor CPU.  
  
 Na etapie dane wyjściowe strumienia nie są wizualizowane w oknie etapy potoku.  
  
 **Etap rasteryzatora**  
 Etap rasteryzatora jest jednostki sprzętu (nieprzewidywalnych) fixed — funkcja, która konwertuje podstawowych wektor — punkty, linii, trójkąty — do rastrowych obrazu przez wykonanie konwersji skanowania linii. Podczas rasteryzacji wierzchołki są przekształcane na jednorodnego przestrzeni przycinania i przycięte. Jako dane wyjściowe są mapowane do cieniowania pikseli i atrybuty każdego wierzchołka są interpolowane przez element pierwotny i udostępnienie do programu do cieniowania pikseli.  
  
 Na etapie rasteryzatora nie są wizualizowane w oknie etapy potoku.  
  
 **Program do cieniowania pikseli**  
 Piksel programu do cieniowania etapu procesy rasteryzowany prymitywów wraz z danymi wierzchołek interpolowanego do generowania każdego piksela wartości takich jak kolor i głębi.  
  
 W oknie etapy potoku dane wyjściowe programu do cieniowania pikseli są wizualizowane jako obraz kolorowych rastrowych. Aby Przyjrzyj się bliżej wynik, wybierz pozycję **programu do cieniowania pikseli** w **etapy potoku grafiki** okna, aby wyświetlić w edytorze obrazu przetworzonej podstawowych.  
  
 **Scalanie danych wyjściowych**  
 Etap połączenia danych wyjściowych łączy efekt nowo renderowane pikseli, wraz z istniejącą zawartość elementu ich odpowiednich buforów — kolor, głębi i wzornika — Aby utworzyć nowe wartości na liście bufory.  
  
 W oknie etapy potoku danych wyjściowych połączenia dane wyjściowe są wizualizowane jako obraz kolorowych rastrowych. Aby Przyjrzyj się bliżej wyniki, wybierz pozycję **scalanie danych wyjściowych** w **etapy potoku grafiki** okna, aby wyświetlić scalonych bufor ramki.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Wierzchołka i programu do cieniowania geometrii w wersji zapoznawczej  
 Po wybraniu etapu programu do cieniowania wierzchołków lub geometrii w **etapy potoku** okna, można wyświetlić dane wejściowe i dane wyjściowe z programu do cieniowania w panelu poniżej.  W tym miejscu znajdziesz szczegółowe informacje dotyczące listy wierzchołków dostarczane do programów do cieniowania, po zostały zgromadzone przez etap asemblera wejściowego.  

 ![Podgląd buforu wejściowego etapu programu do cieniowania wierzchołków](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Aby wyświetlić wynik etapu programu do cieniowania wierzchołków, wybierz program do cieniowania wierzchołków etapu miniaturę, aby wyświetlić w pełnym rozmiarze, szkielet rasteryzowany oczek po jego został przekształcony przez program do cieniowania wierzchołków.  
  
 ![Podgląd wyników etapu programu do cieniowania wierzchołka](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)