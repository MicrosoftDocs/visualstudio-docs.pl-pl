---
title: Przegląd właściwości niestandardowego dokumentu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 11c344b683a67f369ef3848a41b7907622945ffa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866860"
---
# <a name="custom-document-properties-overview"></a>Przegląd właściwości niestandardowego dokumentu

Podczas tworzenia projektów dokumentów programu Visual Studio dodaje dwie właściwości niestandardowych do dokumentu w projekcie: \_AssemblyLocation i \_AssemblyName. Po otwarciu dokumentu aplikacji Microsoft Office wyszukuje te niestandardowe właściwości dokumentu. Jeśli istnieją w dokumencie, ładowania aplikacji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], co spowoduje włączenie dostosowania. Aby uzyskać więcej informacji, zobacz [rozwiązania architektury pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Ta właściwość zawiera identyfikator CLSID interfejsu w składniku modułu ładującego rozwiązanie Office z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Wartość identyfikatora CLSID jest 4E3C66D5 58D 4-491E-A7D4-64AF99AF6E8B. Nigdy nie należy zmieniać tej wartości.

## <a name="assemblylocation"></a>\_AssemblyLocation

Ta właściwość zawiera ciąg, który zawiera szczegółowe informacje o pliku manifestu wdrożenia dla dostosowania. Aby uzyskać więcej informacji na temat manifestów, zobacz [stosowania i wdrażania manifestów w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_AssemblyLocation wartość właściwości może mieć różnych formatach, w zależności od tego, w jaki sposób rozwiązanie będzie wdrożone:

- Jeśli rozwiązanie zostanie opublikowana do zainstalowania z witryny sieci Web, ścieżka UNC lub dysk CD lub dysk USB, _AssemblyLocation właściwość ma format *DeploymentManifestPath*|*SolutionID*. Następujący ciąg znajduje się przykład:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Jeśli są uruchomione lub debugowanie rozwiązania w programie Visual Studio, _AssemblyLocation właściwość ma format *DeploymentManifestName*|*SolutionID*| vstolocal. Następujący ciąg znajduje się przykład:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *SolutionID* jest identyfikatorem GUID, który [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa do identyfikowania rozwiązania. *SolutionID* jest generowana automatycznie podczas tworzenia projektu. **Vstolocal** wskazuje termin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , z tym samym folderze co dokument powinien można załadować zestawu.

## <a name="see-also"></a>Zobacz także

- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Instrukcje: Publikowanie rozwiązań pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Instrukcje: Tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)
