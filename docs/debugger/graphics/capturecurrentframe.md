---
title: CaptureCurrentFrame | Microsoft Docs
description: Użyj metody CaptureCurrentFrame klasy VsgDbg, aby przechwycić pozostałą część bieżącej ramki do pliku dziennika grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17c917c6c23dff41a5692e95588ce757a8d08293
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232734"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Przechwytuje pozostałą część bieżącej ramki do pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Uwagi
 Jeśli jest obecnie w toku inne przechwytywanie — takie jak przechwytywanie, które zostało uruchomione przez funkcję — to przechwytywanie jest ukończone i rejestrowane w dzienniku graficznym jako `BeginCapture` odrębna ramka. Natychmiast potem diagnostyka grafiki rozpoczyna przechwytywanie pozostałej części bieżącej ramki, która jest również rejestrowana jako odrębna ramka. Koniec bieżącej ramki jest oznaczony wywołaniem do przedstawienia.

 Aby przechwycić ramkę, należy przygotować aplikację do przechwytywania i nagrywania informacji graficznych— oznacza to, że przed wywołaniem klasy należy wywołać element [Init](init.md) za pośrednictwem `VsgDbg` wystąpienia klasy `CaptureCurrentFrame` .

## <a name="see-also"></a>Zobacz też
- [Init](init.md)
- [BeginCapture](begincapture.md)