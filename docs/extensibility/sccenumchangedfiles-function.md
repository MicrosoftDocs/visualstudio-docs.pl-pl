---
title: Funkcja SccEnumChangedFiles | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700902"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles, funkcja
Biorąc pod uwagę listę plików lokalnych, ta funkcja określa, które pliki różnią się od odpowiednich wersji w bazie danych kontroli kodu źródłowego.

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

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 cFiles

[w] Liczba nazw plików określonych `lpFileNames` w tablicy. Określa również rozmiar `plIsFileDifferent` tablicy.

 lpFileNames

[w] Tablica lokalnych nazw plików do sprawdzenia.

 plIsFileRóżny

[w, na zewnątrz] Tablica wartości wskazująca stan różnicy każdego pliku `cFiles` (tablica musi zawierać co najmniej wpisy). Nonzero oznacza, że plik jest inny.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została zakończona pomyślnie.|
|SCC_UNSPECIFIEDERROR|Błąd ogólny.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
