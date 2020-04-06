---
title: MSSCCPRJ. Plik SCC | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702467"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Plik SCC
Po umieszczeniu rozwiązania programu Visual Studio lub projektu pod kontrolą źródła przy użyciu IDE, IDE odbiera dwa kluczowe informacje. Informacje pochodzą z wtyczki kontroli źródła w postaci ciągów. Te ciągi,"AuxPath" i "ProjName", są nieprzezroczyste dla IDE, ale są używane przez wtyczkę do lokalizowania rozwiązania lub projektu w kontroli wersji. IDE zazwyczaj pobiera te ciągi po raz pierwszy, wywołując [SccGetProjPath](../extensibility/sccgetprojpath-function.md), a następnie zapisuje je w pliku rozwiązania lub projektu dla przyszłych wywołań [SccOpenProject](../extensibility/sccopenproject-function.md). Po osadzaniu w plikach rozwiązania i projektu ciągi "AuxPath" i "ProjName" nie są automatycznie aktualizowane, gdy użytkownik rozgałęzia, rozwidli lub kopiuje pliki rozwiązania i projektu, które są w kontroli wersji. Aby upewnić się, że pliki rozwiązania i projektu wskazują ich poprawne położenie w kontroli wersji, użytkownicy muszą ręcznie zaktualizować ciągi. Ponieważ ciągi mają być nieprzezroczyste, nie zawsze może być jasne, jak powinny być aktualizowane.

 Wtyczka kontroli źródła może uniknąć tego problemu, przechowując ciągi "AuxPath" i "ProjName" w specjalnym pliku o nazwie plik *MSSCCPRJ.SCC.* Jest to lokalny plik po stronie klienta, który jest własnością i jest obsługiwany przez wtyczkę. Ten plik nigdy nie jest umieszczany pod kontrolą źródła, ale jest generowany przez wtyczkę dla każdego katalogu, który zawiera pliki kontrolowane przez źródło. Aby ustalić, które pliki są rozwiązania programu Visual Studio i pliki projektu, wtyczka kontroli źródła można porównać rozszerzenia plików z listy standardowej lub dostarczonej przez użytkownika. Gdy IDE wykryje, że wtyczka obsługuje plik *MSSCCPRJ.SCC,* przestaje osadzić ciągi "AuxPath" i "ProjName" do plików rozwiązania i projektu, a zamiast tego odczytuje te ciągi z pliku *MSSCCPRJ.SCC.*

 Wtyczka kontroli źródła obsługująca plik *MSSCCPRJ.SCC* musi być zgodna z następującymi wytycznymi:

- Na katalog może istnieć tylko jeden plik *MSSCCPRJ.SCC.*

- Plik *MSSCCPRJ.SCC* może zawierać "AuxPath" i "ProjName" dla wielu plików, które są pod kontrolą źródła w danym katalogu.

- Ciąg "AuxPath" nie może zawierać cudzysłowów. Dozwolone jest, aby cudzysłów wokół niego jako ograniczniki (na przykład para cudzysłowów podwójne mogą być używane do wskazania pustego ciągu). IDE będzie paski wszystkie cudzysłowy z ciągu "AuxPath", gdy jest odczytywany z pliku *MSSCCPRJ.SCC.*

- Ciąg "ProjName" w *mssccprj. Plik SCC* musi dokładnie odpowiadać `SccGetProjPath` ciągowi zwróconemu z funkcji. Jeśli ciąg zwracany przez funkcję ma cudzysłowy wokół niego, ciąg w pliku *MSSCCPRJ.SCC* musi mieć cudzysłowy wokół niego i vice versa.

- Plik *MSSCCPRJ.SCC* jest tworzony lub aktualizowany za każdym razem, gdy plik jest umieszczany pod kontrolą źródła.

- Jeśli plik *MSSCCPRJ.SCC* zostanie usunięty, dostawca powinien ponownie wygenerować go przy następnym wykonaniu operacji kontroli źródła dotyczącej tego katalogu.

- Plik *MSSCCPRJ.SCC* musi ściśle przestrzegać zdefiniowanego formatu.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja MSSCCPRJ. Format pliku SCC
 Poniżej znajduje się przykład formatu pliku *MSSCCPRJ.SCC* (numery wierszy są dostarczane tylko jako przewodnik i nie powinny być zawarte w treści pliku):

- [Linia 1]`SCC = This is a Source Code Control file`

- [Linia 2]

- [Linia 3]`[TestApp.sln]`

- [Linia 4]`SCC_Aux_Path = "\\server\vss\"`

- [Linia 5]`SCC_Project_Name = "$/TestApp"`

- [Linia 6]

- [Linia 7]`[TestApp.csproj]`

- [Linia 8]`SCC_Aux_Path = "\\server\vss\"`

- [Linia 9]`SCC_Project_Name = "$/TestApp"`

 Pierwszy wiersz określa cel pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien pojawić się dokładnie tak we wszystkich plikach *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 Poniższa sekcja zawiera szczegółowe informacje o ustawieniach każdego pliku, oznaczonych nazwą pliku w nawiasach kwadratowych. Ta sekcja jest powtarzana dla każdego śledzonego pliku. Ten wiersz jest próbką nazwy pliku, `[TestApp.csproj]`a mianowicie . IDE oczekuje następujących dwóch wierszy. Nie definiuje jednak stylu zdefiniowanych wartości. Zmienne są `SCC_Aux_Path` `SCC_Project_Name`i .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Nie ma ogranicznika końcowego do tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku, są zdefiniowane w pliku nagłówka scc.h. Aby uzyskać więcej informacji, zobacz [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
