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
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: acfa1e274b7c0744c2d9968682960b1cd50e0044
ms.sourcegitcommit: 2dc924c96a6d48803c8eedc3d6781202629b41fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57736928"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Przewodnik: Analizowanie kodu C/C++ pod kątem błędów

W tym instruktażu pokazano, jak analizować kodu C/C++ pod kątem potencjalnych błędów za pomocą narzędzie do analizy kodu dla kodu C/C++.

- Przeprowadź analizę kodu w kodzie natywnym.
- Analizuj ostrzeżenia wady kodu.
- Traktuj ostrzeżenia jako błędy.
- Dodawanie adnotacji do kodu źródłowego w celu poprawy analizy wady kodu.

## <a name="prerequisites"></a>Wymagania wstępne

- Kopię [próbka Demo](../code-quality/demo-sample.md).
- Podstawową wiedzę na temat języka C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Aby uruchomić analizę wad kodu w kodzie natywnym

1. Otwórz rozwiązanie pokaz w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Pokaz rozwiązania teraz wypełnia **Eksploratora rozwiązań**.

2. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Rozwiązanie zostanie skompilowane bez żadnych ostrzeżeń ani błędów.

3. W **Eksploratora rozwiązań**, wybierz projekt CodeDefects.

4. Na **projektu** menu, kliknij przycisk **właściwości**.

     **Stron właściwości CodeDefects** zostanie wyświetlone okno dialogowe.

5. Kliknij przycisk **analiza kodu**.

6. Kliknij przycisk **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru.

7. Ponownie skompiluj projekt CodeDefects.

     Ostrzeżenia analizy kodu są wyświetlane w **lista błędów**.

### <a name="to-analyze-code-defect-warnings"></a>Aby analizować ostrzeżenia wad kodu

1. Na **widoku** menu, kliknij przycisk **lista błędów**.

     W zależności od wybranej w ramach profilu dla deweloperów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Niewykluczone, że wskazywał **Windows inne** na **widoku** menu, a następnie kliknij przycisk **lista błędów**.

2. W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6230: Niejawne rzutowanie pomiędzy różnymi semantycznie typami całkowitymi: użycie HRESULT w kontekście Boolean.

     Edytor kodu wyświetla wiersz, który spowodował ostrzeżenie w funkcji `bool ProcessDomain()`. To ostrzeżenie wskazuje, że wartość HRESULT jest używana w instrukcji "if" gdy oczekiwany jest wynik będący wartością logiczną.

3. Aby poprawić to ostrzeżenie, użycie makra SUCCEEDED. Kod powinien przypominać następujący kod:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6282: Niepoprawny operator: przypisanie stałej w kontekście testu. Został == zamierzony?

5. Testowanie pod kątem równości, aby poprawić to ostrzeżenie. Kod powinien wyglądać podobnie do poniższego kodu:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Aby traktować ostrzeżenia jako błędy

1. W pliku Bug.cpp, Dodaj następujący kod `#pragma` instrukcji na początku pliku mają być traktowane ostrzeżenie C6001 jako błąd:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Ponownie skompiluj projekt CodeDefects.

     W **lista błędów**, C6001 pojawi się jako błąd.

3. Popraw błędy C6001 dwóch pozostałych w **lista błędów** przez inicjowanie `i` i `j` na 0.

4. Ponownie skompiluj projekt CodeDefects.

     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby poprawić ostrzeżenia adnotacji kodu źródłowego w annotation.c

1. W Eksploratorze rozwiązań wybierz projekt adnotacji.

2. Na **projektu** menu, kliknij przycisk **właściwości**.

     **Stron właściwości adnotacji** zostanie wyświetlone okno dialogowe.

3. Kliknij przycisk **analiza kodu**.

4. Wybierz **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru.

5. Ponownie skompiluj projekt adnotacji.

6. W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6011: Wyłuskanie wskaźnika NULL "newNode".

     To ostrzeżenie wskazuje niepowodzenie sprawdzić wartość zwrócona przez obiekt wywołujący. W tym przypadku wywołanie **AllocateNode** może zwrócić wartość NULL (zobacz plik nagłówkowy annotations.h deklaracja funkcji AllocateNode).

7. Otwórz plik annotations.cpp.

8. Aby poprawić to ostrzeżenie, użyj instrukcji "if" do testowania wartości zwracanej. Kod powinien przypominać następujący kod:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Ponownie skompiluj projekt adnotacji.

     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.

### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego

1. Dodawanie adnotacji do parametrów formalnych i zwraca wartość funkcji `AddTail` przy użyciu warunki wstępne i Post, jak pokazano w poniższym przykładzie:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Ponownie skompiluj projekt adnotacji.

3. W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:

     Ostrzeżenie C6011: Wyłuskanie wskaźnika NULL "node".

     Ostrzeżenie to wskazuje, że węzła przekazanego do funkcji może mieć wartości null i wskazuje numer wiersza, w którym został zgłoszony ostrzeżenia.

4. Aby poprawić to ostrzeżenie, użyj instrukcji "if" do testowania wartości zwracanej. Kod powinien przypominać następujący kod:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Ponownie skompiluj projekt adnotacji.

     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Analizowanie kodu zarządzanego pod względem wad kodu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[analiza kodu C/c++](../code-quality/code-analysis-for-c-cpp-overview.md)
