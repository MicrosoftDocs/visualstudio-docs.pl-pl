---
title: Init | Microsoft Docs
description: Użyj metody init () elementu VsgDbg, aby przygotować składnik w aplikacji diagnostyki grafiki do rejestrowania informacji graficznych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17b2490641a85a9a38bdeb2c5cd20038639de6f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891816"
---
# <a name="init"></a>Init
Przygotowuje składnik aplikacji diagnostyki grafiki do aktywnego przechwytywania i rejestrowania informacji graficznych w pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametry
 `vsgLogGetter` Wywoływana jednostka — taka jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcji — który przyjmuje jako parametry długość buforu składającego się z `wchar_t` i wskaźnik do tego buforu i zwraca wartość `void` . Gdy wywoływana jednostka określa nazwę pliku, który będzie używany do rejestrowania informacji graficznych, i zapisuje je do określonego buforu przed zwróceniem.

## <a name="remarks"></a>Uwagi
 `Init`Funkcja jest wywoływana automatycznie, gdy wystąpienie `VsgDbg` klasy jest konstruowane przez określenie `bDefaultInit` parametru jego konstruktora jako `true` ; w przeciwnym razie, `Init` musi zostać wywołane jawnie przed rozpoczęciem aktywnego przechwytywania i rejestrowania informacji graficznych.

 Możesz zakończyć i zamknąć aktywny plik dziennika grafiki `UnInit` , wywołując, a następnie Przechwyć i Zapisz więcej informacji graficznych do nowego pliku dziennika grafiki, wywołując `Init` ponownie. Można powtórzyć tyle razy, ile chcesz utworzyć kilka niezależnych plików dziennika grafiki przy użyciu tego samego `VsgDbg` wystąpienia.

## <a name="see-also"></a>Zobacz też
- [UnInit](init.md)