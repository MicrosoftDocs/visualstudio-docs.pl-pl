---
title: Refaktoryzacja usuwania parametrów (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8962dd95aa46ae75a2d214738e7713ae9da42534
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775200"
---
# <a name="remove-parameters-refactoring-c"></a>Refaktoryzacja usuwania parametrów (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` jest operacji refaktoryzacji, która zapewnia łatwy sposób można usunąć parametry z metod, indeksatorów lub delegatów. Usuń zmiany parametrów zgłoszenia; we wszystkich lokalizacjach, w którym element członkowski jest wywoływana parametr zostaną usunięte, aby odzwierciedlić nowe oświadczenie.  
  
 Wykonujesz operację usunięcia parametrów przez pierwszy ustawieniu kursora na metoda, indeksator lub delegata. Gdy kursor znajduje się w stanie wywołać Usuń `Parameters` operacji, kliknij przycisk **Refaktoryzuj** menu, naciśnij klawisz skrótu klawiaturowego lub wybierz polecenie z menu skrótów.  
  
> [!NOTE]
>  Nie można usunąć pierwszy parametr metody rozszerzenia.  
  
### <a name="to-remove-parameters"></a>Aby usunąć parametrów  
  
1.  Utwórz aplikację konsoli o nazwie `RemoveParameters`, a następnie zastąp `Program` następującym kodem.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Umieść kursor w metodzie `A`, albo w deklaracji metody lub wywołania metody.  
  
3.  Z **Refaktoryzuj** menu, wybierz opcję **Usuń parametry** do wyświetlenia **Usuń parametry** okno dialogowe.  
  
     Możesz również wpisać skrótu klawiaturowego CTRL + R, V, aby wyświetlić **Usuń parametry** okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Usuń parametry** do wyświetlenia **Usuń parametry** okno dialogowe.  
  
4.  Za pomocą **parametry** pola, umieść kursor na `int i`, a następnie kliknij przycisk **Usuń**.  
  
5.  Kliknij przycisk **OK**.  
  
6.  W **podgląd zmian — Usuń parametry** okno dialogowe, kliknij przycisk **Zastosuj**.  
  
## <a name="remarks"></a>Uwagi  
 Parametry można usunąć z deklaracji metody lub wywołania metody. Umieść kursor w nazwie metody deklaracji lub delegata i wywoływać Usuń parametry.  
  
> [!CAUTION]
>  Usuń parametry umożliwia możesz usunąć parametr, do którego odwołuje się w treści elementu członkowskiego, ale nie powoduje usunięcia odwołania do tego parametru w treści metody. Może to powodować błędy kompilacji kodu. Można jednak użyć **podgląd zmian** okno dialogowe, aby sprawdzić kod przed wykonaniem operacji refaktoryzacji.  
  
 Jeśli parametr usuwany jest modyfikowana podczas wywołania metody, usunięcie parametru spowoduje również usunięcie modyfikacji. Na przykład jeśli wywołanie metody została zmieniona z  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 na  
  
```csharp  
MyMethod(param2);  
```  
  
 Operacja refaktoryzacji `param1` nie zwiększa się.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)