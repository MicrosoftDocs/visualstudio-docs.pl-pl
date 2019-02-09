---
title: 'Przewodnik: Korzystanie z hierarchii XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83081b7fb03a4272622c25f783abbc7134fac12b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970390"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Przewodnik: Użycie hierarchii XSLT

Narzędzie hierarchii XSLT upraszcza wiele zadań programistycznych XML. Arkusz stylów XSLT często używa `includes` i `imports` instrukcje. Kompilacja zaczyna się od arkusza stylów jednostki, ale gdy zostanie wyświetlony błąd w wyniku kompilacji arkusz stylów XSLT błędu mogą pochodzić z innego źródła niż arkusza stylów podmiotu zabezpieczeń. Naprawianie błędu lub edytowania arkusza stylów mogą wymagać dostępu do arkuszy stylów dołączanego lub importowanego. Krokowego wykonywania arkusza stylów w debugerze mogą otwierać arkusze stylów dołączone i importowanie i chcesz dodać punkt przerwania w pewnym momencie w co najmniej jednej arkusze stylów dołączone.

Inny scenariusz, w którym narzędzie hierarchii XSLT może być przydatne jest umieszczenie punktów przerwania w regułach wbudowany szablon. Szablon reguły są specjalne szablony generowane dla każdego trybu arkusza stylów i wywoływane przez `xsl:apply-templates` gdy szablon nie pasuje do węzła. Aby zaimplementować profilowanie wbudowanych szablonów reguł, debuger XSLT generuje plik z zasadami w folderze tymczasowym i kompiluje je wraz z arkusza stylów podmiotu zabezpieczeń. Bez Przechodzenie do kodu z niektórych `xsl:apply-template`, może być trudno znaleźć arkuszy stylów, które zostały uwzględnione w arkuszu stylów podmiotu zabezpieczeń lub znaleźć i otworzyć arkusz stylów za pomocą wbudowanego szablonu reguły.

W przykładzie w tym temacie pokazano, debugowanie w arkuszu stylów odwołania.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Aby debugować w arkuszu stylów odwołania

1. Otwórz dokument XML w programie Visual Studio. W tym przykładzie użyto następujący dokument:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Dodaj następujący kod *xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  Dodaj następujący kod *xslinclude.xsl* pliku:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  Dodaj punkt przerwania w instrukcji `<xsl:include href="xslincludefile.xsl" />`.

5.  Rozpocznij debugowanie.

6.  Gdy debuger zatrzymuje się w instrukcji `<xsl:include href="xslincludefile.xsl" />`, naciśnij klawisz **Step Into** przycisku. Debugowanie może być kontynuowane w arkuszu stylów odwołania. Hierarchia jest widoczna i Projektant wyświetla prawidłową ścieżkę.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: XSLT profiler](../xml-tools/walkthrough-xslt-profiler.md)