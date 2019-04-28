---
title: Debugowania arkuszy stylów XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808511"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: Debugowanie arkusza stylów XSLT

Kroki opisane w tym przewodniku pokazują, jak za pomocą debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawiania punktów przerwania i krokowe wykonywanie kodu. Debuger umożliwia wykonywanie jednego wiersza kodu naraz.

Aby przygotować się do tego instruktażu, należy najpierw skopiować dwa [przykładowe pliki](#sample-files) na komputerze lokalnym. Jeden jest arkusza stylów, a drugi plik XML, które będą używane jako dane wejściowe do arkusza stylów. W tym przewodniku arkusza stylów, których używamy znajduje wszystkie książki, których koszt znajduje się poniżej średnią cenę książek.

> [!NOTE]
> Debuger XSLT jest dostępna tylko w wersji Enterprise programu Visual Studio.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Z **pliku** menu, wybierz **Otwórz** > **pliku**.

2. Znajdź *poniżej average.xsl* pliku, a następnie wybierz **Otwórz**.

   Arkusz stylów zostanie otwarty w edytorze XML.

3. Kliknij przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu. (Jeśli **właściwości** okno nie jest widoczna, kliknij prawym przyciskiem myszy w dowolnym miejscu na Otwórz plik w edytorze, a następnie wybierz **właściwości**.)

4. Znajdź *books.xml* , a następnie wybierz **Otwórz**.

   Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.

5. Ustaw [punktu przerwania](../debugger/using-breakpoints.md) w wierszu 12 *poniżej average.xsl*. To zrobić w jednym z wielu sposobów:

   - Kliknij na marginesie edytora w wierszu 12.

   - Kliknij w dowolnym miejscu w wierszu 12, a następnie naciśnij klawisz **F9**.

   - Kliknij prawym przyciskiem myszy `xsl:if` tag początkowy, a następnie wybierz **punktu przerwania** > **Wstaw punkt przerwania**.

      ![Wstaw punkt przerwania w pliku XSL w programie Visual Studio](media/insert-breakpoint.PNG)

6. Na pasku menu wybierz **XML** > **Rozpocznij debugowanie kodu XSLT** (lub naciśnij **Alt**+**F5**).

   Rozpocznie się proces debugowania.

   W edytorze, Debuger jest ustawiony na `xsl:if` element arkusza stylów. Inny plik o nazwie *poniżej average.xml* zostanie otwarty w edytorze; jest to plik wyjściowy, który zostanie wypełniony jako każdego węzła w pliku wejściowym *books.xml* jest przetwarzany.

   **Autos**, **lokalne**, i **Czujka 1** systemu windows są wyświetlane w dolnej części okna programu Visual Studio. **Lokalne** oknie zostaną wyświetlone wszystkie zmienne lokalne oraz ich bieżących wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów, a także zmienne używane przez debuger do śledzenia węzły, które są obecnie dostępne w kontekście.

## <a name="watch-window"></a>okno czujki

Dodamy dwóch zmiennych **Czujka 1** okna, dlatego firma Microsoft można sprawdzić ich wartości jako plik wejściowy jest przetwarzany. (Możesz również użyć **lokalne** okna, aby sprawdzić wartości w przypadku zmiennych, którą chcesz obserwować już istnieje.)

1. Z **debugowania** menu, wybierz **Windows** > **Obejrzyj** > **Czujka 1**.

   **Czujka 1** okno staje się widoczny.

2. Typ `$bookAverage` w **nazwa** pola, a następnie naciśnij klawisz **Enter**.

   Wartość `$bookAverage` jest wyświetlany w **wartość** pola.

3. W następnym wierszu, wpisz `self::node()` w **nazwa** pola, a następnie naciśnij klawisz **Enter**.

   `self::node()` to wyrażenie XPath, które daje w wyniku bieżącego węzła kontekstu. Wartość `self::node()` wyrażenie XPath jest pierwszym węźle książki. To zmian w miarę postępów za pomocą transformacji.

4. Rozwiń `self::node()` węzła, a następnie rozwiń węzeł kto ma wartość `price`.

   ![W oknie czujki podczas debugowanie kodu XSLT w programie Visual Studio](media/xslt-debugging-watch-window.png)

   Można zobaczyć wartość cenę książek dla bieżącego węzła książki i porównać go do `$bookAverage` wartości. Ponieważ cena książki jest poniżej średniej, `xsl:if` warunek ma być pomyślnie wykonane, jeśli będziesz kontynuować procesu debugowania.

## <a name="step-through-the-code"></a>Przejść przez kod

1. Naciśnij klawisz **F5** aby kontynuować.

   Ponieważ spełnione pierwszego węzła książki `xsl:if` węzła książki warunek, jest dodawany do *poniżej average.xml* pliku wyjściowego. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony na drugim węźle książki w *books.xml* pliku.

   W **Czujka 1** oknie `self::node()` wartość zmienia się na drugiego węzła książki. Sprawdzając wartość elementu ceny, należy określić, że cena jest powyżej średniej, dlatego `xsl:if` warunku powinna zakończyć się niepowodzeniem.

2. Naciśnij klawisz **F5** aby kontynuować.

   Ponieważ nie spełnia drugiego węzła książki `xsl:if` warunku węzła książki nie jest dodawany do *poniżej average.xml* pliku wyjściowego. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony w trzeciej `book` w węźle *books.xml* pliku.

   W **Czujka 1** oknie `self::node()` zmiany wartości na trzeci węzła książki. Sprawdzając wartość `price` elementu, można określić czy cena wynosi poniżej średniej. `xsl:if` Warunek ma być pomyślnie wykonane.

3. Naciśnij klawisz **F5** aby kontynuować.

   Ponieważ `xsl:if` warunek był spełniony, trzeci książki jest dodawany do *poniżej average.xml* pliku wyjściowego. Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzymuje się.

## <a name="sample-files"></a>Przykładowe pliki

Następujące dwa pliki są używane przez instruktażu.

### <a name="below-averagexsl"></a>below-average.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books.XML

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)