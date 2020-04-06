---
title: POPLISTFUNC | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702059"
---
# <a name="poplistfunc"></a>POPLISTFUNC
To wywołanie zwrotne jest dostarczane do [SccPopulateList](../extensibility/sccpopulatelist-function.md) przez IDE i jest używany przez wtyczkę kontroli źródła, `SccPopulateList` aby zaktualizować listę plików lub katalogów (również dostarczone do funkcji).

 Gdy użytkownik wybierze polecenie **Pobierz** w IDE, IDE wyświetla pole listy wszystkich plików, które użytkownik może uzyskać. Niestety IDE nie zna dokładnej listy wszystkich plików, które użytkownik może uzyskać; tylko wtyczka ma tę listę. Jeśli inni użytkownicy dodali pliki do projektu kontroli kodu źródłowego, te pliki powinny pojawić się na liście, ale IDE nie wie o nich. IDE tworzy listę plików, które uważa, że użytkownik może uzyskać. Zanim wyświetli tę listę do użytkownika, wywołuje [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dając wtyczkę kontroli źródła szansę na dodanie i usunięcie plików z listy.

## <a name="signature"></a>Sygnatura
 Wtyczka kontroli źródła modyfikuje listę, wywołując funkcję zaimplementowana ide z następującym prototypem:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData `pvCallerData` Parametr przekazany przez wywołującego (IDE) do [listy SccPopulateList](../extensibility/sccpopulatelist-function.md). Wtyczka kontroli źródła powinna zakładać, że nic o zawartości tego parametru.

 fAddRemove `TRUE`If `lpFileName` jest plikiem, który powinien zostać dodany do listy plików. Jeśli `FALSE` `lpFileName` plik , który powinien zostać usunięty z listy plików.

 nStatus Status `lpFileName` of (kombinacja `SCC_STATUS` bitów; zobacz kod stanu [pliku,](../extensibility/file-status-code-enumerator.md) aby uzyskać szczegółowe informacje).

 lpFileName Pełna ścieżka katalogu nazwy pliku do dodania lub usunięcia z listy.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|`TRUE`|Wtyczka może nadal wywoływać tę funkcję.|
|`FALSE`|Wystąpił problem po stronie IDE (na przykład sytuacja braku pamięci). Wtyczka powinna zatrzymać działanie.|

## <a name="remarks"></a>Uwagi
 Dla każdego pliku, który wtyczka kontroli źródła chce dodać lub usunąć z listy plików, `lpFileName`wywołuje tę funkcję, przechodząc w pliku . Flaga `fAddRemove` wskazuje nowy plik do dodania do listy lub stary plik do usunięcia. Parametr `nStatus` podaje stan pliku. Po zakończeniu dodawania i usuwania plików przez wtyczkę SCC zwraca ją z wywołania [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Bit `SCC_CAP_POPULATELIST` możliwości jest wymagany dla programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
