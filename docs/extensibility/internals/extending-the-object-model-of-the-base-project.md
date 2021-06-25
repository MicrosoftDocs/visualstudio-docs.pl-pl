---
title: Rozszerzanie modelu obiektów projektu podstawowego | Microsoft Docs
description: Dowiedz się, jak rozszerzyć model obiektów automatyzacji projektu podstawowego w programie Visual Studio przy użyciu podtypu projektu.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899345"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektów projektu podstawowego

Podtyp projektu może rozszerzyć model obiektów automatyzacji projektu podstawowego w następujących miejscach:

- Project.Extender(" "): umożliwia podtypowi projektu zaoferowania \<ProjectSubtypeName> obiektu z metodami niestandardowymi z <xref:EnvDTE.Project> obiektu . Podtyp projektu może uwidaczniać obiekt za pomocą rozszerzenia `Project` automatyzacji. Interfejs zaimplementowany w agregatonie podtypu głównego projektu powinien oferować obiekt dla obiektu z (odpowiadającego wartości <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender(" "): umożliwia podtypowi projektu zaoferowania obiektu z metodami niestandardowymi \<ProjectSubtypeName> z określonego obiektu w <xref:EnvDTE.ProjectItem> projekcie. Podtyp projektu może uwidaczniać ten obiekt za pomocą rozszerzenia automatyzacji. Interfejs zaimplementowany w agregatonie głównego podtypu projektu musi oferować obiekt dla obiektu <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadające żądanemu <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> identyfikatorowi CATID).

- Project.Properties: ta kolekcja uwidacznia właściwości obiektu niezależne od `Project` konfiguracji. Aby uzyskać więcej informacji na `Project` temat właściwości, zobacz <xref:EnvDTE.Project.Properties%2A> . Podtyp projektu może używać rozszerzenia automatyzacji, aby dodać jego właściwości do tej kolekcji. Interfejs zaimplementowany w agregatonie głównego podtypu projektu musi oferować swój obiekt dla obiektu z (odpowiadający wartości <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: ta kolekcja uwidacznia zależne od konfiguracji właściwości projektu dla określonej konfiguracji (na przykład Debugowanie). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu może używać rozszerzenia automatyzacji, aby dodać jego właściwości do tej kolekcji. Interfejs zaimplementowany w agregatonie podtypu głównego projektu oferuje swój obiekt dla <xref:EnvDTE80.IInternalExtenderProvider> identyfikatorów CATID (odpowiadających wartości `VSHPROPID_CfgBrowseObjectCATID` `itemid` [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> służy do odróżnienia jednego obiektu przeglądania konfiguracji od innego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
