---
title: Dodawanie usług sieci Web do systemów projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002663"
---
# <a name="adding-web-services-to-project-systems"></a>Dodawanie usług sieci Web do systemów projektów
Usługi sieci Web XML, ogólnie rzecz biorąc, adresy URL, które zwracają programistyczne informacje do systemu projektu przy użyciu protokołu SOAP (Simple Object Access Protocol). Usługi sieci Web można zintegrować z systemem projektu pakietu VSPackage przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfejsu.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>Aby dodać usługę sieci Web do systemu projektu  
  
1. Wywołanie `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interfejsu przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> usługę.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> metodę. Jeśli parametr zostanie przekazany `pDiscoverySession` jako `NULL` , sesja odnajdowania zostanie utworzona, a sesja jest buforowana, aby była dostępna do późniejszego użycia przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interfejs. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> Metoda zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> metodę. Przekaż obiekt automatyzacji dla folderu odwołania usługi sieci Web jako `pUnkWebReferenceFolder` parametr. Środowisko programu Visual Studio sprawdza, czy usługa sieci Web już istnieje. Jeśli usługa sieci Web nie istnieje, środowisko pobiera i dodaje usługę sieci Web do folderu oraz wszelkich dodatkowych plików (takich jak pliki WSDL) do węzłów podrzędnych folderu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>