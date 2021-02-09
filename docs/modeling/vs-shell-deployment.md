---
title: Wdrażanie powłoki VS Shell
description: Dowiedz się, w jaki sposób izolowana Powłoka pozwala określić, które funkcje programu Visual Studio muszą być używane w połączeniu z DSL i jak powinno wyglądać rozwiązanie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924219"
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