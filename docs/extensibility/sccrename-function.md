---
description: Ta funkcja zmienia nazwę pliku w systemie kontroli źródła.
title: Funkcja SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcfb68518f42e969b7c9d52acfb37723e9774f97
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221343"
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

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 lpFileName

podczas W pełni kwalifikowana nazwa pliku, którego nazwę zmieniono.

 lpNewName

podczas W pełni kwalifikowana nazwa. Jeśli ścieżka katalogu jest inna, plik został przeniesiony z jednego podkatalogu do innego.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja zmiany nazwy została zakończona pomyślnie.|
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty w kontroli źródła.|
|SCC_E_FILENOTCONTROLLED|Plik nie znajduje się pod kontrolą źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do wykonania tej operacji.|
|SCC_E_COULDNOTCREATEPROJECT|Nie można utworzyć projektu w ramach procesu zmiany nazwy.|
|SCC_E_OPNOTPERFORMED|Operacja nie została wykonana.|
|SCC_E_NONSPECIFICERROR|Wystąpił błąd nieokreślony lub ogólny.|

## <a name="remarks"></a>Uwagi
 Ta funkcja może służyć do zmiany nazwy pliku lub przenoszenia go z jednej lokalizacji do innej w systemie kontroli źródła. Wtyczka do kontroli źródła nie powinna próbować uzyskać dostępu do pliku na dysku. W środowisku IDE leży zmiana nazwy pliku lokalnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
