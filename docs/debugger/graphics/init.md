---
title: init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
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
 `vsgLogGetter` możliwej do napisania jednostce — takiej jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcji — który przyjmuje jako parametry długość buforu składającego się z `wchar_t` i wskaźnik do tego buforu i zwraca `void`. Gdy wywoływana jednostka określa nazwę pliku, który będzie używany do rejestrowania informacji graficznych, i zapisuje je do określonego buforu przed zwróceniem.

## <a name="remarks"></a>Uwagi
 Funkcja `Init` jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` jest konstruowane przez określenie parametru `bDefaultInit` jego konstruktora jako `true`; w przeciwnym razie `Init` musi zostać wywołana jawnie przed rozpoczęciem aktywnego przechwytywania i rejestrowania informacji graficznych.

 Można sfinalizować i zamknąć plik dziennika grafiki Active, wywołując `UnInit`, a następnie przechwycić i nagrać więcej informacji graficznych do nowego pliku dziennika grafiki, wywołując `Init` ponownie. Możesz powtórzyć tyle razy, ile chcesz utworzyć kilka niezależnych plików dziennika grafiki przy użyciu tego samego wystąpienia `VsgDbg`.

## <a name="see-also"></a>Zobacz także
- [UnInit](init.md)