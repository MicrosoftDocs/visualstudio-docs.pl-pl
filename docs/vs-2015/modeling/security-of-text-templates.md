---
title: Bezpieczeństwo szablonów tekstowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671212"
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony tekstowe mają następujące kwestie dotyczące zabezpieczeń:

- Szablony tekstowe są podatne na dowolne wstawienia kodu.

- Jeśli mechanizm wykorzystywany przez hosta do znajdowania procesora dyrektywy nie jest zabezpieczony, może zostać uruchomiony złośliwy procesor dyrektywy.

## <a name="arbitrary-code"></a>Dowolny kod
 Podczas pisania szablonu można umieścić dowolny kod w tagach > \< # #. Umożliwia to wykonywanie dowolnego kodu z poziomu szablonu tekstu.

 Upewnij się, że uzyskujesz szablony z zaufanych źródeł. Pamiętaj, aby ostrzec użytkowników końcowych aplikacji, aby nie wykonywały szablonów, które nie pochodzą z zaufanych źródeł.

## <a name="malicious-directive-processor"></a>Procesor złośliwej dyrektywy
 Aparat szablonu tekstu współdziała z hostem transformacji oraz co najmniej jednym procesorem dyrektywy w celu przekształcenia tekstu szablonu w plik wyjściowy. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md).

 Jeśli mechanizm używany przez hosta do znajdowania procesora dyrektywy nie jest zabezpieczony, jest w nim wykonywane ryzyko uruchomienia procesora złośliwej dyrektywy. Procesor złośliwej dyrektywy może dostarczyć kod, który jest uruchamiany w trybie `FullTrust`, gdy szablon zostanie uruchomiony. W przypadku tworzenia niestandardowego hosta transformacji szablonu tekstu należy użyć mechanizmu bezpiecznego, takiego jak rejestr, aby aparat znalazł procesory dyrektywy.
