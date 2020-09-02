---
title: Rozszerzanie modelu obiektów projektu podstawowego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187165"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu projektu podstawowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu może zwiększyć model obiektów automatyzacji projektu podstawowego w następujących miejscach:  
  
- Project. Extender (" \<ProjectSubtypeName> ") — umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z <xref:EnvDTE.Project> . Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić `Project` obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu powinien oferować swój obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadającego `itemid` wartości VSITEMID_ROOT, z `VSITEMID` ) CATID.  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") — umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić ten obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadającego pożądanemu `VSITEMID` ) CATID.  
  
- Project. Properties — ta kolekcja uwidacznia niezależne właściwości konfiguracji `Project` obiektu. Aby uzyskać więcej informacji na temat właściwości projektu, zobacz <xref:EnvDTE.Project.Properties%2A> . Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_BrowseObjectCATID` from VSHPROPID2 (odpowiadający `itemid` wartości VSITEMID_ROOT z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties — ta kolekcja uwidacznia zależne od konfiguracji właściwości projektu dla określonej konfiguracji (na przykład debugowanie). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu oferuje swój obiekt dla CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartości <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do rozróżnienia jednego obiektu przeglądania konfiguracji od innego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
