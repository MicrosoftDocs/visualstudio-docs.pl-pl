---
title: Debuger cieniowania HLSL | Microsoft Docs
description: Użyj debugera HLSL w analizatorze grafiki, aby opanujesz, w jaki sposób kod HLSL działa w aplikacji. Debuger może symulować dokładny HLSL wątek, który Cię interesuje.
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
ms.openlocfilehash: 65f643d0f03f9754d580de8be95fb5c1f65a940d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995138"
---
# <a name="hlsl-shader-debugger"></a>Debuger programu do cieniowania HLSL
Debuger HLSL w analizator grafiki programu Visual Studio pomaga zrozumieć, w jaki sposób kod programu do cieniowania HLSL działa w rzeczywistych warunkach aplikacji.

 To jest debuger języka HLSL:

 ![Debugowanie HLSL przy użyciu okna Czujka i stosu wywołań.](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>Opis debugera HLSL
 Debuger HLSL ułatwia lepsze poznanie problemów, które występują w kodzie modułu cieniującego. Debugowanie kodu HLSL w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przypomina Debugowanie kodu, który jest pisany w innych językach — na przykład C++, C# lub Visual Basic. Można zbadać zawartość zmiennych, ustawić punkty przerwania, wykonywać kod krokowo i przechodzić przez stos wywołań, podobnie jak podczas debugowania innych języków.

 Ponieważ jednak procesory GPU osiągają wysoką wydajność przez uruchamianie kodu programu do cieniowania na setkach wątków jednocześnie, debuger HLSL został zaprojektowany tak, aby współpracował z innymi narzędziami analizatora grafiki, aby przedstawić wszystkie te informacje w sposób, który ułatwia ich zrozumienie. Analizator grafiki ponownie tworzy przechwycone ramki przy użyciu informacji, które zostały zapisane w dzienniku grafiki; debuger HLSL nie monitoruje wykonywania procesora GPU w czasie rzeczywistym, ponieważ uruchamia kod programu do cieniowania. Ponieważ dziennik grafiki zawiera wystarczające informacje, aby odtworzyć każdą część danych wyjściowych, a ponieważ analiza grafiki zawiera narzędzia, które mogą pomóc w określeniu dokładnego piksela i zdarzenia w przypadku wystąpienia błędu, debuger HLSL musi tylko symulować dokładnie odpowiedni wątek programu do cieniowania. Oznacza to, że działanie programu cieniującego może być symulowane w procesorze CPU, gdzie działanie jego wewnętrznych mechanizmów jest w pełni widoczne. Dzięki temu debugger HLSL otrzymuje debugowanie podobne do procesora.

 Jednak debuger języka HLSL jest obecnie ograniczony pod następującymi względami:

- Debuger HLSL nie obsługuje funkcji Edit-and-Continue, ale można wprowadzać zmiany do programów do cieniowania, a następnie ponownie wygenerować ramkę, aby zobaczyć wyniki.

- Nie jest możliwe debugowanie aplikacji i jej kodu cieniowania w tym samym czasie. Można jednak używać ich zamiennie.

- W oknie czujki można dodać zmienne i rejestry, ale wyrażenia nie są obsługiwane.

  Niemniej jednak debuger języka HLSL oferuje lepsze, przypominające zachowanie znane z procesorów CPU debugowanie, niż byłoby to możliwe w innym przypadku.

## <a name="hlsl-shader-edit--apply"></a>HLSL & edycji cieniowania
 Debuger modułu cieniującego HLSL nie obsługuje edycji & Kontynuuj w taki sam sposób, jak debuger procesora działa, ponieważ model wykonywania procesora GPU nie zezwala na cofnięcie stanu programu do cieniowania. Zamiast tego debuger HLSL obsługuje funkcję Edit & Apply, która umożliwia edytowanie plików źródłowych HLSL, a następnie wybierz pozycję **Zastosuj** , aby ponownie wygenerować ramkę, aby zobaczyć efekt zmian. Zmodyfikowany kod programu do cieniowania jest przechowywany w osobnym pliku, aby zachować integralność oryginalnego pliku źródłowego HLSL projektu, ale po spełnieniu zmian możesz wybrać **Kopiuj do...** , aby skopiować zmiany do projektu. Korzystając z tej funkcji, można szybko wykonać iterację w kodzie programu do cieniowania, który zawiera błędy, i wyeliminować kosztowne ponowne kompilowanie i przechwytywanie z przepływu pracy debugowania HLSL.

## <a name="hlsl-disassembly"></a>Demontaż HLSL
 Debuger modułu cieniującego HLSL zawiera listę zestawu HLSL Shader z prawej strony listy kodu źródłowego HLSL.

## <a name="debugging-hlsl-code"></a>Debugowanie kodu HLSL
 Możesz uzyskać dostęp do debugera HLSL z etapów potoku lub okien historii pikseli.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Aby uruchomić debuger HLSL z okna Etapy potoku grafiki

1. W oknie **etapy potoku grafiki** zlokalizuj etap potoku, który jest skojarzony z modułem cieniującego, który chcesz debugować.

2. Poniżej tytułu etapu potoku wybierz **Rozpocznij debugowanie**, które pojawia się jako mała Zielona strzałka.

    > [!NOTE]
    > Ten punkt wejścia do debugera HLSL debuguje tylko pierwszy wątek modułu cieniującego dla odpowiedniego etapu, czyli pierwszy wierzchołek lub piksel, który jest przetwarzany. Możesz użyć historii pikseli, aby uzyskać dostęp do innych wątków tych etapów programu do cieniowania.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Aby uruchomić debuger HLSL z okna Historia pikseli grafiki

1. W oknie **Historia pikseli grafiki** rozwiń wywołanie rysowania skojarzone z programem do cieniowania, który chcesz debugować. Każde wywołanie rysowania może odpowiadać wielu obiektom pierwotnym.

2. W szczegółach wywołania rysowania, rozwiń prymityw, którego wynikowy kolor sugeruje błąd w kodzie modułu cieniującego. Jeśli wiele prymitywów sugeruje błąd, wybierz pierwszy prymityw, który go sugeruje, tak aby uniknąć nagromadzenia błędów, które mogą utrudnić diagnozę problemu.

3. W obszarze Szczegóły pierwotne wybierz, czy debugować program do **cieniowania wierzchołków** , czy **cieniowanie pikseli**. Debuguj program do cieniowania wierzchołków, gdy istnieje podejrzenie, że program do cieniowania pikseli jest poprawny, ale generuje niepoprawny kolor, ponieważ program do cieniowania wierzchołków przekazuje mu nieprawidłowe stałe. W przeciwnym razie debuguj program do cieniowania pikseli.

    Na prawo od wybranego modułu cieniującego wybierz **Rozpocznij debugowanie**, które pojawia się jako mała Zielona strzałka.

   > [!NOTE]
   > Ten punkt wejścia do debugera HLSL debuguje program cieniowania pikseli, który odpowiada wybranemu wywołaniu rysowania, prymitywowi i pikselowi lub wątkom cieniowania wierzchołków, których wyniki są interpolowane przez wywołanie wybranego rysowania, prymitywu i piksela. W przypadku programów do cieniowania wierzchołków można dodatkowo dostosować punkt wejścia do konkretnego przez rozwijanie szczegółów modułu cieniującego wierzchołek.

   Aby zapoznać się z przykładami dotyczącymi sposobu używania debugera HLSL do debugowania błędów programu do cieniowania, zobacz [przykłady](graphics-diagnostics-examples.md) lub instruktaże powiązane z w sekcji Zobacz też.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [Przewodnik: używanie diagnostyki grafiki do debugowania cieniowania obliczenia](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)