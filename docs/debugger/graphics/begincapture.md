---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736140"
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna Interwał przechwytywania, który zakończy się `EndCapture`.

## <a name="syntax"></a>Składnia

```C++
void BeginCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka obejmuje interwał między wywołaniem `BeginCapture` i wywołaniem do prezentacji. Druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody a wywołaniem do `EndCapture`.

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że przed wywołaniem `BeginCapture` lub `EndCapture` należy wywołać metodę [init](init.md) za pomocą wystąpienia klasy `VsgDbg`.

## <a name="see-also"></a>Zobacz także
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)