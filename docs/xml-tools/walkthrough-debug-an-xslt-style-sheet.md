---
title: 'Przewodnik: Debugowanie arkusza stylów XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e04a2baa31c9fbcd7dd9c2ceeba7ed0840e8b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930080"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: Debugowanie arkusza stylów XSLT

Kroki opisane w tym przewodniku pokazują, jak za pomocą debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawiania punktów przerwania i krokowe wykonywanie kodu. Arkusz stylów znajduje wszystkie książki, które koszt poniżej średnią cenę książek.

## <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika

1.  Zamknij wszystkie otwarte rozwiązania.

2.  Skopiuj dwa pliki przykładowe do komputera lokalnego.

## <a name="start-debugging"></a>Rozpocznij debugowanie

### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie

1.  Z **pliku** menu wskaż **Otwórz**i kliknij przycisk **pliku**.

2.  Znajdź *belowAvg.xsl* plik i kliknij przycisk **Otwórz**.

     Arkusz stylów jest otwarty w edytorze XML.

3.  Kliknij przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.

4.  Znajdź *books.xml* plik i kliknij przycisk **Otwórz**.

     Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.

5.  Kliknij prawym przyciskiem myszy `xsl:if` tag początkowy, wskaż opcję **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.

6.  Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.

Spowoduje to uruchomienie procesu debugowania i otwiera kilka nowych oknach, które są używane przez debuger.

Istnieją dwa okna wyświetlające wejściowych arkusza stylów i dokumentów. Debuger używa tych okien, aby wyświetlić bieżący stan wykonania. Debuger jest ustawiony na `xsl:if` element arkusza stylów i w pierwszym węźle książki w *books.xml* pliku.

**Lokalne** oknie zostaną wyświetlone wszystkie zmienne lokalne oraz ich bieżących wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów, a także zmienne używane przez debuger do śledzenia węzły, które są obecnie dostępne w kontekście.

**Danych wyjściowych XSL** okna wyświetla dane wyjściowe transformacji XSL. To okno jest oddzielony od **Visual Studio dane wyjściowe** okna.

## <a name="watch-window"></a>okno czujki

### <a name="to-use-the-watch-window"></a>Aby użyć okna czujki

1.  Z **debugowania** menu wskaż **Windows**, wskaż polecenie **Obejrzyj**i kliknij przycisk **Czujka 1**.

     To sprawia, że **Czujka 1** okno jest widoczne.

2.  Typ `$bookAverage` w **nazwa** pole i naciśnij klawisz **Enter**.

     Wartość `$bookAverage` zmienna jest wyświetlany w oknie.

3.  Typ `self::node()` w **nazwa** pole i naciśnij klawisz **Enter**.

     `self::node()` to wyrażenie XPath, które daje w wyniku bieżącego węzła kontekstu. Wartość `self::node()` wyrażenie XPath jest pierwszym węźle książki. To zmian w miarę postępów za pomocą transformacji.

4.  Rozwiń `self::node()` węzła, a następnie rozwiń węzeł `price` węzła.

     Dzięki temu można zobaczyć wartość ceny książki i należy go do łatwiejszego porównania `$bookAverage` wartość. Ponieważ cena książki jest poniżej średniej, `xsl:if` warunek ma być pomyślnie wykonane.

## <a name="step-through-the-code"></a>Przejść przez kod
 Debuger umożliwia wykonywanie jednego wiersza kodu naraz.

### <a name="to-step-through-the-code"></a>Aby przejść przez kod

1.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ spełnione pierwszego węzła książki `xsl:if` węzła książki warunek, jest dodawany do **danych wyjściowych XSL** okna. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony na drugim węźle książki w *books.xml* pliku.

     W **Czujka 1** okna `self::node()` wartość zmienia się na drugiego węzła książki. Sprawdzając wartość elementu ceny, należy określić, że cena jest powyżej średniej, dlatego `xsl:if` warunku powinna zakończyć się niepowodzeniem.

2.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ nie spełnia drugiego węzła książki `xsl:if` warunku węzła książki nie jest dodawany do **danych wyjściowych XSL** okna. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony w trzeciej `book` w węźle *books.xml* pliku.

     W **Czujka 1** okna `self::node()` zmiany wartości na trzeci węzła książki. Sprawdzając wartość `price` elementu, można określić czy cena wynosi poniżej średniej, dlatego `xsl:if` warunek ma być pomyślnie wykonane.

3.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ `xsl:if` warunek był spełniony, trzeci książki jest dodawany do **danych wyjściowych XSL** okna. Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzymuje się.

## <a name="sample-files"></a>Przykładowe pliki

Następujące dwa pliki są używane przez instruktażu.

### <a name="belowavgxsl"></a>belowAvg.xsl

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
        <xsl:if test="price < $bookAverage">
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