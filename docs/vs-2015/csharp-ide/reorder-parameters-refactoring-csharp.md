---
title: Zmień kolejność parametrów Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9bec38846f7703ff3958aa1c0fcc9a660a5e080d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784133"
---
# <a name="reorder-parameters-refactoring-c"></a>Refaktoryzacja zmiany kolejności parametrów (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` jest Visual C# operacja refaktoryzacji, która zapewnia łatwy sposób zmiany kolejności parametrów dla metod, indeksatorów i delegatów. `Reorder Parameters` Zmienia deklaracji, i we wszystkich lokalizacjach, w którym element członkowski jest wywoływana, parametry są ponownie rozmieszczać w celu odzwierciedlenia nowego zamówienia.  
  
 Aby wykonać `Reorder Parameters` operacji, umieść kursor na lub obok metoda, indeksator lub delegata. Gdy kursor znajduje się w miejscu, należy wywołać `Reorder Parameters` operacji, naciskając klawisz skrótu klawiaturowego lub przez kliknięcie przycisku polecenia z menu skrótów.  
  
> [!NOTE]
>  Nie można zmienić kolejności pierwszy parametr w metodzie rozszerzenia.  
  
### <a name="to-reorder-parameters"></a>Aby zmienić kolejność parametrów  
  
1.  Utwórz bibliotekę klas o nazwie `ReorderParameters`, a następnie zastąp `Class1` poniższym przykładowym kodem.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Umieść kursor w `MethodB`, albo w deklaracji metody lub wywołania metody.  
  
3.  Na **Refaktoryzuj** menu, kliknij przycisk **Zmień kolejność parametrów**.  
  
     **Zmień kolejność parametrów** pojawi się okno dialogowe.  
  
4.  W **Zmień kolejność parametrów** okno dialogowe, wybierz opcję `int i` w **parametry** listy, a następnie kliknij przycisk w dół.  
  
     Alternatywnie, można przeciągnąć `int i` po `bool b` w **parametry** listy.  
  
5.  W **Zmień kolejność parametrów** okno dialogowe, kliknij przycisk **OK**.  
  
     Jeśli **podgląd zmian odwołania** jest zaznaczona opcja **Zmień kolejność parametrów** okno dialogowe **podgląd zmian — Zmień kolejność parametrów** zostanie wyświetlone okno dialogowe. Umożliwia podgląd zmian w liście parametrów dla `MethodB` zarówno podpis, jak i wywołania metody.  
  
    1.  Jeśli **podgląd zmian — Zmień kolejność parametrów** pojawi się okno dialogowe, kliknij przycisk **Zastosuj**.  
  
         W tym przykładzie deklaracji metody i wszystkie metody wywołania dla `MethodB` są aktualizowane.  
  
## <a name="remarks"></a>Uwagi  
 Można zmieniać kolejność parametrów w deklaracji metody lub wywołania metody. Umieść kursor na lub obok deklaracji metody lub delegata, ale nie w treści.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)