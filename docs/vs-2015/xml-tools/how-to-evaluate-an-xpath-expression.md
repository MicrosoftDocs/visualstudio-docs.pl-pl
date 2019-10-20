---
title: 'Instrukcje: szacowanie wyrażenia XPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670868"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Instrukcje: szacowanie wyrażenia XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyrażenia XPath można obliczyć przy użyciu okna dialogowego **QuickWatch** . Wyrażenie XPath musi być prawidłowe zgodnie z zaleceniem W3C XPath 1,0. Bieżący kontekst XSLT — to znaczy węzeł `self::node()` w oknie **zmiennych lokalnych** — zawiera kontekst oceny dla wyrażenia XPath.

 Na poniższej liście opisano, które funkcje są obsługiwane podczas oceniania wyrażenia XPath:

- Obsługiwane są wbudowane funkcje języka XPath.

- Wbudowane funkcje XSLT nie są obsługiwane.

- Funkcje zdefiniowane przez użytkownika nie są obsługiwane.

> [!NOTE]
> Poniższa procedura korzysta z plików belowAvg. xsl i Books. XML z [przewodnika: debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Aby oszacować wyrażenie XPath

1. Wstaw punkt przerwania w tagu początkowym `xsl:if`.

2. Kliknij przycisk **DEBUGUJ XSL** na pasku narzędzi edytora XML.

     Debuger rozpocznie działanie i przerwie w tagu `xsl:if`.

3. Kliknij prawym przyciskiem myszy i wybierz pozycję **QuickWatch**.

     Zostanie wyświetlone okno dialogowe **QuickWatch** .

4. W polu **wyrażenie** okna dialogowego **QuickWatch** wprowadź `./price/text()` i kliknij przycisk **Oblicz**ponownie.

     W polu **wartość** zostanie wyświetlona cena bieżącego węzła księgi.

5. Zmień wyrażenie XPath na `./price/text() < $bookAverage` i kliknij przycisk **Oblicz wszystko**.

     Pole **wartość** pokazuje, że wyrażenie XPath oblicza wartość `true`.

## <a name="see-also"></a>Zobacz też
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
