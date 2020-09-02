---
title: Przegląd właściwości dokumentu niestandardowego
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
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951178"
---
# <a name="custom-document-properties-overview"></a>Przegląd właściwości dokumentu niestandardowego

Podczas kompilowania projektu na poziomie dokumentu program Visual Studio dodaje dwie właściwości niestandardowe do dokumentu w projekcie: \_ AssemblyLocation i \_ AssemblyName. Gdy użytkownik otwiera dokument, aplikacja Microsoft Office sprawdza te właściwości dokumentu niestandardowego. Jeśli istnieją w dokumencie, aplikacja ładuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , która uruchamia dostosowanie. Aby uzyskać więcej informacji, zobacz [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Ta właściwość zawiera identyfikator CLSID interfejsu w składniku modułu ładującego rozwiązania pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Wartość CLSID to 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Nie należy zmieniać tej wartości.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Ta właściwość zawiera ciąg, który zawiera szczegółowe informacje dotyczące manifestu wdrażania dla dostosowywania. Aby uzyskać więcej informacji na temat manifestów, zobacz [manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_Wartość właściwości AssemblyLocation może mieć różne formaty, w zależności od sposobu wdrożenia rozwiązania:

- Jeśli rozwiązanie zostało opublikowane do zainstalowania z witryny sieci Web, ścieżki UNC lub dysku CD lub USB, właściwość _AssemblyLocation ma format *DeploymentManifestPath* | *solutionId*. Następujący ciąg jest przykładem:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- W przypadku uruchamiania lub debugowania rozwiązania z programu Visual Studio Właściwość _AssemblyLocation ma format *DeploymentManifestName* | *solutionId*| vstolocal. Następujący ciąg jest przykładem:

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionId* jest identyfikatorem GUID, który służy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do identyfikowania rozwiązania. *SolutionId* jest generowany automatycznie podczas kompilowania projektu. Termin **vstolocal** wskazuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , że zestaw powinien być załadowany z tego samego folderu co dokument.

## <a name="see-also"></a>Zobacz też

- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Instrukcje: publikowanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego](../vsto/how-to-create-and-modify-custom-document-properties.md)
