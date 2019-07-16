---
title: Szablon zasad i okno właściwości | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156022"
---
# <a name="template-policy-and-the-properties-window"></a>Szablon zasad i okno właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy projekt znajduje się wewnątrz szablonu projektu w przedsiębiorstwie, tego szablonu projektu przedsiębiorstwa mogą wymusić zasady. Szablon zasad staje się ograniczający system, który może służyć do ustawiania wartości domyślnej właściwości, Ukryj właściwości, dodać właściwości i tak dalej.  
  
 Za pomocą zasad szablonu do sterowania wyświetlaniem informacje zawarte w **właściwości** okna różni się od wykonania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> szablon zasad można zastosować, aby ograniczyć właściwości obiektów na poziomie rozwiązania lub projektu, obsługuje właściwości obiektów na poziomie składnika. Innymi słowy  
  
- Implementowanie metod na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Aby ustalić, co jest wyświetlane w **właściwości** okna dla określonych obiektów  
  
- Użyj szablonu zasad na poziomie rozwiązania i projektu Aby ustalić, co jest wyświetlane w **właściwości** okno wcześniej określone obiekty  
  
  Przy użyciu szablonu zasad selektywne ograniczenie właściwości określone w **właściwości** wybrano okna, jeśli element projektu o określonym typie **Eksploratora rozwiązań** może być korzystne, aby wszystkie elementy członkowskie pracujesz nad projektem zespołu programistycznego. Na przykład za pomocą szablonu zasad, można skonfigurować wszystkie parametry połączenia informacje w bazie danych dla deweloperów i wprowadzić parametry połączenia tylko do odczytu. W ten sposób można określić prosty sposób zapewnić, że każdy Deweloper używa poprawną ścieżkę dostępu do danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
