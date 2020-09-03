---
title: Zasady szablonów i okno właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156022"
---
# <a name="template-policy-and-the-properties-window"></a>Szablon zasad i okno właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy projekt jest zawarty w projekcie szablonu przedsiębiorstwa, ten projekt szablonu przedsiębiorstwa może wymusić zasady. Zasady szablonów staną się systemem ograniczającym, który może służyć do ustawiania wartości domyślnych właściwości, ukrywania właściwości, dodawania właściwości i tak dalej.  
  
 Używanie zasad szablonu do kontrolowania wyświetlania informacji w oknie **Właściwości** jest inne niż implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> obsługuje właściwości obiektów na poziomie składnika, podczas gdy zasady szablonów mogą służyć do ograniczania właściwości obiektów na poziomie rozwiązania lub projektu. Innymi słowy  
  
- Zaimplementuj metody w, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Aby określić, co jest wyświetlane w oknie **Właściwości** dla określonych obiektów  
  
- Użyj zasad szablonu na poziomie rozwiązania i projektu, aby określić, co jest wyświetlane w oknie **Właściwości** dla poprzednio określonych obiektów  
  
  Używanie zasad szablonów do selektywnego ograniczania określonych właściwości w oknie **Właściwości** , gdy element projektu określonego typu jest wybrany w **Eksplorator rozwiązań** może być korzystne dla wszystkich członków zespołu projektowego pracującego nad projektem. Na przykład za pomocą zasad szablonu można skonfigurować wszystkie informacje o parametrach połączenia w bazie danych dla deweloperów i wprowadzić parametry połączenia tylko do odczytu. W ten sposób można zapewnić prostą metodę, aby zapewnić, że każdy deweloper korzysta z właściwej ścieżki dostępu do danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
