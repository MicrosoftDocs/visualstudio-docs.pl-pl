---
title: Rozszerzanie modelu obiektu projektu podstawowego | Dokumentacja firmy Microsoft
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
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db8ec193b49b7b72e922d2e4f715061d78be37ad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783288"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu projektu podstawowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtypu projektu może rozszerzyć modelu obiektu automatyzacji projektu podstawowego w następujących miejscach:  
  
-   Project.Extender ("\<ProjectSubtypeName >") — dzięki temu podtypem projektu do zaoferowania obiektu przy użyciu niestandardowych metod z <xref:EnvDTE.Project>. Podtypu projektu można użyć rozszerzeń automatyzacji do udostępnienia `Project` obiektu. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs implementowany w agregatorze podtypu projektu głównego powinno oferować się jego obiekt dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadający `itemid` wartość VSITEMID_ROOT, z `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >") — dzięki temu podtypem projektu do zaoferowania obiektu przy użyciu niestandardowych metod z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtypu projektu można użyć rozszerzeń automatyzacji do udostępnienia tego obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego musi oferować jego obiekt dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadający żądaną `VSITEMID`) CATID.  
  
-   Project.Properties — Ta kolekcja udostępnia konfiguracji niezależnie od właściwości `Project` obiektu. Aby uzyskać więcej informacji na temat właściwości projektu, zobacz <xref:EnvDTE.Project.Properties%2A>. Podtypu projektu można użyć rozszerzeń automatyzacji można dodać właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego musi oferować jego obiekt dla `VSHPROPID_BrowseObjectCATID` z VSHPROPID2 (odpowiadający `itemid` wartość VSITEMID_ROOT, z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties — Ta kolekcja przedstawia zależny właściwości konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtypu projektu można użyć rozszerzeń automatyzacji można dodać właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego umożliwia jego obiekt CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartość <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do odróżnienia jednego obiektu przeglądania konfiguracji od siebie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>

