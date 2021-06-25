---
description: Na liście w pełni kwalifikowanych nazw plików ta funkcja sprawdza je na dysku lokalnym.
title: SccCheckout, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d36ccaf5c6dcddb6730f52b0ce1c3074c605a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904724"
---
# <a name="scccheckout-function"></a>Funkcja SccCheckout
Na liście w pełni kwalifikowanych nazw plików ta funkcja sprawdza je na dysku lokalnym. Komentarz dotyczy wszystkich wyewidencjonowanych plików. Argument komentarza może być `null` ciągiem.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które zawiera.

 nFiles

[in] Liczba plików wybranych do wyewidencjonowania.

 lpFileNames

[in] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików do wyewidencjonowania.

 lpComment

[in] Komentarz, który ma zostać zastosowany do każdego z wyewidencjonowanych wybranych plików.

 Foptions

[in] Flagi poleceń (zobacz [Bitflags używane przez określone polecenia).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[in] Opcje specyficzne dla wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sprawdzanie się powiodło.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub z powodu wystąpienia problemów z siecią. Zaleca się ponawianie próby.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został wyewidencjonowany.|
|SCC_E_ALREADYCHECKEDOUT|Użytkownik ma już wyewidencjonowany plik.|
|SCC_E_FILEISLOCKED|Plik jest zablokowany, co zabrania tworzenia nowych wersji.|
|SCC_E_FILEOUTEXCLUSIVE|Inny użytkownik wykonał wyłączne wyewidencjonowanie tego pliku.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
