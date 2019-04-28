---
title: Szablony domyślne XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2910a9f81a8bf4bf1e5f25245ad9a3b02adffe1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807702"
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT

Domyślny szablon jest używany podczas przetwarzania, gdy nie ma pasującego jawnego szablonu reguły w arkuszu stylów XSLT. Domyślny szablon, nazywana także wbudowany szablon reguły, jest zdefiniowany w sekcji 5.8 zalecenia 1.0 W3C XSLT. Domyślny szablon umożliwia procesora XSLT można przetworzyć węzła, nawet jeśli nie jawnego szablonu reguły, który mu odpowiada. Jednak ponieważ reguły wbudowany szablon nie jest jawnie zdefiniowany w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylące wyniki przekształcenia XSLT.

Debuger XSLT wyświetla teraz kod szablony domyślne XSLT. Kiedy wkraczasz przy użyciu transformacji XSLT, jeśli użyty zostanie szablon domyślny, debuger wyświetla domyślny szablon w oknie. Dzięki temu można przejść przez kod szablonu domyślnego i ustawiania punktów przerwania w instrukcji.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)