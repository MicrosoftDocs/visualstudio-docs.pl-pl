---
title: Przykładowy kod nawigacji (Xaml i C#) debugera | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8f4266bc-4597-43ab-b620-8b08ea988a8e
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88193fc4ec7061771ebba53139cdc0ecce67dbfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552084"
---
# <a name="debugger-navigation-sample-code-xaml-and-c"></a>Debuger przykładowy kod nawigacji (Xaml i C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod w tym temacie jest przykładowy plik dla [nawigowanie po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) tematu.  
  
## <a name="sample-code"></a>Przykładowy kod  
  
```csharp  
public MainPage()  
{  
    InitializeComponent();  
    methodTrack = "Main Page";             
    Example1();  
}  
  
int Example1()  
{  
    int a = 1;  
    methodTrack += "->Example1 ";  
    int x = Example1_A();  
    return a;  
}  
  
int Example1_A()  
{  
    int b = 2;  
    methodTrack += "->Example1_B ";  
    return b;  
}  
  
void Example2()  
{  
    int c = 3;  
    methodTrack += "->Example2 ";  
    int x = Example2_A();  
    int y = Example2_A();  
    int z = Example2_B();  
}  
  
int Example2_A()  
{  
    int c = 3;  
    methodTrack += "->Example2_A ";  
    return c;  
}  
  
int Example2_B()  
{  
    int d = 3;  
    methodTrack += "->Example2_B ";  
    return d;  
}  
  
void Example3()  
{  
    string s = String.Empty;  
    for (int i = 0; i < 1000; i++)  
    {  
        s += i.ToString() + '\n';  
    }  
    methodTrack += "->Example3 ";  
  
}  
  
void Example4()  
{  
    int x = 0;  
    int y = 100;  
    if (x != 0)  
    {  
        x = 1;  
    }  
    double result = y / x;  
    methodTrack = "->Example4";  
}  
  
string methodTrack = String.Empty;  
  
```
