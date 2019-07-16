---
title: 'Instrukcje: Wyzwolenie zdarzenia po utracie fokusu przez Edytor | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204191"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Instrukcje: Wyzwalanie zdarzeń po utracie fokusu przez edytor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami zachodzi konieczność wiadomo, kiedy redaktorem traci fokus ramki okna. Na przykład może być konieczne pobierania kodu z okna kodu, po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które trzeba wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby wyzwolić zdarzenie w odpowiedzi na Edytor tracąc koncentracji  
  
1. Monitorowanie zdarzeń dotyczących wyboru dzięki uzyskaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.  
  
3. W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, poszukaj `elementid==SEID_WindowFrame`.  
  
4. Test `varValueNew` parametr dwie rzeczy:  
  
    1. Ramka okna, którego szukasz.  
  
    2. Punkt, w którym program traci zaznaczenia do tej ramki okna.
