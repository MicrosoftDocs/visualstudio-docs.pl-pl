---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bc86574b380e0a29042dcc1dc20851258c9f1bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033573"
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