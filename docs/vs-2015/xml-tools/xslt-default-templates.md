---
title: Domyślne szablony XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bb4351d6b95c7aee929274135454ecf7aa91574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669335"
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon domyślny jest używany podczas przetwarzania XSLT, gdy w arkuszu stylów nie ma zgodnej reguły jawnego szablonu. Szablon domyślny, nazywany również regułą szablonu wbudowanego, jest zdefiniowany w sekcji 5,8 zalecenia W3C XSLT 1,0. Szablon domyślny pozwala procesorowi XSLT przetwarzać węzeł, mimo że nie istnieje jawna reguła szablonu, która go odpowiada. Jednak ponieważ wbudowana reguła szablonu nie jest jawnie zdefiniowana w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylących wyników transformacji XSLT.

 Debuger XSLT wyświetla teraz kod domyślnych szablonów XSLT. W przypadku przechodzenia przez transformację XSLT w przypadku użycia szablonu domyślnego debuger wyświetla szablon domyślny w oknie. Pozwala to na przechodzenie przez kod szablonu domyślnego i ustawianie punktów przerwania w instrukcji.

## <a name="see-also"></a>Zobacz też
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
