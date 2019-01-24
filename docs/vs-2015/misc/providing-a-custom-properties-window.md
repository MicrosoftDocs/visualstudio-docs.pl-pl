---
title: Zapewnianie okno właściwości niestandardowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 31c33bfafeba1210e6cd70db48643a6329c21a45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768311"
---
# <a name="providing-a-custom-properties-window"></a>Zapewnianie okno właściwości niestandardowe
Można podać własne **właściwości** okna dla danego projektu systemu, zamiast rozszerzenia **właściwości** okien, dostarczonych przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Większość często spotykanych scenariuszy jest, gdy samodzielnie implementacji obiektu ulokowany w ramki okna.  
  
 W przypadku nie implementuje obiektu ulokowany w ramki okna, ale nadal mieć do niego dostęp za pomocą innych środków, istnieje kilka sposobów uzyskania dostępu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu zgodnie z opisem w poprzedniej procedurze na tej stronie.  
  
### <a name="to-provide-your-properties-window"></a>Aby zapewnić okna właściwości  
  
1.  Zdefiniuj identyfikator GUID, który reprezentuje swoje **właściwości** implementacji okna.  
  
2.  W swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> wdrożenia, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> usługi udąło się Twoje **właściwości** okno jako usługę do środowiska programu Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Aby wywołać okno właściwości  
  
1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metody.  
  
2.  `QueryService` Aby uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> przekazany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metody.  
  
3.  Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługi.  
  
4.  Wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> z pierwszym parametrem ustawionym na `SEID_PropertyBrowserSID` (pobierane z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> wyliczenie), a trzeci parametr `varValue`, reprezentujący formę ciągu identyfikatora GUID, który reprezentuje swoje **właściwości** okno. Wykonać to wywołanie, tylko raz podczas pierwszego tworzenia swojej **właściwości** okna, okno dokumentu. Po wywołaniu to **właściwości** okno jest skojarzony z oknem.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Do uzyskiwania obiektu ramki okna, jeśli nie jesteś implementujący  
  
-   Możesz `QueryService` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługi z <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> z parametrem `propid` równa <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
-   Okna aktywnego dokumentu można uzyskać wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> za pośrednictwem usługi SVsMonitorSelection. Ustaw parametr `elementid` do `SEID_WindowFrame`, pobranego z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)   
 [Pola i interfejsy okna właściwości](../extensibility/internals/properties-window-fields-and-interfaces.md)