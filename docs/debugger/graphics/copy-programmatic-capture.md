---
title: Kopiowanie (przechwycenie programowe) | Microsoft Docs
description: Użyj metody copy klasy VsgDbg, aby skopiować zawartość aktywnego pliku dziennika grafiki (. vsglog) do nowego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62140f279d805e5162661c22110671871afff1ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879192"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
Kopiuje zawartość aktywnego pliku dziennika grafiki (. vsglog) do nowego pliku.

## <a name="syntax"></a>Składnia

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametry
 `szNewVSGLog` Nazwa pliku nowego pliku dziennika grafiki.

## <a name="remarks"></a>Uwagi
 Aby skopiować informacje graficzne do nowego pliku, należy wcześniej przechwycić niektóre informacje graficzne; w przeciwnym razie nic się nie dzieje.