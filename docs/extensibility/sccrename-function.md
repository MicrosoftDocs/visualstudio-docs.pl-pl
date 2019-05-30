---
title: Funkcja SccRename | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1329f847f7f961bf4c792cbdf7f40f8f04b1694c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338732"
---
# <a name="sccrename-function"></a>SccRename, funkcja
Ta funkcja zmienia nazwę pliku w systemie kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Struktura kontekście wtyczki kontroli źródła.

 hWnd

[in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.

 lpFileName

[in] W pełni kwalifikowaną nazwę pliku nazwa jest zmieniana.

 lpNewName

[in] W pełni kwalifikowana nazwa nowego. Jeśli ścieżka katalogu jest inna, plik został przeniesiony w z jednego podkatalogu do innego.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie ukończono operację zmiany nazwy.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wykonania tej operacji.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć projektu jako część procesu zmiany nazwy.|
|SCC_E_OPNOTPERFORMED|Nie można wykonać operacji.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja może służyć do zmiany nazwy pliku lub przenieść je z jednej lokalizacji do innej, w systemie kontroli źródła. Wtyczka do kontroli źródła nie należy próbować uzyskać dostęp do pliku na dysku. Odpowiada środowiska IDE można zmienić nazwy pliku lokalnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)