---
title: DslTextTransform — Polecenie
description: Dowiedz się, że DslTextTransform. cmd jest skryptem, który wywołuje TextTransform.exe i uruchamia go przy użyciu typowych opcji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924508"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform. cmd jest skryptem, który wywołuje TextTransform.exe i uruchamia go ze wspólnymi opcjami. Możesz użyć DslTextTransformation. cmd, aby zautomatyzować nocną kompilację [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd znajduje się w następującym katalogu:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Można określić następujące argumenty jako dane wejściowe do DslTextTransform. cmd:

- Katalog wyjściowy projektu modelu domeny.

- Katalog wyjściowy projektu definicji projektanta.

- Lokalizacja pliku szablonu tekstu.

  DslTextTransform. cmd przetwarza określony plik szablonu tekstowego przy użyciu domyślnych procesorów dyrektywy i zestawów. W przypadku tworzenia niestandardowych procesorów dyrektywy można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowym można określić zestawy i skojarzone procesory dyrektywy niestandardowej.
