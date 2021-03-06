---
title: Wdrażanie powłoki VS Shell
description: Dowiedz się, jak izolowana powłoka pozwala określić, Visual Studio funkcji języka DSL i jak powinno wyglądać to rozwiązanie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388311"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Izolowana powłoka pozwala określić, Visual Studio, które są potrzebne do interakcji z językiem specyficznym dla domeny i jak powinno wyglądać to rozwiązanie. Aby uzyskać więcej informacji na temat Visual Studio izolowanej powłoki, zobacz [Dostosowywanie izolowanej powłoki](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Aby ustawić Visual Studio Shell jako miejsce docelowe wdrożenia:

1. W **projekcie DslPackage** **otwórz** source.extension.tt .

2. W obszarze `<SupportedProducts>` Wstaw:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Zastąp *myIsolatedShell* nazwą pakietu izolowanej powłoki.