---
title: Pokaz przykładowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 9e85944e93b952b8239015761e8fb364cb265291
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201434"
---
# <a name="demo-sample"></a>Przykład
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten poniższe procedury pokazują, jak utworzyć przykład dla [instruktażu: Analizowanie kodu C/C++ pod względem wad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Utwórz procedury:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania o nazwie CppDemo.  
  
- Projekt biblioteki statycznej o nazwie CodeDefects.  
  
- Projekt biblioteki statycznej o nazwie adnotacji.  
  
  Procedury również podać kod dla plików nagłówka, jak i .cpp bibliotek statycznych.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Tworzenie rozwiązania CppDemo i projektu CodeDefects  
  
1. Kliknij przycisk **pliku** menu wskaż **New**, a następnie kliknij przycisk **nowy projekt**.  
  
2. W **typów projektów** listy drzewa, jeśli program Visual C++ nie jest językiem domyślnym w programie VS rozwiń **inne języki**.  
  
3. Rozwiń **Visual C++** , a następnie kliknij przycisk **ogólne**.  
  
4. W **szablony**, kliknij przycisk **pusty projekt**.  
  
5. W **nazwa** polu tekstowym **CodeDefects**.  
  
6. Wybierz **Utwórz katalog rozwiązania** pole wyboru.  
  
7. W **Nazwa rozwiązania** polu tekstowym **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurowanie projektu CodeDefects jako biblioteka statyczna  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **CodeDefects** a następnie kliknij przycisk **właściwości**.  
  
2. Rozwiń **właściwości konfiguracji** a następnie kliknij przycisk **ogólne**.  
  
3. W **ogólne** listy, zaznacz tekst w kolumnie obok **rozszerzenie docelowe**, a następnie wpisz **.lib**.  
  
4. W **domyślne wartości projektu**, kliknij kolumnę **typu konfiguracji**, a następnie kliknij przycisk **biblioteki statycznej (lib)** .  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Dodawanie pliku nagłówka i źródła do projektu CodeDefects  
  
1. W Eksploratorze rozwiązań rozwiń **CodeDefects**, kliknij prawym przyciskiem myszy **pliki nagłówkowe**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kodu**, a następnie kliknij przycisk **plik nagłówka (.h)** .  
  
3. W **nazwa** wpisz **Bug.cpp** a następnie kliknij przycisk **Dodaj**.  
  
4. Skopiuj poniższy kod i wklej go w **Bug.cpp** w pliku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
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
  
5. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki źródłowe**, wskaż polecenie **New**, a następnie kliknij przycisk **nowy element**.  
  
6. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **plik C++ (.cpp)**  
  
7. W **nazwa** wpisz **Bug.cpp** a następnie kliknij przycisk **Dodaj**.  
  
8. Skopiuj poniższy kod i wkleić go do pliku Bug.h w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
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
  
9. Kliknij przycisk **pliku** menu, a następnie kliknij przycisk **Zapisz wszystko**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Dodaj projekt adnotacje i skonfiguruje je jako biblioteki statycznej  
  
1. W Eksploratorze rozwiązań kliknij **CppDemo**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2. W **Dodaj nowy projekt** okna dialogowego rozwiń Visual C++, kliknij przycisk **ogólne**, a następnie kliknij przycisk **pusty projekt**.  
  
3. W **nazwa** polu tekstowym **adnotacje**, a następnie kliknij przycisk **Dodaj**.  
  
4. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **adnotacje** a następnie kliknij przycisk **właściwości**.  
  
5. Rozwiń **właściwości konfiguracji** a następnie kliknij przycisk **ogólne**.  
  
6. W **ogólne** listy, zaznacz tekst w kolumnie obok **rozszerzenie docelowe**, a następnie wpisz **.lib**.  
  
7. W **domyślne wartości projektu**, kliknij kolumnę **typu konfiguracji**, a następnie kliknij przycisk **biblioteki statycznej (lib)** .  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Dodaj plik nagłówkowy i plik źródłowy do projektu adnotacji  
  
1. W Eksploratorze rozwiązań rozwiń **adnotacje**, kliknij prawym przyciskiem myszy **pliki nagłówkowe**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **plik nagłówka (.h)** .  
  
3. W **nazwa** wpisz **annotations.h** a następnie kliknij przycisk **Dodaj**.  
  
4. Skopiuj poniższy kod i wklej go w **annotations.h** w pliku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
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
  
5. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki źródłowe**, wskaż polecenie **New**, a następnie kliknij przycisk **nowy element**.  
  
6. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kodu** a następnie kliknij przycisk **plik C++ (.cpp)**  
  
7. W **nazwa** wpisz **annotations.cpp** a następnie kliknij przycisk **Dodaj**.  
  
8. Skopiuj poniższy kod i wklej go w **annotations.cpp** w pliku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
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
  
9. Kliknij przycisk **pliku** menu, a następnie kliknij przycisk **Zapisz wszystko**.
