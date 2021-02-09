---
title: AddMessage | Microsoft Docs
description: Użyj metody AddMessage klasy VsgDbg, aby dodać niestandardową wiadomość do ekranu Head-Up diagnostyki grafiki (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874642"
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