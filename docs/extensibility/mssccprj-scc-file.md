---
title: MSSCCPRJ. Plik SCC | Microsoft Docs
description: Dowiedz się więcej o MSSCCPRJ. Plik SCC, który jest lokalnym plikiem po stronie klienta używanym przez wtyczkę kontroli kodu źródłowego, która współpracuje z Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899254"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Plik SCC
Po Visual Studio lub projektu pod kontrolą źródła przy użyciu środowiska IDE idee odbierają dwie kluczowe informacje. Informacje pochodzą z wtyczki kontroli źródła w postaci ciągów. Te ciągi, "AuxPath" i "ProjName", są nieprzezroczyste dla środowiska IDE, ale są używane przez wtyczkę do lokalizowania rozwiązania lub projektu w kontroli wersji. Ide zwykle pobiera te ciągi po raz pierwszy, wywołując [klasę SccGetProjPath,](../extensibility/sccgetprojpath-function.md)a następnie zapisuje je w pliku rozwiązania lub projektu na przyszłość w celu wywołania do [projektu SccOpenProject](../extensibility/sccopenproject-function.md). Po osadzona w plikach rozwiązania i projektu ciągi "AuxPath" i "ProjName" nie są automatycznie aktualizowane, gdy użytkownik odgałęzienia, widły ani kopiuje pliki rozwiązania i projektu, które są w kontroli wersji. Aby upewnić się, że pliki rozwiązania i projektu wskazują poprawną lokalizację w kontroli wersji, użytkownicy muszą ręcznie zaktualizować ciągi. Ponieważ ciągi mają być nieprzezroczyste, nie zawsze jest jasne, jak powinny być aktualizowane.

 Wtyczka kontroli źródła może uniknąć tego problemu, przechowując ciągi "AuxPath" i "ProjName" w specjalnym pliku o nazwie *MSSCCPRJ.SCC.* Jest to lokalny plik po stronie klienta, który jest własnością wtyczki i jest przez niego utrzymywany. Ten plik nigdy nie jest umieszczany pod kontrolą źródła, ale jest generowany przez wtyczkę dla każdego katalogu zawierającego pliki kontrolowane przez źródło. Aby określić, które pliki Visual Studio pliki rozwiązania i projektu, wtyczka kontroli źródła może porównać rozszerzenia plików z listą standardową lub dostarczoną przez użytkownika. Gdy idee wykryje, że wtyczka obsługuje plik *MSSCCPRJ.SCC,* przestanie osadzać ciągi "AuxPath" i "ProjName" w plikach rozwiązania i projektu, a zamiast tego odczytuje te ciągi z pliku *MSSCCPRJ.SCC.*

 Wtyczka kontroli źródła, która obsługuje plik *MSSCCPRJ.SCC,* musi być zgodna z następującymi wytycznymi:

- W katalogu może być tylko jeden plik *MSSCCPRJ.SCC.*

- Plik *MSSCCPRJ.SCC* może zawierać wartości "AuxPath" i "ProjName" dla wielu plików, które są pod kontrolą źródła w danym katalogu.

- Ciąg "AuxPath" nie może zawierać cudzysłowów. Cudzysłowy wokół niego mogą być ogranicznikami (na przykład para podwójnych cudzysłowów może służyć do wskazywania pustego ciągu). Podczas odczytywania z pliku *MSSCCPRJ.SCC* w idee zostaną odczytane wszystkie cudzysłowy z ciągu "AuxPath".

- Ciąg "ProjName" w *MSSCCPRJ. Plik SCC* musi odpowiadać dokładnie ciągowi zwróconemu z `SccGetProjPath` funkcji. Jeśli ciąg zwracany przez funkcję zawiera cudzysłowy wokół niego, ciąg w pliku *MSSCCPRJ.SCC* musi zawierać cudzysłowy wokół niego i na odwrót.

- Plik *MSSCCPRJ.SCC* jest tworzony lub aktualizowany za każdym razem, gdy plik jest umieszczany w kontroli źródła.

- Jeśli plik *MSSCCPRJ.SCC* zostanie usunięty, dostawca powinien go ponownie wygenerować przy następnym wykona operacji kontroli źródła dotyczącej tego katalogu.

- Plik *MSSCCPRJ.SCC* musi ściśle przestrzegać zdefiniowanego formatu.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustracja mssccprj. Format pliku SCC
 Poniżej przedstawiono przykładowy format pliku *MSSCCPRJ.SCC* (numery wiersza są podane tylko jako przewodnik i nie powinny być zawarte w treści pliku):

- [Wiersz 1] `SCC = This is a Source Code Control file`

- [Wiersz 2]

- [Wiersz 3] `[TestApp.sln]`

- [Wiersz 4] `SCC_Aux_Path = "\\server\vss\"`

- [Wiersz 5] `SCC_Project_Name = "$/TestApp"`

- [Wiersz 6]

- [Wiersz 7] `[TestApp.csproj]`

- [Wiersz 8] `SCC_Aux_Path = "\\server\vss\"`

- [Wiersz 9] `SCC_Project_Name = "$/TestApp"`

 Pierwszy wiersz zawiera przeznaczenie pliku i służy jako podpis dla wszystkich plików tego typu. Ten wiersz powinien wyglądać dokładnie tak we wszystkich *plikach MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 W poniższej sekcji przedstawiono ustawienia dla każdego pliku oznaczone nazwą pliku w nawiasach kwadratowych. Ta sekcja jest powtarzana dla każdego śledzonego pliku. Ten wiersz jest próbką nazwy pliku, a mianowicie `[TestApp.csproj]` . Ide oczekuje następujących dwóch wierszy. Nie definiuje jednak stylu zdefiniowanych wartości. Zmienne to `SCC_Aux_Path` i `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Nie ma żadnego ogranicznika końcowego do tej sekcji. Nazwa pliku, a także wszystkie literały, które pojawiają się w pliku, są zdefiniowane w pliku nagłówkowym scc.h. Aby uzyskać więcej informacji, zobacz [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
- [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
