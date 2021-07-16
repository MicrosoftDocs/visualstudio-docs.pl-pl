---
title: AddMessage | Microsoft Docs
description: Użyj metody AddMessage klasy VsgDbg, aby dodać niestandardowy komunikat do diagnostyki grafiki Head-Up Display (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1046b7d8a71efb7d628302041a83fb9d20138a29
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232859"
---
# <a name="addmessage"></a>AddMessage
Dodaje niestandardowy komunikat do graficznego obrazu *HUD* (Head-Up Display).

## <a name="syntax"></a>Składnia

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametry
 `szMessage` Komunikat, który ma zostać dodany do hud.

## <a name="remarks"></a>Uwagi
 Graficzne dane diagnostyczne HUD są wyświetlane w lewym górnym rogu aplikacji uruchomionej w ramach diagnostyki grafiki. Wyświetla informacje o aplikacji w czasie działania oraz informacje o przechwytywaniu informacji graficznych i komunikatach dodawanych przez wywołanie tej funkcji.

 Aby dodać komunikat do interfejsu HUD, nie trzeba aktywnie przechwytywać informacji graficznych — oznacza to, że komunikat może zostać dodany za pośrednictwem wystąpienia klasy, ale funkcja członkowski Init nie musi być wywoływana `VsgDbg` jako pierwsza. [](init.md) Komunikaty są wyświetlane tylko w interfejsie HUD, ale nie są rejestrowane w pliku dziennika grafiki.