---
description: Ta funkcja dodaje listę plików z kontroli źródła do aktualnie otwartego projektu.
title: SccAddFilesFromSCC, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fa08ec93383fa661d1e2dd055b3139b2ba90f34
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904867"
---
# <a name="sccaddfilesfromscc-function"></a>Funkcja SccAddFilesFromSCC
Ta funkcja dodaje listę plików z kontroli źródła do aktualnie otwartego projektu.

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
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 lpUser

[in, out] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator o wartości null).

 lpAuxProjPath

[in, out] Ciąg pomocniczy identyfikujący projekt (do `SCC_PRJPATH_` SIZE, łącznie z terminatorem o wartości null).

 Pliki cFile

[in] Liczba plików podanych przez `lpFilePaths` .

 lpFilePaths

[in, out] Tablica nazw plików do dodania do bieżącego projektu.

 lpDestination

[in] Ścieżka docelowa, w której mają zostać zapisane pliki.

 lpComment

[in] Komentarz, który ma zostać zastosowany do każdego dodawanego pliku.

 pbResults

[in, out] Tablica flag, które są ustawione w celu wskazania powodzenia (niezerowego lub TRUE) lub błędu (zero lub FALSE) dla każdego pliku (rozmiar tablicy musi być co najmniej `cFiles` długi).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty.|
|SCC_E_OPNOTPERFORMED|Połączenie nie jest tym samym projektem, co określone przez `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do aktualizowania bazy danych.|
|SCC_E_NONSPECIFICERROR|Nieznany błąd.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
