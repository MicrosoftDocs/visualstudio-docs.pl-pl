---
title: Uzyskiwanie dostępu do warstw tekstowych przy użyciu starszej wersji interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148021"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do warstw tekstu za pomocą starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Warstwa tekstowa zazwyczaj hermetyzuje pewną część układu tekstu. Na przykład warstwa "function-in-Time" ukrywa tekst przed i po funkcji zawierającej karetkę (punkt wstawiania tekstu).  
  
 Warstwa tekstowa znajduje się między buforem a widokiem i modyfikuje sposób, w jaki widok widzi zawartość bufora.  
  
## <a name="text-layer-information"></a>Informacje o warstwie tekstowej  
 Na poniższej liście opisano, jak warstwy tekstu działają w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Tekst w warstwie tekstowej można wykonać przy użyciu kolorowania składni i znaczników.  
  
- Obecnie nie można zaimplementować własnych warstw.  
  
- Warstwa uwidacznia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , która pochodzi od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Sam bufor tekstowy jest również implementowany jako warstwa, co umożliwia niezależny wgląd z warstwami bazowymi.  
  
- Między widokiem a buforem mogą znajdować się dowolna liczba warstw. Każda warstwa zajmuje się tylko warstwą poniżej, a widok zajmuje się dużą górną warstwą. (Widok zawiera pewne informacje o buforze).  
  
- Warstwa może mieć wpływ tylko na warstwy, które znajdują się poniżej. Nie może to wpływać na powyższe warstwy, które wykraczają poza źródłowe zdarzenia standardowe.  
  
- W edytorze, tekst ukryty, tekst syntetyczny i zawijanie wierszy są implementowane jako warstwy. Można zaimplementować ukryty i syntetyczny tekst bez współpracy bezpośrednio z warstwami. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu w starszej wersji usługi językowej](../extensibility/internals/outlining-in-a-legacy-language-service.md) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Każda warstwa tekstowa ma własny lokalny system współrzędnych, który jest udostępniany za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfejsu. Warstwa zawijania wierszy, na przykład, może zawierać dwie linie, podczas gdy bufor tekstu podstawowego może zawierać tylko jeden wiersz.  
  
- Widok komunikuje się z warstwami za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfejsu. Użyj tego interfejsu do uzgadniania współrzędnych widoku ze współrzędnymi buforu.  
  
- Każda warstwa, taka jak warstwa tekstu syntetycznego, która pochodzi z tekstu, musi zapewniać lokalną implementację programu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Oprócz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> tego warstwa tekstowa musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i uruchamiać zdarzenia w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfejsie.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Dostosowywanie kontrolek i menu w edytorze za pomocą starszego interfejsu API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
