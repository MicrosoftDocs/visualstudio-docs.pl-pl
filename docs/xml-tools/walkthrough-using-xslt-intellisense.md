---
title: 'Przewodnik: używanie funkcji XSLT IntelliSense'
description: Dowiedz się, jak używać funkcji IntelliSense XSLT do autouzupełniania wartości niektórych atrybutów, wykonując kroki opisane w tym instruktażu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c8bbed6a70316e92e2c79aaa6cabc20930f10e7
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351469"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Przewodnik: używanie funkcji XSLT IntelliSense

W tym instruktażu pokazano, jak używać funkcji IntelliSense XSLT do autouzupełniania wartości niektórych atrybutów.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Aby użyć funkcji IntelliSense w atrybucie name atrybutu xsl: with-param i xsl: call-template

1. Utwórz nowy plik XSLT i skopiuj go w następującym kodzie:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Wstaw kursor po `<xsl:template name="msg23" match="msg23">` naciśnięciu klawisza **Enter**. Następnie zacznij wpisywać następujący `xsl:call-template` element:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Lista nazw szablonów pojawia się w `name=""` atrybucie `xsl:call-template` elementu podczas pisania.

3. Wstaw kursor po `<xsl:call-template name="localized-message">` naciśnięciu klawisza **Enter**. Następnie zacznij wpisywać następujący `xsl:with-param` element:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Lista nazw parametrów pojawia się w `name=""` atrybucie `xsl:with-param` elementu.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Aby użyć funkcji IntelliSense w atrybucie Mode elementu xsl: Apply-templates

1. Utwórz nowy plik XSLT i skopiuj go w następującym kodzie:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Wstaw kursor po `<xsl:apply-templates select="phone" />` naciśnięciu klawisza **Enter**. Następnie zacznij wpisywać następujący `xsl: apply-templates` element:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Lista trybów szablonów pojawia się w `mode=""` atrybucie `xsl:apply-templates` elementu.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Aby użyć funkcji IntelliSense we właściwościach stylesheet-prefix i prefix elementu xsl: Namespace-alias

1. Utwórz nowy plik XSLT i skopiuj go w następującym kodzie:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Wstaw kursor po `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` naciśnięciu klawisza **Enter**. Następnie zacznij wpisywać następujący `xsl:namespace-alias` element:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Zwróć uwagę na to, jak lista prefiksów występuje `stylesheet-prefix` w `result-prefix` atrybuty i `xsl:namespace-alias` elementu.

## <a name="see-also"></a>Zobacz też

- [Funkcje IntelliSense w edytorze XML](../xml-tools/xml-editor-intellisense-features.md)
