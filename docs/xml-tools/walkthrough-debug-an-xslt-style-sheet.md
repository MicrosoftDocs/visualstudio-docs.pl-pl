---
title: Debuguj arkusze stylów XSLT
description: Dowiedz się, jak za pomocą debugera XSLT w programie Visual Studio debugować arkusz stylów XSLT, wykonując kroki opisane w tym instruktażu.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a6f1efc85366bc74206dc8637c992f249c4eb44
ms.sourcegitcommit: e443866e3468f838bc3655ad56a83a552013ceed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925888"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: Debugowanie arkusza stylów XSLT

W krokach w tym instruktażu pokazano, jak używać debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawianie punktów przerwania i przechodzenie przez kod. Debuger umożliwia wykonywanie kodu jeden wiersz jednocześnie.

Aby przygotować się do tego przewodnika, najpierw skopiuj dwa [pliki przykładowe](#sample-files) na komputer lokalny. Jeden jest arkusz stylów, a drugi to plik XML, który będzie używany jako dane wejściowe do arkusza stylów. W tym instruktażu używany arkusz stylów znajduje wszystkie książki, których koszt jest niższy niż średnia cena książki.

> [!NOTE]
> Debuger XSLT jest dostępny tylko w wersjach Professional i Enterprise programu Visual Studio.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Z menu **plik** wybierz polecenie **Otwórz**  >  **plik**.

2. Znajdź plik *below-Average. xsl* i wybierz polecenie **Otwórz**.

   Arkusz stylów zostanie otwarty w edytorze XML.

3. Kliknij przycisk Przeglądaj (**...**) w polu **wejściowym** okna właściwości dokumentu. (Jeśli okno **Właściwości** nie jest widoczne, kliknij prawym przyciskiem myszy w dowolnym miejscu w otwartym pliku w edytorze, a następnie wybierz polecenie **Właściwości**.)

4. Znajdź plik *books.xml* , a następnie wybierz polecenie **Otwórz**.

   Ustawia plik dokumentu źródłowego używany do przekształcania XSLT.

5. Ustaw [punkt przerwania](../debugger/using-breakpoints.md) w wierszu 12 *below-Average. xsl*. Można to zrobić na kilka sposobów:

   - Kliknij na marginesie edytora w wierszu 12.

   - Kliknij w dowolnym miejscu w wierszu 12, a następnie naciśnij klawisz **F9**.

   - Kliknij prawym przyciskiem myszy `xsl:if` tag początkowy, a następnie wybierz **punkt przerwania**  >  **Wstaw punkt przerwania**.

      ![Wstaw punkt przerwania w pliku XSL w programie Visual Studio](media/insert-breakpoint.PNG)

6. Na pasku menu wybierz pozycję **XML**  >  **Rozpocznij debugowanie XSLT** (lub naciśnij klawisz **Alt** + **F5**).

   Rozpocznie się proces debugowania.

   W edytorze debuger jest umieszczony na `xsl:if` elemencie arkusza stylów. Inny plik o nazwie *below-average.xml* otwiera się w edytorze; jest to plik wyjściowy, który zostanie wypełniony jako każdy węzeł w pliku wejściowym *books.xml* jest przetwarzany.

   Okna **Autokorekty**, **lokalne** i **czujka 1** są wyświetlane u dołu okna programu Visual Studio. W oknie **Ustawienia lokalne** są wyświetlane wszystkie zmienne lokalne i ich bieżące wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów i zmienne, które są używane przez debuger do śledzenia węzłów, które znajdują się obecnie w kontekście.

## <a name="watch-window"></a>okno czujki

Dodamy dwie zmienne do okna **czujki 1** , aby można było przeanalizować wartości jako plik wejściowy. (Można również użyć okna **zmiennych lokalnych** do sprawdzenia wartości, jeśli zmienne, które chcesz obejrzeć, już tam znajdują się).

1. Z menu **Debuguj** wybierz polecenie **Windows**  >  **Watch**  >  **Watch 1**.

   Okno **czujki 1** staną się widoczne.

2. Wpisz `$bookAverage` w polu **Nazwa** , a następnie naciśnij klawisz **Enter**.

   Wartość `$bookAverage` zmiennej zostanie wyświetlona w polu **wartość** .

3. W następnym wierszu wpisz `self::node()` w polu **Nazwa** , a następnie naciśnij klawisz **Enter**.

   `self::node()` jest wyrażeniem XPath, które jest obliczane do bieżącego węzła kontekstu. Wartość `self::node()` wyrażenia XPath jest pierwszym węzłem książki. Zmiany są wprowadzane w trakcie transformacji.

4. Rozwiń `self::node()` węzeł, a następnie rozwiń węzeł, który ma wartość `price` .

   ![okno wyrażeń kontrolnych podczas debugowania XSLT w programie Visual Studio](media/xslt-debugging-watch-window.png)

   Możesz zobaczyć wartość ceny książki dla bieżącego węzła księgi i porównać ją z `$bookAverage` wartością. Ze względu na to, że cena książki jest niższa od średniej, `xsl:if` warunek powinien zostać zakończony pomyślnie, gdy będziesz kontynuować proces debugowania.

## <a name="step-through-the-code"></a>Przechodzenie przez kod

1. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ pierwszy węzeł książki spełnił `xsl:if` warunek, węzeł książki jest dodawany do *below-average.xml* pliku wyjściowego. Debuger będzie nadal wykonywany do momentu ponownego pozycjonowania `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony w drugim węźle książki w pliku *books.xml* .

   W oknie **czujka 1** `self::node()` wartość zmieni się na drugi węzeł książki. Sprawdzając wartość elementu Price, można określić, że cena jest wyższa niż średnia, w rezultacie `xsl:if` warunek powinien zakończyć się niepowodzeniem.

2. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ drugi węzeł książki nie spełnia `xsl:if` warunku, węzeł książki nie zostanie dodany do pliku wyjściowego *below-average.xml* . Debuger kontynuuje działanie, dopóki nie zostanie ponownie umieszczony na `xsl:if` elemencie w arkuszu stylów. Debuger jest teraz umieszczony w trzecim `book` węźle w pliku *books.xml* .

   W oknie **czujka 1** `self::node()` wartość zmieni się na trzeci węzeł książki. Sprawdzając wartość `price` elementu, można określić, że cena jest niższa od średniej. `xsl:if`Warunek powinien się powieść.

3. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ `xsl:if` warunek został spełniony, trzecia książka jest dodawana do pliku wyjściowego *below-average.xml* . Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzyma działanie.

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

### <a name="booksxml"></a>books.xml

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
