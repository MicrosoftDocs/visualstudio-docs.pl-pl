---
title: Funkcja SccRunScc | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700395"
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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[w] Liczba plików określonych `lpFileNames` w tablicy.

 lpFileNames

[w] Tablica wybranych nazw plików.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Narzędzie administracyjne kontroli źródła zostało pomyślnie wywołane.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu kontroli źródła.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją.|
|SCC_E_CONNECTIONFAILURE|Nie można połączyć się z systemem kontroli źródła.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja umożliwia wywołującemu dostęp do pełnego zakresu funkcji systemu kontroli źródła za pośrednictwem zewnętrznego narzędzia administracyjnego. Jeśli system kontroli źródła nie ma interfejsu użytkownika, wtyczka kontroli źródła może zaimplementować interfejs do wykonywania niezbędnych funkcji administracyjnych.

 Ta funkcja jest wywoływana z liczbą i tablicą nazw plików dla aktualnie wybranych plików. Jeśli narzędzie administracyjne obsługuje to, lista plików może służyć do wstępnego zaznaczania plików w interfejsie administracyjnym; w przeciwnym razie lista może zostać zignorowana.

 Ta funkcja jest zazwyczaj wywoływana, gdy użytkownik wybierze **>\<z** menu**Kontrola źródła** **uruchamiania.** ->  Ta opcja menu **Uruchom** można zawsze wyłączyć lub nawet ukryć, ustawiając wpis rejestru. Zobacz Jak: Aby uzyskać szczegółowe informacje, [zobacz Jak: Zainstaluj wtyczkę kontroli źródła.](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Ta funkcja jest wywoływana tylko wtedy, `SCC_CAP_RUNSCC` [gdy SccInitialize](../extensibility/sccinitialize-function.md) zwraca bit możliwości (zobacz Flagi [możliwości, aby](../extensibility/capability-flags.md) uzyskać szczegółowe informacje na temat tego i innych bitów możliwości).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
