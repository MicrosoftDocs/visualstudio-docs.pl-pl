---
title: MSSCCPRJ. Plik SCC | Microsoft Docs
description: Dowiedz się więcej o MSSCCPRJ. Plik SCC, który jest lokalnym plikiem po stronie klienta używanym przez wtyczkę kontroli źródła, która współpracuje z zestawem SDK programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 945d1a4d1acde0ac3fef9918123f963cf27127f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090554"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Plik SCC
Po umieszczeniu rozwiązania lub projektu programu Visual Studio pod kontrolą źródła przy użyciu IDE, IDE odbiera dwa kluczowe fragmenty informacji. Informacje pochodzą z wtyczki kontroli źródła w postaci ciągów. Te ciągi, "AuxPath" i "Projname", są nieprzezroczyste dla środowiska IDE, ale są używane przez wtyczkę do lokalizowania rozwiązania lub projektu w kontroli wersji. IDE zazwyczaj pobiera te ciągi po raz pierwszy przez wywołanie [SccGetProjPath](../extensibility/sccgetprojpath-function.md), a następnie zapisuje je w pliku rozwiązania lub projektu w celu przyszłego wywołania do [SccOpenProject](../extensibility/sccopenproject-function.md). Po osadzeniu w plikach rozwiązania i projektu ciągi "AuxPath" i "Projname" nie są automatycznie aktualizowane, gdy rozgałęzienia użytkownika, rozwidlenia lub kopiowania są używane w kontroli wersji. Aby upewnić się, że rozwiązanie i pliki projektu wskazują ich poprawną lokalizację w kontroli wersji, użytkownicy muszą ręcznie zaktualizować te ciągi. Ponieważ ciągi mają być nieprzezroczyste, może nie zawsze być jasne, jak powinny być aktualizowane.

 Wtyczka do kontroli źródła może uniknąć tego problemu, przechowując ciągi "AuxPath" i "Projname" w specjalnym pliku o nazwie *MSSCCPRJ. SCC* . Jest to lokalny plik po stronie klienta, który jest własnością i jest obsługiwany przez wtyczkę. Ten plik nigdy nie znajduje się pod kontrolą źródła, ale jest generowany przez wtyczkę dla każdego katalogu, który zawiera pliki z kontrolą źródła. Aby określić, które pliki są rozwiązaniami programu Visual Studio i plikami projektu, wtyczka do kontroli źródła może porównać rozszerzenia plików z listą standardową lub dostarczaną przez użytkownika. Gdy środowisko IDE wykryje, że wtyczka obsługuje plik *MSSCCPRJ. SCC* , traci osadzenie ciągów "AuxPath" i "Projname" w plikach rozwiązań i projektu, a zamiast tego odczytuje te ciągi z pliku *MSSCCPRJ. SCC* .

 Wtyczka do kontroli źródła, która obsługuje plik *MSSCCPRJ. SCC* , musi być zgodna z następującymi wskazówkami:

- Może istnieć tylko jeden plik *MSSCCPRJ. SCC* dla katalogu.

- Plik *MSSCCPRJ. SCC* może zawierać ciąg "AuxPath" i "Projname" dla wielu plików, które znajdują się pod kontrolą źródła w danym katalogu.

- Ciąg "AuxPath" nie może zawierać cudzysłowu. Może mieć cudzysłowy wokół niego jako ograniczniki (na przykład para podwójnych cudzysłowów może być używana do wskazania pustego ciągu). IDE będzie wszystkie cudzysłowy z ciągu "AuxPath", gdy jest odczytywane z pliku *MSSCCPRJ. SCC* .

- Ciąg "Projname" w *MSSCCPRJ. Plik SCC* musi dokładnie pasować do ciągu zwróconego przez `SccGetProjPath` funkcję. Jeśli ciąg zwracany przez funkcję ma wokół niego cudzysłowy, ciąg w pliku *MSSCCPRJ. SCC* musi mieć cudzysłowy wokół niego i na odwrót.

- Plik *MSSCCPRJ. SCC* jest tworzony lub aktualizowany za każdym razem, gdy plik zostanie umieszczony pod kontrolą źródła.

- Jeśli plik *MSSCCPRJ. SCC* zostanie usunięty, dostawca powinien ponownie wygenerować go przy następnym wykonywaniu operacji kontroli źródła na tym katalogu.

- Plik *MSSCCPRJ. SCC* musi być ściśle zgodny ze zdefiniowanym formatem.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja przedstawiająca MSSCCPRJ. Format pliku SCC
 Poniżej znajduje się przykładowy format pliku *MSSCCPRJ. SCC* (numery wierszy są podane tylko jako przewodnik i nie powinny być zawarte w treści pliku):

- [Wiersz 1] `SCC = This is a Source Code Control file`

- [Wiersz 2]

- [Wiersz 3] `[TestApp.sln]`

- [Wiersz 4] `SCC_Aux_Path = "\\server\vss\"`

- [Wiersz 5] `SCC_Project_Name = "$/TestApp"`

- [Wiersz 6]

- [Wiersz 7] `[TestApp.csproj]`

- [Wiersz 8] `SCC_Aux_Path = "\\server\vss\"`

- [Wiersz 9] `SCC_Project_Name = "$/TestApp"`

 Pierwszy wiersz określa przeznaczenie pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien wyglądać dokładnie tak samo jak w przypadku wszystkich plików *MSSCCPRJ. SCC* :

 `SCC = This is a Source Code Control file`

 W poniższej sekcji przedstawiono ustawienia poszczególnych plików oznaczone nazwą pliku w nawiasach kwadratowych. Ta sekcja jest powtarzana dla każdego śledzonego pliku. Ten wiersz jest przykładem nazwy pliku, czyli `[TestApp.csproj]` . IDE oczekuje następujących dwóch wierszy. Nie definiuje jednak stylu zdefiniowanych wartości. Zmienne są `SCC_Aux_Path` i `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Brak ogranicznika końcowego do tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku, są zdefiniowane w pliku nagłówkowym SCC. h. Aby uzyskać więcej informacji, zobacz [ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
