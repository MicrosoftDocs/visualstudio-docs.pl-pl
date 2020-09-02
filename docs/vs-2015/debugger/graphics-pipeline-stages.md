---
title: Etapy potoku grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9eee83ba90248c15387771f355919e345375ff05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824963"
---
# <a name="graphics-pipeline-stages"></a>Etapy potoku grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno etapy potoku grafiki ułatwia zrozumienie, w jaki sposób poszczególne wywołania rysowania są przekształcane przez poszczególne etapy potoku grafiki Direct3D.  
  
 To jest okno Etapy potoku:  
  
 ![Obiekt 3&#45;D przechodzi przez etapy potoku.](../debugger/media/gfx-diag-demo-pipeline-stages-orientation.png "gfx_diag_demo_pipeline_stages_orientation")  
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Informacje o oknie etapy potoku grafiki  
 Okno etapy potoku wizualizowa wyniki poszczególnych etapów potoku grafiki osobno dla każdego wywołania rysowania. Zwykle wyniki etapów w środku potoku są ukryte, dzięki czemu trudno jest stwierdzić, gdzie został uruchomiony problem z renderowaniem. Wizualizacja poszczególnych etapów polega na tym, że okno Etapy potoku ułatwia sprawdzenie, gdzie zaczyna się problem — na przykład można łatwo zobaczyć, kiedy Etap cieniowania wierzchołka nieoczekiwanie powoduje, że obiekt jest rysowany poza ekranem.  
  
 Po zidentyfikowaniu etapu, w którym występuje ten problem, można użyć innych narzędzi analizatora grafiki do sprawdzenia, jak dane zostały zinterpretowane lub przekształcone. Problemy z renderowaniem, które pojawiają się w etapach potoku, często są związane z nieprawidłowymi deskryptorami formatu wierzchołków, programami do cieniowania debugowania lub nieprawidłowo skonfigurowanym stanem.  
  
### <a name="links-to-related-graphics-objects"></a>Linki do powiązanych obiektów graficznych  
 Czasami trzeba dodać dodatkowy kontekst, aby określić, dlaczego wywołanie rysowania współdziała w określony sposób z potokiem grafiki. Aby ułatwić znalezienie tego dodatkowego kontekstu, okno Etapy potoku grafiki łączy się z co najmniej jednym obiektem, który zapewnia dodatkowy kontekst związany z tym, co dzieje się w potoku grafiki.  
  
- W programie Direct3D 12 Ten obiekt jest zazwyczaj listą poleceń.  
  
- W programie Direct3D 11 ten obiekt jest zazwyczaj kontekstem urządzenia graficznego.  
  
  Te linki są częścią bieżącej sygnatury zdarzenia grafiki, która znajduje się w lewym górnym rogu okna etapy potoku grafiki. Wykonaj dowolne z tych linków, aby zapoznać się z dodatkowymi szczegółami dotyczącymi obiektu.  
  
### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania  
 Można przeanalizować i debugować kod dla wierzchołków, kadłuba, domeny, geometrii i cieniowania pikseli przy użyciu kontrolek w dolnej części poszczególnych etapów w oknie etapy potoku.  
  
##### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy programu do cieniowania  
  
- W oknie **etapy potoku grafiki** zlokalizuj Etap cieniowania, który odnosi się do programu do cieniowania, który ma zostać sprawdzony. Następnie, poniżej obrazu podglądu, postępuj zgodnie z linkiem do tytułu etapu cieniowania — na przykład postępuj zgodnie z tym, aby wyświetlić kod źródłowy modułu cieniującego wierzchołka linku **: 30** .  
  
    > [!TIP]
    > Numer obiektu, **obj: 30**, identyfikuje ten program do cieniowania w interfejsie analizatora grafiki, taki jak w oknie Historia obiektów i w pikselach.  
  
##### <a name="to-debug-a-shader"></a>Aby debugować cieniowanie  
  
- W oknie **etapy potoku grafiki** zlokalizuj Etap cieniowania, który odnosi się do programu do cieniowania, który ma być debugowany. Następnie, poniżej obrazu podglądu, wybierz **Rozpocznij debugowanie**. Ten punkt wejścia do debugera HLSL jest domyślnie używany do pierwszego wywołania cieniowania dla odpowiedniego etapu — czyli pierwszego piksela, wierzchołka lub elementu pierwotnego, który jest przetwarzany przez program do cieniowania podczas tego wywołania. Za pomocą **historii pikseli grafiki**można uzyskać dostęp do wywołań tego modułu cieniującego w określonym pikselu lub wierzchołku.  
  
### <a name="the-pipeline-stages"></a>Etapy potoku  
 Okno etapy potoku wizualizuje tylko etapy potoku, które były aktywne podczas wywołania rysowania. Każdy etap potoku grafiki przekształca dane wejściowe z poprzedniego etapu i przekazuje wynik do kolejnego etapu. Pierwszy etap — Asembler wejściowy — pobiera dane indeksów i wierzchołków z aplikacji jako dane wejściowe; bardzo ostatni etap — scalanie danych wyjściowych — łączy nowo renderowane piksele z bieżącą zawartością bufor ramki lub obiektu docelowego renderowania jako dane wyjściowe, aby utworzyć obraz końcowy widoczny na ekranie.  
  
> [!NOTE]
> Cieniowanie obliczeniowe nie są obsługiwane w oknie **etapy potoku grafiki** .  
  
 **Asembler wejściowy**  
 Asembler wejściowy odczytuje dane indeksów i wierzchołków określone przez aplikację i składa je dla sprzętu graficznego.  
  
 W oknie etapy potoku, dane wyjściowe asemblera wejściowego są wizualizowane jako model szkieletowy. Aby przyjrzeć się bliżej wyniku, wybierz pozycję **asembler wejściowy** w oknie **etapy potoku grafiki** , aby wyświetlić złożone wierzchołki w pełnej 3D przy użyciu edytora modelu.  
  
> [!NOTE]
> Jeśli `POSITION` semantyka nie występuje w danych wyjściowych asemblera wejściowego, nic nie zostanie wyświetlone na etapie **asemblera wejściowego** .  
  
 **Program do cieniowania wierzchołków**  
 Etap modułu cieniującego wierzchołków przetwarza wierzchołki, zazwyczaj wykonując operacje, takie jak przekształcanie, tworzenie karnacji i oświetlenie. Programy do cieniowania wierzchołków tworzą tę samą liczbę wierzchołków, które pobierają jako dane wejściowe.  
  
 W oknie etapy potoku, dane wyjściowe programu do cieniowania wierzchołka są wizualizowane jako obraz szkieletu rastrowego. Aby przyjrzeć się bliżej wyniku, wybierz opcję program do **cieniowania wierzchołków** w oknach **etapy potoku grafiki** , aby wyświetlić przetworzone wierzchołki w edytorze obrazów.  
  
> [!NOTE]
> Jeśli `POSITION` `SV_POSITION` semantyka lub nie występuje w danych wyjściowych programu do cieniowania wierzchołków, nic nie jest wyświetlane na etapie **cieniowania wierzchołka** .  
  
 Program do **cieniowania kadłuba** (tylko program Direct3D 11 i program Direct3D 12)  
 Etap programu do cieniowania kadłuba przetwarza punkty kontrolne, które definiują powierzchnię o niskiej kolejności, taką jak linia, Trójkąt lub cztery. Ponieważ dane wyjściowe generują poprawkę geometryczną o wyższej kolejności i stałe poprawek, które są przekazywane do etapu mozaikowania stałej funkcji.  
  
 Etap modułu cieniującego nie jest wizualizacją w oknie etapy potoku.  
  
 **Etap tessellator** (tylko Direct3D 11 i Direct3D 12)  
 Etap tessellator to stała funkcja (nieprogramowalna), która wstępnie przetwarza domenę reprezentowane przez dane wyjściowe programu do cieniowania kadłuba. Jako dane wyjściowe tworzy wzorzec próbkowania domeny i zestaw mniejszych elementów podstawowych — punkty, linie, Trójkąty, które łączą te próbki.  
  
 Etap tessellator nie jest wizualizacją w oknie etapy potoku.  
  
 Program do **cieniowania domen** (tylko program Direct3D 11 i program Direct3D 12)  
 Etap modułu cieniującego w domenie przetwarza poprawki geometryczne wyższej kolejności z modułu cieniującego kadłuba, wspólnie mozaikowaniae czynniki z etapu mozaikowania. Czynniki mozaikowania mogą obejmować współczynniki wejściowe tessellator, a także czynniki wyjściowe. Jako dane wyjściowe oblicza położenie wierzchołka punktu na podstawie poprawki wyjściowej, w zależności od czynników tessellator.  
  
 Etap programu do cieniowania domeny nie jest wizualizacją w oknie etapy potoku.  
  
 **Cieniowanie geometrii**  
 Etap cieniowania geometrii przetwarza wszystkie elementy pierwotne — punkty, linie lub Trójkąty — wraz z opcjonalnymi danymi wierzchołków dla sąsiadujących elementów pierwotnych. W przeciwieństwie do programów do cieniowania wierzchołków, cieniowanie geometryczne może generować więcej lub mniej elementów pierwotnych niż te, które przyjmuje jako dane wejściowe.  
  
 W oknie etapy potoku, dane wyjściowe cieniowania geometrii są wizualizowane jako obraz szkieletu rastrowego. Aby przyjrzeć się bliżej wyniku, wybierz opcję **cieniowanie geometrii** w oknie **etapy potoku grafiki** , aby wyświetlić przetworzone elementy podstawowe w edytorze obrazu.  
  
 **Etap wyjścia strumienia**  
 Etap wyjścia strumienia może przechwycić przekształcone elementy pierwotne przed rasteryzacją i zapisać je w pamięci; z tego miejsca dane można resłużyć jako dane wejściowe do wcześniejszych etapów potoku grafiki lub być odczytane przez procesor CPU.  
  
 Etap wyjścia strumienia nie jest wizualizacją w oknie etapy potoku.  
  
 **Etap rasteryzacji**  
 Etap Rasteryzuj to stała funkcja (nieprogramowalna), która konwertuje elementy podstawowe wektorów — punkty, linie, trójkąty — do obrazu rastrowego, wykonując konwersję w wierszu skanowania. Podczas wierzchołków rasteryzacji są przekształcane w jednorodne miejsce na klipy i obcinane. Jako dane wyjściowe programy do cieniowania pikseli są mapowane i atrybuty na wierzchołkach są interpolowane w obrębie pierwotnej i gotowe do cieniowania pikseli.  
  
 Etap rasteryzacji nie jest wizualizacją w oknie etapy potoku.  
  
 **Program do cieniowania pikseli**  
 Etap programu do cieniowania pikseli przetwarza rastrowe elementy podstawowe wraz z interpolowanymi danymi wierzchołków, aby generować wartości dla pikseli, takie jak kolor i głębokość.  
  
 W oknie etapy potoku, dane wyjściowe programu do cieniowania pikseli są wizualizowane jako obraz rastrowy w pełnej postaci. Aby przyjrzeć się bliżej wyniku, wybierz pozycję program do **cieniowania pikseli** w oknie **etapy potoku grafiki** , aby wyświetlić przetworzone elementy podstawowe w edytorze obrazu.  
  
 **Fuzja danych wyjściowych**  
 Etap scalania danych wyjściowych łączy efekt nowo renderowanych pikseli wraz z istniejącą zawartością odpowiednich buforów — koloru, głębokości i wzornika — w celu utworzenia nowych wartości w tych buforach.  
  
 W oknie etapy potoku dane wyjściowe scalania są wizualizowane jako obraz obrazu rastrowego w pełnej postaci. Aby zajrzeć się na wyniki, wybierz pozycję **scalanie danych wyjściowych** w oknie **etapy potoku grafiki** , aby wyświetlić scalone bufor ramki.  
  
### <a name="vertex-shader-preview"></a>Podgląd wierzchołków — wersja zapoznawcza  
 Po wybraniu etapu cieniowania wierzchołków w oknie **etapy potoku grafiki** zostanie wyświetlony panel **bufory wejściowe** . W tym miejscu znajdziesz szczegółowe informacje o liście wierzchołków dostarczonych do programu do cieniowania wierzchołków po ich złożeniu przez etap asemblera wejściowego.  
  
 ![Podgląd buforu wejściowego etapu programu do cieniowania wierzchołków](../debugger/media/gfx-diag-vertex-shader-inbuffers.png "gfx_diag_vertex_shader_inbuffers")  
  
 Aby wyświetlić wynik etapu programu do cieniowania wierzchołków, wybierz miniaturę etapu cieniowania wierzchołka, aby wyświetlić rozmiar siatki rastrowej, który został przestawiony przez program do cieniowania wierzchołków.  
  
 ![Podgląd wyników etapu programu do cieniowania wierzchołków](../debugger/media/gfx-diag-vertex-shader-preview.png "gfx_diag_vertex_shader_preview")  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów ze względu na cieniowanie wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)
