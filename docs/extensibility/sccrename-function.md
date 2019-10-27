---
title: Funkcja SccRename | Microsoft Docs
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
ms.openlocfilehash: 30b2928653507b670160c72ca3ce09a0227a4170
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720766"
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

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)