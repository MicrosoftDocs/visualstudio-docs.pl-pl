---
title: Ręcznie uruchom starszą wersję analizy kodu (.NET)
description: Dowiedz się, jak wykryć możliwe wady w kodzie źródłowym. Zobacz jak ręcznie uruchomić starszą analizę kodu na zarządzanym kodzie w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f214ac47ad3d831432b91652c5bbe3249ce5f1c5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223488"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Instrukcje: ręczne uruchamianie starszej analizy kodu dla kodu zarządzanego

Narzędzie do analizy kodu zawiera informacje o możliwych defektach w kodzie źródłowym. Można uruchomić analizę kodu automatycznie przy każdej kompilacji projektu kodu, a także przeprowadzić analizę kodu ręcznie. Reguły sprawdzane podczas uruchamiania analizy kodu są określone na stronie Analiza kodu na stronach właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Aby ręcznie uruchomić analizę kodu

1. Jeśli używasz programu Visual Studio 2019 w wersji 16,5 lub nowszej, uruchom następujące polecenie w wierszu polecenia przed uruchomieniem programu Visual Studio:

```
setx EnableLegacyCodeAnalysis true
```

2. W **Eksplorator rozwiązań** kliknij projekt.

3. W menu **Analizuj** kliknij polecenie **Uruchom analizę kodu w** polu *Nazwa projektu*.
