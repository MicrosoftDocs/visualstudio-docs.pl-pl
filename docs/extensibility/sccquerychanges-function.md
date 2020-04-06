---
title: Funkcja SccQueryChanges | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700494"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
Ta funkcja wylicza daną listę plików, dostarczając informacji o zmianach nazw dla każdego pliku za pośrednictwem funkcji wywołania zwrotnego.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 nFiles

[w] Liczba plików `lpFileNames` w tablicy.

 lpFileNames

[w] Tablica nazw plików, aby uzyskać informacje na temat.

 pfnCallback (powrót do)

[w] Wywołanie funkcji wywołania dla każdej nazwy pliku na liście (szczegółowe informacje można znaleźć w [programie QUERYCHANGESFUNC).](../extensibility/querychangesfunc.md)

 pvCallerData

[w] Wartość, która zostanie przekazana bez zmian do funkcji wywołania zwrotnego.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Proces kwerendy został pomyślnie zakończony.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Zmiany, o które należy szukać, to obszar nazw: w szczególności zmiana nazwy, dodanie i usunięcie pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kody błędów](../extensibility/error-codes.md)
