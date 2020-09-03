---
title: MSSCCPRJ. Plik SCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194217"
---
# <a name="mssccprjscc-file"></a>Plik MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy rozwiązanie lub projekt programu Visual Studio znajduje się pod kontrolą źródła przy użyciu IDE, IDE odbiera dwa kluczowe fragmenty informacji z wtyczki kontroli źródła w postaci ciągów. Te ciągi, "AuxPath" i "Projname", są nieprzezroczyste dla IDE, ale są używane przez wtyczkę do lokalizowania rozwiązania lub projektu w kontroli wersji. IDE zwykle uzyskuje te ciągi po raz pierwszy przez wywołanie [SccGetProjPath](../extensibility/sccgetprojpath-function.md), a następnie zapisuje je w pliku rozwiązania lub projektu w celu przyszłego wywołania do [SccOpenProject](../extensibility/sccopenproject-function.md). Po osadzeniu w plikach rozwiązania i projektu ciągi "AuxPath" i "Projname" nie są automatycznie aktualizowane, gdy rozgałęzienia użytkownika, rozwidlenia lub kopiowania są używane w kontroli wersji. Aby upewnić się, że rozwiązanie i pliki projektu wskazują ich poprawną lokalizację w kontroli wersji, użytkownicy muszą ręcznie zaktualizować te ciągi. Ponieważ ciągi mają być nieprzezroczyste, może nie zawsze być jasne, jak powinny być aktualizowane.  
  
 Wtyczka do kontroli źródła może uniknąć tego problemu, przechowując ciągi "AuxPath" i "Projname" w specjalnym pliku o nazwie MSSCCPRJ. Plik SCC. Jest to lokalny plik po stronie klienta, który jest własnością i jest obsługiwany przez wtyczkę. Ten plik nigdy nie znajduje się pod kontrolą źródła, ale jest generowany przez wtyczkę dla każdego katalogu, który zawiera pliki z kontrolą źródła. Aby określić, które pliki są rozwiązaniami programu Visual Studio i plikami projektu, wtyczka do kontroli źródła może porównać rozszerzenia plików z listą standardową lub dostarczaną przez użytkownika. Gdy IDE wykryje, że wtyczka obsługuje MSSCCPRJ. Plik SCC, traci osadzenie ciągów "AuxPath" i "Projname" w plikach rozwiązania i projektu i odczytuje te ciągi z MSSCCPRJ. Zamiast tego plik SCC.  
  
 Wtyczka do kontroli źródła, która obsługuje MSSCCPRJ. Plik SCC musi być zgodny z następującymi wskazówkami:  
  
- Może istnieć tylko jeden MSSCCPRJ. Plik SCC na katalog.  
  
- MSSCCPRJ. Plik SCC może zawierać "AuxPath" i "Projname" dla wielu plików, które znajdują się pod kontrolą źródła w danym katalogu.  
  
- Ciąg "AuxPath" nie może zawierać cudzysłowu. Może mieć cudzysłowy wokół niego jako ograniczniki (na przykład para podwójnych cudzysłowów może być używana do wskazania pustego ciągu). IDE będzie wszystkie cudzysłowy z ciągu "AuxPath", gdy zostanie odczytany z MSSCCPRJ. Plik SCC.  
  
- Ciąg "Projname" w MSSCCPRJ. Plik SCC musi dokładnie pasować do ciągu zwróconego przez `SccGetProjPath` funkcję. Jeśli ciąg zwracany przez funkcję zawiera cudzysłowy, ciąg w MSSCCPRJ. Plik SCC musi zawierać cudzysłowy i na odwrót.  
  
- MSSCCPRJ. Plik SCC jest tworzony lub aktualizowany za każdym razem, gdy plik jest umieszczony pod kontrolą źródła.  
  
- Jeśli MSSCCPRJ. Plik SCC zostanie usunięty, dostawca powinien ponownie wygenerować go przy następnym wykonywaniu operacji kontroli źródła na tym katalogu.  
  
- MSSCCPRJ. Plik SCC musi być ściśle zgodny ze zdefiniowanym formatem.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja przedstawiająca MSSCCPRJ. Format pliku SCC  
 Poniżej znajduje się przykład MSSCCPRJ. Format pliku SCC (numery wierszy są podane tylko jako przewodnik i nie powinny być zawarte w treści pliku):  
  
 [Wiersz 1] `SCC = This is a Source Code Control file`  
  
 [Wiersz 2]  
  
 [Wiersz 3] `[TestApp.sln]`  
  
 [Wiersz 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Wiersz 6]  
  
 [Wiersz 7] `[TestApp.csproj]`  
  
 [Wiersz 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 9] `SCC_Project_Name = "$/TestApp"`  
  
 Pierwszy wiersz określa przeznaczenie pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien wyglądać dokładnie tak samo jak w przypadku wszystkich MSSCCPRJ. Pliki SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Poniżej znajduje się sekcja ustawień dla każdego pliku oznaczona jako nazwa pliku w nawiasach kwadratowych. Ta sekcja jest powtarzana dla każdego śledzonego pliku. Ten wiersz jest przykładem nazwy pliku, czyli `[TestApp.csproj]` . IDE oczekuje następujących dwóch wierszy. Nie definiuje jednak stylu zdefiniowanych wartości. Zmienne są `SCC_Aux_Path` i `SCC_Project_Name` .  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Brak ogranicznika końcowego do tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku, są zdefiniowane w pliku nagłówkowym SCC. h. Aby uzyskać więcej informacji, zobacz [ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)   
 [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
