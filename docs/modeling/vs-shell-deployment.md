---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535853"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Izolowana Powłoka pozwala określić, które funkcje programu Visual Studio mają być używane w celu współdziałania z językiem specyficznym dla domeny oraz jak ma wyglądać to rozwiązanie. Aby uzyskać więcej informacji na temat izolowanej powłoki programu Visual Studio, zobacz [Dostosowywanie powłoki izolowanej](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Aby ustawić program Visual Studio Shell jako element docelowy wdrożenia:

1. W projekcie **DslPackage** Otwórz **source.Extension.tt**.

2. W obszarze `<SupportedProducts>` Wstaw:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *MyIsolatedShell* nazwą pakietu izolowanej powłoki.
