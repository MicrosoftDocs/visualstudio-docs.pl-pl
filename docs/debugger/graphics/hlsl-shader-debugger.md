---
title: Debuger programu do cieniowania HLSL | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 794b9605664315e47e7ae2a778c76652c420a7f7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066393"
---
# <a name="hlsl-shader-debugger"></a>Debuger programu do cieniowania HLSL
Debuger HLSL w analizatora grafiki programu Visual Studio pomaga zrozumieć, jak działa kod modułu cieniującego HLSL w warunkach rzeczywistych aplikacji.

 To jest debuger języka HLSL:

 ![Debugowanie przy użyciu języka HLSL Oglądaj i okna stosu wywołań. ](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>Opis debugera HLSL
 Debuger HLSL ułatwia lepsze poznanie problemów, które występują w kodzie modułu cieniującego. Debugowanie kodu języka HLSL w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przypomina debugowania kodu, który jest zapisywany w innych językach — na przykład, C++, C# lub Visual Basic. Można zbadać zawartość zmiennych, ustawić punkty przerwania, wykonywać kod krokowo i przechodzić przez stos wywołań, podobnie jak podczas debugowania innych języków.

 Jednak ponieważ GPU osiąga wysoką wydajność przez uruchamianie kodu modułu cieniującego na setkach wątków jednocześnie, Debuger języka HLSL jest przeznaczony do pracy razem z innymi narzędziami analizatora grafiki programu, aby przedstawić wszystkie te informacje w sposób, który pomoże Ci zrozumieć go. Analizator grafiki odtwarza przechwycone ramki za pomocą informacji, które zostały zapisane w dzienniku grafiki; Debuger HLSL nie monitoruje wykonania przez GPU w czasie rzeczywistym, jak działa kod modułu cieniującego. Ponieważ dziennik grafiki zawiera wystarczająco dużo informacji, aby odtworzyć wszystkie części danych wyjściowych, a ponieważ analizy grafiki zapewnia narzędzia, które mogą pomóc Ci zlokalizowania dokładny piksel i zdarzenie, gdzie występuje błąd, Debuger języka HLSL musi tylko zasymulować dokładny programu do cieniowania Wątek, który Cię interesuje. Oznacza to, że działanie programu cieniującego może być symulowane w procesorze CPU, gdzie działanie jego wewnętrznych mechanizmów jest w pełni widoczne. Dzięki temu debugger HLSL otrzymuje debugowanie podobne do procesora.

 Jednak debuger języka HLSL jest obecnie ograniczony pod następującymi względami:

- Debuger HLSL nie obsługuje edit-and-continue, ale możesz wprowadzać zmiany z programów do cieniowania, a następnie ponownie Wygeneruj ramki, aby zobaczyć wyniki.

- Nie jest możliwe debugowanie aplikacji i jej kodu cieniowania w tym samym czasie. Można jednak używać ich zamiennie.

- W oknie czujki można dodać zmienne i rejestry, ale wyrażenia nie są obsługiwane.

  Niemniej jednak debuger języka HLSL oferuje lepsze, przypominające zachowanie znane z procesorów CPU debugowanie, niż byłoby to możliwe w innym przypadku.

## <a name="hlsl-shader-edit--apply"></a>Edytowanie modułu cieniującego HLSL i Zastosuj
 Debuger programu do cieniowania HLSL nie obsługuje Edytuj i Kontynuuj w taki sam sposób, który jest debugera procesora CPU, ponieważ model wykonywania procesora GPU nie zezwala na stan programu do cieniowania można cofnąć. Zamiast tego, Debuger języka HLSL obsługuje & Zastosuj, dzięki czemu można edytować pliki źródłowe języka HLSL, a następnie wybierz pozycję Edytuj **Zastosuj** ponownie wygenerować ramki, aby zobaczyć efekt zmian. Kod modyfikacji programu do cieniowania jest przechowywana w oddzielnym pliku w celu zachowania spójności projektu oryginalnego pliku źródłowego języka HLSL, ale po zakończeniu zmiany możesz **skopiuj...**  skopiujesz zmiany do projektu. Przy użyciu tej funkcji, można szybko powtarzanie czynności w kodu programu do cieniowania, który zawiera błędy i wyeliminować kosztownych ponownej kompilacji i przechwytywania czynności z Twojej HLSL debugowanie przepływu pracy.

## <a name="hlsl-disassembly"></a>Dezasemblacja HLSL
 Debuger programu do cieniowania HLSL daje dostęp do listy zestawu modułu cieniującego HLSL z prawej strony listing kodu języka HLSL źródła.

## <a name="debugging-hlsl-code"></a>Debugowanie kodu HLSL
 Można uzyskać dostęp do debugera HLSL z okna etapy potoku lub z historii pikseli.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Aby uruchomić debuger HLSL z okna Etapy potoku grafiki

1. W **etapy potoku grafiki** okna, zlokalizuj etap potoku, który jest skojarzony z modułem cieniującym, który chcesz debugować.

2. Poniżej tytułu etapu potoku wybierz **Rozpocznij debugowanie**, które pojawia się jako mała zielona strzałka.

    > [!NOTE]
    >  Ten punkt wejścia do debugera HLSL debuguje tylko pierwszy wątek modułu cieniującego dla odpowiedniego etapu, czyli pierwszy wierzchołek lub piksel, który jest przetwarzany. Historia pikseli umożliwia dostęp do innych wątków z tych etapów modułu cieniującego.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Aby uruchomić debuger HLSL z okna Historia pikseli grafiki

1. W **Historia pikseli grafiki** okna, rozwiń wywołanie rysowania skojarzone z modułem cieniującym, który chcesz debugować. Każde wywołanie rysowania może odpowiadać wielu obiektom pierwotnym.

2. W szczegółach wywołania rysowania, rozwiń prymityw, którego wynikowy kolor sugeruje błąd w kodzie modułu cieniującego. Jeśli wiele prymitywów sugeruje błąd, wybierz pierwszy prymityw, który go sugeruje, tak aby uniknąć nagromadzenia błędów, które mogą utrudnić diagnozę problemu.

3. W szczegółach prymitywu Określ, czy chcesz debugować **program do cieniowania wierzchołków** lub **programu do cieniowania pikseli**. Debuguj program do cieniowania wierzchołków, gdy istnieje podejrzenie, że program do cieniowania pikseli jest poprawny, ale generuje niepoprawny kolor, ponieważ program do cieniowania wierzchołków przekazuje mu nieprawidłowe stałe. W przeciwnym razie debuguj program do cieniowania pikseli.

    Z prawej strony wybranego modułu cieniującego wybierz **Rozpocznij debugowanie**, które pojawia się jako mała zielona strzałka.

   > [!NOTE]
   >  Ten punkt wejścia do debugera HLSL debuguje program cieniowania pikseli, który odpowiada wybranemu wywołaniu rysowania, prymitywowi i pikselowi lub wątkom cieniowania wierzchołków, których wyniki są interpolowane przez wywołanie wybranego rysowania, prymitywu i piksela. W przypadku programów do cieniowania wierzchołków można dodatkowo dostosować punkt wejścia do konkretnego przez rozwijanie szczegółów modułu cieniującego wierzchołek.

   Aby uzyskać przykłady o sposobach używania debugera HLSL w celu debugowania błędów modułu cieniującego, zobacz [przykłady](graphics-diagnostics-examples.md) lub powiązane instruktaże w sekcji Zobacz też.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [Przewodnik: Używanie diagnostyki grafiki do debugowania cieniowania obliczenia](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)