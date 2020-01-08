---
title: Debuguj arkusze stylów XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592480"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: debugowanie arkusza stylów XSLT

W krokach w tym instruktażu pokazano, jak używać debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawianie punktów przerwania i przechodzenie przez kod. Debuger umożliwia wykonywanie kodu jeden wiersz jednocześnie.

Aby przygotować się do tego przewodnika, najpierw skopiuj dwa [pliki przykładowe](#sample-files) na komputer lokalny. Jeden jest arkusz stylów, a drugi to plik XML, który będzie używany jako dane wejściowe do arkusza stylów. W tym instruktażu używany arkusz stylów znajduje wszystkie książki, których koszt jest niższy niż średnia cena książki.

> [!NOTE]
> Debuger XSLT jest dostępny tylko w wersji Enterprise programu Visual Studio.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Z menu **plik** wybierz **Otwórz** > **plik**.

2. Znajdź plik *below-Average. xsl* i wybierz polecenie **Otwórz**.

   Arkusz stylów zostanie otwarty w edytorze XML.

3. Kliknij przycisk Przeglądaj ( **...** ) w polu **wejściowym** okna właściwości dokumentu. (Jeśli okno **Właściwości** nie jest widoczne, kliknij prawym przyciskiem myszy w dowolnym miejscu w otwartym pliku w edytorze, a następnie wybierz polecenie **Właściwości**.)

4. Znajdź plik *Books. XML* , a następnie wybierz polecenie **Otwórz**.

   Ustawia plik dokumentu źródłowego używany do przekształcania XSLT.

5. Ustaw [punkt przerwania](../debugger/using-breakpoints.md) w wierszu 12 *below-Average. xsl*. Można to zrobić na kilka sposobów:

   - Kliknij na marginesie edytora w wierszu 12.

   - Kliknij w dowolnym miejscu w wierszu 12, a następnie naciśnij klawisz **F9**.

   - Kliknij prawym przyciskiem myszy `xsl:if` znacznik początkowy, a następnie wybierz **punkt przerwania** > **Wstaw punkt przerwania**.

      ![Wstaw punkt przerwania w pliku XSL w programie Visual Studio](media/insert-breakpoint.PNG)

6. Na pasku menu wybierz pozycję **XML** > **Rozpocznij debugowanie XSLT** (lub naciśnij klawisz **Alt**+**F5**).

   Rozpocznie się proces debugowania.

   W edytorze debuger jest umieszczony na `xsl:if` elemencie arkusza stylów. W edytorze zostanie otwarty inny plik o nazwie *below-Average. XML* . jest to plik wyjściowy, który zostanie wypełniony jako każdy węzeł w pliku *Books. XML* jest przetwarzany.

   Okna **Autokorekty**, **lokalne**i **czujka 1** są wyświetlane u dołu okna programu Visual Studio. W oknie **Ustawienia lokalne** są wyświetlane wszystkie zmienne lokalne i ich bieżące wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów i zmienne, które są używane przez debuger do śledzenia węzłów, które znajdują się obecnie w kontekście.

## <a name="watch-window"></a>Obserwuj okno

Dodamy dwie zmienne do okna **czujki 1** , aby można było przeanalizować wartości jako plik wejściowy. (Można również użyć okna **zmiennych lokalnych** do sprawdzenia wartości, jeśli zmienne, które chcesz obejrzeć, już tam znajdują się).

1. Z menu **Debuguj** wybierz polecenie **Windows** > **Watch** > **Obejrzyj 1**.

   Okno **czujki 1** staną się widoczne.

2. Wpisz `$bookAverage` w polu **Nazwa** , a następnie naciśnij klawisz **Enter**.

   Wartość zmiennej `$bookAverage` zostanie wyświetlona w polu **wartość** .

3. W następnym wierszu wpisz `self::node()` w polu **Nazwa** , a następnie naciśnij klawisz **Enter**.

   `self::node()` jest wyrażeniem XPath, które jest obliczane do bieżącego węzła kontekstu. Wartość wyrażenia `self::node()` XPath jest pierwszym węzłem książki. Zmiany są wprowadzane w trakcie transformacji.

4. Rozwiń węzeł `self::node()`, a następnie rozwiń węzeł, którego wartość jest `price`.

   ![okno wyrażeń kontrolnych podczas debugowania XSLT w programie Visual Studio](media/xslt-debugging-watch-window.png)

   Możesz zobaczyć wartość ceny książki dla bieżącego węzła księgi i porównać ją z wartością `$bookAverage`. Ze względu na to, że cena książki jest niższa od średniej, warunek `xsl:if` powinien się powieść, gdy będziesz kontynuować proces debugowania.

## <a name="step-through-the-code"></a>Przechodzenie przez kod

1. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ pierwszy węzeł książki spełnił warunek `xsl:if`, węzeł książki jest dodawany do pliku wyjściowego *below-Average. XML* . Debuger kontynuuje działanie, dopóki nie zostanie ponownie umieszczony na `xsl:if` elemencie w arkuszu stylów. Debuger jest teraz umieszczony w drugim węźle książki w pliku *Books. XML* .

   W oknie **czujka 1** wartość `self::node()` zmieni się na drugi węzeł książki. Sprawdzając wartość elementu Price, możesz określić, że cena jest wyższa niż średnia, dlatego warunek `xsl:if` nie powinien kończyć się niepowodzeniem.

2. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ drugi węzeł książki nie spełnia warunku `xsl:if`, węzeł książki nie zostanie dodany do pliku wyjściowego *below-Average. XML* . Debuger kontynuuje działanie, dopóki nie zostanie ponownie umieszczony na `xsl:if` elemencie w arkuszu stylów. Debuger jest teraz umieszczony w trzecim węźle `book` w pliku *Books. XML* .

   W oknie **czujka 1** wartość `self::node()` zmieni się na trzeci węzeł książki. Sprawdzając wartość `price` elementu, można określić, że cena jest niższa od średniej. Warunek `xsl:if` powinien się powieść.

3. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ warunek `xsl:if` był spełniony, trzecia książka jest dodawana do pliku wyjściowego *below-Average. XML* . Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzyma działanie.

## <a name="sample-files"></a>Pliki przykładowe

Przewodnik korzysta z poniższych dwóch plików.

### <a name="below-averagexsl"></a>below-Average. xsl

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

### <a name="booksxml"></a>{1&gt;Books.XML&lt;1}

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
