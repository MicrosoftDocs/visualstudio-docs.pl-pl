---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54e8b12f4d3b924b363f42cb098a1d528a8108b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735982"
---
# <a name="endcapture"></a>EndCapture
Zakończenie interwału przechwytywania, który został uruchomiony z `BeginCapture`.

## <a name="syntax"></a>Składnia

```C++
void EndCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka obejmuje interwał między wywołaniem `BeginCapture` i wywołaniem do prezentacji. Druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody a wywołaniem do `EndCapture`.

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że przed wywołaniem `BeginCapture` lub `EndCapture` należy wywołać metodę [init](init.md) za pomocą wystąpienia klasy `VsgDbg`.

## <a name="see-also"></a>Zobacz także
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)