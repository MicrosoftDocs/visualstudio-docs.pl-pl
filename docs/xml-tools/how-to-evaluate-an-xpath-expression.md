---
title: Oceń wyrażenie XPath podczas debugowania
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64113461cd081eb97e2eb927119f1cd67f8a8d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816257"
---
# <a name="evaluate-xpath-expressions"></a>Oceń wyrażenia XPath

Wyrażenia XPath można oszacować przy użyciu okna **QuickWatch** podczas debugowania. Wyrażenie XPath musi być prawidłowe zgodnie z zaleceniem W3C XPath 1,0. Bieżący kontekst XSLT (czyli `self::node()` węzeł w oknie **zmiennych lokalnych** ) zawiera kontekst oceny dla wyrażenia XPath.

Podczas oceniania wyrażenia XPath:

- Obsługiwane są wbudowane funkcje języka XPath.

- Wbudowane funkcje XSLT i funkcje zdefiniowane przez użytkownika nie są obsługiwane.

> [!NOTE]
> Debugowanie XSLT jest dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Ocena wyrażenia XPath

Poniższa procedura korzysta z plików *below-Average. xsl* i *books.xml* z [przewodnika: debugowanie strony arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Wstaw punkt przerwania w `xsl:if` tagu początkowym.

2. Aby rozpocząć debugowanie, wybierz pozycję **XML**  >  **Rozpocznij debugowanie XSLT** na pasku menu (lub naciśnij klawisz **Alt** + **F5**).

   Debuger zostanie uruchomiony i podzielony na `xsl:if` tag.

3. Kliknij prawym przyciskiem myszy i wybierz pozycję **QuickWatch**.

   Zostanie otwarte okno **QuickWatch** .

4. Wprowadź `./price/text()` wartość w polu **wyrażenie** okna dialogowego **QuickWatch** , a następnie wybierz pozycję ponownie **Oceń**.

   W polu **wartość** zostanie wyświetlona cena bieżącego węzła księgi.

   ![Oceń wyrażenie XPath w oknie QuickWatch](media/quickwatch-price.png)

5. Zmień wyrażenie XPath na `./price/text() < $bookAverage` a następnie kliknij pozycję **Oblicz ocenę**.

   Pole **wartość** pokazuje, że wyrażenie XPath daje wynik `true` .

## <a name="see-also"></a>Zobacz też

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
