---
title: BeginCapture | Microsoft Docs
description: Użyj metody BeginCapture klasy VsgDbg, aby rozpocząć Interwał przechwytywania, który zakończy się nieEndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874577"
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna Interwał przechwytywania, który zakończy się od `EndCapture` .

## <a name="syntax"></a>Składnia

```C++
void BeginCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka rozciąga się między wywołaniem `BeginCapture` i wywołaniem metody. druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody i wywołaniem metody `EndCapture` .

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że [](init.md) `VsgDbg` przed wywołaniem `BeginCapture` lub `EndCapture` .

## <a name="see-also"></a>Zobacz też
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)