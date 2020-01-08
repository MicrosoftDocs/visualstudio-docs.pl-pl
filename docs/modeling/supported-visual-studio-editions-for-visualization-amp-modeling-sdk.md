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
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591908"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Obsługiwane wersje programu Visual Studio dla zestawu Visualization & Modeling SDK

Poniżej przedstawiono listę wersji programu Visual Studio, które są obsługiwane w przypadku [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] w środowiskach tworzenia i wdrażania. Aby uzyskać więcej informacji o tych wersjach, zobacz programu Microsoft Visual Studio [Centrum deweloperów](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Tworzenie wersji

Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

|||
|-|-|
|{1&gt;Visual Studio&lt;1}|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|{1&gt;{2&gt;Visual Studio Visualisation i Modeling SDK&lt;2}&lt;1}|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Wersje wdrożenia

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Wdrażanie języki specyficzne dla domeny, które tworzysz obsługuje następujące konfiguracje:

- Visual Studio Enterprise

- Visual Studio Professional

- Studio Shell (tryb zintegrowany) pakiet redystrybucyjny pakiet redystrybucyjny programu Visual

- Studio Shell (tryb izolowany) pakiet redystrybucyjny pakiet redystrybucyjny programu Visual

> [!NOTE]
> Aby było uruchomić produkt powłoki języka DSL, należy ustawić **obsługiwanych wersji programu VS** pole manifestu rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Zobacz także

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
