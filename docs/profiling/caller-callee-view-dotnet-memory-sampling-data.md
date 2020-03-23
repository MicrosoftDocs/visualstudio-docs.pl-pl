---
title: Widok wywołujący wywoływany — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 50e278e858ea086c83b29ef4eebf6b48ee8e477e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773312"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Widok wywołujący/wywoływany — dane próbkowania pamięci .NET
W widoku wywołujący/wywoływany są wyświetlane dane profilowania pamięci .NET dla wybranej funkcji oraz jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje profilowania pamięci o wybranej funkcji. Wartości obejmują wszystkie próbkowanie wywołań funkcji.

 **Funkcje, które wywołały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują wartość wybranej (bieżącej) funkcji wygenerowanej przez wywołania z funkcji wywołującego (nadrzędnego).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje dane profilowania pamięci dla wywoływane (podrzędne) funkcje wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kliknij dwukrotnie wiersz funkcji wywołującego lub wywoływanego, aby ten wiersz był bieżącą funkcją.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Typ**|Kontekst funkcji:<br /><br /> **0** - bieżąca funkcja<br /><br /> **1** - funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** - funkcja wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Poziom**|Głębokość funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Alokacje włącznie**|- Dla bieżącej funkcji liczba obiektów, które zostały przydzielone przez funkcję w przebiegu profilowania. Numer ten zawiera obiekty, które zostały utworzone w wywoływanych funkcji.<br />- Dla funkcji wywołującego, numer alokacji włącznie bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />- Dla funkcji wywoływanej liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba ta zawiera alokacje, które zostały wykonane przez funkcje, które były wywoływane przez funkcję wywoływana.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Alokacje wyłączne**|- Dla bieżącej funkcji liczba obiektów, które zostały utworzone, gdy funkcja była wykonywanie kodu treści funkcji (czyli gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które były wywoływane przez funkcję.<br />- Dla funkcji wywołującego, numer wyłącznych alokacji bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />- Dla funkcji wywoływanej liczba obiektów, które zostały utworzone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Numer nie zawiera obiektów, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję wywoływana.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Bajty włącznie**|- Dla bieżącej funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba zawiera pamięć, która została przydzielona w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla funkcji wywołującego, numer bajtów włącznie bieżącej funkcji, które zostały wygenerowane z wywołań przez funkcję wywołującego.<br />- Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba zawiera bajty, które zostały przydzielone przez funkcje, które były wywoływane przez funkcję wywoływana.|
|**Bajty włącznie %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Bajty wyłączne**|- Dla bieżącej funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba ta nie obejmuje pamięci, która została przydzielona przez funkcje, które zostały wywołane przez bieżącą funkcję.<br />- Dla funkcji wywołującego, numer wyłącznych bajtów bieżącej funkcji, które zostały wygenerowane przez wywołania z funkcji wywołującego.<br />- Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Numer nie zawiera bajtów, które zostały przydzielone przez funkcje, które zostały wywołane przez funkcję wywoływana.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany — dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok rozmówcy/wywoływania — dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)
