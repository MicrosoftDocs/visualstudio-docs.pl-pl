---
title: MSSCCPRJ.SCC File | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194217"
---
# <a name="mssccprjscc-file"></a>Plik MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umieszczeniem rozwiązania programu Visual Studio lub projektu objętego kontrolą źródła przy użyciu IDE, IDE otrzymuje dwa kluczowych informacji z wtyczka do kontroli źródła w postaci ciągów. Te ciągi "AuxPath" i "ProjName" są nieprzezroczyste IDE, ale są one używane przez wtyczkę do zlokalizowania rozwiązania lub projektu w kontroli wersji. IDE zwykle uzyskuje te ciągi po raz pierwszy, wywołując [SccGetProjPath](../extensibility/sccgetprojpath-function.md), a następnie zapisuje je w pliku rozwiązania lub projektu w przyszłych wywołaniach do [SccOpenProject](../extensibility/sccopenproject-function.md). Po osadzeniu w plikach rozwiązania i projektu, ciągi "AuxPath" i "ProjName" nie są automatycznie aktualizowane po użytkownik gałęzi, rozwidleń, lub kopiuje pliki rozwiązań i projektów, które znajdują się w kontroli wersji. Aby upewnić się, że pliki rozwiązań i projektów wskazują ich poprawnej lokalizacji w kontroli wersji, należy ręcznie zaktualizować ciągi. Ponieważ ciągi mają być nieprzezroczyste, jego mogą nie być jasne jak powinny być aktualizowane.  
  
 Wtyczka do kontroli źródła można uniknąć tego problemu, przechowując ciągi "AuxPath" i "ProjName" w specjalnym pliku o nazwie MSSCCPRJ. Plik SCC. Jest to plik lokalnego, po stronie klienta jest własnością i utrzymywane przez wtyczkę. Ten plik nigdy nie jest umieszczony pod kontrolą źródła, ale jest generowany przez wtyczki dla każdego katalogu, który zawiera pliki pod kontrolą źródła. Aby określić, które pliki są pliki rozwiązań i projektów programu Visual Studio, wtyczka do kontroli źródła można porównać rozszerzeń plików z listą standardowy lub podanego przez użytkownika. Gdy IDE wykrywa, że wtyczka obsługuje MSSCCPRJ. Plik SCC przestaje osadzić "AuxPath" i "ProjName" ciągów do rozwiązania i pliki projektu i odczytuje te ciągi z MSSCCPRJ. Zamiast tego z pliku SCC.  
  
 Wtyczka do kontroli źródła obsługującego MSSCCPRJ. Plik SCC muszą być zgodne z następującymi zasadami:  
  
- Może istnieć tylko jeden MSSCCPRJ. Plik SCC dla katalogu.  
  
- MSSCCPRJ. Plik SCC może zawierać "AuxPath" i "ProjName", w przypadku wielu plików, które są pod kontrolą źródła w danym katalogu.  
  
- Ciąg "AuxPath" nie może mieć cudzysłowy wewnątrz niego. Może on być ma ją w cudzysłowie jako ograniczników (na przykład para podwójnych cudzysłowów służy do wskazania ciągiem pustym). Środowisko IDE będzie paska wszystkich ofert z ciągu "AuxPath" przeczytaniu z MSSCCPRJ. Plik SCC.  
  
- Ciąg "ProjName" w MSSCCPRJ. Plik SCC musi być zgodna dokładnie ciąg zwracany z `SccGetProjPath` funkcji. Jeśli ciąg zwracany przez funkcję ma ją ciąg w MSSCCPRJ w cudzysłowie. Plik SCC musi mieć cudzysłowów wokół niej i na odwrót.  
  
- MSSCCPRJ. SCC pliku jest tworzony lub aktualizowany, gdy plik zostanie umieszczony pod kontrolą źródła.  
  
- Jeśli MSSCCPRJ. Plik SCC zostaje usunięte, dostawcy należy ponownie wygenerować go następnym razem wykonuje operacja kontroli źródła, dotyczących tego katalogu.  
  
- MSSCCPRJ. Plik SCC musi ścisłe zdefiniowanym formacie.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja MSSCCPRJ. Format pliku SCC  
 Poniżej przedstawiono przykładowe MSSCCPRJ. Format pliku SCC (numery wierszy są podane tylko jako wskazówki i nie powinny znajdować się w treści pliku):  
  
 [Wiersz 1] `SCC = This is a Source Code Control file`  
  
 [Wiersz 2]  
  
 [Wiersz 3] `[TestApp.sln]`  
  
 [Wiersz 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Wiersz 6]  
  
 [Wiersz 7] `[TestApp.csproj]`  
  
 [Wiersz 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Wiersz 9] `SCC_Project_Name = "$/TestApp"`  
  
 Pierwszy wiersz stany zastosowanie pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien pojawić się dokładnie tak jak poniżej w MSSCCPRJ wszystkich. Pliki SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Występuje po części ustawień dla każdego pliku, który jest oznaczony według nazwy pliku w nawiasach kwadratowych. W tej sekcji jest powtarzane dla każdego pliku, które są śledzone. Ten wiersz jest przykładem nazwy pliku, to znaczy, `[TestApp.csproj]`. IDE oczekuje, że następujące dwa wiersze. Nie, jednak definiuje styl wartości zdefiniowane. Zmienne są `SCC_Aux_Path` i `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Nie ma żadnych ogranicznika końcowego do tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku są definiowane w pliku nagłówkowym scc.h. Aby uzyskać więcej informacji, zobacz [ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
