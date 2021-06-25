---
description: Ta funkcja wyświetla różnice między bieżącym katalogiem lokalnym na dysku klienta i odpowiadającym mu projektem w ramach kontroli źródła.
title: SccDirDiff, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e938cdaedf8541d787673371cfce3d07e005711f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904646"
---
# <a name="sccdirdiff-function"></a>SccDirDiff, funkcja
Ta funkcja wyświetla różnice między bieżącym katalogiem lokalnym na dysku klienta i odpowiadającym mu projektem w ramach kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 Pcontext

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 lpDirName

[in] W pełni kwalifikowana ścieżka do katalogu lokalnego, dla którego ma być pokazywana różnica wizualna.

 Dwflags

[in] Flagi poleceń (zobacz sekcję Uwagi).

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Katalog na dysku jest taki sam jak projekt w kontroli kodu źródłowego.|
|SCC_I_FILESDIFFER|Katalog na dysku różni się od projektu w kontroli kodu źródłowego.|
|SCC_I_RELOADFILE|Należy ponownie załadować plik lub projekt.|
|SCC_E_FILENOTCONTROLLED|Katalog nie jest pod kontrolą kodu źródłowego.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|
|SCC_E_FILENOTEXIST|Nie można odnaleźć katalogu lokalnego.|

## <a name="remarks"></a>Uwagi
 Ta funkcja służy do instruowanie wtyczki kontroli źródła, aby wyświetlała użytkownikowi listę zmian w określonym katalogu. Wtyczka otwiera własne okno w odpowiednim formacie, aby wyświetlić różnice między katalogiem użytkownika na dysku i odpowiadającym mu projektem w ramach kontroli wersji.

 Jeśli wtyczka obsługuje porównanie katalogów, musi obsługiwać porównywanie katalogów na podstawie nazw plików, nawet jeśli opcje "quick-diff" nie są obsługiwane.

|`dwFlags`|Interpretacja|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania liter (może być używane do szybkiej różnicy lub wizualizacji).|
|SCC_DIFF_IGNORESPACE|Ignoruje białe miejsca (może służyć do szybkiego porównywania lub wizualizacji).|
|SCC_DIFF_QD_CONTENTS|Jeśli jest obsługiwana przez wtyczkę kontroli źródła, w trybie dyskretnym porównuje katalog z bajtami.|
|SCC_DIFF_QD_CHECKSUM|Jeśli ta wtyczka jest obsługiwana, dyskretnie porównuje katalog za pośrednictwem sumy kontrolnej lub, jeśli nie jest obsługiwana, powraca do SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Jeśli jest obsługiwana przez wtyczkę, program dyskretnie porównuje katalog za pośrednictwem sygnatury czasowej lub, jeśli nie jest obsługiwany, powraca do katalogu SCC_DIFF_QD_CHECKSUM lub SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../extensibility/sccdiff-function.md). Jednak wtyczka kontroli źródła może nie obsługiwać operacji "quick-diff" dla katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
