---
title: SccAddFilesFromSCC Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfe58c3eef4b09fccb5cd21b714e5987ae1e08aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333965"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC function
Ta funkcja dodaje listę plików z kontroli źródła do aktualnie otwartym projekcie.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parametry
 pContext

[in] Wskaźnik kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 lpUser

[out w] Nazwa użytkownika (maksymalnie SCC_USER_SIZE, łącznie z terminatorem null).

 lpAuxProjPath

[out w] Pomocnicze ciąg identyfikujący projekt (maksymalnie `SCC_PRJPATH_`rozmiar, łącznie z terminatorem null).

 cFiles

[in] Liczba plików określone przez `lpFilePaths`.

 lpFilePaths

[out w] Tablica nazw plików do dodania do bieżącego projektu.

 lpDestination

[in] Ścieżka docelowa, w którym mają być zapisywane pliki.

 lpComment

[in] Komentarz, który ma zostać zastosowany do wszystkich plików dodawanych.

 pbResults

[out w] Tablica flag, które są zestawu, informując o powodzeniu (PRAWDA lub wartość różną od zera) lub błąd (0 lub FALSE) dla każdego pliku (rozmiar tablicy musi wynosić co najmniej `cFiles` długie).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty.|
|SCC_E_OPNOTPERFORMED|Połączenie nie jest w tym samym projekcie, określony przez `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do aktualizacji bazy danych.|
|SCC_E_NONSPECIFICERROR|Nieznany błąd.|
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)