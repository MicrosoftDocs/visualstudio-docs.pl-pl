---
description: Na podstawie listy plików lokalnych ta funkcja określa, które pliki różnią się od odpowiednich wersji w bazie danych kontroli kodu źródłowego.
title: SccEnumChangedFiles, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0707c049013fd3a0272d1f024e4fdbc342bab1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904542"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles, funkcja
Na podstawie listy plików lokalnych ta funkcja określa, które pliki różnią się od odpowiednich wersji w bazie danych kontroli kodu źródłowego.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parametry
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 Pliki cFile

[in] Liczba nazw plików określonych w `lpFileNames` tablicy. Określa również rozmiar `plIsFileDifferent` tablicy.

 lpFileNames

[in] Tablica nazw plików lokalnych do sprawdzenia.

 plIsFileSzybki

[in, out] Tablica wartości wskazująca stan różnicy każdego pliku (tablica musi zawierać co najmniej `cFiles` wpisy). Niezerowe oznacza, że plik jest inny.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została zakończona pomyślnie.|
|SCC_UNSPECIFIEDERROR|Błąd ogólny.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
