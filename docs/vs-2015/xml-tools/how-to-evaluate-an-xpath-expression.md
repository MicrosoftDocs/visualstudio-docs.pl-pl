---
title: 'Instrukcje: Ocena wyrażenia XPath | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a0c79da47b83f8bf5b44af16ca291e2424011b80
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075613"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Instrukcje: Ocena wyrażenia XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można obliczyć wyrażenia XPath z **QuickWatch** okno dialogowe. Wyrażenie XPath muszą być prawidłowe zgodnie z zaleceniem W3C XPath 1.0. Bieżący kontekst w XSLT — oznacza to, `self::node()` w węźle **lokalne** okna — zapewnia kontekstu oceny wyrażenia XPath.  
  
 Na poniższej liście opisano, jakie funkcje są obsługiwane podczas obliczania wyrażenia XPath:  
  
- Wbudowane funkcje XPath są obsługiwane.  
  
- Wbudowane funkcje XSLT nie są obsługiwane.  
  
- Funkcje zdefiniowane przez użytkownika nie są obsługiwane.  
  
> [!NOTE]
>  W poniższej procedurze użyto belowAvg.xsl i books.xml pliki z [instruktażu: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tematu.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Aby szacować wyrażenia XPath  
  
1. Wstaw punkt przerwania w `xsl:if` taga otwierającego.  
  
2. Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.  
  
     Debuger rozpoczyna się i przerywa na `xsl:if` tagu.  
  
3. Kliknij prawym przyciskiem myszy i wybierz **QuickWatch**.  
  
     **QuickWatch** zostanie wyświetlone okno dialogowe.  
  
4. Wprowadź `./price/text()` w **wyrażenie** pole **QuickWatch** dialogowym i kliknij przycisk **to ponowne ocenienie**.  
  
     Cena bieżącego węzła książki, który pojawia się w **wartość** pole.  
  
5. Zmień wyrażenie XPath `./price/text() < $bookAverage` i kliknij przycisk **to ponowne ocenienie**.  
  
     **Wartość** pole pokazuje, że wyrażenie XPath daje w wyniku `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
