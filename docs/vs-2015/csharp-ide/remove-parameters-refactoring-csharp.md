---
title: Refaktoryzacja usuwania parametrów (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667494"
---
# <a name="remove-parameters-refactoring-c"></a>Refaktoryzacja usuwania parametrów (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` jest operacją refaktoryzacji, która zapewnia łatwy sposób usuwania parametrów z metod, indeksatorów lub delegatów. Usuwanie parametrów powoduje zmianę deklaracji; w każdym miejscu, w którym jest wywoływana składowa, parametr zostanie usunięty w celu odzwierciedlenia nowej deklaracji.

 Aby wykonać operację usuwania parametrów, należy najpierw pozycjonować kursor w metodzie, indeksatorze lub delegacie. Gdy kursor znajduje się na pozycji, aby wywołać operację usuwania `Parameters` , kliknij menu **Refaktoryzacja** , naciśnij skrót klawiaturowy lub wybierz polecenie z menu skrótów.

> [!NOTE]
> Nie można usunąć pierwszego parametru w metodzie rozszerzenia.

### <a name="to-remove-parameters"></a>Aby usunąć parametry

1. Utwórz aplikację konsolową o nazwie `RemoveParameters` , a następnie zastąp ciąg `Program` poniższym kodem.

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

2. Umieść kursor w metodzie `A` w deklaracji metody lub wywołaniu metody.

3. Z menu **refaktoryzacji** wybierz pozycję **Usuń parametry** , aby wyświetlić okno dialogowe **Usuwanie parametrów** .

     Możesz również wpisać skrót klawiaturowy CTRL + R, V, aby wyświetlić okno dialogowe **Usuwanie parametrów** .

     Możesz również kliknąć prawym przyciskiem myszy kursor, wskazać polecenie **Refaktoryzacja**, a następnie kliknąć polecenie **Usuń parametry** , aby wyświetlić okno dialogowe **Usuwanie parametrów** .

4. Za pomocą pola **Parametry** , umieść kursor na `int i` , a następnie kliknij przycisk **Usuń**.

5. Kliknij przycisk **OK**.

6. W oknie dialogowym **Podgląd zmian — Usuwanie parametrów** kliknij przycisk **Zastosuj**.

## <a name="remarks"></a>Uwagi
 Parametry można usunąć z deklaracji metody lub wywołania metody. Umieść kursor w deklaracji metody lub nazwie delegata i Wywołaj parametry Remove.

> [!CAUTION]
> Polecenie Usuń parametry umożliwia usunięcie parametru, do którego istnieje odwołanie w treści elementu członkowskiego, ale nie powoduje usunięcia odwołań do tego parametru w treści metody. Może to spowodować błędy kompilacji w kodzie. Można jednak użyć okna dialogowego **Podgląd zmian** , aby przejrzeć swój kod przed wykonaniem operacji refaktoryzacji.

 Jeśli usuwany parametr jest modyfikowany podczas wywołania metody, usunięcie parametru spowoduje również usunięcie modyfikacji. Na przykład, jeśli wywołanie metody zostało zmienione z

```csharp
MyMethod(param1++, param2);
```

 na wartość

```csharp
MyMethod(param2);
```

 w wyniku operacji refaktoryzacji `param1` nie będą zwiększane.

## <a name="see-also"></a>Zobacz też
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)