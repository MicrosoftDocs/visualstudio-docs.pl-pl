---
title: Rozszerzanie modelu obiektu projektu podstawowego | Dokumenty firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708394"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu projektu podstawowego

Podtyp projektu może rozszerzyć model obiektu automatyzacji projektu podstawowego w następujących miejscach:

- Project.Extender("\<ProjectSubtypeName>"): Dzięki temu podtyp projektu może oferować obiekt <xref:EnvDTE.Project> z niestandardowymi metodami z obiektu. Podtyp projektu można użyć funkcji `Project` Rozszerzenia automatyzacji do udostępnienia obiektu. Interfejs <xref:EnvDTE80.IInternalExtenderProvider> zaimplementowany w agregatorze podtypu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> projektu głównego `itemid` powinien oferować swój obiekt dla from (odpowiadający wartości [VSITEMID. Korzeń](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): Dzięki temu podtyp projektu może oferować obiekt <xref:EnvDTE.ProjectItem> z niestandardowymi metodami z określonego obiektu w ramach projektu. Podtyp projektu można użyć rozszerzenia automatyzacji do udostępnienia tego obiektu. Interfejs <xref:EnvDTE80.IInternalExtenderProvider> zaimplementowany w głównym agregatorze podtypu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> projektu musi <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>oferować swój obiekt dla `VSHPROPID_ExtObjectCATID` z (odpowiadającego żądanemu) CATID.

- Project.Properties: Ta kolekcja udostępnia właściwości niezależne od `Project` konfiguracji obiektu. Aby uzyskać `Project` więcej informacji <xref:EnvDTE.Project.Properties%2A>na temat właściwości, zobacz . Podtyp projektu można użyć rozszerzenia automatyzacji, aby dodać jego właściwości do tej kolekcji. Interfejs <xref:EnvDTE80.IInternalExtenderProvider> zaimplementowany w głównym agregatorze podtypu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> projektu musi `itemid` oferować swój obiekt dla `VSHPROPID_BrowseObjectCATID` od (odpowiadający wartości [VSITEMID. Korzeń](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Ta kolekcja udostępnia właściwości zależne od konfiguracji projektu dla określonej konfiguracji (na przykład Debug). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu można użyć rozszerzenia automatyzacji, aby dodać jego właściwości do tej kolekcji. Interfejs <xref:EnvDTE80.IInternalExtenderProvider> zaimplementowany w głównym agregatorze podtypu projektu oferuje swój obiekt dla CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartości [VSITEMID. Korzeń](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> służy do odróżnienia jednego obiektu przeglądania konfiguracji od innego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
