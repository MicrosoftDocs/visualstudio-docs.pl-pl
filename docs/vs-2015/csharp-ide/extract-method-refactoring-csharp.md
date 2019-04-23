---
title: Wyodrębnij metodę Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a889250e641e004bdb0d89f6965c43c3d6b8e2a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041401"
---
# <a name="extract-method-refactoring-c"></a>Refaktoryzacja wyodrębniania metody (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Wyodrębnij metodę** jest operacji refaktoryzacji, która zapewnia łatwy sposób utworzyć nową metodę z fragmentu kodu w istniejącą składową.  
  
 Za pomocą **Wyodrębnij metodę**, można utworzyć nowej metody, wyodrębniając wybór kodu z wewnątrz bloku kodu z istniejącą składową. Metoda nowe, wyodrębnione zawiera zaznaczony kod i zaznaczony kod w istniejący element członkowski jest zastępowany wywołanie do nowej metody. Przekształcanie fragmentu kodu w jego własnej metody pozwala szybko i dokładnie zmianę kod, aby uzyskać lepszą czytelność i ponowne użycie.  
  
 **Wyodrębnij metodę** ma następujące zalety:  
  
- Zaleca najlepsze rozwiązania, podkreślając metody dyskretnych, wielokrotnego użytku.  
  
- Zachęca własnym dokumentowanie kodu za pośrednictwem dobre organizacji.  
  
     Gdy opisowe nazwy są używane, wysokiego poziomu metody można Dowiedz się więcej, takich jak seria komentarzy.  
  
- Zaleca się tworzenie bardziej szczegółowej metody, aby uprościć zastępowanie.  
  
- Zmniejsza zduplikowania kodu.  
  
### <a name="to-use-extract-method"></a>Aby użyć Wyodrębnij metodę  
  
1. Utwórz aplikację konsoli o nazwie `ExtractMethod`, a następnie zastąp `Program` poniższym przykładowym kodem.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2. Wybierz fragment kodu, które mają zostać wyodrębnione:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3. Na **Refaktoryzuj** menu, kliknij przycisk **Wyodrębnij metodę**.  
  
     **Wyodrębnij metodę** pojawi się okno dialogowe.  
  
     Alternatywnie, możesz również wpisać skrótu klawiaturowego CTRL + R, M, aby wyświetlić **Wyodrębnij metodę** okno dialogowe.  
  
     Można również prawym przyciskiem myszy wybrane kodu, wskaż opcję **Refaktoryzuj**, a następnie kliknij przycisk **Wyodrębnij metodę** do wyświetlenia **Wyodrębnij metodę** okno dialogowe.  
  
4. Określ nazwę dla nowej metody, takie jak `CircleArea`w **nową nazwę metody** pole.  
  
     Wersję zapoznawczą nowej sygnatury metody będzie wyświetlana **Podgląd sygnatury metody**.  
  
5. Kliknij przycisk **OK**.  
  
## <a name="remarks"></a>Uwagi  
 Kiedy używasz **Wyodrębnij metodę** polecenia, dodaje się nową metodę następującego elementu członkowskiego źródła z tej samej klasy.  
  
## <a name="partial-types"></a>Typy częściowe  
 Jeśli klasa jest typu częściowego, następnie **Wyodrębnij metodę** generuje nową metodę natychmiast po Członkowskie źródła. **Wyodrębnij metodę** Określa podpis nowej metody, Tworzenie statycznej metody, gdy żadne dane wystąpienia odwołuje się do kodu w nowej metodzie.  
  
## <a name="generic-type-parameters"></a>Parametry typu ogólnego  
 Podczas wyodrębniania metody, która ma parametr typu ogólnego nieograniczonego wygenerowany kod nie doda `ref` modyfikatora tego parametru, chyba że wartość jest do niej przypisany. Jeśli wyodrębnionej metody będą obsługuje typy odwołań jako argument typu ogólnego, a następnie należy ręcznie dodawać `ref` modyfikator parametru w podpisie metody.  
  
## <a name="anonymous-methods"></a>Metody anonimowe  
 Jeśli zostanie podjęta próba wyodrębnienia część metody anonimowej, który zawiera odwołanie do zmiennej lokalnej, która jest zadeklarowana lub do których odwołuje się poza metody anonimowej, następnie programu Visual Studio wyświetli ostrzeżenie o potencjalnych zmian semantycznych.  
  
 Gdy metoda anonimowa używa wartości zmiennej lokalnej, uzyskuje się wartość w tej chwili, metoda anonimowa jest wykonywane. Gdy metoda anonimowa jest następnie wyodrębniany do innej metody, w momencie wywołania do wyodrębnionej metody, uzyskuje się wartość zmiennej lokalnej.  
  
 Poniższy przykład ilustruje tę zmianę semantycznego. Jeśli ten kod jest wykonywany, następnie **11** będą drukowane w konsoli. Jeśli używasz **Wyodrębnij metodę** do wyodrębnienia region kod, który jest oznaczony za komentarze w kodzie do jego własnej metody, a następnie wykonywania refaktoryzować kod, następnie **10** będą drukowane w konsoli.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Aby obejść tę sytuację, należy zmienne lokalne, które są używane w polach metody anonimowej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)