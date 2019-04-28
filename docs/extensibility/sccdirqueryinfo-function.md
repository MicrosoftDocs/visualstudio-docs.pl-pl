---
title: SccDirQueryInfo Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4953c8478e25a1534691e99c41dce03930ac46ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434661"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo function
Ta funkcja sprawdza, czy lista katalogów w pełni kwalifikowaną ich bieżący stan.

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
 pContext

[in] Struktura kontekście wtyczki kontroli źródła.

 nDirs

[in] Liczba katalogów wybranych być badana.

 lpDirNames

[in] Tablica ścieżek katalogów, wysyłanie kwerend do w pełni kwalifikowanych.

 lpStatus

[out w] Struktura tablicy wtyczka do kontroli źródła do zwrócenia flagi stanu (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) Aby uzyskać szczegółowe informacje).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Zapytanie zakończyło się pomyślnie.|
|SCC_E_OPNOTSUPPORTED|System kontroli kodu źródłowego nie obsługuje tej operacji.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Funkcja wypełnia zwracana tablica z maską bitów bitów z `SCC_DIRSTATUS` rodziny (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)), jeden wpis dla każdego katalogu, biorąc pod uwagę. Tablica stanu jest przydzielany przez obiekt wywołujący.

 Tej funkcji używa środowiska IDE, zanim katalogu została zmieniona, aby sprawdzić, czy katalog znajduje się pod kontrolą źródła, badając, czy ma ona odpowiedniego projektu. Jeśli katalog nie jest pod kontrolą źródła, IDE może zapewnić odpowiednie ostrzeżenie dla użytkownika.

> [!NOTE]
> Jeśli wtyczka do kontroli źródła nie zaimplementować jedną lub więcej wartości stanu, niezaimplementowana bity powinny być ustawione na zero.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)