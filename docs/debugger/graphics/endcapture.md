---
title: EndCapture | Microsoft Docs
description: Użyj metody EndCapture klasy VsgDbg, aby zakończyć interwał przechwytywania, który został uruchomiony przy użyciu funkcji BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b0820950980860465e5129211c77e48ff641bdf
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232677"
---
# <a name="endcapture"></a>EndCapture
Kończy interwał przechwytywania, który został uruchomiony przy użyciu . `BeginCapture`

## <a name="syntax"></a>Składnia

```C++
void EndCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zwykle obejmuje podzbiór jednej ramki, na przykład gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołaniu rysowania. Jeśli interwał przechwytywania obejmuje wywołanie do przedstawienia, przechwytywane są dwie ramki informacji graficznych. Pierwsza ramka obejmuje interwał między wywołaniem i wywołaniem do prezentowania; druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu do przedstawienia i wywołaniem `BeginCapture` `EndCapture` .

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i nagrywania informacji graficznych— oznacza to, że przed wywołaniem lub należy wywołać element [Init](init.md) za pośrednictwem `VsgDbg` wystąpienia klasy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Zobacz też
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)