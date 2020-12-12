---
title: Zabezpieczenia szablonów tekstowych
description: Dowiedz się więcej na temat szablonów zabezpieczeń i tekstu, w tym tematów, takich jak dowolny kod i złośliwe procesory dyrektyw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d54421ea4df9c54fd4ec8c1804a1a292061996ab
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363799"
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
Szablony tekstowe mają następujące kwestie dotyczące zabezpieczeń:

- Szablony tekstowe są podatne na dowolne wstawienia kodu.

- Jeśli mechanizm wykorzystywany przez hosta do znajdowania procesora dyrektywy nie jest zabezpieczony, może zostać uruchomiony złośliwy procesor dyrektywy.

## <a name="arbitrary-code"></a>Dowolny kod
 Podczas pisania szablonu można umieścić dowolny kod w \<# #> tagach. Umożliwia to wykonywanie dowolnego kodu z poziomu szablonu tekstu.

 Upewnij się, że uzyskujesz szablony z zaufanych źródeł. Pamiętaj, aby ostrzec użytkowników końcowych aplikacji, aby nie wykonywały szablonów, które nie pochodzą z zaufanych źródeł.

## <a name="malicious-directive-processor"></a>Procesor złośliwej dyrektywy
 Aparat szablonu tekstu współdziała z hostem transformacji oraz co najmniej jednym procesorem dyrektywy w celu przekształcenia tekstu szablonu w plik wyjściowy. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md).

 Jeśli mechanizm używany przez hosta do znajdowania procesora dyrektywy nie jest zabezpieczony, jest w nim wykonywane ryzyko uruchomienia procesora złośliwej dyrektywy. Procesor złośliwej dyrektywy może dostarczyć kod, który jest uruchamiany w `FullTrust` trybie, gdy szablon zostanie uruchomiony. W przypadku tworzenia niestandardowego hosta transformacji szablonu tekstu należy użyć mechanizmu bezpiecznego, takiego jak rejestr, aby aparat znalazł procesory dyrektywy.
