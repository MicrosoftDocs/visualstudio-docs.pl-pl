---
title: 'Instrukcje: Wyzwolenie zdarzenia po utracie fokusu przez Edytor | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec28c704cb8fecb38395c0c7b3f3e3d22ead389b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052899"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Instrukcje: Wyzwolenie zdarzenia po utracie fokusu przez Edytor
Czasami zachodzi konieczność wiadomo, kiedy redaktorem traci fokus ramki okna. Na przykład może być konieczne pobierania kodu z okna kodu, po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które trzeba wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.

## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby wyzwolić zdarzenie w odpowiedzi na Edytor tracąc koncentracji

1. Monitorowanie zdarzeń dotyczących wyboru dzięki uzyskaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.

3. W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, poszukaj `elementid==SEID_WindowFrame`.

4. Test `varValueNew` parametr dwie rzeczy:

    1. Ramka okna, którego szukasz.

    2. Punkt, w którym program traci zaznaczenia do tej ramki okna.