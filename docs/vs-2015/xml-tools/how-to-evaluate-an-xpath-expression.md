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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670868"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Instrukcje: Ocena wyrażenia XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyrażenia XPath można obliczyć przy użyciu okna dialogowego **QuickWatch** . Wyrażenie XPath musi być prawidłowe zgodnie z zaleceniem W3C XPath 1,0. Bieżący kontekst XSLT — czyli `self::node()` węzeł w oknie **zmiennych lokalnych** — zawiera kontekst oceny dla wyrażenia XPath.

 Na poniższej liście opisano, które funkcje są obsługiwane podczas oceniania wyrażenia XPath:

- Obsługiwane są wbudowane funkcje języka XPath.

- Wbudowane funkcje XSLT nie są obsługiwane.

- Funkcje zdefiniowane przez użytkownika nie są obsługiwane.

> [!NOTE]
> Poniższa procedura korzysta z plików belowAvg. xsl i books.xml z [przewodnika: debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Aby oszacować wyrażenie XPath

1. Wstaw punkt przerwania w `xsl:if` tagu początkowym.

2. Kliknij przycisk **DEBUGUJ XSL** na pasku narzędzi edytora XML.

     Debuger zostanie uruchomiony i podzielony na `xsl:if` tag.

3. Kliknij prawym przyciskiem myszy i wybierz pozycję **QuickWatch**.

     Zostanie wyświetlone okno dialogowe **QuickWatch** .

4. Wprowadź `./price/text()` wartość w polu **wyrażenie** okna dialogowego **QuickWatch** i kliknij przycisk **Oblicz**ponownie.

     W polu **wartość** zostanie wyświetlona cena bieżącego węzła księgi.

5. Zmień wyrażenie XPath na `./price/text() < $bookAverage` a następnie kliknij pozycję **Oblicz ocenę**.

     Pole **wartość** pokazuje, że wyrażenie XPath daje wynik `true` .

## <a name="see-also"></a>Zobacz też
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
