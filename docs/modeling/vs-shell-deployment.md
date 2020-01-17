---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115273"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Izolowana Powłoka pozwala określić, które funkcje programu Visual Studio mają być używane w celu współdziałania z językiem specyficznym dla domeny oraz jak ma wyglądać to rozwiązanie. Aby uzyskać więcej informacji na temat izolowanej powłoki programu Visual Studio, zobacz [Dostosowywanie powłoki izolowanej](https://vspartner.com/pages/vsshells).

Aby ustawić program Visual Studio Shell jako element docelowy wdrożenia:

1. W projekcie **DslPackage** Otwórz **source.Extension.tt**.

2. W obszarze `<SupportedProducts>` Wstaw:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *MyIsolatedShell* nazwą pakietu izolowanej powłoki.
