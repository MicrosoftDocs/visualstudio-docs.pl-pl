---
title: Przykładowy C++ projekt na potrzeby analizy kodu
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: a7e06b29b4778bf2a9b1b327d015bb7eb12e8ec5
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271282"
---
# <a name="sample-c-project-for-code-analysis"></a>Przykładowy C++ projekt na potrzeby analizy kodu

W poniższych procedurach przedstawiono sposób tworzenia przykładu dla [przewodnika: Analizowanie kodu CC++ /Code pod kątem wad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Procedury tworzą:

- A [! INCLUDEvsprvs] rozwiązanie o nazwie CppDemo.

- Projekt biblioteki statycznej o nazwie CodeDefects.

- Projekt biblioteki statycznej o nazwie adnotacje.

Procedury te zawierają również kod dla plików nagłówkowych i *. cpp* dla bibliotek statycznych.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Tworzenie rozwiązania CppDemo i projektu CodeDefects

1. Otwórz [! INCLUDEvsprvs] i wybierz pozycję **Utwórz nowy projekt**

2. Zmień filtr języka na**C++**

3. Wybierz pozycję **pusty projekt** i kliknij przycisk **dalej** .

4. W polu tekstowym **Nazwa projektu** wpisz **CodeDefects**

5. W polu tekstowym **Nazwa rozwiązania** wpisz **CppDemo**

6. Kliknij przycisk **Utwórz**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurowanie projektu CodeDefects jako biblioteki statycznej

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **CodeDefects** , a następnie kliknij pozycję **Właściwości**.

2. Rozwiń węzeł **Właściwości konfiguracji** , a następnie kliknij pozycję **Ogólne**.

3. Na liście **Ogólne** Zmień **Typ konfiguracji**na **Biblioteka statyczna (. lib)** .

4. Na liście **Zaawansowane** Zmień **rozszerzenie pliku docelowego** na **. lib**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Dodaj nagłówek i plik źródłowy do projektu CodeDefects

1. W Eksplorator rozwiązań rozwiń węzeł **CodeDefects**, kliknij prawym przyciskiem myszy pozycję **pliki nagłówkowe**, kliknij pozycję **Dodaj**, a następnie kliknij pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kod**, a następnie kliknij pozycję **plik nagłówka (. h)** .

3. W polu **Nazwa** wpisz **błąd. h** , a następnie kliknij przycisk **Dodaj**.

4. Skopiuj poniższy kod i wklej go do pliku *usterek. h* w edytorze.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **pliki źródłowe**, wskaż polecenie **Nowy**, a następnie kliknij pozycję **nowy element**.

6. W oknie dialogowym **Dodaj nowy element** kliknij pozycję  **C++ plik (. cpp).**

7. W polu **Nazwa** wpisz **usterkę. cpp** , a następnie kliknij przycisk **Dodaj**.

8. Skopiuj poniższy kod i wklej go do pliku *usterek. cpp* w edytorze.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

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
    return i + j;
}
```

9. Kliknij menu **plik** , a następnie kliknij polecenie **Zapisz wszystko**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Dodaj projekt adnotacji i skonfiguruj go jako bibliotekę statyczną

1. W Eksplorator rozwiązań kliknij pozycję **CppDemo**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Dodawanie nowego projektu** Zmień filtr języka na **C++** i wybierz pozycję **pusty projekt** , a następnie kliknij przycisk **dalej**.

3. W polu tekstowym **Nazwa projektu** wpisz **Adnotacje**, a następnie kliknij przycisk **Utwórz**.

4. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **Adnotacje** , a następnie kliknij polecenie **Właściwości**.

5. Rozwiń węzeł **Właściwości konfiguracji** , a następnie kliknij pozycję **Ogólne**.

6. Na liście **Ogólne** Zmień **Typ konfiguracji**na, a następnie kliknij pozycję **Biblioteka statyczna (. lib)** .

7. Na liście **Zaawansowane** zaznacz tekst w kolumnie obok **rozszerzenia pliku docelowego**, a następnie wpisz **. lib**.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Dodaj plik nagłówka i plik źródłowy do projektu adnotacji

1. W Eksplorator rozwiązań rozwiń pozycję **Adnotacje**, kliknij prawym przyciskiem myszy pozycję **pliki nagłówkowe**, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **plik nagłówka (. h)** .

3. W polu **Nazwa** wpisz **Adnotacje. h** , a następnie kliknij przycisk **Dodaj**.

4. Skopiuj poniższy kod i wklej go do pliku *Annotations. h* w edytorze.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **pliki źródłowe**, wskaż polecenie **Nowy**, a następnie kliknij pozycję **nowy element**.

6. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kod** , a następnie kliknij pozycję  **C++ plik (. cpp).**

7. W polu **Nazwa** wpisz **Adnotacje. cpp** , a następnie kliknij przycisk **Dodaj**.

8. Skopiuj poniższy kod i wklej go do pliku *Annotation. cpp* w edytorze.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. Kliknij menu **plik** , a następnie kliknij polecenie **Zapisz wszystko**.


Rozwiązanie jest teraz ukończone i powinno zostać skompilowane bez błędów.
