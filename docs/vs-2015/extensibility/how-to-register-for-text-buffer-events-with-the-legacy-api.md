---
title: 'Instrukcje: rejestrowanie zdarzeń związanych z buforem tekstu przy użyciu starszej wersji interfejsu API | Microsoft Docs'
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
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204095"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Instrukcje: rejestrowanie w zdarzeniach buforu tekstowego przy użyciu starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli uzyskujesz dostęp do bufora tekstowego przy użyciu starszego interfejsu API, należy zarejestrować zdarzenia w buforze tekstu, jak pokazano w poniższej procedurze.  
  
### <a name="to-advise-text-buffer-events"></a>Aby powiadomić o zdarzeniach buforu tekstu  
  
1. Ze wskaźnika do jednego z interfejsów w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , należy wywołać `QueryInterface` wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metodę i przekaż identyfikator interfejsu zdarzeń, dla których chcesz zarejestrować.  
  
     Na przykład jeśli chcesz zarejestrować się w usłudze <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , Przekaż identyfikator interfejsu IID_IVsTextLinesEvents.  
  
     Bufor tekstowy zwraca wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu dla odpowiedniego obiektu punktu połączenia.  
  
3. Za pomocą tego wskaźnika Wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metodę, przekazując wskaźnik do implementacji interfejsu zdarzeń, dla którego chcesz się zarejestrować, na przykład w `IVsTextLinesEvents` interfejsie.  
  
     Środowisko zwraca plik cookie, którego można następnie użyć do zatrzymania nasłuchiwania zdarzeń przez wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia buforu tekstowego w starszym interfejsie API](../extensibility/text-buffer-events-in-the-legacy-api.md)
