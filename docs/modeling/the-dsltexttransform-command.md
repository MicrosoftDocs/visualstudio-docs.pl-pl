---
title: DslTextTransform — Polecenie
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605935"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform. cmd to skrypt, który wywołuje element TextTransform. exe i uruchamia go z typowymi opcjami. Możesz użyć DslTextTransformation. cmd, aby zautomatyzować nocną kompilację projektów [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Aby uzyskać więcej informacji, zobacz [generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd znajduje się w następującym katalogu:

 **Ścieżka instalacji zestawu SDK \<Visual Studio > \VisualStudioIntegration\Tools\Bin**

 Można określić następujące argumenty jako dane wejściowe do DslTextTransform. cmd:

- Katalog wyjściowy projektu modelu domeny.

- Katalog wyjściowy projektu definicji projektanta.

- Lokalizacja pliku szablonu tekstu.

  DslTextTransform. cmd przetwarza określony plik szablonu tekstowego przy użyciu domyślnych procesorów dyrektywy i zestawów. W przypadku tworzenia niestandardowych procesorów dyrektywy można utworzyć własny plik wsadowy, który wywołuje element TextTransform. exe. W tym pliku wsadowym można określić zestawy i skojarzone procesory dyrektywy niestandardowej.