---
title: 'Przewodnik: debugowanie arkusza stylów XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c205ff68ebc51d0b0f5b32038763c1741855d7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656107"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: debugowanie arkusza stylów XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W krokach w tym instruktażu pokazano, jak używać debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawianie punktów przerwania i przechodzenie przez kod. Arkusz stylów znajduje wszystkie książki, które są tańsze pod względem ceny za średnią książkę.

### <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika

1. Zamknij wszystkie otwarte rozwiązania.

2. Skopiuj dwa przykładowe pliki na komputer lokalny.

## <a name="start-debugging"></a>Rozpocznij debugowanie

#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie

1. W menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **plik**.

2. Znajdź plik belowAvg. xsl i kliknij przycisk **Otwórz**.

    Arkusz stylów zostanie otwarty w edytorze XML.

3. Kliknij przycisk Przeglądaj ( **...** ) w polu **wejściowym** okna właściwości dokumentu.

4. Znajdź plik Books. XML i kliknij przycisk **Otwórz**.

    Ustawia plik dokumentu źródłowego używany do przekształcania XSLT.

5. Kliknij prawym przyciskiem myszy `xsl:if` znacznik początkowy, wskaż **punkt przerwania**, a następnie kliknij polecenie **Wstaw punkt przerwania**.

6. Kliknij przycisk **DEBUGUJ XSL** na pasku narzędzi edytora XML.

   Spowoduje to uruchomienie procesu debugowania i otwarcie kilku nowych okien, które są używane przez debuger.

   Istnieją dwa okna, które wyświetlają dokument wejściowy i arkusz stylów. Debuger używa tych okien do wyświetlania bieżącego stanu wykonania. Debuger jest umieszczony na `xsl:if` elemencie arkusza stylów i w pierwszym węźle książki w pliku Books. XML.

   W oknie Ustawienia lokalne są wyświetlane wszystkie zmienne lokalne i ich bieżące wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów i zmienne, które są używane przez debuger do śledzenia węzłów, które znajdują się obecnie w kontekście.

   W oknie **dane wyjściowe XSL** zostaną wyświetlone dane wyjściowe przekształcenia XSL. To okno jest niezależne od okna **danych wyjściowych programu Visual Studio** .

## <a name="watch-window"></a>Okno czujka

#### <a name="to-use-the-watch-window"></a>Aby użyć okno wyrażeń kontrolnych

1. Z menu **Debuguj** wskaż pozycję **Windows**, wskaż pozycję **Obejrzyj**, a następnie kliknij pozycję **czujka 1**.

     Spowoduje to, że okno czujka 1 jest widoczne.

2. Wpisz `$bookAverage` w polu **Nazwa** , a następnie naciśnij klawisz ENTER.

     W oknie zostanie wyświetlona wartość zmiennej `$bookAverage`.

3. Wpisz `self::node()` w polu **Nazwa** , a następnie naciśnij klawisz ENTER.

     `self::node()` jest wyrażeniem XPath, które jest obliczane do bieżącego węzła kontekstu. Wartość wyrażenia `self::node()` XPath jest pierwszym węzłem książki. Zmiany są wprowadzane w trakcie transformacji.

4. Rozwiń węzeł `self::node()`, a następnie rozwiń węzeł `price`.

     Pozwala to zobaczyć wartość ceny książki i można ją łatwo porównać do wartości `$bookAverage`. Ze względu na to, że cena książki jest niższa od średniej, warunek `xsl:if` powinien się powieść.

## <a name="step-through-the-code"></a>Przechodzenie przez kod
 Debuger umożliwia wykonywanie kodu jeden wiersz jednocześnie.

#### <a name="to-step-through-the-code"></a>Aby przejść przez kod

1. Naciśnij klawisz **F5** , aby kontynuować.

     Ponieważ pierwszy węzeł książki spełnił warunek `xsl:if`, węzeł książki jest dodawany do okna dane wyjściowe XSL. Debuger kontynuuje działanie, dopóki nie zostanie ponownie umieszczony na `xsl:if` elemencie w arkuszu stylów. Debuger jest teraz umieszczony w drugim węźle książki w pliku Books. XML.

     W oknie Watch1 wartość `self::node()` zmieni się na drugi węzeł książki. Sprawdzając wartość elementu Price, możesz określić, że cena jest wyższa niż średnia, dlatego warunek `xsl:if` nie powinien kończyć się niepowodzeniem.

2. Naciśnij klawisz **F5** , aby kontynuować.

     Ponieważ drugi węzeł książki nie spełnia warunku `xsl:if`, węzeł książki nie zostanie dodany do okna dane wyjściowe XSL. Debuger kontynuuje działanie, dopóki nie zostanie ponownie umieszczony na `xsl:if` elemencie w arkuszu stylów. Debuger jest teraz umieszczony w trzecim węźle `book` w pliku Books. XML.

     W oknie Watch1 wartość `self::node()` zmieni się na trzeci węzeł książki. Sprawdzając wartość `price` elementu, można określić, że cena jest niższa od średniej, w rezultacie warunek `xsl:if` powinien się powieść.

3. Naciśnij klawisz **F5** , aby kontynuować.

     Ponieważ warunek `xsl:if` był spełniony, trzecia książka jest dodawana do okna dane wyjściowe XSL. Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzyma działanie.

## <a name="sample-files"></a>Pliki przykładowe
 Przewodnik korzysta z poniższych dwóch plików.

### <a name="belowavgxsl"></a>belowAvg. xsl

```
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

### <a name="booksxml"></a>Books. XML

```
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
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
