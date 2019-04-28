---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934298"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Powłoka w trybie izolowanym pozwala określić, które program Visual Studio funkcji należy korzystać z języka specyficznego dla domeny i wygląd tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio, izolowany zobacz [Dostosowywanie programu Isolated Shell](https://vspartner.com/pages/vsshells).

Aby ustawić Visual Studio Shell jako cel wdrożenia:

1. W **DslPackage** otwarty projekt **source.extension.tt**.

2. W obszarze `<SupportedProducts>` Wstaw:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *MyIsolatedShell* o nazwie pakietu shell w trybie izolowanym.