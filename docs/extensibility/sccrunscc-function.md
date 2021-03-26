---
description: Ta funkcja wywołuje narzędzie administracyjne kontroli źródła.
title: Funkcja SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e78e58eafebd06d1ce7c710a31ce295b49f26340
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073823"
---
# <a name="sccrunscc-function"></a>SccRunScc, funkcja
Ta funkcja wywołuje narzędzie administracyjne kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parametry
 pvContext

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 nFiles

podczas Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

podczas Tablica wybranych nazw plików.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie wywołano narzędzie administracyjne kontroli źródła.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu kontroli źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_CONNECTIONFAILURE|Nie można nawiązać połączenia z systemem kontroli źródła.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta funkcja umożliwia obiektowi wywołującemu dostęp do pełnego zakresu funkcji systemu kontroli źródła za pomocą zewnętrznego narzędzia administracyjnego. Jeśli system kontroli źródła nie ma interfejsu użytkownika, wtyczka do kontroli źródła może zaimplementować interfejs do wykonywania niezbędnych funkcji administracyjnych.

 Ta funkcja jest wywoływana z liczbą i tablicą nazw plików dla aktualnie wybranych plików. Jeśli narzędzie administracyjne je obsługuje, lista plików może służyć do prewybierania plików w interfejsie administracyjnym. w przeciwnym razie lista może być ignorowana.

 Ta funkcja jest zazwyczaj wywoływana, gdy użytkownik wybierze **opcję \<Source Control Server> Uruchom** z   ->  menu **kontroli źródła** pliku. Ta opcja menu **uruchamiania** może być zawsze wyłączona lub nawet ukryta przez ustawienie wpisu rejestru. Zobacz [jak: zainstalować wtyczkę kontroli źródła,](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Aby uzyskać szczegółowe informacje. Ta funkcja jest wywoływana tylko wtedy, gdy [SccInitialize](../extensibility/sccinitialize-function.md) zwraca `SCC_CAP_RUNSCC` bit możliwości (zobacz [flagi możliwości](../extensibility/capability-flags.md) , aby uzyskać szczegółowe informacje o tej i innych bitach możliwości).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
