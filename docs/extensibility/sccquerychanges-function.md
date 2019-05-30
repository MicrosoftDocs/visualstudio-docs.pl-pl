---
title: SccQueryChanges Function | Microsoft Docs
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
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353506"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges, funkcja
Ta funkcja wylicza danej listy plików, przekazywania informacji na temat zmiany nazwy dla każdego pliku za pomocą funkcji wywołania zwrotnego.

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

[in] Wskaźnik kontekście wtyczki kontroli źródła.

 Niepowodzeń

[in] Liczba plików w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica nazw plików, aby uzyskać informacje na.

 pfnCallback

[in] Funkcja wywołania zwrotnego do wywołania dla każdej nazwy pliku na liście (patrz [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Aby uzyskać szczegółowe informacje).

 pvCallerData

[in] Niezmieniona wartość, które zostaną przekazane do funkcji wywołania zwrotnego.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Proces wykonywania zapytania, zostało ukończone pomyślnie.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Odpytywane dla zmiany są do przestrzeni nazw: ściślej mówiąc, zmiana nazwy, dodawania i usuwania pliku.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Kody błędów](../extensibility/error-codes.md)