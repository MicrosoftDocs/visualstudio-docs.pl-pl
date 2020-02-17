---
title: 'Wskazówki: analizowanie kodu C++ pod względem wad'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 74a878b8c64955927357e45c668c4d100007d373
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271812"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Wskazówki: analizowanie kodu C++ pod względem wad

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

2. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.

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

     W zależności od profilu dewelopera wybranego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], może być konieczne wskazanie **innych okien** w menu **Widok** , a następnie kliknięcie przycisku **Lista błędów**.

2. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6230: niejawne rzutowanie między różnymi semantycznie typami: użycie HRESULT w kontekście Boolean.

     W edytorze kodu jest wyświetlany wiersz, który spowodował ostrzeżenie w `bool ProcessDomain()`funkcji. To ostrzeżenie wskazuje, że `HRESULT` jest używana w instrukcji "If", gdzie oczekiwano wyniku logicznego.  Zwykle jest to błąd, ponieważ w przypadku zwrócenia `S_OK` HRESULT z funkcji IT wskazuje powodzenie, ale po przekonwertowaniu na wartość logiczną, która ma być `false`.

3. Popraw to ostrzeżenie przy użyciu makra `SUCCEEDED`, które jest konwertowane na `true`, gdy wartość zwracana `HRESULT` wskazuje na powodzenie. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Warning C6282: nieprawidłowy operator: przypisanie do stałej w kontekście testu. Czy = = zamierzony?

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

3. Popraw pozostałe dwa błędy C6001 w **Lista błędów** przez zainicjowanie `i` i `j` na 0.

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

     Ostrzeżenie C6011: wyłuskanie wskaźnika o wartości NULL "newNode".

     To ostrzeżenie wskazuje, że obiekt wywołujący nie może sprawdzić zwracanej wartości. W takim przypadku wywołanie **AllocateNode** może zwrócić wartość null (zobacz plik nagłówkowy Annotations. h dla deklaracji funkcji dla AllocateNode).

7. Otwórz plik Annotations. cpp.

8. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" do przetestowania wartości zwracanej. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

9. Kompiluj ponownie projekt adnotacji.

     Projekt kompiluje się bez żadnych ostrzeżeń lub błędów.

### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego

1. Adnotuj parametry formalne i wartość zwracaną funkcji `AddTail`, aby wskazać, że wartości wskaźnika mogą mieć wartość null:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

2. Kompiluj ponownie projekt adnotacji.

3. W **Lista błędów**kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6011: wyłuskanie "Node" wskaźnika o wartości NULL.

     To ostrzeżenie wskazuje, że węzeł przekazano do funkcji może mieć wartość null i wskazuje numer wiersza, w którym zostało zgłoszone ostrzeżenie.

4. Aby poprawić to ostrzeżenie, należy użyć instrukcji "If" na początku funkcji, aby przetestować przekazaną wartość. Kod powinien wyglądać podobnie do następującego kodu:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

5. Kompiluj ponownie projekt adnotacji.

     Projekt teraz kompiluje się bez żadnych ostrzeżeń lub błędów.

## <a name="see-also"></a>Zobacz też

[Przewodnik: Analizowanie kodu zarządzanego pod kątem wad kodu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[analizy kodu dla językaC++ C/](../code-quality/code-analysis-for-c-cpp-overview.md)
