---
title: 'Szybki Start: Analiza kodu C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 00dedc25185dfc3a9f12ba645205ce47925003df
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825204"
---
# <a name="quickstart-code-analysis-for-cc"></a>Szybki start: Analiza kodu C/C++

Aby poprawić jakość aplikacji, należy regularnie uruchamiania analizy kodu dla kodu C lub C++. To może pomóc w znalezieniu typowe problemy, naruszeń dobrą praktyką programowania lub usterki, które są trudne do odnajdywania za pomocą testowania. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ analiza kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurowanie zestawów reguł dla projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy projektu, a następnie wybierz **właściwości**.

2. Poniższe kroki są opcjonalne:

    1. W **konfiguracji** i **platformy** listy, wybierz platformę kompilacji konfiguracji i docelowej.

    2. Domyślnie program analizy kodu nie raportuje ostrzeżenia z kodu, który jest generowany automatycznie przez narzędzia zewnętrzne. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, należy wyczyścić **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

        > [!NOTE]
        > Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można wyświetlać lub zachować kod źródłowy dla formularza lub szablonu.

3. Aby uruchomić analizę kodu, za każdym razem, gdy projekt jest kompilowany przy użyciu wybranej konfiguracji, zaznacz **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru. Można również uruchomić analizę kodu ręcznie, otwierając **analizy** menu, a następnie wybierając **Uruchom analizę kodu dla** *ProjectName*.

4. W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który chcesz użyć.

    - Wybierz  **\<Przeglądaj … >** do określenia, ustaw istniejącej reguły niestandardowe, który nie jest na liście.

    - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Standard języka C/C++ zestawy reguł

Program Visual Studio zawiera dwa standardowe zestawy reguł dla kodu natywnego:

|Zestaw reguł|Opis|
|--------------|-----------------|
|Zalecane reguły kodu natywnego firmy Microsoft, co najmniej|Ten zestaw reguł koncentruje się na najważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|Zalecane reguły kodu natywnego firmy Microsoft|Ten zestaw reguł obejmuje szerokiej gamy problemów. Zawiera ono wszystkie reguły w Microsoft Native Minimum reguł zalecanych.|

## <a name="run-code-analysis"></a>Przeprowadź analizę kodu

Na stronie analizy kodu na stronach właściwości projektu można skonfigurować analizy kodu do uruchomienia każdorazowo kompilacji projektu. Można również uruchamiać analizę kodu ręcznie.

Aby uruchomić analizę kodu na rozwiązanie:

- Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla rozwiązania**.

Aby uruchomić analizę kodu w projekcie:

1. W Eksploratorze rozwiązań wybierz nazwę projektu.

2. Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla** *Nazwa projektu*.

   Projektu lub rozwiązania jest kompilowana i uruchamia analizy kodu. Wyniki są wyświetlane na liście błędów.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizowanie i rozwiązywanie ostrzeżenia analizy kodu

Aby analizować szczególne ostrzeżenie, wybierz tytuł ostrzeżenia na liście błędów. Ostrzeżenie rozwija, aby wyświetlić dodatkowe informacje o problemie. Jeśli to możliwe, analizy kodu wyświetla numery wierszy i logika analizy, które doprowadziło do ostrzeżenia. Aby uzyskać szczegółowe informacje na temat ostrzeżenia, w tym możliwe rozwiązania problemu należy wybrać identyfikator ostrzeżenia, aby wyświetlić jego odpowiedniego tematu Pomocy online.

Po wybraniu ostrzeżenie, wiersz kodu, który spowodował ostrzeżenie jest wyróżniony w edytorze kodu programu Visual Studio.

Po zrozumieniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlany na liście błędów, a rozwiązanie problemu nie został zgłoszony wszelkie nowe ostrzeżenia.

## <a name="suppress-code-analysis-warnings"></a>Pomijanie ostrzeżeń analizy kodu

Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Poszczególne ostrzeżenia można pominąć, tak aby nie były widoczne na liście błędów.

Aby pominąć Ostrzeżenie:

1. Jeśli nie są wyświetlane szczegółowe informacje, wybierz tytuł ostrzeżenie, aby ją rozwinąć.

2. Wybierz **akcje** widocznego u dołu ostrzeżenia.

3. Wybierz **Pomiń komunikat** , a następnie wybierz **w źródłowej**.

   Pomijanie wiadomości wstawia `#pragma warning (disable:[warning ID])` który umożliwia pominięcie ostrzeżenia dla wiersza kodu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Utwórz elementy robocze dla kodu ostrzeżenia analizy

Element roboczy, funkcja śledzenia umożliwia rejestrowanie błędów z poziomu programu Visual Studio. Aby użyć tej funkcji, należy połączyć się z wystąpieniem programu Team Foundation Server.

**Aby utworzyć element roboczy dla co najmniej jedno ostrzeżenie kodu C/C++**

1. Na liście błędów Rozwiń i wybierz ostrzeżenia

2. W menu skrótów dla ostrzeżenia wybierz **Utwórz element pracy**, a następnie wybierz typ elementu roboczego.

3. Program Visual Studio tworzy pojedynczym elemencie roboczym dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu w IDE.

4. Dodaj wszelkie dodatkowe informacje, a następnie wybierz **Zapisz element roboczy**.

## <a name="search-and-filter-code-analysis-results"></a>Wyszukiwanie i filtrowanie wyników analizy kodu

Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.

- **Aby ostrzeżeń filtru według tytułu lub identyfikator ostrzeżenia**: Wprowadź słowo kluczowe w polu wyszukiwania.

- **Aby ostrzeżeń filtru według ważności**: Domyślnie komunikaty analizy kodu są przypisywane ważność **ostrzeżenie**. Możesz przypisać wagi co najmniej jedna wiadomość jako **błąd** w zestawie reguł niestandardowych. Na **ważność** kolumny **lista błędów**, wybierz strzałkę listy rozwijanej, a następnie ikonę filtru. Wybierz **ostrzeżenie** lub **błąd** do wyświetlenia tylko komunikaty, które są przypisane do odpowiednich ważności. Wybierz **Zaznacz wszystko** Aby wyświetlić wszystkie komunikaty.

## <a name="see-also"></a>Zobacz także

[Analiza kodu C/c++](../code-quality/code-analysis-for-c-cpp-overview.md)