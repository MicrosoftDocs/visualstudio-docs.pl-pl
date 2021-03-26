---
description: Po otrzymaniu listy plików lokalnych ta funkcja określa, które pliki różnią się od odpowiednich wersji w bazie danych kontroli kodu źródłowego.
title: Funkcja SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 10f14fb915d461255eddbd4a00747dfbdf59cde4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085562"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles, funkcja
Po otrzymaniu listy plików lokalnych ta funkcja określa, które pliki różnią się od odpowiednich wersji w bazie danych kontroli kodu źródłowego.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 cFiles

podczas Liczba nazw plików określona w `lpFileNames` tablicy. Określa również rozmiar `plIsFileDifferent` tablicy.

 lpFileNames

podczas Tablica lokalnych nazw plików do sprawdzenia.

 plIsFileDifferent

[in. out] Tablica wartości wskazująca stan różnicy każdego pliku (Tablica musi zawierać co najmniej następującą liczbę `cFiles` wpisów). Różna od zera oznacza, że plik jest inny.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została ukończona pomyślnie.|
|SCC_UNSPECIFIEDERROR|Błąd rodzajowy.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
