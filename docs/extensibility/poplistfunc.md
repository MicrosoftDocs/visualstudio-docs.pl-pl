---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54b73a7f34c663661ae9cc2e2805e5fb6bd11480
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696444"
---
# <a name="poplistfunc"></a>POPLISTFUNC
To wywołanie zwrotne jest dostarczony do [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE i jest używany przez wtyczka do kontroli źródła do aktualizowania listy plików lub katalogów (również dostarczane do `SccPopulateList` funkcji).

 Kiedy użytkownik wybierze **uzyskać** polecenie w IDE, środowisko IDE wyświetla pola listy wszystkich plików, które użytkownik może otrzymać. Niestety IDE znasz dokładną listę wszystkich plików, które użytkownik może otrzymać; tylko dodatek używa tej listy. Jeśli innym użytkownikom dodane pliki do projektu kontroli kodu źródłowego, pliki te powinna zostać wyświetlona na liście, ale IDE nie wie o nich. IDE kompiluje listę plików, które uważa, że użytkownik może otrzymać. Przed wyświetleniem tej listy do użytkownika wywoływanych przez nią [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` zapewniając wtyczka do kontroli źródła możliwość dodawania i usuwania plików z listy.

## <a name="signature"></a>Podpis
 Wtyczka do kontroli źródła modyfikuje listę przez wywołanie funkcji implementowane przez środowisko IDE z poniższy prototyp:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData `pvCallerData` parametr przekazany przez wywołującego (IDE) do [SccPopulateList](../extensibility/sccpopulatelist-function.md). Wtyczka do kontroli źródła założyć, że nic o zawartość tego parametru.

 fAddRemove Jeśli `TRUE`, `lpFileName` plik, który powinien zostać dodany do listy plików. Jeśli `FALSE`, `lpFileName` jest plikiem, która powinna zostać usunięta z listy.

 nStatus stan z `lpFileName` (kombinację `SCC_STATUS` bitów; zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) Aby uzyskać szczegółowe informacje).

 lpFileName ścieżkę katalogu pełną nazwę pliku, aby dodać lub usunąć z listy.

## <a name="return-value"></a>Wartość zwracana

|Wartość|Opis|
|-----------|-----------------|
|`TRUE`|Wtyczka nadal wywołaniu tej funkcji.|
|`FALSE`|Wystąpił problem po stronie IDE (takich jak poza sytuacji pamięci). Wtyczkę należy zatrzymać operacji.|

## <a name="remarks"></a>Uwagi
 Dla każdego pliku, który chce wtyczka do kontroli źródła, dodawanie do lub usuwanie z listy plików, wywołuje tę funkcję, przekazując `lpFileName`. `fAddRemove` Flaga wskazuje nowy plik, aby dodać do listy lub stary plik do usunięcia. `nStatus` Parametr zapewnia stan pliku. Po zakończeniu SCC wtyczki, dodawanie i usuwanie plików, zwraca od [SccPopulateList](../extensibility/sccpopulatelist-function.md) wywołania.

> [!NOTE]
>  `SCC_CAP_POPULATELIST` Bit możliwości jest wymagany dla programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)