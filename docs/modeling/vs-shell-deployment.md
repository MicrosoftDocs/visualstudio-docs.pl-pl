---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445002"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Izolowana powłoka pozwala określić, które funkcje programu Visual Studio należy współdziałać z językiem specyficznym dla domeny i jak to rozwiązanie powinno się pojawić. Aby uzyskać więcej informacji na temat izolowanej powłoki programu Visual Studio, zobacz [Dostosowywanie izolowanej powłoki](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Aby ustawić powłokę programu Visual Studio jako miejsce docelowe wdrożenia:

1. W projekcie **DslPackage** otwórz **source.extension.tt**.

2. Pod `<SupportedProducts>` wkładką:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *MyIsolatedShell* nazwą pakietu izolowanej powłoki.
