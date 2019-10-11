---
title: 'Przewodnik: Analizowanie kodu C/C++ pod kątem błędów'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018341"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Przewodnik: Analizowanie kodu C/C++ pod kątem błędów

W tym instruktażu pokazano, jak analizowaćC++ kod c/Code pod kątem potencjalnych wad kodu za pomocą narzędzia do analizyC++ kodu dla języka C/Code.

- Uruchom analizę kodu w kodzie natywnym.
- Analizuj ostrzeżenia wady kodu.
- Traktuj ostrzeżenie jako błąd.
- Adnotuj kod źródłowy, aby poprawić analizę wad kodu.

## <a name="prerequisites"></a>Wymagania wstępne

- Kopia [przykładu demonstracyjnego](../code-quality/demo-sample.md).
- Podstawowe informacje o języku CC++/.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Aby uruchomić analizę wad kodu w kodzie natywnym

1. Otwórz rozwiązanie demonstracyjne w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Rozwiązanie demonstracyjne wypełnia teraz **Eksplorator rozwiązań**.

2. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Rozwiązanie kompiluje się bez błędów lub ostrzeżeń.

3. W **Eksplorator rozwiązań**wybierz projekt CodeDefects.

4. W menu **projekt** kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości CodeDefects** .

5. Kliknij pozycję **Analiza kodu**.

6. Kliknij pole wyboru **Włącz analizę kodu dla CC++ /on Build** .

7. Skompiluj ponownie projekt CodeDefects.

     Ostrzeżenia analizy kodu są wyświetlane w **Lista błędów**.

### <a name="to-analyze-code-defect-warnings"></a>Aby analizować ostrzeżenia defektu kodu

1. W menu **Widok** kliknij **Lista błędów**.

     W zależności od profilu dewelopera wybranego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może zajść potrzeba wskaż **inne okna** w menu **Widok** , a następnie kliknij pozycję **Lista błędów**.

2. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6230: Niejawne rzutowanie między różnymi semantycznie typami: użycie HRESULT w kontekście Boolean.

     W edytorze kodu jest wyświetlana linia, która spowodowała ostrzeżenie w funkcji `bool ProcessDomain()`. To ostrzeżenie wskazuje, że wynik HRESULT jest używany w instrukcji "If", gdzie oczekiwano wyniku logicznego.

3. Popraw to ostrzeżenie przy użyciu pomyślnego makra. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6282: Nieprawidłowy operator: przypisanie do stałej w kontekście testu. Czy = = zamierzony?

5. Popraw to ostrzeżenie, sprawdzając pod kątem równości. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Aby traktować ostrzeżenie jako błąd

1. W pliku usterek. cpp Dodaj następującą instrukcję `#pragma` na początku pliku, aby traktować ostrzeżenie C6001 jako błąd:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Skompiluj ponownie projekt CodeDefects.

     W **Lista błędów**, C6001 teraz pojawia się jako błąd.

3. Popraw pozostałe dwa błędy C6001 w **Lista błędów** , inicjując `i` i `j` do 0.

4. Skompiluj ponownie projekt CodeDefects.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby poprawić ostrzeżenia adnotacji kodu źródłowego w adnotacji. c

1. W Eksplorator rozwiązań wybierz projekt adnotacji.

2. W menu **projekt** kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości adnotacji** .

3. Kliknij pozycję **Analiza kodu**.

4. Zaznacz pole wyboru **Włącz analizę kodu dla CC++ /on Build** .

5. Kompiluj ponownie projekt adnotacji.

6. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6011: Wyłuskanie wskaźnika o wartości NULL "newNode".

     To ostrzeżenie wskazuje, że obiekt wywołujący nie może sprawdzić zwracanej wartości. W takim przypadku wywołanie **AllocateNode** może zwrócić wartość null (zobacz plik nagłówkowy Annotations. h dla deklaracji funkcji dla AllocateNode).

7. Otwórz plik Annotations. cpp.

8. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" do przetestowania wartości zwracanej. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Kompiluj ponownie projekt adnotacji.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego

1. Dodawanie adnotacji do parametrów formalnych i zwracanej wartości funkcji `AddTail` przy użyciu warunków wstępnych i post, jak pokazano w tym przykładzie:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Kompiluj ponownie projekt adnotacji.

3. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6011: Odwołuje się do PUSTEgo wskaźnika "Node".

     To ostrzeżenie wskazuje, że węzeł przekazano do funkcji może mieć wartość null i wskazuje numer wiersza, w którym zostało zgłoszone ostrzeżenie.

4. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" do przetestowania wartości zwracanej. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Kompiluj ponownie projekt adnotacji.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Analizowanie kodu zarządzanego dla wad kodu @ no__t-0 @ no__t-1[Analiza kodu dla C/C++ ](../code-quality/code-analysis-for-c-cpp-overview.md)
