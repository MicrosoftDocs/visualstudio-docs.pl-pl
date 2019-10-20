---
title: 'Przewodnik: używanie hierarchii XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46e6acc8f65a9c9589348508f57cc75b04c61ccc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669553"
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Przewodnik: używanie hierarchii XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie hierarchii XSLT upraszcza wiele zadań związanych z programowaniem XML. Arkusz stylów XSLT często używa instrukcji `includes` i `imports`. Kompilacja zaczyna się od głównego arkusza stylów, ale gdy zobaczysz błąd w wyniku kompilowania arkusza stylów XSLT, błąd może pochodzić z innego źródła niż główny arkusz stylów. Usunięcie błędu lub edytowanie arkusza stylów może wymagać dostępu do arkuszy stylów dołączonych lub zaimportowanych. Przechodzenie przez arkusz stylów w debugerze może otwierać dołączone i zaimportowane arkusze stylów. w pewnym momencie można dodać punkt przerwania w jednym lub kilku dołączonych arkuszach stylów.

 Innym scenariuszem, który może być przydatne narzędzie hierarchii XSLT, jest umieszczenie punktów przerwania w regułach wbudowanych szablonów. Reguły szablonów to specjalne szablony wygenerowane dla każdego trybu arkusza stylów i wywoływane przez `xsl:apply-templates`, gdy żaden inny szablon nie jest zgodny z węzłem. Aby zaimplementować debugowanie w regułach wbudowanych szablonów, debuger XSLT generuje plik z regułami w folderze tymczasowym i kompiluje je razem z głównym arkuszem stylów. Bez przechodzenia do kodu z niektórych `xsl:apply-template` może być trudno znaleźć arkusze stylów, które zostały uwzględnione w głównym arkuszu stylów lub znaleźć i otworzyć arkusz stylów z wbudowanymi regułami szablonu.

 W przykładzie w tym temacie pokazano debugowanie w arkuszu stylów, do którego się odwołuje.

### <a name="procedure-title"></a>Tytuł procedury

1. Otwórz dokument XML w programie Visual Studio. W tym przykładzie zastosowano następujący dokument `collection.xml`.

    ```
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

2. Dodaj następujące `xslincludefile.xsl`:

    ```
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

3. Dodaj następujący plik `xslinclude.xsl`:

    ```
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

4. Dodaj punkt przerwania w instrukcji: `<xsl:include href="xslincludefile.xsl" />`

5. Rozpocznij debugowanie.

6. Gdy debuger zatrzyma się na instrukcji `<xsl:include href="xslincludefile.xsl" />`, naciśnij przycisk Przejdź do przycisku. Należy zauważyć, że debugowanie może być kontynuowane w przywoływanym arkuszu stylów. Hierarchia jest widoczna, a Projektant wyświetla właściwą ścieżkę.

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Profiler XSLT](../xml-tools/walkthrough-xslt-profiler.md)
