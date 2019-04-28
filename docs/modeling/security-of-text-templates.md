---
title: Zabezpieczenia szablonów tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66159516c6b1360203130dedb56c0e6c192a118a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824023"
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
Szablony tekstowe mają następujące problemy dotyczące zabezpieczeń:

- Szablony tekstowe są narażone na wstawienia dowolnego kodu.

- Jeśli mechanizm używany przez hosta można znaleźć procesor dyrektywy nie jest bezpieczne, można uruchomić złośliwe procesora dyrektywy.

## <a name="arbitrary-code"></a>Dowolnego kodu
 Podczas pisania szablonu można umieścić dowolny kod w ramach \<## > tagów. Umożliwia to dowolnego kodu do wykonania z w ramach szablonu tekstu.

 Upewnij się, że można uzyskać szablony z zaufanych źródeł. Upewnij się ostrzec użytkowników końcowych w aplikacji nie można wykonać szablonów, które nie pochodzą z zaufanych źródeł.

## <a name="malicious-directive-processor"></a>Złośliwy procesora dyrektywy
 Aparat szablonów tekstu współdziała z hosta przekształcania i co najmniej jeden procesor dyrektywy do przekształcania szablonu tekstu do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md).

 Jeśli mechanizm używany przez hosta można znaleźć procesor dyrektywy nie jest bezpieczne, uruchamia ryzyko uruchomienia złośliwych procesora dyrektywy. Złośliwy procesor dyrektywy może dostarczyć kod, który jest uruchamiany w `FullTrust` tryb uruchamiania szablonu. Jeśli utworzono hosta przekształcania szablonu niestandardowego tekstu, należy użyć mechanizm bezpiecznego, takich jak rejestr, aparat do zlokalizowania procesory dyrektyw.