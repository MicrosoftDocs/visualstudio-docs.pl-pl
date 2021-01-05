---
title: EndCapture | Microsoft Docs
description: Użyj metody EndCapture klasy VsgDbg, aby zakończyć Interwał przechwytywania, który został uruchomiony z BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727834"
---
# <a name="endcapture"></a>EndCapture
Zakończenie interwału przechwytywania, który został uruchomiony z `BeginCapture` .

## <a name="syntax"></a>Składnia

```C++
void EndCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka rozciąga się między wywołaniem `BeginCapture` i wywołaniem metody. druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody i wywołaniem metody `EndCapture` .

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że [](init.md) `VsgDbg` przed wywołaniem `BeginCapture` lub `EndCapture` .

## <a name="see-also"></a>Zobacz też
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)