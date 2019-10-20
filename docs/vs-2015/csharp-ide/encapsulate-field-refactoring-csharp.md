---
title: Refaktoryzacja pola hermetyzowania (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667569"
---
# <a name="encapsulate-field-refactoring-c"></a>Refaktoryzacja hermetyzowania pola (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Operacja refaktoryzacji **pola hermetyzowania** umożliwia szybkie tworzenie właściwości na podstawie istniejącego pola, a następnie bezproblemowe Aktualizowanie kodu przy użyciu odwołań do nowej właściwości.

 Gdy [pole](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) jest [publiczne](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), inne obiekty mają bezpośredni dostęp do tego pola i mogą być modyfikowane przez obiekt, który jest właścicielem tego pola. Używając [Właściwości](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) do hermetyzacji tego pola, możesz uniemożliwić bezpośredni dostęp do pól.

 Aby utworzyć nową właściwość, operacja **hermetyzowania pola** zmienia modyfikator dostępu dla pola, które ma być hermetyzowane do [prywatnego](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), a następnie generuje metody dostępu [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) i [Set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) dla tego pola. W niektórych przypadkach jest generowana tylko metoda dostępu `get`, na przykład wtedy, gdy pole jest zadeklarowane jako tylko do odczytu.

 Aparat refaktoryzacji aktualizuje swój kod z odwołaniami do nowej właściwości w obszarach określonych w sekcji **odwołania aktualizacji** okna dialogowego **hermetyzacja pola** .

### <a name="to-create-a-property-from-a-field"></a>Aby utworzyć właściwość z pola

1. Utwórz aplikację konsolową o nazwie `EncapsulateFieldExample`, a następnie zastąp `Program` następującym przykładowym kodem.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. W [edytorze kodu](../ide/writing-code-in-the-code-and-text-editor.md)Umieść kursor w deklaracji na nazwie pola, które chcesz hermetyzować. W poniższym przykładzie Umieść kursor w słowie `width`:

    ```csharp
    public int width, height;
    ```

3. W menu **refaktoryzacji** kliknij opcję **hermetyzacja pola**.

     Zostanie wyświetlone okno dialogowe **hermetyzacja pola** .

     Możesz również wpisać skrót klawiaturowy CTRL + R, E, aby wyświetlić okno dialogowe **hermetyzacja pola** .

     Możesz również kliknąć prawym przyciskiem myszy kursor, wskazać polecenie **Refaktoryzacja**, a następnie kliknąć opcję **Hermetyzuj pole** , aby wyświetlić okno dialogowe **hermetyzacja pola** .

4. Określ ustawienia.

5. Naciśnij klawisz ENTER lub kliknij przycisk **OK** .

6. W przypadku wybrania opcji **Podgląd zmian odwołań** zostanie otwarte okno **zmiany w wersji zapoznawczej** . Kliknij przycisk **Zastosuj** .

     W pliku źródłowym zostanie wyświetlony następujący `get` i kod dostępu `set`:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     Kod w metodzie `Main` został również zaktualizowany do nowej nazwy właściwości `Width`.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Uwagi
 Operacja **hermetyzowania pola** jest możliwa tylko wtedy, gdy kursor znajduje się w tym samym wierszu co deklaracja pola.

 W przypadku deklaracji, które deklarują wiele pól, **hermetyzowane pole** używa przecinka jako granicy między polami i inicjuje refaktoryzację w polu, które znajduje się bliżej kursora i w tym samym wierszu, co kursor. Możesz również określić pole, które ma zostać hermetyzowane, wybierając nazwę tego pola w deklaracji.

 Kod generowany przez tę operację refaktoryzacji jest modelowany przez funkcję fragmentów kodu pola hermetyzowania. Fragmenty kodu są modyfikowane. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).

## <a name="see-also"></a>Zobacz też
 [Refaktoryzacje (C#)](../csharp-ide/refactoring-csharp.md) [ C# wizualne fragmenty kodu](../ide/visual-csharp-code-snippets.md)