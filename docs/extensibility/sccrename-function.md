---
title: Funkcja SccRename | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700430"
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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 lpFileName

[w] W pełni kwalifikowana nazwa pliku, który został zmieniony.

 lpNewName

[w] W pełni kwalifikowana nowa nazwa. Jeśli ścieżka katalogu jest inna, plik został przeniesiony z jednego podkatalogu do drugiego.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja zmiany nazwy została pomyślnie zakończona.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie jest upoważniony do wykonania tej operacji.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć projektu w ramach procesu zmiany nazwy.|
|SCC_E_OPNOTPERFORMED|Operacja nie została wykonana.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony lub ogólny błąd.|

## <a name="remarks"></a>Uwagi
 Tej funkcji można użyć do zmiany nazwy pliku lub przeniesienia go z jednej lokalizacji do drugiej w systemie kontroli źródła. Wtyczka kontroli źródła nie powinna podejmować prób uzyskania dostępu do pliku na dysku. Jest ide jest odpowiedzialny za zmianę nazwy pliku lokalnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
