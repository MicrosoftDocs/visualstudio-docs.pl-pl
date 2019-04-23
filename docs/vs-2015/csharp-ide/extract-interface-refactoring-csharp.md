---
title: Wyodrębnianie interfejsu Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55b24facd3a9ec935277a42c211a64d824ed6d7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116748"
---
# <a name="extract-interface-refactoring-c"></a>Refaktoryzacja wyodrębniania interfejsu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyodrębnij interfejs jest operacji refaktoryzacji, która zapewnia łatwy sposób utworzyć nowy interfejs z elementami członkowskimi, które pochodzą z istniejącej klasy, struktury lub interfejsu.  
  
 Korzystając z kilku klientów ten sam podzestaw elementów członkowskich z klasy, struktury lub interfejsu, lub gdy wiele klasami, strukturami lub interfejsy wspólnym podzestaw elementów członkowskich, może być przydatne do międzynarodowym podzestaw elementów członkowskich w interfejsie. Aby uzyskać więcej informacji na temat używania interfejsów zobacz [interfejsów](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Wyodrębnij interfejs generuje interfejs w nowym pliku i umieszcza kursor na początku nowego pliku. Można określić elementów członkowskich, które można wyodrębnić do nowego interfejsu, Nazwa nowego interfejsu i nazwę wygenerowanego pliku przy użyciu **Wyodrębnij interfejs** okno dialogowe.  
  
### <a name="to-use-extract-interface"></a>Aby użyć Wyodrębnij interfejs  
  
1. Utwórz aplikację konsoli o nazwie `ExtractInterface`, a następnie zastąp `Program` następującym kodem  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2. Umieść kursor w `MethodB`i kliknij przycisk **Wyodrębnij interfejs** na **Refaktoryzuj** menu.  
  
     **Wyodrębnij interfejs** pojawi się okno dialogowe.  
  
     Możesz również wpisać skrótu klawiaturowego CTRL + R, do wyświetlenia **Wyodrębnij interfejs** okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy przycisk myszy, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Wyodrębnij interfejs** do wyświetlenia **Wyodrębnij interfejs** okno dialogowe.  
  
3. Kliknij przycisk **Zaznacz wszystko**.  
  
4. Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony nowy plik, IProtoA.cs i następujący kod:  
  
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
 Ta funkcja jest dostępna tylko w przypadku, gdy kursor znajduje się w klasy, struktury lub interfejsu, który zawiera elementy członkowskie, które chcesz wyodrębnić. Gdy kursor znajduje się w tym miejscu, należy wywołać operacja refaktoryzacji Wyodrębnij interfejs.  
  
 Po wywołaniu wyodrębniania interfejsu na klasę lub strukturę do uwzględnienia nowej nazwy interfejsu modyfikacji listy podstaw i interfejsy. Po wywołaniu wyodrębniania interfejsu w interfejsie listy baz i interfejsów nie jest modyfikowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)