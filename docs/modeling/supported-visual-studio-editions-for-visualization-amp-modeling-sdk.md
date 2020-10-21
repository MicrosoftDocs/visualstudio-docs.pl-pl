---
title: Obsługiwane wersje programu Visual Studio dla wizualizacji i modelowania SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 908a224feb9f6ad463ae14812b3a8550bf932e35
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2020
ms.locfileid: "92298557"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Obsługiwane wersje programu Visual Studio dla zestawu Visualization & Modeling SDK

Poniżej przedstawiono listę wersji programu Visual Studio, które są obsługiwane przez program [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] w środowiskach tworzenia i wdrażania. Aby uzyskać więcej informacji na temat tych wersji, zobacz [Centrum deweloperów](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Wersja autorstwa

Aby zdefiniować DSL, należy zainstalować następujące składniki:

|Produkt|Link pobierania|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio Wizualizacja i Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Wersje wdrożenia

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Program obsługuje następujące konfiguracje wdrażania utworzonych języków specyficznych dla domeny:

- Visual Studio Enterprise

- Visual Studio Professional

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (tryb zintegrowany)

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (Tryb izolowany)

> [!NOTE]
> Aby można było uruchomić interfejs DSL w produkcie powłoki, należy ustawić pole **obsługiwanego programu vs Edition** w manifeście rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych Domain-Specific](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))