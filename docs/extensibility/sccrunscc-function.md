---
description: Ta funkcja wywołuje narzędzie administracyjne kontroli źródła.
title: SccRunScc, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c865931ed52601761f0bd519bf360d584d49ec04
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904116"
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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 nFiles

[in] Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in] Tablica wybranych nazw plików.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Narzędzie administracyjne kontroli źródła zostało pomyślnie wywołane.|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu kontroli źródła.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub zdyskusją.|
|SCC_E_CONNECTIONFAILURE|Nie można nawiązać połączenia z systemem kontroli źródła.|
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą źródła.|
|SCC_E_NONSPECIFICERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja umożliwia wywołującym dostęp do pełnego zakresu funkcji systemu kontroli źródła za pośrednictwem zewnętrznego narzędzia administracyjnego. Jeśli system kontroli źródła nie ma interfejsu użytkownika, wtyczka kontroli źródła może zaimplementować interfejs do wykonywania niezbędnych funkcji administracyjnych.

 Ta funkcja jest wywoływana z licznikiem i tablicą nazw plików dla aktualnie wybranych plików. Jeśli narzędzie administracyjne go obsługuje, lista plików może służyć do wstępnego wyboru plików w interfejsie dministracyjnych; W przeciwnym razie listę można zignorować.

 Ta funkcja jest zwykle wywoływana, gdy użytkownik wybierze pozycję **Uruchom z \<Source Control Server>** menu **Kontrola**  ->  **źródła** pliku. Tę **opcję** menu Uruchom można zawsze wyłączyć, a nawet ukryć, ustawiając wpis rejestru. Aby uzyskać szczegółowe informacje, zobacz [Instaluj wtyczkę kontroli](../extensibility/internals/how-to-install-a-source-control-plug-in.md) kodu źródłowego. Ta funkcja jest wywoływana tylko wtedy, gdy [funkcja SccInitialize](../extensibility/sccinitialize-function.md) zwraca bit możliwości (zobacz Flagi możliwości, aby uzyskać szczegółowe informacje na temat tego i `SCC_CAP_RUNSCC` innych bitów możliwości). [](../extensibility/capability-flags.md)

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
