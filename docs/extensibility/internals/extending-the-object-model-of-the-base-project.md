---
title: Rozszerzanie modelu obiektu projektu podstawowego | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c148a675dbf4a5602ce620042d488e19127c09ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909971"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu projektu podstawowego

Podtypu projektu może rozszerzyć modelu obiektu automatyzacji projektu podstawowego w następujących miejscach:

- Project.Extender("\<ProjectSubtypeName>"): Dzięki temu podtypem projektu do zaoferowania obiektu przy użyciu niestandardowych metod z <xref:EnvDTE.Project> obiektu. Podtypu projektu można użyć rozszerzeń automatyzacji do udostępnienia `Project` obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego powinno oferować się jego obiekt dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): Dzięki temu podtypem projektu do zaoferowania obiektu przy użyciu niestandardowych metod z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtypu projektu można użyć rozszerzeń automatyzacji do udostępnienia tego obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego musi oferować jego obiekt dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadający żądaną <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

- Project.Properties: Ta kolekcja udostępnia właściwości niezależne od konfiguracji `Project` obiektu. Aby uzyskać więcej informacji na temat `Project` właściwości, zobacz <xref:EnvDTE.Project.Properties%2A>. Podtypu projektu można użyć rozszerzeń automatyzacji można dodać właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego musi oferować jego obiekt dla `VSHPROPID_BrowseObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Ta kolekcja udostępnia właściwości zależne od konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtypu projektu można użyć rozszerzeń automatyzacji można dodać właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejs implementowany w agregatorze podtypu projektu głównego umożliwia jego obiekt CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> Interfejs jest używany do odróżnienia jednego obiektu przeglądania konfiguracji od siebie.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>