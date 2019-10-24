---
title: Funkcja SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 617f07a11f92ab65f079c7d1b41773494e3d0c8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720850"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
Ta funkcja wylicza daną listę plików, dostarczając informacje o zmianach nazw poszczególnych plików za pośrednictwem funkcji wywołania zwrotnego.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

podczas Liczba plików w tablicy `lpFileNames`.

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

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kody błędów](../extensibility/error-codes.md)