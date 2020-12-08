---
title: Przegląd właściwości dokumentu niestandardowego
description: Dowiedz się, że podczas kompilowania projektu na poziomie dokumentu program Visual Studio dodaje dwie właściwości niestandardowe do dokumentu w projekcie.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c30e0b3253e19316eed24fa26500cd55a3dd515
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847796"
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

## <a name="see-also"></a>Zobacz także

- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Instrukcje: publikowanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego](../vsto/how-to-create-and-modify-custom-document-properties.md)