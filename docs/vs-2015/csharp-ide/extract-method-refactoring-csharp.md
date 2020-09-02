---
title: Refaktoryzacja metody wyodrębniania (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667547"
---
# <a name="extract-method-refactoring-c"></a>Refaktoryzacja wyodrębniania metody (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extract Metoda** jest operacją refaktoryzacji, która zapewnia łatwy sposób tworzenia nowej metody ze fragmentu kodu w istniejącym elemencie członkowskim.

 Za pomocą **metody Extract**można utworzyć nową metodę przez wyodrębnienie zaznaczenia kodu z wewnątrz bloku kodu istniejącego elementu członkowskiego. Nowa, wyodrębniona Metoda zawiera wybrany kod, a wybrany kod w istniejącym elemencie członkowskim jest zastępowany wywołaniem nowej metody. Włączenie fragmentu kodu do jego własnej metody pozwala szybko i dokładnie zreorganizować kod w celu lepszego ponownego użycia i czytelności.

 **Metoda Extract** ma następujące zalety:

- Zachęca do korzystania z najlepszych praktyk dotyczących kodowania, podkreślając dyskretne metody wielokrotnego użytku.

- Zachęca do samodokumentowania kodu poprzez dobrą organizację.

     Gdy są używane nazwy opisowe, metody wysokiego poziomu mogą odczytywać więcej jak serie komentarzy.

- Zachęca do tworzenia bardziej precyzyjnych metod w celu uproszczenia zastępowania.

- Zmniejsza duplikowanie kodu.

### <a name="to-use-extract-method"></a>Aby użyć metody Extract

1. Utwórz aplikację konsolową o nazwie `ExtractMethod` , a następnie zastąp ciąg `Program` następującym przykładowym kodem.

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

2. Wybierz fragment kodu, który chcesz wyodrębnić:

    ```csharp
    double area = PI * radius * radius;
    ```

3. W menu **refaktoryzacji** kliknij pozycję **Wyodrębnij metodę**.

     Zostanie wyświetlone okno dialogowe **Wyodrębnij metodę** .

     Alternatywnie można również wpisać skrót klawiaturowy CTRL + R, M, aby wyświetlić okno dialogowe **Wyodrębnij metodę** .

     Możesz również kliknąć prawym przyciskiem myszy wybrany kod, wskazać polecenie **Refaktoryzacja**, a następnie kliknąć polecenie **Wyodrębnij metodę** , aby wyświetlić okno dialogowe **Wyodrębnij metodę** .

4. Określ nazwę nowej metody, `CircleArea` na przykład, w polu **Nowa nazwa metody** .

     Wersja zapoznawcza nowego podpisu metody zostanie wyświetlona w sekcji **Podgląd sygnatury metody**.

5. Kliknij przycisk **OK**.

## <a name="remarks"></a>Uwagi
 W przypadku użycia polecenia **Wyodrębnij metodę** Nowa metoda zostanie wstawiona po elemencie członkowskim źródłowym w tej samej klasie.

## <a name="partial-types"></a>Typy częściowe
 Jeśli klasa jest typem częściowym, **Metoda Extract** generuje nową metodę bezpośrednio po źródłowym elemencie członkowskim. **Metoda Extract** określa sygnaturę nowej metody, tworząc metodę statyczną, gdy kod w nowej metodzie nie odwołuje się do danych wystąpienia.

## <a name="generic-type-parameters"></a>Parametry typu ogólnego
 W przypadku wyodrębnienia metody, która ma parametr typu ogólnego nieograniczonego, wygenerowany kod nie dodaje `ref` modyfikatora do tego parametru, chyba że zostanie przypisana wartość. Jeśli wyodrębniona Metoda będzie obsługiwać typy odwołań jako argument typu ogólnego, należy ręcznie dodać `ref` modyfikator do parametru w podpisie metody.

## <a name="anonymous-methods"></a>Metody anonimowe
 Jeśli spróbujesz wyodrębnić część metody anonimowej, która zawiera odwołanie do zmiennej lokalnej, która jest zadeklarowana lub przywoływana poza metodą anonimową, program Visual Studio wyświetli ostrzeżenie o potencjalnych zmianach semantycznych.

 Gdy metoda anonimowa używa wartości zmiennej lokalnej, wartość jest uzyskiwana w momencie wykonywania metody anonimowej. W przypadku wyodrębnienia metody anonimowej do innej metody wartość zmiennej lokalnej jest uzyskiwana w momencie wywołania wyodrębnionej metody.

 Poniższy przykład ilustruje tę zmianę semantyczną. Jeśli ten kod jest wykonywany, **11** zostanie wydrukowany w konsoli programu. W przypadku użycia **metody Extract** do wyodrębnienia regionu kodu, który jest oznaczony przez Komentarze do kodu do własnej metody, a następnie wykonania kodu refaktoryzacji, **10** zostanie wydrukowany w konsoli programu.

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

 Aby obejść tę sytuację, należy wprowadzić zmienne lokalne, które są używane w polach metody anonimowej klasy.

## <a name="see-also"></a>Zobacz też
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)