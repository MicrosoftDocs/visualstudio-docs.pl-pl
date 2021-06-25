---
description: Ta funkcja sprawdza listę w pełni kwalifikowanych katalogów pod tematem ich bieżącego stanu.
title: Funkcja SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9a3e65fa03c7fc2b6a8ce83ba2bb39250547aadb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904620"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo, funkcja
Ta funkcja sprawdza listę w pełni kwalifikowanych katalogów pod tematem ich bieżącego stanu.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 nDirs

[in] Liczba katalogów wybranych do zapytania.

 lpDirNames

[in] Tablica w pełni kwalifikowanych ścieżek katalogów, które mają być zbadane.

 lpStatus

[in, out] Struktura tablicy wtyczki kontroli źródła, która zwraca flagi stanu (zobacz [Kod stanu katalogu,](../extensibility/directory-status-code-enumerator.md) aby uzyskać szczegółowe informacje).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Zapytanie powiodło się.|
|SCC_E_OPNOTSUPPORTED|System kontroli kodu źródłowego nie obsługuje tej operacji.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskulacji. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Funkcja wypełnia tablicę zwracaną za pomocą maski bitów z rodziny (zobacz Kod stanu katalogu ), po jednym wpisie `SCC_DIRSTATUS` dla każdego podanego katalogu. [](../extensibility/directory-status-code-enumerator.md) Tablica stanu jest przydzielana przez wywołujący.

 Ide używa tej funkcji, zanim nazwa katalogu zostanie zmieniona, aby sprawdzić, czy katalog jest pod kontrolą źródła, przez odpytanie, czy ma odpowiadający mu projekt. Jeśli katalog nie jest pod kontrolą źródła, ide może dostarczyć użytkownikowi odpowiednie ostrzeżenie.

> [!NOTE]
> Jeśli wtyczka kontroli źródła nie chce implementować co najmniej jednej wartości stanu, niezaimplementowane bity powinny być ustawione na zero.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)
