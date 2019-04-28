---
title: Polecenie DslTextTransform | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 220ceab29cb2b9bc1b117a98326d22c3c546a162
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548510"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia je przy użyciu typowe opcje. DslTextTransformation.cmd można użyć do zautomatyzowania nocna kompilacja z Twojej [!INCLUDE[dsl](../includes/dsl-md.md)] projektów. Aby uzyskać więcej informacji, zobacz [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd znajduje się w następującym katalogu:  
  
 **\<Ścieżka instalacji zestawu SDK programu Visual Studio > \VisualStudioIntegration\Tools\Bin**  
  
 Jako dane wejściowe DslTextTransform.cmd, należy określić następujące argumenty:  
  
- Katalog wyjściowy projektu modelu domeny.  
  
- Katalog wyjściowy projektu Projektanta definicji.  
  
- Lokalizacja pliku szablonu tekstu.  
  
  DslTextTransform.cmd przetwarza plik szablonu określony tekst przy użyciu domyślnego procesorów dyrektyw i zestawów. Jeśli utworzono niestandardowe procesory dyrektyw, można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowego można określić zestawy i skojarzone niestandardowe procesory dyrektyw.
