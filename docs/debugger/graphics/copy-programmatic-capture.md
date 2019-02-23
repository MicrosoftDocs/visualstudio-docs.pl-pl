---
title: Kopiowanie (przechwycenie programowe) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719083"
---
# <a name="copy-programmatic-capture"></a>Kopiowanie (przechwycenie programowe)
Kopiuje zawartość active grafiki (.vsglog) pliku do nowego pliku.

## <a name="syntax"></a>Składnia

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametry
 `szNewVSGLog` Nazwa pliku nowy plik dziennika grafiki.

## <a name="remarks"></a>Uwagi
 Aby skopiować informacje graficzne do nowego pliku, muszą już udało się przechwycić pewne informacje grafiki; w przeciwnym razie nic się nie dzieje.