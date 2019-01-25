---
title: Zabezpieczenia szablonów tekstowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce0a5b008df683694a20cce360fbd5e779e408d8
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54835034"
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony tekstowe mają następujące problemy dotyczące zabezpieczeń:  
  
-   Szablony tekstowe są narażone na wstawienia dowolnego kodu.  
  
-   Jeśli mechanizm używany przez hosta można znaleźć procesor dyrektywy nie jest bezpieczne, można uruchomić złośliwe procesora dyrektywy.  
  
## <a name="arbitrary-code"></a>Dowolnego kodu  
 Podczas pisania szablonu można umieścić dowolny kod w ramach \<## > tagów. Umożliwia to dowolnego kodu do wykonania z w ramach szablonu tekstu.  
  
 Upewnij się, że można uzyskać szablony z zaufanych źródeł. Upewnij się ostrzec użytkowników końcowych w aplikacji nie można wykonać szablonów, które nie pochodzą z zaufanych źródeł.  
  
## <a name="malicious-directive-processor"></a>Złośliwy procesora dyrektywy  
 Aparat szablonów tekstu współdziała z hosta przekształcania i co najmniej jeden procesor dyrektywy do przekształcania szablonu tekstu do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md).  
  
 Jeśli mechanizm używany przez hosta można znaleźć procesor dyrektywy nie jest bezpieczne, uruchamia ryzyko uruchomienia złośliwych procesora dyrektywy. Złośliwy procesor dyrektywy może dostarczyć kod, który jest uruchamiany w `FullTrust` tryb uruchamiania szablonu. Jeśli utworzono hosta przekształcania szablonu niestandardowego tekstu, należy użyć mechanizm bezpiecznego, takich jak rejestr, aparat do zlokalizowania procesory dyrektyw.
