---
title: Jak ręcznie uruchomić analizę starszego kodu dla kodu zarządzanego
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38c3de83dc0df39314ad236f647c69bbe614b75d
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371823"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Instrukcje: ręczne uruchamianie starszej analizy kodu dla kodu zarządzanego
Narzędzie do analizy kodu zawiera informacje o możliwych defektach w kodzie źródłowym. Można uruchomić analizę kodu automatycznie przy każdej kompilacji projektu kodu, a także przeprowadzić analizę kodu ręcznie. Reguły sprawdzane podczas uruchamiania analizy kodu są określone na stronie Analiza kodu na stronach właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Aby ręcznie uruchomić analizę kodu

1. Jeśli używasz programu Visual Studio 2019 w wersji 16,5 lub nowszej, uruchom następujące polecenie w wierszu polecenia przed uruchomieniem programu Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. W **Eksplorator rozwiązań**kliknij projekt.

3. W menu **Analizuj** kliknij polecenie **Uruchom analizę kodu w** polu *Nazwa projektu*.

