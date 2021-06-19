---
title: DslTextTransform — Polecenie
description: Dowiedz się, że DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia go za pomocą typowych opcji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388649"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia go za pomocą typowych opcji. Aby zautomatyzować nocne kompilacje projektów, można użyć polecenia DslTextTransformation.cmd. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Aby uzyskać więcej informacji, zobacz [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd znajduje się w następującym katalogu:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Możesz określić następujące argumenty jako dane wejściowe dla metody DslTextTransform.cmd:

- Katalog wyjściowy projektu modelu domeny.

- Katalog wyjściowy projektu definicji projektanta.

- Lokalizacja pliku szablonu tekstowego.

  DslTextTransform.cmd przetwarza określony plik szablonu tekstowego przy użyciu domyślnych procesorów dyrektyw i zestawów. Jeśli tworzysz niestandardowe procesory dyrektyw, możesz utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowym można określić zestawy i skojarzone niestandardowe procesory dyrektyw.
