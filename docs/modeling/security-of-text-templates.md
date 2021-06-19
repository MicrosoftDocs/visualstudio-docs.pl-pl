---
title: Zabezpieczenia szablonów tekstowych
description: Dowiedz się więcej o szablonach zabezpieczeń i tekstowych, w tym tematach, takich jak dowolny kod i złośliwe procesory dyrektyw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385763"
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
Szablony tekstowe mają następujące kwestie związane z zabezpieczeniami:

- Szablony tekstowe są podatne na dowolne wstawienia kodu.

- Jeśli mechanizm używany przez hosta do znalezienia procesora dyrektywy nie jest bezpieczny, można uruchomić złośliwy procesor dyrektywy.

## <a name="arbitrary-code"></a>Dowolny kod
 Podczas pisania szablonu możesz umieścić dowolny kod w \<# #> tagach. Dzięki temu dowolny kod może być wykonywany z poziomu szablonu tekstowego.

 Upewnij się, że uzyskujesz szablony z zaufanych źródeł. Pamiętaj, aby ostrzec użytkowników końcowych aplikacji, aby nie wykonywali szablonów, które nie pochodzą z zaufanych źródeł.

## <a name="malicious-directive-processor"></a>Złośliwy procesor dyrektywy
 Aparat szablonów tekstowych współdziała z hostem przekształcania i co najmniej jednym procesorem dyrektywy w celu przekształcenia tekstu szablonu w plik wyjściowy. Aby uzyskać więcej informacji, [zobacz The Text Template Transformation Process (Proces przekształcania szablonu tekstu).](../modeling/the-text-template-transformation-process.md)

 Jeśli mechanizm używany przez hosta do znalezienia procesora dyrektywy nie jest bezpieczny, istnieje ryzyko uruchomienia złośliwego procesora dyrektywy. Złośliwy procesor dyrektywy może dostarczyć kod, który jest uruchamiany w `FullTrust` trybie podczas uruchamiania szablonu. W przypadku tworzenia niestandardowego hosta przekształceń szablonu tekstu należy użyć bezpiecznego mechanizmu, takiego jak rejestr, aby aparat zlokalizował procesory dyrektyw.
