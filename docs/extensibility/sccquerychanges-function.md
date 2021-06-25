---
description: Ta funkcja wylicza podaną listę plików, dostarczając informacje o zmianach nazw dla każdego pliku za pośrednictwem funkcji wywołania zwrotnego.
title: SccQueryChanges, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f93ed14671995502356ae4a19664b14bbd32ce7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900476"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
Ta funkcja wylicza podaną listę plików, dostarczając informacje o zmianach nazw dla każdego pliku za pośrednictwem funkcji wywołania zwrotnego.

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
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

[in] Liczba plików w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica nazw plików, o których można uzyskać informacje.

 pfnCallback

[in] Funkcja wywołania zwrotnego do wywołania dla każdej nazwy pliku na liście (zobacz [QUERYCHANGESFUNC,](../extensibility/querychangesfunc.md) aby uzyskać szczegółowe informacje).

 pvCallerData

[in] Wartość, która zostanie przekazana bez zmian do funkcji wywołania zwrotnego.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Proces zapytania został ukończony pomyślnie.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskusją.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Zmiany, których dotyczy zapytanie, dotyczą przestrzeni nazw : w szczególności zmiany nazwy, dodawania i usuwania pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kody błędów](../extensibility/error-codes.md)
