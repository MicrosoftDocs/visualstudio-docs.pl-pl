---
title: Zasady szablonów i okno właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722689"
---
# <a name="template-policy-and-the-properties-window"></a>Szablon zasad i okno właściwości
Gdy projekt jest zawarty w projekcie szablonu przedsiębiorstwa, ten projekt szablonu przedsiębiorstwa może wymusić zasady. Zasady szablonów staną się systemem ograniczającym, który może służyć do ustawiania wartości domyślnych właściwości, ukrywania właściwości, dodawania właściwości i tak dalej.

 Używanie zasad szablonu do kontrolowania wyświetlania informacji w oknie **Właściwości** różni się od implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> obsługuje właściwości obiektów na poziomie składnika, podczas gdy zasady szablonów mogą służyć do ograniczenia właściwości obiektów na poziomie rozwiązania lub projektu. Innymi słowy

- Zaimplementuj metody na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>, aby określić, co jest wyświetlane w oknie **Właściwości** dla określonych obiektów

- Użyj zasad szablonu na poziomie rozwiązania i projektu, aby określić, co jest wyświetlane w oknie **Właściwości** dla poprzednio określonych obiektów

  Używanie zasad szablonów do selektywnego ograniczania określonych właściwości w oknie **Właściwości** , gdy element projektu określonego typu jest wybrany w **Eksplorator rozwiązań** może być korzystne dla wszystkich członków zespołu projektowego pracującego nad projektem. Na przykład za pomocą zasad szablonu można skonfigurować wszystkie informacje o parametrach połączenia w bazie danych dla deweloperów i wprowadzić parametry połączenia tylko do odczytu. W ten sposób można zapewnić prostą metodę, aby zapewnić, że każdy deweloper korzysta z właściwej ścieżki dostępu do danych.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)