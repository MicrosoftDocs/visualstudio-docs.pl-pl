---
title: Obsługiwane wersje programu Visual Studio dla wizualizacji i modelowania SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547657"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Obsługiwane wersje programu Visual Studio dla zestawu Visualization &amp; Modeling SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniżej przedstawiono listę wersji programu Visual Studio, które są obsługiwane przez program [!INCLUDE[dsl](../includes/dsl-md.md)] w środowiskach tworzenia i wdrażania. Aby uzyskać więcej informacji na temat tych wersji, zobacz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Centrum deweloperów](https://msdn.microsoft.com/vstudio/products/)Microsoft.

## <a name="authoring-edition"></a>Wersja autorstwa
 Aby zdefiniować DSL, należy zainstalować następujące składniki:

|Produkt|Link pobierania|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Wizualizacja i Modeling SDK|[Pobieranie zestawu SDK modelowania](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Wersje wdrożenia
 [!INCLUDE[dsl](../includes/dsl-md.md)]Program obsługuje następujące konfiguracje wdrażania utworzonych języków specyficznych dla domeny:

- Visual Studio Enterprise

- Visual Studio Professional

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (tryb zintegrowany)

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (Tryb izolowany)

> [!NOTE]
> Aby można było uruchomić interfejs DSL w produkcie powłoki, należy ustawić pole **obsługiwanego programu vs Edition** w manifeście rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
