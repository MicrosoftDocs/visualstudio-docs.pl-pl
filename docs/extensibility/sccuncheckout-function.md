---
title: Funkcja SccUncheckout | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700244"
---
# <a name="sccuncheckout-function"></a>SccUncheckout, funkcja
Ta funkcja cofa poprzednią operację wyewidencjonowywania, przywracając w ten sposób zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowania. Wszystkie zmiany wprowadzone w pliku od momentu realizacji transakcji zostały utracone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[w] Liczba plików określonych `lpFileNames` w tablicy.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików, dla których można cofnąć wyewidencjonowanie.

 Foptions

[w] Flagi poleceń (nie używane).

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Cofnij wyewidencjonowanie zakończyło się pomyślnie.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria. Cofnij wyewidencjonowanie nie powiodło się.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma wyewidencjonowany plik.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|

## <a name="remarks"></a>Uwagi
 Po tej operacji `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` i flagi zostaną wyczyszczone dla plików, na których wykonano wyewidencjonowanie cofania.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
