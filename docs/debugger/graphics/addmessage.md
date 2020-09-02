---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62896359"
---
# <a name="addmessage"></a>AddMessage
Dodaje niestandardowy komunikat do *HUD* diagnostyki grafiki (wyświetlacz podręczny).

## <a name="syntax"></a>Składnia

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametry
 `szMessage` Komunikat, który ma zostać dodany do HUD.

## <a name="remarks"></a>Uwagi
 HUD diagnostyki grafiki jest wyświetlana w lewym górnym rogu aplikacji, która jest uruchamiana w obszarze Diagnostyka grafiki. Są w nim wyświetlane informacje o aplikacji i informacje o grafice i komunikaty dodawane przez wywołanie tej funkcji.

 Aby dodać komunikat do HUD, nie musisz aktywnie przechwytywać informacji graficznych — to znaczy, że komunikat można dodać za pomocą wystąpienia `VsgDbg` klasy, ale funkcja [init](init.md) member nie jest wywoływana jako pierwsza. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.