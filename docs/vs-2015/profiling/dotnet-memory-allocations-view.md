---
title: Widok alokacji pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 563826c63d851e412b7c74a99f5b8a9ad1c1556e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798810"
---
# <a name="net-memory-allocations-view"></a>.NET Widok alokacji pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok alokacji zawiera typy, które zostały utworzone podczas uruchomienia profilowania. Każdy typ jest węzeł główny drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowały alokacji typu.  
  
 Dane w wierszu Typ wyświetlana całkowita liczba obiektów tego typu, które zostały utworzone w trakcie uruchomienia profilowania i całkowita liczba bajtów przydzielonych do obiektów tego typu. Wartości włączne i wyłączne dla typu są zawsze takie same.  
  
- Wartości włączne dotyczą obiektów utworzonych w wystąpieniach funkcji i jej funkcji podrzędnych, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.  
  
- Wyłączne wartości są obiekty, które zostały utworzone bezpośrednio za pomocą funkcji, jeśli zostały one wywoływane przez nadrzędne funkcję. Obiekty utworzone w funkcji podrzędnej nie są uwzględniane.  
  
  Dane dla funkcji Wyświetla liczbę obiektów utworzonych i liczba bajtów przydzielonych dla obiektów typu nadrzędnego.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżka aktywna wykonywania  
 Można znaleźć ścieżki wykonywania drzewo wywołań, utworzony większość obiektów o typie elementu nadrzędnego.  
  
-   Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy typu lub funkcji, a następnie kliknij **Rozwiń ścieżkę aktywną**.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa przydzielonego typu lub funkcji.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera typ lub funkcja.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera typu lub funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla typu lub funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej definicji typu lub funkcji w pliku źródłowym.|  
|**Poziom**|Wskazuje, czy dane są dla typu lub funkcji.|  
|**Przydziały włączne**|— Dla funkcji, całkowita liczba obiektów o typie elementu nadrzędnego, które zostały utworzone przez funkcję. Liczba ta obejmuje obiektów utworzonych w funkcji podrzędnych.<br />— Dla typu, całkowita liczba wystąpień tego typu, które zostały utworzone.|  
|**% Przydziałów włącznych**|— Dla funkcji, wartość procentowa wszystkie obiekty utworzone w trakcie uruchomienia profilowania, które zostały przydziałów włącznych typu nadrzędnego przez funkcję.<br />— Dla typu procent całkowitej liczby obiektów, które zostały utworzone w profilowania, były wystąpienia typu.|  
|**Przydziały wyłączne**|— W przypadku funkcji liczbę obiektów, które zostały utworzone podczas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Ta liczba nie ma obiektów utworzonych w funkcji podrzędnych.<br />— Dla typu, całkowita liczba wystąpień tego typu, które zostały utworzone.|  
|**% Przydziałów wyłącznych**|— Dla funkcji, wartość procentowa wszystkie obiekty utworzone w trakcie uruchomienia profilowania, które zostały przydziałów wyłącznych typu nadrzędnego przez funkcję.<br />— Dla typu procent całkowitej liczby obiektów, które zostały utworzone w profilowania, były wystąpienia typu.|  
|**Bajty włączne**|— W przypadku funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Liczba ta obejmuje pamięć, która została przydzielona przez jej funkcji podrzędnych.<br />— Dla typu, całkowita liczba bajtów, która została przydzielona w profilowania dla wystąpień tego typu.|  
|**% Bajtów włącznych**|— W przypadku funkcji procent wszystkich przydzielonej pamięci w profilowania, był przydziałów włącznych typu nadrzędnego przez funkcję.<br />— Dla typu, procent wszystkich przydzielonej pamięci w profilowania, została przydzielona dla wystąpienia typu.|  
|**Bajty wyłączne**|— W przypadku funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Ta liczba nie obejmuje pamięć, która została przydzielona przez jej funkcji podrzędnych.<br />— Dla typu całkowita liczba bajtów przydzielonych w profilowania są uruchamiane dla wystąpień tego typu.|  
|**% Bajtów wyłącznych**|— W przypadku funkcji procent wszystkich przydzielonej pamięci w profilowania, był przydziałów wyłącznych typu nadrzędnego przez funkcję.<br />— Dla typu, procent wszystkich przydzielonej pamięci w profilowania, została przydzielona dla wystąpienia typu.|
