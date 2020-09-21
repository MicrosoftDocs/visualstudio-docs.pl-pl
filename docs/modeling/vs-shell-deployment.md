---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809651"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Izolowana Powłoka pozwala określić, które funkcje programu Visual Studio mają być używane w celu współdziałania z językiem specyficznym dla domeny oraz jak ma wyglądać to rozwiązanie. Aby uzyskać więcej informacji na temat izolowanej powłoki programu Visual Studio, zobacz [Dostosowywanie powłoki izolowanej](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Aby ustawić program Visual Studio Shell jako element docelowy wdrożenia:

1. W projekcie **DslPackage** Otwórz **source.Extension.tt**.

2. W obszarze `<SupportedProducts>` Wstaw:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *MyIsolatedShell* nazwą pakietu izolowanej powłoki.