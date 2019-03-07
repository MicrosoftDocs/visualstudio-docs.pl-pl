---
title: Ocena wyrażenia XPath podczas debugowania
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526325"
---
# <a name="evaluate-xpath-expressions"></a>Obliczanie wyrażeń XPath

Można obliczać wyrażeń XPath przy użyciu **QuickWatch** okna podczas debugowania. Wyrażenie XPath muszą być prawidłowe zgodnie z zaleceniem W3C XPath 1.0. Bieżący kontekst w XSLT (oznacza to, `self::node()` w węźle **lokalne** okna) zapewnia kontekstu oceny wyrażenia XPath.

Podczas obliczania wyrażenia XPath:

- Wbudowane funkcje XPath są obsługiwane.

- Wbudowane funkcje XSLT i funkcji zdefiniowanych przez użytkownika nie są obsługiwane.

> [!NOTE]
> Debugowanie kodu XSLT jest dostępna tylko w wersji Enterprise programu Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Ocena wyrażenia XPath

W poniższej procedurze użyto *poniżej average.xsl* i *books.xml* plików ze [instruktażu: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) strony.

1. Wstaw punkt przerwania w `xsl:if` taga otwierającego.

2. Aby rozpocząć debugowanie, wybierz **XML** > **Rozpocznij debugowanie kodu XSLT** na pasku menu (lub naciśnij **Alt**+**F5** ).

   Debuger rozpoczyna się i przerywa na `xsl:if` tagu.

3. Kliknij prawym przyciskiem myszy i wybierz **QuickWatch**.

   **QuickWatch** zostanie otwarte okno.

4. Wprowadź `./price/text()` w **wyrażenie** pole **QuickWatch** okna dialogowego pole, a następnie wybierz **to ponowne ocenienie**.

   Cena bieżącego węzła książki, który pojawia się w **wartość** pole.

   ![Ocena wyrażenia XPath w oknie Quickwatch](media/quickwatch-price.png)

5. Zmień wyrażenie XPath `./price/text() < $bookAverage` i kliknij przycisk **to ponowne ocenienie**.

   **Wartość** pole pokazuje, że wyrażenie XPath daje w wyniku `true`.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)