---
title: Widok Caller-Callee — dane próbkowania pamięci platformy .NET | Microsoft Docs
description: Dowiedz się, jak widok wywołujący/wywoływany wyświetla dane próbkowania pamięci platformy .NET dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych w Eksplorator wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 58236bbacfaa262c23400506cb32331719000b81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967530"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET
Widok wywołujący/wywoływany wyświetla dane profilowania pamięci platformy .NET dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje profilowania pamięci dotyczące wybranej funkcji. Wartości obejmują wszystkie przykładowe wywołania funkcji.

 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują ilość wartości wybranej (bieżącej) funkcji wygenerowanej przez wywołania z funkcji wywołującej (nadrzędnej).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i wyświetlają dane profilowania pamięci dla funkcji wywoływanych (podrzędnych) wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kliknij dwukrotnie obiekt wywołujący lub element wywoływanej funkcji, aby uczynić ten wiersz bieżącą funkcją.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Typ**|Kontekst funkcji:<br /><br /> **0** — bieżąca funkcja<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|
|**Poziomie**|Głębokość funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|
|**Przydziały włączne**|— Dla bieżącej funkcji liczba obiektów, które zostały przydzielone przez funkcję w przebiegu profilowania. Ta liczba obejmuje obiekty, które zostały utworzone w funkcjach wywoływanych.<br />-Dla funkcji wywołującej liczba przydziałów włącznie dla bieżącej funkcji, które zostały wygenerowane przez wywołania tej funkcji.<br />-Dla funkcji wywoływanej liczba obiektów przydzielonej przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba zawiera przydziały, które zostały wykonane przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były przydzielone do tej funkcji.|
|**Alokacje wyłączne**|— Dla bieżącej funkcji — liczba obiektów, które zostały utworzone, gdy funkcja wykonywała kod treści funkcji (to oznacza, gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />-Dla funkcji wywołującej liczba wyłącznych alokacji bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />-Dla funkcji wywoływanej, liczba obiektów utworzonych przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba nie obejmuje obiektów, które zostały utworzone przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były przydzielone do tej funkcji.|
|**Bajty włączne**|— Dla bieżącej funkcji — liczba bajtów pamięci przydzielonej przez funkcję w ramach uruchomienia profilowania. Liczba zawiera pamięć, która została przypisana w funkcjach, które zostały wywołane przez tę funkcję.<br />-Dla funkcji wywołującej liczba bajtów (włącznie) bieżącej funkcji, które zostały wygenerowane na podstawie wywołań przez funkcję wywołującą.<br />-Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba zawiera bajty, które zostały przydzielone przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Bajtów włącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która obejmuje przydziały tej funkcji.|
|**Bajty wyłączne**|— Dla bieżącej funkcji — liczba bajtów pamięci przydzielonej przez funkcję w ramach uruchomienia profilowania. Ta liczba nie obejmuje pamięci przydzielonej przez funkcje, które zostały wywołane przez bieżącą funkcję.<br />-Dla funkcji wywołującej liczba wyłącznych bajtów bieżącej funkcji, które zostały wygenerowane przez wywołania z funkcji wywołującej.<br />-Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów, które zostały przydzielone przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Bajtów wyłącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która wystąpiła na wyłączność alokacji tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok elementu wywołującego/wywoływanego — dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany-Dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok wywołujący/wywoływany-Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
