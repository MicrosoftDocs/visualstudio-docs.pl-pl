---
title: Jak ręcznie uruchomić analizę starszego kodu dla kodu zarządzanego
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8a6b52a09729cbc76f91eee76f23e652f07c934f
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250526"
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
