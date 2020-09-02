---
title: 'Instrukcje: Wyzwalanie zdarzeń po utracie fokusu przez Edytor | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204191"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Instrukcje: wyzwalanie zdarzeń po utracie fokusu przez edytor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami trzeba wiedzieć, kiedy Edytor utraci fokus w ramce okna. Na przykład może być konieczne wyodrębnienie kodu z okna kodu, gdy Edytor nie jest już na nim skoncentrowany. Poniższa procedura zawiera kroki, które należy wykonać, aby otrzymywać powiadomienie edytora o utracie fokusu.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby uruchomić zdarzenie w odpowiedzi na Edytor utraci fokus  
  
1. Monitoruj zdarzenia wyboru, uzyskując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiekt z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i podaj swój <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiekt.  
  
3. Wyszukaj w wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> `elementid==SEID_WindowFrame` .  
  
4. Przetestuj `varValueNew` parametr dla dwóch rzeczy:  
  
    1. Ramka okna, którego szukasz.  
  
    2. Punkt, w którym program utraci zaznaczenie do tego ramki okna.
