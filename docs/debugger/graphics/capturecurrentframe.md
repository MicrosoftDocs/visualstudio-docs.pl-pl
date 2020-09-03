---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736134"
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