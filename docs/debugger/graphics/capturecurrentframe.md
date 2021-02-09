---
title: CaptureCurrentFrame | Microsoft Docs
description: Użyj metody CaptureCurrentFrame klasy VsgDbg, aby przechwycić resztę bieżącej ramki do pliku dziennika grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c55a34ee71f8002d31613d64ff978f0a546b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874551"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Przechwytuje resztę bieżącej ramki do pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Uwagi
 Jeśli trwa wykonywanie innego przechwytywania, takiego jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcję — to przechwycenie zostanie zakończone i zarejestrowane w dzienniku grafiki jako odrębna ramka. Natychmiast po wykonaniu tej czynności Diagnostyka grafiki rozpocznie przechwytywanie reszty bieżącej ramki, która jest również rejestrowana jako odrębna ramka. Zakończenie bieżącej ramki jest oznaczone przez wywołanie do prezentacji.

 Aby przechwycić ramkę, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że przed wywołaniem należy wywołać [init](init.md) za pomocą wystąpienia `VsgDbg` klasy `CaptureCurrentFrame` .

## <a name="see-also"></a>Zobacz też
- [Init](init.md)
- [BeginCapture](begincapture.md)