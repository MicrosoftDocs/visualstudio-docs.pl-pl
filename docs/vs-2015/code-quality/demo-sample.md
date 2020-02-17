---
title: Przykład demonstracyjny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277882"
---
# <a name="demo-sample"></a>Przykład
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W poniższych procedurach pokazano, jak utworzyć przykład dla [przewodnika: Analizowanie kodu CC++ /Code dla wad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Procedury tworzą:  
  
- Rozwiązanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o nazwie CppDemo.  
  
- Projekt biblioteki statycznej o nazwie CodeDefects.  
  
- Projekt biblioteki statycznej o nazwie adnotacje.  
  
  Procedury te zawierają również kod dla plików nagłówkowych i. cpp dla bibliotek statycznych.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Tworzenie rozwiązania CppDemo i projektu CodeDefects  
  
1. Kliknij menu **plik** , wskaż polecenie **Nowy**, a następnie kliknij pozycję **Nowy projekt**.  
  
2. Na liście drzewo **typów projektu** , jeśli Wizualizacja C++ nie jest domyślnym językiem programu vs rozwiń **inne języki**.  
  
3. Rozwiń **węzeł C++Wizualizacja** , a następnie kliknij pozycję **Ogólne**.  
  
4. W obszarze **Szablony**kliknij pozycję **pusty projekt**.  
  
5. W polu tekstowym **Nazwa** wpisz **CodeDefects**.  
  
6. Zaznacz pole wyboru **Utwórz katalog dla rozwiązania** .  
  
7. W polu tekstowym **Nazwa rozwiązania** wpisz **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurowanie projektu CodeDefects jako biblioteki statycznej  
  
1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **CodeDefects** , a następnie kliknij pozycję **Właściwości**.  
  
2. Rozwiń węzeł **Właściwości konfiguracji** , a następnie kliknij pozycję **Ogólne**.  
  
3. Na liście **Ogólne** zaznacz tekst w kolumnie obok **rozszerzenia docelowego**, a następnie wpisz **. lib**.  
  
4. W obszarze **Ustawienia domyślne projektu**kliknij kolumnę obok pozycji **Typ konfiguracji**, a następnie kliknij pozycję **statyczna biblioteka (. lib)** .  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Dodaj nagłówek i plik źródłowy do projektu CodeDefects  
  
1. W Eksplorator rozwiązań rozwiń węzeł **CodeDefects**, kliknij prawym przyciskiem myszy pozycję **pliki nagłówkowe**, kliknij pozycję **Dodaj**, a następnie kliknij pozycję **nowy element**.  
  
2. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kod**, a następnie kliknij pozycję **plik nagłówka (. h)** .  
  
3. W polu **Nazwa** wpisz **usterkę. cpp** , a następnie kliknij przycisk **Dodaj**.  
  
4. Skopiuj następujący kod i wklej go do pliku **usterek. cpp** w edytorze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **pliki źródłowe**, wskaż polecenie **Nowy**, a następnie kliknij pozycję **nowy element**.  
  
6. W oknie dialogowym **Dodaj nowy element** kliknij pozycję  **C++ plik (. cpp).**  
  
7. W polu **Nazwa** wpisz **usterkę. cpp** , a następnie kliknij przycisk **Dodaj**.  
  
8. Skopiuj następujący kod i wklej go do pliku usterek. h w edytorze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Kliknij menu **plik** , a następnie kliknij polecenie **Zapisz wszystko**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Dodaj projekt adnotacji i skonfiguruj go jako bibliotekę statyczną  
  
1. W Eksplorator rozwiązań kliknij pozycję **CppDemo**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.  
  
2. W oknie dialogowym **Dodaj nowy projekt** rozwiń pozycję Wizualizacja C++, kliknij pozycję **Ogólne**, a następnie kliknij pozycję **pusty projekt**.  
  
3. W polu tekstowym **Nazwa** wpisz **Adnotacje**, a następnie kliknij przycisk **Dodaj**.  
  
4. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **Adnotacje** , a następnie kliknij polecenie **Właściwości**.  
  
5. Rozwiń węzeł **Właściwości konfiguracji** , a następnie kliknij pozycję **Ogólne**.  
  
6. Na liście **Ogólne** zaznacz tekst w kolumnie obok **rozszerzenia docelowego**, a następnie wpisz **. lib**.  
  
7. W obszarze **Ustawienia domyślne projektu**kliknij kolumnę obok pozycji **Typ konfiguracji**, a następnie kliknij pozycję **statyczna biblioteka (. lib)** .  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Dodaj plik nagłówka i plik źródłowy do projektu adnotacji  
  
1. W Eksplorator rozwiązań rozwiń pozycję **Adnotacje**, kliknij prawym przyciskiem myszy pozycję **pliki nagłówkowe**, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.  
  
2. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **plik nagłówka (. h)** .  
  
3. W polu **Nazwa** wpisz **Adnotacje. h** , a następnie kliknij przycisk **Dodaj**.  
  
4. Skopiuj poniższy kod i wklej go do pliku **Annotations. h** w edytorze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **pliki źródłowe**, wskaż polecenie **Nowy**, a następnie kliknij pozycję **nowy element**.  
  
6. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kod** , a następnie kliknij pozycję  **C++ plik (. cpp).**  
  
7. W polu **Nazwa** wpisz **Adnotacje. cpp** , a następnie kliknij przycisk **Dodaj**.  
  
8. Skopiuj poniższy kod i wklej go do pliku **Annotation. cpp** w edytorze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Kliknij menu **plik** , a następnie kliknij polecenie **Zapisz wszystko**.
