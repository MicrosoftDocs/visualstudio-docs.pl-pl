---
title: Funkcja SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35d7287d8fc12100da9ba3b8383d8e92cee73d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720531"
---
# <a name="sccuncheckout-function"></a>SccUncheckout, funkcja
Ta funkcja cofa poprzednią operację wyewidencjonowania, a tym samym przywraca zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowania. Wszystkie zmiany wprowadzone do pliku od momentu ich wyewidencjonowania zostaną utracone.

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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 nFiles

podczas Liczba plików określona w tablicy `lpFileNames`.

 lpFileNames

podczas Tablica w pełni kwalifikowanych nazw ścieżek lokalnych dla plików, dla których ma zostać cofnięte wyewidencjonowanie.

 fOptions

podczas Flagi poleceń (nieużywane).

 pvOptions

podczas Opcje dotyczące wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Cofnięcie wyewidencjonowania zakończyło się pomyślnie.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą kodu źródłowego.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Cofnięcie wyewidencjonowania nie powiodło się.|
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma wyewidencjonowanego pliku.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="remarks"></a>Uwagi
 Po tej operacji flagi `SCC_STATUS_CHECKEDOUT` i `SCC_STATUS_MODIFIED` zostaną wyczyszczone dla plików, na których wykonano wyewidencjonowanie.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)