---
title: EndCapture | Microsoft Docs
description: Użyj metody EndCapture klasy VsgDbg, aby zakończyć Interwał przechwytywania, który został uruchomiony z BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f7733eb9bed86bc450e4438ce34054312b13db5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880284"
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