---
title: 'Szybki start: analiza kodu C/C++'
description: Uruchom analizę statyczną C++ w kodzie w programie Visual Studio, aby wykrywać typowe problemy z kodowaniem i wady.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 4beaff14e896eae15d4ce68acf35331d03203246
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445633"
---
# <a name="quickstart-code-analysis-for-cc"></a>Szybki start: analiza kodu C/C++

Jakość aplikacji można poprawić, uruchamiając analizę kodu regularnie w języku C lub C++ kodzie. Może to pomóc w znalezieniu typowych problemów, naruszeniu dobrych rozwiązań programistycznych lub wad, które trudno wykryć poprzez testowanie. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń kompilatora, ponieważ analiza kodu wyszukuje określone wzorce kodu, które są prawidłowe, ale mogą nadal tworzyć problemy dla Ciebie lub innych osób korzystających z Twojego kodu.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurowanie zestawów reguł dla projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla nazwy projektu, a następnie wybierz polecenie **Właściwości**.

2. Opcjonalnie na listach **Konfiguracja** i **platforma** wybierz konfigurację kompilacji i platformę docelową.

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt zostanie skompilowany przy użyciu wybranej konfiguracji, zaznacz pole wyboru **Włącz analizę kodu podczas kompilacji** . Możesz również ręcznie uruchomić analizę kodu, otwierając menu **Analizuj** , a następnie wybierając polecenie **Uruchom analizę kodu na** *ProjectName* lub **uruchomić analizę kodu dla pliku**.

4. Wybierz [zestaw reguł](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md) , którego chcesz użyć, lub Utwórz [niestandardowy zestaw reguł](../code-quality/how-to-create-a-custom-rule-set.md). Jeśli używasz LLVM/Clang-CL, zobacz [using Clang-uporządkowanego in Visual Studio](../code-quality/clang-tidy.md) , aby skonfigurować opcje analizy Clang-uporządkowanego.

### <a name="standard-cc-rule-sets"></a>Standardowe C/C++ zestawy reguł

Program Visual Studio zawiera dwa standardowe zestawy reguł dla kodu natywnego:

|Zestaw reguł|Opis|
|--------------|-----------------|
|Minimalne zalecane reguły natywne firmy Microsoft|Ten zestaw reguł dotyczy najważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|Zalecane reguły natywne firmy Microsoft|Ten zestaw reguł obejmuje szeroki zakres problemów. Zawiera wszystkie reguły w minimalnych zalecanych regułach firmy Microsoft w języku macierzystym.|

## <a name="run-code-analysis"></a>Uruchom analizę kodu

Na stronie Analiza kodu na stronie właściwości projektu można skonfigurować analizę kodu, która będzie uruchamiana za każdym razem, gdy kompilujesz projekt. Możesz również ręcznie uruchomić analizę kodu.

Aby uruchomić analizę kodu w rozwiązaniu:

- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.

Aby uruchomić analizę kodu w projekcie:

1. W Eksplorator rozwiązań wybierz nazwę projektu.

2. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu dla** *nazwy projektu*.

Aby uruchomić analizę kodu dla pliku:

1. W Eksplorator rozwiązań wybierz nazwę pliku.

2. W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu dla pliku** lub naciśnij **klawisze Ctrl + Shift + Alt + F7**.

   Projekt lub rozwiązanie zostały skompilowane i zostanie uruchomiona Analiza kodu. Wyniki pojawiają się w Lista błędów.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu

Aby przeanalizować określone ostrzeżenie, wybierz tytuł ostrzeżenia w Lista błędów. Ostrzeżenie zostanie rozwinięte, aby wyświetlić dodatkowe informacje o problemie. Gdy jest to możliwe, analiza kodu wyświetla numery wierszy i logikę analizy, które doprowadziły do ostrzeżenia. Aby uzyskać szczegółowe informacje o ostrzeżeniu, w tym o możliwych rozwiązaniach problemu, wybierz identyfikator ostrzeżenia, aby wyświetlić odpowiedni temat pomocy online.

Po wybraniu ostrzeżenia wiersz kodu, który spowodował ostrzeżenie, jest wyróżniony w edytorze kodu programu Visual Studio.

Po zrozumieniu problemu można go rozwiązać w kodzie. Następnie ponownie uruchom analizę kodu, aby upewnić się, że ostrzeżenie nie pojawia się już w Lista błędów i że poprawka nie zgłosiła żadnych nowych ostrzeżeń.

## <a name="suppress-code-analysis-warnings"></a>Pomiń ostrzeżenia analizy kodu

Istnieją przypadki, w których można zrezygnować z naprawienia ostrzeżenia analizy kodu. Użytkownik może zdecydować, że rozwiązanie tego problemu wymaga zbyt dużo ponownego kodowania w odniesieniu do prawdopodobieństwa, że problem będzie występował w jakiejkolwiek rzeczywistej implementacji kodu. Można też zastanowić się, że analiza, która jest używana w ostrzeżeniu, jest nieodpowiedni dla danego kontekstu. Możesz pominąć poszczególne ostrzeżenia, aby nie były wyświetlane w Lista błędów.

Aby pominąć ostrzeżenie:

1. Jeśli szczegółowe informacje nie są wyświetlane, wybierz tytuł ostrzeżenia, aby go rozwinąć.

2. Wybierz łącze **Akcje** u dołu ostrzeżenia.

3. Wybierz pozycję **Pomiń komunikat** , a następnie wybierz pozycję **w polu Źródło**.

   Pomijanie komunikatu powoduje wstawienie `#pragma warning (disable:[warning ID])`, które pomija Ostrzeżenie dla wiersza kodu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Utwórz elementy robocze dla ostrzeżeń analizy kodu

Za pomocą funkcji śledzenia elementów roboczych można rejestrować usterki w programie Visual Studio. Aby użyć tej funkcji, należy nawiązać połączenie z wystąpieniem Team Foundation Server.

**Aby utworzyć element roboczy dla co najmniej jednego ostrzeżenia C/C++ Code**

1. W Lista błędów rozwiń i wybierz ostrzeżenia

2. W menu skrótów dla ostrzeżeń wybierz polecenie **Utwórz element roboczy**, a następnie wybierz typ elementu pracy.

3. Program Visual Studio tworzy pojedynczy element roboczy dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu IDE.

4. Dodaj wszelkie dodatkowe informacje, a następnie wybierz pozycję **Zapisz element roboczy**.

## <a name="search-and-filter-code-analysis-results"></a>Wyszukiwanie i filtrowanie wyników analizy kodu

Można wyszukiwać długie listy komunikatów ostrzegawczych i filtrować ostrzeżenia w rozwiązaniach w ramach projektu.

- **Aby filtrować ostrzeżenia według tytułu lub identyfikatora ostrzeżenia**: Wprowadź słowo kluczowe w polu wyszukiwania.

- **Aby filtrować ostrzeżenia według ważności**: domyślnie komunikaty analizy kodu są przypisywane ważności **ostrzeżenia**. Można przypisać ważność co najmniej jednego komunikatu jako **błąd** w niestandardowym zestawie reguł. W kolumnie **ważność** **Lista błędów**wybierz strzałkę listy rozwijanej, a następnie ikonę filtru. Wybierz **Ostrzeżenie** lub **błąd** , aby wyświetlić tylko te komunikaty, do których przypisano odpowiednią ważność. Wybierz **pozycję Zaznacz wszystko** , aby wyświetlić wszystkie komunikaty.

## <a name="see-also"></a>Zobacz także

- [Analiza kodu dla języka C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
