---
title: 'Jak: Ręczne uruchamianie analizy starszego kodu dla kodu zarządzanego'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432232"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Jak: Ręczne uruchamianie analizy starszego kodu dla kodu zarządzanego
Narzędzie do analizy kodu zawiera informacje o możliwych wadach kodu źródłowego. Analizę kodu można uruchomić automatycznie przy każdej kompilacji projektu kodu, a także można uruchomić analizę kodu ręcznie. Reguły, które są sprawdzane podczas uruchamiania analizy kodu są określone na stronie Analiza kodu na stronach właściwości projektu. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Aby ręcznie uruchomić analizę kodu

1. Jeśli korzystasz z programu Visual Studio 2019 w wersji 16.5 lub nowszej, wykonaj następujące polecenie w wierszu polecenia przed uruchomieniem programu Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. W **Eksploratorze rozwiązań**kliknij projekt.

3. W menu **Analiza** kliknij polecenie **Uruchom analizę kodu w** programie Project *Name*.

