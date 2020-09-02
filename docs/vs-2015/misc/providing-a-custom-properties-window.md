---
title: Udostępnianie okna właściwości niestandardowych | Microsoft Docs
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
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810708"
---
# <a name="providing-a-custom-properties-window"></a>Udostępnianie okna właściwości niestandardowych
Istnieje możliwość udostępnienia własnego okna **Właściwości** dla danego systemu projektu, zamiast rozszerzania okna **Właściwości** udostępnianego przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowane środowisko programistyczne (IDE). Najbardziej często spotykanym scenariuszem jest zaimplementowanie obiektu zlokalizowanego w ramce okna.  
  
 W przypadku nieimplementowania obiektu zlokalizowanego w ramce okna, ale nadal masz dostęp do niego w inny sposób, istnieje kilka sposobów uzyskania dostępu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu, jak opisano w ostatniej procedurze na tej stronie.  
  
### <a name="to-provide-your-properties-window"></a>Aby podać okno Właściwości  
  
1. Zdefiniuj identyfikator GUID, który reprezentuje implementację okna **Właściwości** .  
  
2. W Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji Użyj usługi, <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Aby udąło swoje okno **Właściwości** jako usługę do środowiska programu Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Aby wywołać okno właściwości  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> metodę.  
  
2. `QueryService` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> metody zakończono <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
3. Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługi.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> z pierwszym parametrem ustawionym na `SEID_PropertyBrowserSID` (pobrane z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> wyliczenia) i trzeci parametr, `varValue` reprezentujący ciąg w postaci ciągu identyfikatora GUID, który reprezentuje okno **Właściwości** . To wywołanie należy wykonać tylko raz podczas pierwszego tworzenia okna dokumentu okna **Właściwości** . Po wywołaniu tego okna **Właściwości** z ramką okna.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Aby uzyskać obiekt ramki okna, gdy nie jesteś zaimplementowany  
  
- Można `QueryService` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> usługi z <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> z parametrem `propid` ustawionym na <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Możesz uzyskać okno aktywnego dokumentu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> usługę SVsMonitorSelection. Ustaw parametr `elementid` na `SEID_WindowFrame` , pobrany z <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)   
 [Pola i interfejsy okna właściwości](../extensibility/internals/properties-window-fields-and-interfaces.md)