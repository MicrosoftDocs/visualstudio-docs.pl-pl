---
title: Szablony domyślne XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a764aa45eb74ba110d8b3b5965ede1e62bdadd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607781"
---
# <a name="xslt-default-templates"></a>Domyślne szablony XSLT

Szablon domyślny jest używany podczas przetwarzania XSLT, gdy w arkuszu stylów nie ma zgodnej reguły jawnego szablonu. Szablon domyślny, nazywany również regułą szablonu wbudowanego, jest zdefiniowany w sekcji 5,8 zalecenia W3C XSLT 1,0. Szablon domyślny pozwala procesorowi XSLT przetwarzać węzeł, mimo że nie istnieje jawna reguła szablonu, która go odpowiada. Jednak ponieważ wbudowana reguła szablonu nie jest jawnie zdefiniowana w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylących wyników transformacji XSLT.

Debuger XSLT wyświetla teraz kod domyślnych szablonów XSLT. W przypadku przechodzenia przez transformację XSLT w przypadku użycia szablonu domyślnego debuger wyświetla szablon domyślny w oknie. Pozwala to na przechodzenie przez kod szablonu domyślnego i ustawianie punktów przerwania w instrukcji.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)