---
title: Funkcja SccCheckout | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701108"
---
# <a name="scccheckout-function"></a>SccCheckout, funkcja
Mając listę w pełni kwalifikowanych nazw plików, funkcja ta sprawdza je na dysku lokalnym. Komentarz dotyczy wszystkich plików, które są wyewidencjonowane. Argument komentarza może być `null` ciągiem.

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 nFiles

podczas Liczba plików wybranych do wyewidencjonowania.

 lpFileNames

podczas Tablica w pełni kwalifikowanych nazw ścieżek lokalnych dla plików do wyewidencjonowania.

 lpComment

podczas Komentarz, który ma zostać zastosowany do każdego z wybranych plików do wyewidencjonowania.

 fOptions

podczas Flagi poleceń (zobacz [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

podczas Opcje dotyczące wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Wyewidencjonowanie zakończyło się pomyślnie.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został wyewidencjonowany.|
|SCC_E_ALREADYCHECKEDOUT|Użytkownik ma już wyewidencjonowany plik.|
|SCC_E_FILEISLOCKED|Plik jest zablokowany, zabraniając tworzenia nowych wersji.|
|SCC_E_FILEOUTEXCLUSIVE|Inny użytkownik wykonał wyewidencjonowanie na wyłączność tego pliku.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)
