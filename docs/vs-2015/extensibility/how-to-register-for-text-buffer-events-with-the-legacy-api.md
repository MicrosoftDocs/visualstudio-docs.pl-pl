---
title: 'Instrukcje: Rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab47574be372b565a180082da0930efe61b8360c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759618"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Instrukcje: Rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli uzyskujesz dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API, należy zarejestrować dla zdarzenia buforu tekstu, jak pokazano w poniższej procedurze.  
  
### <a name="to-advise-text-buffer-events"></a>Aby importowali zdarzenia buforu tekstu  
  
1.  Ze wskaźnika do jednego z interfejsów na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, wywołaj `QueryInterface` dla wskaźnika do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metody i przekaż identyfikator interfejsu zdarzenia, dla których chcesz zarejestrować.  
  
     Na przykład, jeśli chcesz zarejestrować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, należy przekazać w interfejsie identyfikator IID_IVsTextLinesEvents.  
  
     Bufor tekstowy zwraca wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs dla obiektu punktu połączenia.  
  
3.  Za pomocą tego wskaźnika, wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metody, przekazując wskaźnik do implementacji interfejsu zdarzenia, dla którego chcesz zarejestrować, na przykład `IVsTextLinesEvents` interfejsu.  
  
     Środowisko zwraca plik cookie, który można następnie przestawaj słuchać zdarzeń przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia buforu tekstowego w starszym interfejsie API](../extensibility/text-buffer-events-in-the-legacy-api.md)
