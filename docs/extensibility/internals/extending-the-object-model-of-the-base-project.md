---
title: Rozszerzanie modelu obiektów projektu podstawowego | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708394"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozwiń model obiektów projektu podstawowego

Podtyp projektu może zwiększyć model obiektów automatyzacji projektu podstawowego w następujących miejscach:

- Project. Extender (" \<ProjectSubtypeName> "): umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z <xref:EnvDTE.Project> obiektu. Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić `Project` obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu powinien oferować jego obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadającego `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić ten obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadającego pożądanemu <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ) CATID.

- Project. Properties: w tej kolekcji są ujawniane niezależne od konfiguracji właściwości `Project` obiektu. Aby uzyskać więcej informacji na temat `Project` właściwości, zobacz <xref:EnvDTE.Project.Properties%2A> . Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadającego `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: Ta kolekcja uwidacznia właściwości zależne od konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu oferuje swój obiekt dla CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do rozróżnienia jednego obiektu przeglądania konfiguracji od innego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
