---
title: POPLISTFUNC | Microsoft Docs
description: Dowiedz się więcej na temat funkcji wywołania zwrotnego POPLISTFUNC, która jest używana przez wtyczkę kontroli źródła w celu zaktualizowania listy plików lub katalogów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddf641cf309eb5b5352904da2ac07b64b0886f97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967361"
---
# <a name="poplistfunc"></a>POPLISTFUNC
To wywołanie zwrotne jest dostarczane do [SccPopulateList](../extensibility/sccpopulatelist-function.md) przez IDE i używane przez wtyczkę kontroli źródła w celu zaktualizowania listy plików lub katalogów (również dostarczonych do `SccPopulateList` funkcji).

 Gdy użytkownik wybierze polecenie **Get** w IDE, IDE Wyświetla pole listy wszystkich plików, które użytkownik może uzyskać. Niestety, IDE nie zna dokładnej listy wszystkich plików, które użytkownik może uzyskać; tylko wtyczka ma tę listę. Jeśli inni użytkownicy dodali pliki do projektu kontroli kodu źródłowego, te pliki powinny pojawić się na liście, ale środowisko IDE nie wie o nich. Środowisko IDE tworzy listę plików, które mogą zostać pobrane przez użytkownika. Zanim wyświetli tę listę dla użytkownika, wywoła [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` nadający wtyczki kontroli źródła Dodawanie i usuwanie plików z listy.

## <a name="signature"></a>Podpis
 Wtyczka do kontroli źródła modyfikuje listę, wywołując funkcję implementowaną przez środowisko IDE o następującym prototypie:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData parametr, który został `pvCallerData` przesłany przez obiekt wywołujący (IDE) do [SccPopulateList](../extensibility/sccpopulatelist-function.md). Wtyczka do kontroli źródła nie powinna zajmować niczego o zawartości tego parametru.

 fAddRemove if `TRUE` , `lpFileName` jest plikiem, który powinien zostać dodany do listy plików. Jeśli `FALSE` , `lpFileName` jest plikiem, który powinien zostać usunięty z listy plików.

 Stan nStatus `lpFileName` (kombinacja `SCC_STATUS` bitów; zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) , aby uzyskać szczegółowe informacje).

 lpFileName pełną ścieżkę katalogu nazwy pliku, aby dodać lub usunąć z listy.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|`TRUE`|Wtyczka może kontynuować wywoływanie tej funkcji.|
|`FALSE`|Wystąpił problem ze stroną IDE (na przykład z powodu braku pamięci). Wtyczka powinna zatrzymać operację.|

## <a name="remarks"></a>Uwagi
 Dla każdego pliku, który wtyczka do kontroli źródła chce dodać lub usunąć z listy plików, wywołuje tę funkcję, przekazując w `lpFileName` . `fAddRemove`Flaga wskazuje nowy plik do dodania do listy lub starego pliku do usunięcia. `nStatus`Parametr przekazuje stan pliku. Gdy wtyczka SCC zakończyła Dodawanie i usuwanie plików, zwraca z wywołania [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

> [!NOTE]
> `SCC_CAP_POPULATELIST`Bit możliwości jest wymagany dla programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
