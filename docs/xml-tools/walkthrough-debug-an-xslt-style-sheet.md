---
title: Arkusze stylów Debugowania XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301721"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: Debugowanie arkusza stylów XSLT

Kroki opisane w tym przewodniku pokazują, jak używać debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawianie punktów przerwania i przechodzenie przez kod. Debuger umożliwia wykonywanie kodu po jednym wierszu naraz.

Aby przygotować się do tego przewodnika, najpierw skopiuj dwa [przykładowe pliki](#sample-files) na komputer lokalny. Jednym z nich jest arkusz stylów, a drugim jest plik XML, którego użyjemy jako danych wejściowych do arkusza stylów. W tym instruktażu arkusz stylów, którego używamy, znajduje wszystkie książki, których koszt jest niższy od średniej ceny książki.

> [!NOTE]
> Debuger XSLT jest dostępny tylko w wersji Enterprise programu Visual Studio.

## <a name="start-debugging"></a>Rozpocznij debugowanie

1. Z menu **Plik** wybierz polecenie **Otwórz** > **plik**.

2. Znajdź plik *poniżej średniej.xsl* i **wybierz**otwórz .

   Arkusz stylów zostanie otwarty w edytorze XML.

3. Kliknij przycisk przeglądaj (**...**) w polu **Wejście** okna właściwości dokumentu. (Jeśli okno **Właściwości** nie jest widoczne, kliknij prawym przyciskiem myszy dowolne miejsce otwartego pliku w edytorze, a następnie wybierz polecenie **Właściwości).**

4. Znajdź plik *books.xml,* a następnie wybierz pozycję **Otwórz**.

   Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.

5. Ustaw [punkt przerwania](../debugger/using-breakpoints.md) w wierszu 12 *poniżej średniej.xsl*. Można to zrobić na jeden z wielu sposobów:

   - Kliknij na marginesie edytora w wierszu 12.

   - Kliknij dowolne miejsce na linii 12, a następnie naciśnij **klawisz F9**.

   - Kliknij prawym `xsl:if` przyciskiem myszy znacznik startowy, a następnie wybierz polecenie **Wstaw** > **punkt przerwania**.

      ![Wstawianie punktu przerwania w pliku XSL w programie Visual Studio](media/insert-breakpoint.PNG)

6. Na pasku menu wybierz polecenie **XML** > **Start XSLT Debugowanie** (lub naciśnij **klawisz Alt**+**F5**).

   Rozpoczyna się proces debugowania.

   W edytorze debuger jest umieszczony `xsl:if` na elemencie arkusza stylów. W edytorze otwiera się kolejny plik o nazwie *poniżej średniej.xml;* jest to plik wyjściowy, który zostanie wypełniony podczas przetwarzania każdego węzła w pliku wejściowym *books.xml.*

   Okna **Autos**, **Locals**i **Watch 1** są wyświetlane w dolnej części okna programu Visual Studio. W oknie **Locals** są wyświetlane wszystkie zmienne lokalne i ich bieżące wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów, a także zmienne używane przez debuger do śledzenia węzłów, które są obecnie w kontekście.

## <a name="watch-window"></a>okno czujki

Dodamy dwie zmienne do okna **Watch 1,** abyśmy mogli sprawdzić ich wartości podczas przetwarzania pliku wejściowego. (Można również użyć okna **Zmiennych lokalnych,** aby sprawdzić wartości, jeśli zmienne, które chcesz obserwować, już istnieją).

1. Z menu **Debugowania** wybierz pozycję **Zegarek Windows** > **Watch** > **1**.

   Okno **Zegarek 1** staje się widoczne.

2. Wpisz `$bookAverage` pole **Nazwa,** a następnie naciśnij klawisz **Enter**.

   Wartość zmiennej `$bookAverage` jest wyświetlana w polu **Wartość.**

3. W następnym wierszu `self::node()` wpisz pole **Nazwa,** a następnie naciśnij klawisz **Enter**.

   `self::node()`jest wyrażenieM XPath, które ocenia bieżący węzeł kontekstu. Wartość wyrażenia `self::node()` XPath jest pierwszym węzłem księgi. Zmienia się to w miarę postępów w transformacji.

4. Rozwiń `self::node()` węzeł, a następnie rozwiń węzeł, który ma `price`wartość .

   ![Okno obserwowanie podczas debugowania XSLT w programie Visual Studio](media/xslt-debugging-watch-window.png)

   Można wyświetlić wartość ceny księgowej dla bieżącego węzła `$bookAverage` księgi i porównać ją z wartością. Ponieważ cena książki jest poniżej `xsl:if` średniej, warunek powinien zakończyć się pomyślnie podczas kontynuowania procesu debugowania.

## <a name="step-through-the-code"></a>Krok po kroku przez kod

1. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ pierwszy węzeł księgi spełnił `xsl:if` warunek, węzeł księgi jest dodawany do pliku wyjściowego *poniżej średniej.xml.* Debuger kontynuuje wykonywanie, dopóki nie zostanie ponownie `xsl:if` umieszczony na elemencie w arkuszu stylów. Debuger jest teraz umieszczony w drugim węźle księgi w pliku *books.xml.*

   W oknie **Czujka 1** `self::node()` wartość zmienia się na drugi węzeł księgi. Badając wartość elementu ceny, można ustalić, że cena jest powyżej średniej, w związku z `xsl:if` tym warunek powinien zakończyć się niepowodzeniem.

2. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ drugi węzeł księgi `xsl:if` nie spełnia tego warunku, węzeł księgi nie jest dodawany do pliku wyjściowego *poniżej średniej.xml.* Debuger kontynuuje wykonywanie, dopóki nie zostanie ponownie `xsl:if` umieszczony na elemencie w arkuszu stylów. Debuger jest teraz umieszczony w `book` trzecim węźle w pliku *books.xml.*

   W oknie **Czujka 1** `self::node()` wartość zmienia się na węzeł trzeciej księgi. Badając wartość `price` elementu, można określić, że cena jest poniżej średniej. Warunek `xsl:if` powinien zakończyć się pomyślnie.

3. Naciśnij klawisz **F5**, aby kontynuować.

   Ponieważ `xsl:if` warunek został spełniony, trzecia książka jest dodawana do pliku *wyjściowego poniżej średniej.xml.* Wszystkie książki w dokumencie XML zostały przetworzone, a debuger zatrzymuje się.

## <a name="sample-files"></a>Przykładowe pliki

Następujące dwa pliki są używane przez przewodnik.

### <a name="below-averagexsl"></a>poniżej średniej.xsl

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

## <a name="see-also"></a>Zobacz też

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
