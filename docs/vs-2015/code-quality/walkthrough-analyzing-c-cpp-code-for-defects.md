---
title: 'Przewodnik: Analizowanie kodu C i C++ pod względem wad | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a5e98ee673d232065dd522b0b81a21760306979
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782313"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Wskazówki: analizowanie kodu C++ pod względem wad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak analizować kodu C/C++ pod kątem potencjalnych błędów za pomocą narzędzie do analizy kodu dla kodu C/C++.  
  
 W tym przewodniku krok po kroku przez proces przy użyciu analizy kodu do analizy kodu C/C++ pod kątem potencjalnych błędów.  
  
 Wykonasz następujące czynności:  
  
-   Przeprowadź analizę kodu w kodzie natywnym.  
  
-   Analizuj ostrzeżenia wady kodu.  
  
-   Traktuj ostrzeżenia jako błędy.  
  
-   Dodawanie adnotacji do kodu źródłowego w celu poprawy analizy wady kodu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] lub [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
-   Kopię [próbka Demo](../code-quality/demo-sample.md).  
  
-   Podstawową wiedzę na temat języka C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Aby uruchomić analizę wad kodu w kodzie natywnym  
  
1.  Otwórz rozwiązanie pokaz w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Pokaz rozwiązania teraz wypełnia **Eksploratora rozwiązań**.  
  
2.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Rozwiązanie zostanie skompilowane bez żadnych ostrzeżeń ani błędów.  
  
3.  W **Eksploratora rozwiązań**, wybierz projekt CodeDefects.  
  
4.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Stron właściwości CodeDefects** zostanie wyświetlone okno dialogowe.  
  
5.  Kliknij przycisk **analiza kodu**.  
  
6.  Kliknij przycisk **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru.  
  
7.  Ponownie skompiluj projekt CodeDefects.  
  
     Ostrzeżenia analizy kodu są wyświetlane w **lista błędów**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Aby analizować ostrzeżenia wad kodu  
  
1.  Na **widoku** menu, kliknij przycisk **lista błędów**.  
  
     W zależności od wybranej w ramach profilu dla deweloperów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Niewykluczone, że wskazywał **Windows inne** na **widoku** menu, a następnie kliknij przycisk **lista błędów**.  
  
2.  W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6230: niejawne rzutowanie pomiędzy różnymi semantycznie typami całkowitymi: użycie HRESULT w kontekście Boolean.  
  
     Edytor kodu wyświetla wiersz, który spowodował ostrzeżenie w funkcji `bool``ProcessDomain()`. To ostrzeżenie wskazuje, że wartość HRESULT jest używana w instrukcji "if" gdy oczekiwany jest wynik będący wartością logiczną.  
  
3.  Aby poprawić to ostrzeżenie, użycie makra SUCCEEDED. Kod powinien przypominać następujący kod:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6282: nieprawidłowy operator: przypisanie stałej w kontekście testu. Został == zamierzony?  
  
5.  Testowanie pod kątem równości, aby poprawić to ostrzeżenie. Kod powinien wyglądać podobnie do poniższego kodu:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Aby traktować ostrzeżenia jako błędy  
  
1.  W pliku Bug.cpp, Dodaj następujący kod `#pragma` instrukcji na początku pliku mają być traktowane ostrzeżenie C6001 jako błąd:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Ponownie skompiluj projekt CodeDefects.  
  
     W **lista błędów**, C6001 pojawi się jako błąd.  
  
3.  Popraw błędy C6001 dwóch pozostałych w **lista błędów** przez inicjowanie `i` i `j` na 0.  
  
4.  Ponownie skompiluj projekt CodeDefects.  
  
     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby poprawić ostrzeżenia adnotacji kodu źródłowego w annotation.c  
  
1.  W Eksploratorze rozwiązań wybierz projekt adnotacji.  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Stron właściwości adnotacji** zostanie wyświetlone okno dialogowe.  
  
3.  Kliknij przycisk **analiza kodu**.  
  
4.  Wybierz **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru.  
  
5.  Ponownie skompiluj projekt adnotacji.  
  
6.  W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6011: wyłuskanie wskaźnika NULL "newNode".  
  
     To ostrzeżenie wskazuje niepowodzenie sprawdzić wartość zwrócona przez obiekt wywołujący. W tym przypadku wywołanie **AllocateNode** może zwrócić wartość NULL (zobacz plik nagłówkowy annotations.h deklaracja funkcji AllocateNode).  
  
7.  Otwórz plik annotations.cpp.  
  
8.  Aby poprawić to ostrzeżenie, użyj instrukcji "if" do testowania wartości zwracanej. Kod powinien przypominać następujący kod:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ponownie skompiluj projekt adnotacji.  
  
     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.  
  
### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego  
  
1.  Dodawanie adnotacji do parametrów formalnych i zwraca wartość funkcji `AddTail` przy użyciu warunki wstępne i Post, jak pokazano w poniższym przykładzie:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Ponownie skompiluj projekt adnotacji.  
  
3.  W **lista błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6011: PUSTEGO wskaźnika "node".  
  
     Ostrzeżenie to wskazuje, że węzła przekazanego do funkcji może mieć wartości null i wskazuje numer wiersza, w którym został zgłoszony ostrzeżenia.  
  
4.  Aby poprawić to ostrzeżenie, użyj instrukcji "if" do testowania wartości zwracanej. Kod powinien przypominać następujący kod:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Ponownie skompiluj projekt adnotacji.  
  
     Projekt zostanie skompilowany bez żadnych ostrzeżeń ani błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Analizowanie kodu zarządzanego pod kątem defektów](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



