---
title: POPLISTFUNC | Microsoft Docs
description: Dowiedz się więcej o funkcji wywołania zwrotnego POPLISTFUNC, która jest używana przez wtyczkę kontroli źródła do aktualizowania listy plików lub katalogów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52ed40397793b44f8a9c7ed9c36aa5996ae0176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900385"
---
# <a name="poplistfunc"></a>POPLISTFUNC
To wywołanie zwrotne jest dostarczane do [listy SccPopulateList](../extensibility/sccpopulatelist-function.md) przez ideę i jest używane przez wtyczkę kontroli źródła do aktualizowania listy plików lub katalogów (dostarczanych również do `SccPopulateList` funkcji).

 Gdy użytkownik wybierze polecenie **Get** w idee IDE, zostanie wyświetlone pole listy wszystkich plików, które użytkownik może pobrać. Niestety, idee nie znają dokładnej listy wszystkich plików, które użytkownik może pobrać; Tylko wtyczka ma tę listę. Jeśli inni użytkownicy dodali pliki do projektu kontroli kodu źródłowego, te pliki powinny pojawić się na liście, ale środowiska IDE o nich nie wiedzą. Ide tworzy listę plików, które użytkownik może uzyskać. Przed wyświetleniem tej listy użytkownikowi wywołuje ona kontrolkę [SccPopulateList,](../extensibility/sccpopulatelist-function.md) co daje wtyczce kontroli źródła możliwość dodawania i usuwania plików `,` z listy.

## <a name="signature"></a>Podpis
 Wtyczka kontroli źródła modyfikuje listę, wywołując funkcję zaimplementowaną w ideach przy użyciu następującego prototypu:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData `pvCallerData` Parametr przekazany przez wywołujący (IDE) do [listy SccPopulateList](../extensibility/sccpopulatelist-function.md). Wtyczka kontroli źródła nie powinna zakładać niczego na temat zawartości tego parametru.

 fAddUsove Jeśli `TRUE` , `lpFileName` to plik, który należy dodać do listy plików. Jeśli `FALSE` , `lpFileName` to plik, który powinien zostać usunięty z listy plików.

 nStatus Status of `lpFileName` (kombinacja `SCC_STATUS` bitów; zobacz [Kod stanu pliku,](../extensibility/file-status-code-enumerator.md) aby uzyskać szczegółowe informacje).

 lpFileName Pełna ścieżka katalogu nazwy pliku do dodania lub usunięcia z listy.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|`TRUE`|Wtyczka może kontynuować wywoływanie tej funkcji.|
|`FALSE`|Po stronie środowiska IDE występuje problem (na przykład brak pamięci). Wtyczka powinna zatrzymać działanie.|

## <a name="remarks"></a>Uwagi
 Dla każdego pliku, który wtyczka kontroli kodu źródłowego chce dodać do listy plików lub usunąć z listy plików, wywołuje ona tę funkcję, przekazując w pliku `lpFileName` . Flaga `fAddRemove` wskazuje nowy plik do dodania do listy lub stary plik do usunięcia. Parametr `nStatus` podaje stan pliku. Po zakończeniu dodawania i usuwania plików przez wtyczkę SCC jest ona zwracana z wywołania [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Bit `SCC_CAP_POPULATELIST` możliwości jest wymagany dla Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego implementowane przez ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
