---
title: BeginCapture | Microsoft Docs
description: Użyj metody BeginCapture klasy VsgDbg, aby rozpocząć interwał przechwytywania, który zakończy się na EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9fc81bdd058d3a8c1dbe26bbe944bcb0e354ac7
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232741"
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna interwał przechwytywania, który kończy się na `EndCapture` .

## <a name="syntax"></a>Składnia

```C++
void BeginCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zwykle obejmuje podzbiór jednej ramki, na przykład gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołaniu rysowania. Jeśli interwał przechwytywania obejmuje wywołanie do przedstawienia, przechwytywane są dwie ramki informacji graficznych. Pierwsza ramka obejmuje interwał między wywołaniem i wywołaniem do prezentowania; druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu do przedstawienia i wywołaniem `BeginCapture` `EndCapture` .

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i nagrywania informacji graficznych— oznacza to, że przed wywołaniem lub należy wywołać element [Init](init.md) za pośrednictwem `VsgDbg` wystąpienia klasy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Zobacz też
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)