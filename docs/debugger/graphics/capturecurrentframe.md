---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec67013b41a5ec8876866044355534c42bfe2ee0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720734"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Uwagi
 Jeśli inny przechwytywania jest obecnie w toku — takich jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcji — tego przechwytywania jest zakończone i rejestrowane w dzienniku grafiki jako odrębne ramki. Natychmiast po tym dniu diagnostyki grafiki rozpoczyna się, przechwytywania w pozostałej części bieżącej ramki, który jest zarejestrowany jako odrębne ramki. Koniec bieżącej ramki jest oznaczona przez wywołanie do przedstawienia.

 Aby przechwycić ramki, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `CaptureCurrentFrame`.

## <a name="see-also"></a>Zobacz też
- [Init](init.md)
- [BeginCapture](begincapture.md)