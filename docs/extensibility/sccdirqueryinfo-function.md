---
title: Funkcja SccDirQueryInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700950"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo, funkcja
Ta funkcja sprawdza listę w pełni kwalifikowanych katalogów dla ich bieżącego stanu.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametry
 Pcontext

[w] Struktura kontekstu wtyczki formantu źródła.

 nDirs (nDirs)

[w] Liczba katalogów wybranych do kwerendy.

 lpDirNames (lpDirNames)

[w] Tablica w pełni kwalifikowanych ścieżek katalogów, które mają być wyszukiwane.

 lpStatus

[w, na zewnątrz] Struktura tablicy dla wtyczki kontroli źródła, aby zwrócić flagi stanu (zobacz [kod stanu katalogu,](../extensibility/directory-status-code-enumerator.md) aby uzyskać szczegółowe informacje).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kwerenda zakończyła się pomyślnie.|
|SCC_E_OPNOTSUPPORTED|System kontroli kodu źródłowego nie obsługuje tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Funkcja wypełnia tablicę zwracaną maską bitową bitów z `SCC_DIRSTATUS` rodziny (zobacz kod stanu [katalogu),](../extensibility/directory-status-code-enumerator.md)po jednym wpisie dla każdego podanego katalogu. Tablica stanu jest przydzielana przez wywołującego.

 IDE używa tej funkcji przed nazwa katalogu jest zmieniana, aby sprawdzić, czy katalog jest pod kontrolą źródła, sprawdzając, czy ma odpowiedni projekt. Jeśli katalog nie jest pod kontrolą źródła, IDE może zapewnić odpowiednie ostrzeżenie dla użytkownika.

> [!NOTE]
> Jeśli wtyczka formantu źródła zdecyduje się nie implementować jednej lub więcej wartości stanu, niewdrożonych bitów należy ustawić na zero.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)
