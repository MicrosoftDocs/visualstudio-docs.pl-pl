---
title: Oceń wyrażenie XPath podczas debugowania
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e0b6c84fa9447dc38aa7976fa59bb5aa67d5c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592727"
---
# <a name="evaluate-xpath-expressions"></a>Oceń wyrażenia XPath

Wyrażenia XPath można oszacować przy użyciu okna **QuickWatch** podczas debugowania. Wyrażenie XPath musi być prawidłowe zgodnie z zaleceniem W3C XPath 1,0. Bieżący kontekst XSLT (czyli węzeł `self::node()` w oknie **zmiennych lokalnych** ) zawiera kontekst oceny dla wyrażenia XPath.

Podczas oceniania wyrażenia XPath:

- Obsługiwane są wbudowane funkcje języka XPath.

- Wbudowane funkcje XSLT i funkcje zdefiniowane przez użytkownika nie są obsługiwane.

> [!NOTE]
> Debugowanie XSLT jest dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Ocena wyrażenia XPath

Poniższa procedura korzysta z plików *below-Average. xsl* i *Books. XML* z [przewodnika: debugowanie strony arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Wstaw punkt przerwania w tagu początkowym `xsl:if`.

2. Aby rozpocząć debugowanie, wybierz pozycję **XML** > **Rozpocznij debugowanie XSLT** na pasku menu (lub naciśnij klawisz **Alt**+**F5**).

   Debuger rozpocznie działanie i przerwie w tagu `xsl:if`.

3. Kliknij prawym przyciskiem myszy i wybierz pozycję **QuickWatch**.

   Zostanie otwarte okno **QuickWatch** .

4. W polu **wyrażenie** okna dialogowego **QuickWatch** wprowadź `./price/text()` a następnie wybierz pozycję **Oblicz**ponownie.

   W polu **wartość** zostanie wyświetlona cena bieżącego węzła księgi.

   ![Oceń wyrażenie XPath w oknie QuickWatch](media/quickwatch-price.png)

5. Zmień wyrażenie XPath na `./price/text() < $bookAverage` i kliknij przycisk **Oblicz wszystko**.

   Pole **wartość** pokazuje, że wyrażenie XPath oblicza wartość `true`.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
