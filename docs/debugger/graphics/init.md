---
title: Init | Microsoft Docs
description: Użyj metody Init() metody VsgDbg, aby przygotować składnik w aplikacji diagnostyki grafiki do rejestrować informacje graficzne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc6732ed506d1aa7e4ac3e47c629aadae796201d
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232378"
---
# <a name="init"></a>Init
Przygotowuje składnik diagnostyki grafiki w aplikacji do aktywnego przechwytywania i nagrywania informacji graficznych w pliku dziennika grafiki.

## <a name="syntax"></a>Składnia

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametry
 `vsgLogGetter` Jednostka wywoływalna — taka jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcji — która przyjmuje jako parametry długość buforu składającego się z elementu i wskaźnik do tego buforu `wchar_t` i zwraca wartość `void` . Po wywołaniu wywoływana jednostka określa nazwę pliku, który będzie używany do nagrywania informacji graficznych, i zapisuje je w określonym buforze przed zwróceniem.

## <a name="remarks"></a>Uwagi
 Funkcja jest wywoływana automatycznie, gdy wystąpienie klasy jest konstruowane przez określenie parametru jego konstruktora jako ; w przeciwnym razie musi być wywoływana jawnie, zanim będzie można aktywnie przechwytywać i rejestrować informacje `Init` `VsgDbg` `bDefaultInit` `true` `Init` graficzne.

 Aktywny plik dziennika grafiki można sfinalizować i zamknąć przez wywołanie funkcji , a następnie przechwycić i zarejestrować więcej informacji graficznych do nowego pliku dziennika grafiki, `UnInit` wywołując `Init` ponownie. Możesz powtórzyć tę czynność tyle razy, ile chcesz utworzyć kilka niezależnych plików dziennika grafiki przy użyciu tego samego `VsgDbg` wystąpienia.

## <a name="see-also"></a>Zobacz też
- [UnInit](init.md)