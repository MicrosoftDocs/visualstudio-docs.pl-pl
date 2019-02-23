---
title: AddMessage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705573"
---
# <a name="addmessage"></a>AddMessage
Dodaje niestandardowy komunikat do diagnostyki grafiki *HUD* (wyświetlanie Head-Up).

## <a name="syntax"></a>Składnia

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametry
 `szMessage` Komunikat, który ma zostać dodany do HUD.

## <a name="remarks"></a>Uwagi
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona w ramach diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie tej funkcji.

 Aby dodać komunikat HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — oznacza to, że można dodać komunikat za pośrednictwem wystąpienia `VsgDbg` klasy, ale [Init](init.md) funkcji składowej nie jest wywoływany jako pierwszy. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.