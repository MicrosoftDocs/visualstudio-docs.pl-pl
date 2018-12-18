---
title: 'Porady: Korzystanie ze znaczników tekstu | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fea8e6d5774e8991cf70cbc84e6b713d59f199f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810208"
---
# <a name="how-to-use-text-markers"></a>Porady: Korzystanie ze znaczników tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znaczniki tekstu można zastosować do edycji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> obiektu.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-apply-text-markers"></a>Aby zastosować znaczniki tekstu  
  
1.  Uzyskaj wystąpienia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> klasy.  
  
    > [!NOTE]
    >  Podstawowy edytor automatycznie stosuje znaczniki standardowy tekst dowolny dokument, który jest jego edycji, a nie może być konieczne jawne stosowanie znaczniki standardowy tekst.  
  
2.  Uzyskać identyfikator typu znacznika znacznika, o których chcesz się dowiedzieć, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody z `GUID` znacznika tekstu chcesz pracować.  
  
    > [!NOTE]
    >  Nie używaj `GUID` pakietu VSPackage lub usługę, która udostępnia znacznik tekstu.  
  
3.  Użyj Identyfikatora typu znaczników można uzyskać przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metoda jako parametr do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metody do stosowania znacznika tekstu dla danego regionu tekstu.  
  
#### <a name="to-add-features-to-text-markers"></a>Aby dodać funkcje do znaczników tekstu  
  
1.  Może być pożądane, aby dodać dodatkowe funkcje do znacznika tekstu, takie jak etykietek narzędzi, menu kontekstowe specjalne lub program obsługi w szczególnych okolicznościach. Aby to zrobić:  
  
2.  Tworzenie, wdrażanie obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
3.  W razie potrzeby dodatkowe funkcje zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> na ten sam obiekt, który implementuje interfejsy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
4.  Przekaż <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs, który tworzysz, do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę używaną do zastosowania znacznika tekstu dla danego regionu tekstu.  
  
5.  Dodanie obsługi menu kontekstowe do regionu znacznika tekstu jest niezbędne do utworzenia w menu.  
  
     Aby uzyskać więcej informacji na temat tworzenia, zobacz menu kontekstowe [menu kontekstowe](../extensibility/context-menus.md).  
  
6.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Środowiska wywołania metod dostarczony interfejsów, takich jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metody, stosownie do potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Dodawanie znaczników standardowy tekst](../extensibility/how-to-add-standard-text-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)

