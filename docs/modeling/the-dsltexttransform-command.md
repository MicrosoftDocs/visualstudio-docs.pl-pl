---
title: DslTextTransform — Polecenie
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114905"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform. cmd to skrypt, który wywołuje element TextTransform. exe i uruchamia go z typowymi opcjami. Możesz użyć DslTextTransformation. cmd, aby zautomatyzować nocną kompilację projektów [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Aby uzyskać więcej informacji, zobacz [generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd znajduje się w następującym katalogu:

 **\<ścieżka instalacji zestawu SDK programu Visual Studio > \VisualStudioIntegration\Tools\Bin**

 Można określić następujące argumenty jako dane wejściowe do DslTextTransform. cmd:

- Katalog wyjściowy projektu modelu domeny.

- Katalog wyjściowy projektu definicji projektanta.

- Lokalizacja pliku szablonu tekstu.

  DslTextTransform. cmd przetwarza określony plik szablonu tekstowego przy użyciu domyślnych procesorów dyrektywy i zestawów. W przypadku tworzenia niestandardowych procesorów dyrektywy można utworzyć własny plik wsadowy, który wywołuje element TextTransform. exe. W tym pliku wsadowym można określić zestawy i skojarzone procesory dyrektywy niestandardowej.
