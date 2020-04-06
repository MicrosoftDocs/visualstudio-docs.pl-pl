---
title: Funkcja SccAddFilesFromSCC | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701288"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC, funkcja
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

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpUżycie

[w, na zewnątrz] Nazwa użytkownika (do SCC_USER_SIZE, w tym null terminator).

 lpAuxProjPath (lpAuxProjPath)

[w, na zewnątrz] Ciąg pomocniczy identyfikujący projekt `SCC_PRJPATH_`(do rozmiaru, w tym zerowy terminator).

 cFiles

[w] Liczba plików podanych przez `lpFilePaths`plik .

 lpFilePaths

[w, na zewnątrz] Tablica nazw plików do dodania do bieżącego projektu.

 lpDestination

[w] Ścieżka docelowa, w której mają być zapisywane pliki.

 lpKomentuj

[w] Komentarz, który ma zostać zastosowany do każdego dodawanych plików.

 wyniki pbResults

[w, na zewnątrz] Tablica flag, które są ustawione w celu wskazania sukcesu (nonzero lub TRUE) lub awarii `cFiles` (zero lub FALSE) dla każdego pliku (rozmiar tablicy musi być co najmniej długi).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty.|
|SCC_E_OPNOTPERFORMED|Połączenie nie jest z tym samym projektem, co określone przez`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Użytkownik nie jest upoważniony do aktualizacji bazy danych.|
|SCC_E_NONSPECIFICERROR|Nieznany błąd.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
