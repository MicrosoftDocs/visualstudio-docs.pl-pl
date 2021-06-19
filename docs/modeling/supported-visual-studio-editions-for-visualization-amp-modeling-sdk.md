---
title: Obsługiwane Visual Studio dla zestawu SDK wizualizacji i modelowania
description: Dowiedz się więcej o Visual Studio obsługiwanych za pomocą narzędzi DSL w środowiskach tworzenia i wdrażania.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8435f37ebe68e954af135be0f513247191ea8a9
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386400"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Obsługiwane wersje programu Visual Studio dla zestawu Visualization & Modeling SDK

Poniżej przedstawiono listę wersji Visual Studio obsługiwanych w programie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] w środowiskach tworzenia i wdrażania. Aby uzyskać więcej informacji na temat tych wersji, zobacz centrum deweloperów Microsoft Visual Studio [Developer Center.](https://visualstudio.microsoft.com/)

## <a name="authoring-edition"></a>Authoring Edition

Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

|Produkt|Link pobierania|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio SDK wizualizacji i modelowania|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Wersje wdrożenia

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Obsługuje następujące konfiguracje wdrażania języków specyficznych dla domeny, które tworzysz:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio redystrybucyjnego pakietu redystrybucyjnego powłoki (tryb zintegrowany)

- Visual Studio redystrybucyjnego pakietu redystrybucyjnego powłoki (w trybie izolowanym)

> [!NOTE]
> Aby można było uruchomić DSL na produkcie Shell, należy ustawić obsługiwane **vs edition** pole w manifeście rozszerzenia. Aby uzyskać więcej informacji, zobacz [Wdrażanie Domain-Specific Language Solutions.](msi-and-vsix-deployment-of-a-dsl.md)

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))