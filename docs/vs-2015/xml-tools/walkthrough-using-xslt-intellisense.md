---
title: 'Przewodnik: Używanie XSLT IntelliSense | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e6d1aa5cbcc4d996f2caf0e42f372dd3de9eee6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773298"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Przewodnik: Używanie XSLT IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tym instruktażu pokazano, jak za pomocą automatycznego uzupełniania wartości niektóre atrybuty XSLT IntelliSense.  
  
### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Można użyć funkcji IntelliSense w atrybut name elementu xsl: z param i Call-szablonu elementów  
  
1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:  
  
    ```  
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
  
2.  Ustaw kursor po `<xsl:template name="msg23" match="msg23">` i naciśnij klawisz ENTER. Następnie zacznij pisać następujące `xsl:call-template` elementu:  
  
    ```  
    <xsl:call-template name="localized-message">  
    </xsl:call-template>  
    ```  
  
     Zostanie wyświetlona lista nazwy szablonów w `name=""` atrybutu `xsl:call-template` elementu podczas wpisywania.  
  
3.  Ustaw kursor po `<xsl:call-template name="localized-message">` i naciśnij klawisz ENTER. Następnie zacznij pisać następujące `xsl:with-param` elementu:  
  
    ```  
    <xsl:with-param name="msgcode">msg23</xsl:with-param>  
    ```  
  
     Zostanie wyświetlona lista nazw parametrów w `name=""` atrybutu `xsl:with-param` elementu.  
  
### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Aby korzystać z technologii IntelliSense w atrybucie tryb XSL: Zastosuj szablony elementu  
  
1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:  
  
    ```  
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
  
2.  Ustaw kursor po `<xsl:apply-templates select="phone" />` i naciśnij klawisz ENTER. Następnie zacznij pisać następujące `xsl: apply-templates` elementu:  
  
    ```  
    <xsl:apply-templates select="phone"  mode="accountNumber">  
    ```  
  
     Lista trybów szablonu jest wyświetlana w `mode=""` atrybutu `xsl:apply-templates` elementu.  
  
### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Aby użyć funkcji IntelliSense w atrybuty prefiks arkusza stylów i wynik prefiks XSL: namespace-alias elementu  
  
1.  Utwórz nowy plik XSLT i skopiuj poniższy kod:  
  
    ```  
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
  
2.  Ustaw kursor po `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` i naciśnij klawisz ENTER. Następnie zacznij pisać następujące `xsl:namespace-alias` elementu:  
  
    ```  
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>  
    ```  
  
     Zwróć uwagę, jak listę prefiksów pojawiła się `stylesheet-prefix` i `result-prefix` atrybuty `xsl:namespace-alias` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje IntelliSense w edytorze XML](../xml-tools/xml-editor-intellisense-features.md)
