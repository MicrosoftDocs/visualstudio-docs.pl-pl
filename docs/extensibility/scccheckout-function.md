---
title: Funkcja SccCheckout | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701108"
---
# <a name="scccheckout-function"></a>SccCheckout, funkcja
Biorąc pod uwagę listę w pełni kwalifikowanych nazw plików, ta funkcja sprawdza je na dysku lokalnym. Komentarz dotyczy wszystkich plików wyewidencjonowanych. Argument komentarza może `null` być ciągiem.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[w] Liczba plików wybranych do wyewidencjonowania.

 lpFileNames

[w] Tablica w pełni kwalifikowanych nazw ścieżek lokalnych plików do wyewidencjonowania.

 lpKomentuj

[w] Komentarz ma zostać zastosowany do każdego z wyewidencjonowanych plików.

 Foptions

[w] Flagi poleceń (patrz [Bitflags używane przez określone polecenia).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOpcje

[w] Opcje specyficzne dla wtyczki sterowania źródłem.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Wymeldowanie zakończyło się sukcesem.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria. Plik nie został wyewidencjonowany.|
|SCC_E_ALREADYCHECKEDOUT|Użytkownik ma już wyewidencjonowany plik.|
|SCC_E_FILEISLOCKED|Plik jest zablokowany, zabraniając tworzenia nowych wersji.|
|SCC_E_FILEOUTEXCLUSIVE|Inny użytkownik dokonał wyłącznej realizacji transakcji w tym pliku.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
