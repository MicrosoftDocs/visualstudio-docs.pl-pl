---
title: 'Instrukcje: Ocena wyrażenia XPath'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b43a82d476e4426b1428f072cc980dbc8631cff2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970403"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Instrukcje: Ocena wyrażenia XPath

Można obliczyć wyrażenia XPath z **QuickWatch** okno dialogowe. Wyrażenie XPath muszą być prawidłowe zgodnie z zaleceniem W3C XPath 1.0. Bieżący kontekst w XSLT — oznacza to, `self::node()` w węźle **lokalne** okna — zapewnia kontekstu oceny wyrażenia XPath.

 Na poniższej liście opisano, jakie funkcje są obsługiwane podczas obliczania wyrażenia XPath:

-   Wbudowane funkcje XPath są obsługiwane.

-   Wbudowane funkcje XSLT nie są obsługiwane.

-   Funkcje zdefiniowane przez użytkownika nie są obsługiwane.

> [!NOTE]
> W poniższej procedurze użyto *belowAvg.xsl* i *books.xml* plików ze [instruktażu: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tematu.

## <a name="to-evaluate-an-xpath-expression"></a>Aby szacować wyrażenia XPath

1.  Wstaw punkt przerwania w `xsl:if` taga otwierającego.

2.  Kliknij przycisk **debugowania XSL** na listwie narzędziowej edytora XML.

     Debuger rozpoczyna się i przerywa na `xsl:if` tagu.

3.  Kliknij prawym przyciskiem myszy i wybierz **QuickWatch**.

     **QuickWatch** zostanie wyświetlone okno dialogowe.

4.  Wprowadź `./price/text()` w **wyrażenie** pole **QuickWatch** dialogowym i kliknij przycisk **to ponowne ocenienie**.

     Cena bieżącego węzła książki, który pojawia się w **wartość** pole.

5.  Zmień wyrażenie XPath `./price/text() < $bookAverage` i kliknij przycisk **to ponowne ocenienie**.

     **Wartość** pole pokazuje, że wyrażenie XPath daje w wyniku `true`.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)