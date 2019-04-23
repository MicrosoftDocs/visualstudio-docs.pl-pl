---
title: Uzyskiwanie dostępu do warstwy tekstu za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082779"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do warstwy tekstu za pomocą starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Warstwa tekstu hermetyzuje zazwyczaj niektóre aspekty układu tekstu. Na przykład warstwa "Funkcja u pojedynczych" powoduje ukrycie opcji tekstu przed i po nim funkcja zawierająca karetki (punktu wstawiania).  
  
 Warstwy tekst, który znajduje się między buforu i widokiem i modyfikuje sposób, w widoku zobaczy zawartość buforu.  
  
## <a name="text-layer-information"></a>Tekst informacji  
 Na poniższej liście opisano, jak działa warstwy tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
- Tekst w warstwie tekstu można powiązany z kolorowanie składni i znacznikami.  
  
- Obecnie nie może implementować własne warstwy.  
  
- Udostępnia warstwę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, który pochodzi od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Bufor tekstowy, sama również jest implementowany jako warstwy, która umożliwia wyświetlanie radzenia sobie polymorphically z warstwy źródłowej.  
  
- Dowolną liczbę warstw może znajdować się między widokiem a buforu. Każda warstwa dotyczy tylko warstwy poniżej, a widok dotyczy głównie warstwy najważniejsze. (W widoku ma pewne informacje o buforze).  
  
- Warstwa może mieć wpływ na tylko warstwy, znajdujących się poniżej. Nie może to wpłynąć na warstwy nad nim poza pochodzące standardowych zdarzeń.  
  
- W edytorze tekstu ukrytego, tekst syntetyczne i zawijania wierszy są implementowane jako warstwy. Możesz zaimplementować tekst ukryty i syntetyczne bez poprzez bezpośrednią interakcję z warstwy. Aby uzyskać więcej informacji, zobacz [zwijania w starszej wersji usługi językowej](../extensibility/internals/outlining-in-a-legacy-language-service.md) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
- Każda warstwa tekst ma swój własny lokalnym układzie współrzędnych, która jest dostępna za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfejsu. Warstwa zawijanie wierszy, na przykład może zawierać dwa wiersze podczas bazowego bufor tekstowy może zawierać tylko jeden wiersz.  
  
- Widok, który komunikuje się z warstwami za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfejsu. Aby uzgodnić wyświetlanie współrzędnych współrzędnych buforu, należy użyć tego interfejsu.  
  
- Dowolny warstw, np. warstwy syntetycznych tekst pochodzący z tekstu, należy podać lokalnego wdrożenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
- Oprócz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, warstwy tekstu musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i wyzwalać zdarzeń w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowanie składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Dostosowywanie kontrolek i menu w edytorze za pomocą starszego interfejsu API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
