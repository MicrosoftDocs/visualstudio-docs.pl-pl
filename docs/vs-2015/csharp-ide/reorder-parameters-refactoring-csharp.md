---
title: Refaktoryzacja zmiany kolejności parametrów (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673146"
---
# <a name="reorder-parameters-refactoring-c"></a>Refaktoryzacja zmiany kolejności parametrów (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` jest operacją C# refaktoryzacji wizualnej, która zapewnia łatwy sposób zmiany kolejności parametrów dla metod, indeksatorów i delegatów. `Reorder Parameters` zmienia deklarację i w każdym miejscu, w którym jest wywoływana członek, parametry są ponownie rozmieszczane w celu odzwierciedlenia nowej kolejności.

 Aby wykonać operację `Reorder Parameters`, umieść kursor na lub obok metody, indeksatora lub delegata. Gdy kursor znajduje się na pozycji, wywołaj operację `Reorder Parameters`, naciskając skrót klawiaturowy lub klikając polecenie w menu skrótów.

> [!NOTE]
> Nie można zmienić kolejności pierwszego parametru w metodzie rozszerzenia.

### <a name="to-reorder-parameters"></a>Aby zmienić kolejność parametrów

1. Utwórz bibliotekę klas o nazwie `ReorderParameters`, a następnie zastąp `Class1` następującym przykładowym kodem.

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

2. Umieść kursor na `MethodB`, w deklaracji metody lub wywołaniu metody.

3. W menu **refaktoryzacji** kliknij pozycję **Zmień kolejność parametrów**.

     Wyświetli się okno dialogowe **Parametry zmiany kolejności** .

4. W oknie dialogowym **Zmienianie kolejności parametrów** wybierz pozycję `int i` na liście **Parametry** , a następnie kliknij przycisk w dół.

     Alternatywnie możesz przeciągnąć `int i` po `bool b` na liście **parametrów** .

5. W oknie dialogowym **Zmienianie kolejności parametrów** kliknij przycisk **OK**.

     Jeśli wybrano opcję **Podgląd zmian odwołań** w oknie dialogowym Zmienianie **kolejności parametrów** , pojawi się okno dialogowe **zmiany w wersji zapoznawczej — parametry zmian kolejności** . Zawiera Podgląd zmian na liście parametrów dla `MethodB` zarówno w sygnaturze, jak i wywołaniu metody.

    1. Jeśli zostanie wyświetlone okno dialogowe **Podgląd zmian-Zmień kolejność parametrów** , kliknij przycisk **Zastosuj**.

         W tym przykładzie, Deklaracja metody i wszystkie lokacje wywołań metody dla `MethodB` są aktualizowane.

## <a name="remarks"></a>Uwagi
 Można zmienić kolejność parametrów z deklaracji metody lub wywołania metody. Umieść kursor na lub obok metody lub delegata deklaracji, ale nie w treści.

## <a name="see-also"></a>Zobacz też
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)