---
title: 'Przewodnik: Debugowanie arkusza stylów XSLT | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e685e77dafe00b8cadd9b273ccc61c8e5d9e1e4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085106"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Przewodnik: Debugowanie arkusza stylów XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroki opisane w tym przewodniku pokazują, jak za pomocą debugera XSLT. Kroki obejmują wyświetlanie zmiennych, ustawiania punktów przerwania i krokowe wykonywanie kodu. Arkusz stylów znajduje wszystkie książki, które koszt poniżej średnią cenę książek.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika  
  
1. Zamknij wszystkie otwarte rozwiązania.  
  
2. Skopiuj dwa pliki przykładowe do komputera lokalnego.  
  
## <a name="start-debugging"></a>Rozpocznij debugowanie  
  
#### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie  
  
1. Z **pliku** menu wskaż **Otwórz**i kliknij przycisk **pliku**.  
  
2. Zlokalizuj plik belowAvg.xsl, a następnie kliknij przycisk **Otwórz**.  
  
    Arkusz stylów jest otwarty w edytorze XML.  
  
3. Kliknij przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.  
  
4. Zlokalizuj plik books.xml, a następnie kliknij przycisk **Otwórz**.  
  
    Spowoduje to ustawienie pliku dokumentu źródłowego, który jest używany do transformacji XSLT.  
  
5. Kliknij prawym przyciskiem myszy `xsl:if` tag początkowy, wskaż opcję **punktu przerwania**i kliknij przycisk **Wstaw punkt przerwania**.  
  
6. Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.  
  
   Spowoduje to uruchomienie procesu debugowania i otwiera kilka nowych oknach, które są używane przez debuger.  
  
   Istnieją dwa okna wyświetlające wejściowych arkusza stylów i dokumentów. Debuger używa tych okien, aby wyświetlić bieżący stan wykonania. Debuger jest ustawiony na `xsl:if` element arkusza stylów i w pierwszym węźle książki w pliku books.xml.  
  
   Okno zmiennych lokalnych, wyświetla wszystkie zmienne lokalne oraz ich bieżących wartości. Obejmuje to zmienne zdefiniowane w arkuszu stylów, a także zmienne używane przez debuger do śledzenia węzły, które są obecnie dostępne w kontekście.  
  
   **Danych wyjściowych XSL** okna wyświetla dane wyjściowe transformacji XSL. To okno jest oddzielony od **Visual Studio dane wyjściowe** okna.  
  
## <a name="watch-window"></a>W oknie czujki  
  
#### <a name="to-use-the-watch-window"></a>Aby użyć okna czujki  
  
1. Z **debugowania** menu wskaż **Windows**, wskaż polecenie **Obejrzyj**i kliknij przycisk **Czujka 1**.  
  
     To sprawia, że w oknie Czujka 1 widoczne.  
  
2. Typ `$bookAverage` w **nazwa** pola, a następnie naciśnij klawisz ENTER.  
  
     Wartość `$bookAverage` zmienna jest wyświetlany w oknie.  
  
3. Typ `self::node()` w **nazwa** pola, a następnie naciśnij klawisz ENTER.  
  
     `self::node()` to wyrażenie XPath, które daje w wyniku bieżącego węzła kontekstu. Wartość `self::node()` wyrażenie XPath jest pierwszym węźle książki. To zmian w miarę postępów za pomocą transformacji.  
  
4. Rozwiń `self::node()` węzła, a następnie rozwiń węzeł `price` węzła.  
  
     Dzięki temu można zobaczyć wartość ceny książki i należy go do łatwiejszego porównania `$bookAverage` wartość. Ponieważ cena książki jest poniżej średniej, `xsl:if` warunek ma być pomyślnie wykonane.  
  
## <a name="step-through-the-code"></a>Przechodź przez kod  
 Debuger umożliwia wykonywanie jednego wiersza kodu naraz.  
  
#### <a name="to-step-through-the-code"></a>Aby przejść przez kod  
  
1. Naciśnij klawisz **F5** aby kontynuować.  
  
     Ponieważ spełnione pierwszego węzła książki `xsl:if` warunku węzła książki jest dodawany do okna danych wyjściowych XSL. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony w drugim węźle książki w pliku books.xml.  
  
     W oknie Watch1 `self::node()` wartość zmienia się na drugiego węzła książki. Sprawdzając wartość elementu ceny, należy określić, że cena jest powyżej średniej, dlatego `xsl:if` warunku powinna zakończyć się niepowodzeniem.  
  
2. Naciśnij klawisz **F5** aby kontynuować.  
  
     Ponieważ nie spełnia drugiego węzła książki `xsl:if` warunku węzła książki nie została dodana do okna danych wyjściowych XSL. Debuger kontynuuje wykonywanie dopóki nie jest ponownie umieszczone na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz umieszczony w trzeciej `book` węzeł w pliku books.xml.  
  
     W oknie Watch1 `self::node()` zmiany wartości na trzeci węzła książki. Sprawdzając wartość `price` elementu, można określić czy cena wynosi poniżej średniej, dlatego `xsl:if` warunek ma być pomyślnie wykonane.  
  
3. Naciśnij klawisz **F5** aby kontynuować.  
  
     Ponieważ `xsl:if` warunek był spełniony, trzeci książka zostanie dodana do okna danych wyjściowych XSL. Wszystkie książki w dokumencie XML zostały przetworzone i debuger zatrzymuje się.  
  
## <a name="sample-files"></a>Przykładowe pliki  
 Następujące dwa pliki są używane przez instruktażu.  
  
### <a name="belowavgxsl"></a>belowAvg.xsl  
  
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
  
### <a name="booksxml"></a>Books.XML  
  
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
