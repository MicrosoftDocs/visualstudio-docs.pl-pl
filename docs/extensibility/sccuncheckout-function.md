---
description: Ta funkcja cofa poprzednią operację wyewidencjonowania, przywracając zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowania.
title: SccUncheckout, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a382a112b5a11acc36c52735c949ebef71052ec
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904090"
---
# <a name="sccuncheckout-function"></a>SccUncheckout, funkcja
Ta funkcja cofa poprzednią operację wyewidencjonowania, przywracając zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowania. Wszystkie zmiany wprowadzone w pliku od momentu wyewidencjonowania zostaną utracone.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[in] Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików, dla których można cofnąć wyewidencjonowanie.

 Foptions

[in] Flagi poleceń (nie są używane).

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Cofnięcie wyewidencjonowania powiodło się.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Cofanie wyewidencjonowania nie powiodło się.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma wyewidencjonowania pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|

## <a name="remarks"></a>Uwagi
 Po wykonaniu tej operacji flagi i zostaną wyczyszone dla plików, dla `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` których wykonano cofnięcie wyewidencjonowania.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
