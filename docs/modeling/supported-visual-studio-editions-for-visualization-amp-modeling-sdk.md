---
title: Obsługiwane wersje programu Visual Studio dla wizualizacji i modelowania SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efe452f059d7184e1f7c87fddd6bdc6c213ece8a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983727"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Obsługiwane wersje programu Visual Studio dla zestawu Visualization & Modeling SDK

Poniżej przedstawiono listę wersji programu Visual Studio, które są obsługiwane przez program [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] w środowiskach tworzenia i wdrażania. Aby uzyskać więcej informacji na temat tych wersji, zobacz [Centrum deweloperów](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Wersja autorstwa

Aby zdefiniować DSL, należy zainstalować następujące składniki:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Wizualizacja i Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Wersje wdrożenia

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] obsługuje następujące konfiguracje wdrażania utworzonych języków specyficznych dla domeny:

- Visual Studio Enterprise

- Visual Studio Professional

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (tryb zintegrowany)

- Pakiet redystrybucyjny pakietu redystrybucyjnego programu Visual Studio Shell (Tryb izolowany)

> [!NOTE]
> Aby można było uruchomić interfejs DSL w produkcie powłoki, należy ustawić pole **obsługiwanego programu vs Edition** w manifeście rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Zobacz także

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)