---
title: Funkcja SccDirDiff | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701014"
---
# <a name="sccdirdiff-function"></a>SccDirDiff, funkcja
Ta funkcja wyświetla różnice między bieżącym katalogiem lokalnym na dysku klienckim a odpowiednim projektem pod kontrolą źródła.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpDirName (nazwa lpDirName)

[w] W pełni kwalifikowana ścieżka do katalogu lokalnego, dla którego ma być ekwiwalnia różnicy wizualnej.

 Dwflags

[w] Flagi poleceń (patrz sekcja Uwagi).

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Katalog na dysku jest taki sam jak projekt w kontroli kodu źródłowego.|
|SCC_I_FILESDIFFER|Katalog na dysku różni się od projektu w kontroli kodu źródłowego.|
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|
|SCC_E_FILENOTCONTROLLED|Katalog nie jest pod kontrolą kodu źródłowego.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|
|SCC_E_FILENOTEXIST|Nie można odnaleźć katalogu lokalnego.|

## <a name="remarks"></a>Uwagi
 Ta funkcja służy do poinstruowania wtyczki formantu źródła, aby wyświetlała użytkownikowi listę zmian w określonym katalogu. Wtyczka otwiera własne okno, w wybranym formacie, aby wyświetlić różnice między katalogiem użytkownika na dysku a odpowiednim projektem pod kontrolą wersji.

 Jeśli wtyczka obsługuje porównanie katalogów w ogóle, musi obsługiwać porównanie katalogów na podstawie nazwy pliku, nawet jeśli opcje "quick-diff" nie są obsługiwane.

|`dwFlags`|Interpretacja|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (może być używane do szybkiego różnicy lub wizualnego).|
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (może być używany do szybkiego różnicowania lub wizualnego).|
|SCC_DIFF_QD_CONTENTS|Jeśli jest obsługiwana przez wtyczkę formantu źródła, dyskretnie porównuje katalog, bajt po bajcie.|
|SCC_DIFF_QD_CHECKSUM|Jeśli jest obsługiwany przez wtyczkę, po dyskretnie porównuje katalog za pomocą sumy kontrolnej lub, jeśli nie jest obsługiwany, wraca do SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Jeśli jest obsługiwany przez wtyczkę, po cichu porównuje katalog za pomocą sygnatury czasowej lub, jeśli nie jest obsługiwany, powraca SCC_DIFF_QD_CHECKSUM lub SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../extensibility/sccdiff-function.md). Jednak wtyczka kontroli źródła może zdecydować się nie obsługiwać operacji "quick-diff" dla katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
