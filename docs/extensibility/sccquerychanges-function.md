---
description: Ta funkcja wylicza daną listę plików, dostarczając informacje o zmianach nazw poszczególnych plików za pośrednictwem funkcji wywołania zwrotnego.
title: Funkcja SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c821453642a3632c98fac153a367e8ba41495adc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073940"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
Ta funkcja wylicza daną listę plików, dostarczając informacje o zmianach nazw poszczególnych plików za pośrednictwem funkcji wywołania zwrotnego.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parametry
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba plików w `lpFileNames` tablicy.

 lpFileNames

podczas Tablica nazw plików, dla których mają zostać wyświetlone informacje.

 pfnCallback

podczas Funkcja wywołania zwrotnego do wywołania dla każdej nazwy pliku na liście (zobacz [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) , aby uzyskać szczegółowe informacje).

 pvCallerData

podczas Wartość, która zostanie przeniesiona bez zmian do funkcji wywołania zwrotnego.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Proces zapytania został ukończony pomyślnie.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_NONSPECIFICERROR|Wystąpił błąd nieokreślony lub ogólny.|

## <a name="remarks"></a>Uwagi
 Zmiany, których dotyczy zapytanie, są w przestrzeni nazw: w przypadku, zmiana nazwy, dodanie i usunięcie pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kody błędów](../extensibility/error-codes.md)
