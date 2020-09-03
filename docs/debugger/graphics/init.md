---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735002"
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