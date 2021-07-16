---
title: Kopiowanie (przechwytywanie programowe) | Microsoft Docs
description: Użyj metody Copy klasy VsgDbg, aby skopiować zawartość aktywnego pliku dziennika grafiki (vsglog) do nowego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e4006803364407fed4b837ea992a95429c1db39
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232664"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
Kopiuje zawartość aktywnego pliku dziennika grafiki (vsglog) do nowego pliku.

## <a name="syntax"></a>Składnia

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametry
 `szNewVSGLog` Nazwa nowego pliku dziennika grafiki.

## <a name="remarks"></a>Uwagi
 Aby skopiować informacje graficzne do nowego pliku, musisz już przechwycić pewne informacje graficzne; w przeciwnym razie nic się nie dzieje.