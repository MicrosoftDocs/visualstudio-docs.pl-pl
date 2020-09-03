---
title: Polecenie DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658462"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd jest skryptem, który wywołuje TextTransform.exe i uruchamia go ze wspólnymi opcjami. Możesz użyć DslTextTransformation. cmd, aby zautomatyzować nocną kompilację [!INCLUDE[dsl](../includes/dsl-md.md)] projektów. Aby uzyskać więcej informacji, zobacz [generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd znajduje się w następującym katalogu:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Można określić następujące argumenty jako dane wejściowe do DslTextTransform. cmd:

- Katalog wyjściowy projektu modelu domeny.

- Katalog wyjściowy projektu definicji projektanta.

- Lokalizacja pliku szablonu tekstu.

  DslTextTransform. cmd przetwarza określony plik szablonu tekstowego przy użyciu domyślnych procesorów dyrektywy i zestawów. W przypadku tworzenia niestandardowych procesorów dyrektywy można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowym można określić zestawy i skojarzone procesory dyrektywy niestandardowej.
