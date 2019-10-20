---
title: Refaktoryzacja wyodrębniania interfejsu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667554"
---
# <a name="extract-interface-refactoring-c"></a>Refaktoryzacja wyodrębniania interfejsu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extract Interface jest operacją refaktoryzacji, która zapewnia łatwy sposób tworzenia nowego interfejsu z elementami członkowskimi, które pochodzą z istniejącej klasy, struktury lub interfejsu.

 Gdy kilku klientów używa tego samego podzestawu elementów członkowskich z klasy, struktury lub interfejsu, lub gdy wiele klas, struktur lub interfejsów ma podzestaw składowych wspólnych, może być przydatne do dopełnienia podzbioru elementów członkowskich w interfejsie. Aby uzyskać więcej informacji o korzystaniu z interfejsów, zobacz [interfejsy](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Wyodrębnij interfejs generuje interfejs w nowym pliku i umieszcza kursor na początku nowego pliku. Można określić, które elementy członkowskie mają zostać wyodrębnione do nowego interfejsu, nazwę nowego interfejsu i nazwę wygenerowanego pliku przy użyciu okna dialogowego **wyodrębnianie interfejsu** .

### <a name="to-use-extract-interface"></a>Aby użyć wyodrębnienia interfejsu

1. Utwórz aplikację konsolową o nazwie `ExtractInterface`, a następnie zastąp `Program` następującym kodem

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Kursor umieszczony w `MethodB`, a następnie kliknij pozycję **Wyodrębnij interfejs** w menu **refaktoryzacji** .

     Zostanie wyświetlone okno dialogowe **wyodrębnianie interfejsu** .

     Możesz również wpisać skrót klawiaturowy CTRL + R, I, aby wyświetlić okno dialogowe **Wyodrębnij interfejs** .

     Możesz również kliknąć prawym przyciskiem myszy mysz, wskazać polecenie **Refaktoryzacja**, a następnie kliknąć polecenie **Wyodrębnij interfejs** , aby wyświetlić okno dialogowe **Wyodrębnij interfejs** .

3. Kliknij pozycję **Zaznacz wszystko**.

4. Kliknij przycisk **OK**.

     Zobaczysz nowy plik, IProtoA.cs i następujący kod:

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>Uwagi
 Ta funkcja jest dostępna tylko wtedy, gdy kursor znajduje się w klasie, strukturze lub interfejsie zawierającym elementy członkowskie, które mają zostać wyodrębnione. Gdy kursor znajduje się w tym miejscu, wywołaj operację refaktoryzacji wyodrębniania interfejsu.

 Po wywołaniu wyodrębnienia interfejsu w klasie lub strukturze, Lista baz i interfejsów zostanie zmodyfikowana w celu uwzględnienia nowej nazwy interfejsu. Po wywołaniu wyodrębniania interfejsu w interfejsie Lista baz i interfejsów nie jest modyfikowana.

## <a name="see-also"></a>Zobacz też
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)