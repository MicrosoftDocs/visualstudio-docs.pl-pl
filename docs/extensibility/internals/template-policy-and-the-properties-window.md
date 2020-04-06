---
title: Zasady szablonu i okno Właściwości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704664"
---
# <a name="template-policy-and-the-properties-window"></a>Szablon zasad i okno właściwości
Gdy projekt znajduje się wewnątrz projektu szablonu przedsięwzięcia, ten projekt szablonu przedsięwzięcia może wymusić zasady. Zasady szablonu stają się systemem ograniczającym, który może służyć do ustawiania wartości domyślnych właściwości, ukrywania właściwości, dodawania właściwości itd.

 Używanie zasad szablonu do kontrolowania **Properties** wyświetlania informacji w oknie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Właściwości różni się od implementacji . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>obsługuje właściwości obiektu na poziomie składnika, podczas gdy zasady szablonu mogą być używane do ograniczania właściwości obiektu na poziomie rozwiązania lub projektu. Innymi słowy,

- Zaimplementuj metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> aby określić, co jest wyświetlane w oknie **Właściwości** dla określonych obiektów

- Użyj zasad szablonu na poziomie rozwiązania i projektu, aby określić, co jest wyświetlane w oknie **Właściwości** dla wcześniej określonych obiektów

  Za pomocą zasad szablonu selektywnie ograniczyć określone właściwości w oknie **Właściwości,** gdy element projektu określonego typu jest zaznaczony w **Eksploratorze rozwiązań** może być korzystne dla wszystkich członków zespołu deweloperów pracujących nad projektem. Na przykład za pomocą zasad szablonu, można skonfigurować wszystkie informacje o ciągu połączenia w bazie danych dla deweloperów i ustawić tylko do odczytu ciągu połączenia. W ten sposób można zapewnić prosty sposób, aby zapewnić, że każdy deweloper używa poprawnej ścieżki dostępu do danych.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
