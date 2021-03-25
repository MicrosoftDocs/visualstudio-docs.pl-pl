---
title: Rozszerzanie modelu obiektów projektu podstawowego | Microsoft Docs
description: Dowiedz się, jak zwiększyć model obiektów automatyzacji projektu podstawowego w programie Visual Studio przy użyciu podtypu projektu.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
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
ms.openlocfilehash: 7f220d1e0c97647162c621bc565147bc74f40103
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069624"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozwiń model obiektów projektu podstawowego

Podtyp projektu może zwiększyć model obiektów automatyzacji projektu podstawowego w następujących miejscach:

- Project. Extender (" \<ProjectSubtypeName> "): umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z <xref:EnvDTE.Project> obiektu. Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić `Project` obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu powinien oferować jego obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadającego `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): umożliwia to podtype projektu zaoferowanie obiektu z metodami niestandardowymi z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtyp projektu może użyć rozszerzeń automatyzacji, aby uwidocznić ten obiekt. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadającego pożądanemu <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ) CATID.

- Project. Properties: w tej kolekcji są ujawniane niezależne od konfiguracji właściwości `Project` obiektu. Aby uzyskać więcej informacji na temat `Project` właściwości, zobacz <xref:EnvDTE.Project.Properties%2A> . Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu musi oferować obiekt dla elementu `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadającego `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: Ta kolekcja uwidacznia właściwości zależne od konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu może użyć rozszerzeń automatyzacji, aby dodać jego właściwości do tej kolekcji. <xref:EnvDTE80.IInternalExtenderProvider>Interfejs zaimplementowany w głównym agregatorze podtypu projektu oferuje swój obiekt dla CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartości [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do rozróżnienia jednego obiektu przeglądania konfiguracji od innego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
