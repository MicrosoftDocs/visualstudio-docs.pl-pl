---
title: Szablony domyślne XSLT
description: Dowiedz się więcej o domyślnych szablonach XSLT, które są używane podczas przetwarzania XSLT, gdy w arkuszu stylów nie ma zgodnej reguły jawnego szablonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e8efdc1a35e6129de7e33d28fa7592ead48e17e
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350130"
---
# <a name="xslt-default-templates"></a>Domyślne szablony XSLT

Szablon domyślny jest używany podczas przetwarzania XSLT, gdy w arkuszu stylów nie ma zgodnej reguły jawnego szablonu. Szablon domyślny, nazywany również regułą szablonu wbudowanego, jest zdefiniowany w sekcji 5,8 zalecenia W3C XSLT 1,0. Szablon domyślny pozwala procesorowi XSLT przetwarzać węzeł, mimo że nie istnieje jawna reguła szablonu, która go odpowiada. Jednak ponieważ wbudowana reguła szablonu nie jest jawnie zdefiniowana w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylących wyników transformacji XSLT.

Debuger XSLT wyświetla teraz kod domyślnych szablonów XSLT. W przypadku przechodzenia przez transformację XSLT w przypadku użycia szablonu domyślnego debuger wyświetla szablon domyślny w oknie. Pozwala to na przechodzenie przez kod szablonu domyślnego i ustawianie punktów przerwania w instrukcji.

## <a name="see-also"></a>Zobacz też

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
