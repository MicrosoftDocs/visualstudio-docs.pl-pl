---
title: 'Instrukcje: korzystanie ze znaczników tekstu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800717"
---
# <a name="how-to-use-text-markers"></a>Instrukcje: korzystanie ze znaczników tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Do edycji obiektu można zastosować znaczniki tekstu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-apply-text-markers"></a>Aby zastosować znaczniki tekstu  
  
1. Uzyskaj wystąpienie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> klasy.  
  
    > [!NOTE]
    > Podstawowy edytor automatycznie stosuje standardowe znaczniki tekstowe do dowolnych dokumentów, które są edytowane, i nie powinno być konieczne jawne stosowanie standardowych znaczników tekstu.  
  
2. Uzyskaj identyfikator typu znacznika, który Cię interesuje, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metodę z `GUID` znacznikiem tekstu, z którym chcesz współpracować.  
  
    > [!NOTE]
    > Nie należy używać `GUID` elementu pakietu VSPackage ani usługi, która zawiera znacznik tekstu.  
  
3. Użyj identyfikatora typu znacznika uzyskanego przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody jako parametru, aby wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodę lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę w celu zastosowania znacznika tekstu do danego regionu tekstu.  
  
#### <a name="to-add-features-to-text-markers"></a>Aby dodać funkcje do znaczników tekstu  
  
1. Może być pożądane dodanie dodatkowych funkcji do znacznika tekstu, takich jak etykietki narzędzi, specjalne menu kontekstowe lub procedura obsługi dla specjalnych okoliczności. W tym celu:  
  
2. Utwórz obiekt implementujący <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs.  
  
3. Jeśli pożądane są dodatkowe funkcje, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> interfejsy na tym samym obiekcie, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs.  
  
4. Przekaż <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs, który tworzysz, do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metody użytej do zastosowania znacznika tekstu do danego regionu tekstu.  
  
5. Podczas dodawania obsługi menu kontekstowego do regionu znacznika tekstu konieczne jest utworzenie menu.  
  
     Aby uzyskać więcej informacji na temat tworzenia menu kontekstowego, zobacz [menu kontekstowe](../extensibility/context-menus.md).  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Środowisko wywołuje metody dostarczonych interfejsów, takich jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> Metoda lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Metoda zgodnie z wymaganiami.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Instrukcje: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)   
 [Instrukcje: Tworzenie niestandardowych znaczników tekstu](../extensibility/how-to-create-custom-text-markers.md)   
 [Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)
