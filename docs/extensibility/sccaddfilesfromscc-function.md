---
title: Funkcja SccAddFilesFromSCC | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpUser

[in. out] Nazwa użytkownika (do SCC_USER_SIZE, w tym terminator o wartości null).

 lpAuxProjPath

[in. out] Ciąg pomocniczy identyfikujący projekt (do `SCC_PRJPATH_` rozmiaru, łącznie z terminatorem wartości null).

 cFiles

podczas Liczba plików podaną przez `lpFilePaths` .

 lpFilePaths

[in. out] Tablica nazw plików do dodania do bieżącego projektu.

 lpDestination

podczas Ścieżka docelowa, w której mają być zapisywane pliki.

 lpComment

podczas Komentarz, który ma zostać zastosowany do każdego dodawanego pliku.

 pbResults

[in. out] Tablica flag, które są ustawione tak, aby wskazywały powodzenie (niezerowe lub prawdziwe) lub niepowodzenie (zero lub FAŁSZ) dla każdego pliku (rozmiar tablicy musi być co najmniej `cFiles` długi).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty.|
|SCC_E_OPNOTPERFORMED|Połączenie nie jest tym samym projektem określonym przez `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do aktualizacji bazy danych.|
|SCC_E_NONSPECIFICERROR|Nieznany błąd.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
