---
title: 'Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2875ff13302b1f54d87f1f69a68757b10fb98dca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749223"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami zachodzi konieczność wiadomo, kiedy redaktorem traci fokus ramki okna. Na przykład może być konieczne pobierania kodu z okna kodu, po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które trzeba wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby wyzwolić zdarzenie w odpowiedzi na Edytor tracąc koncentracji  
  
1.  Monitorowanie zdarzeń dotyczących wyboru dzięki uzyskaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.  
  
3.  W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, poszukaj `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr dwie rzeczy:  
  
    1.  Ramka okna, którego szukasz.  
  
    2.  Punkt, w którym program traci zaznaczenia do tej ramki okna.

