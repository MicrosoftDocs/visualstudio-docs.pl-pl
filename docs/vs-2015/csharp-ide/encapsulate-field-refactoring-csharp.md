---
title: Hermetyzuj pole Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a2c8d54b1625a4097d6b5a0acf6555d74fe83001
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116605"
---
# <a name="encapsulate-field-refactoring-c"></a>Refaktoryzacja hermetyzowania pola (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Hermetyzuj pole** operacja refaktoryzacji pozwala na szybkie tworzenie właściwości z istniejącego pola, a następnie bezproblemowo zaktualizować swój kod z odwołaniami do nowej właściwości.  
  
 Gdy [pola](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) jest [publicznych](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), inne obiekty mają bezpośredniego dostępu do tego pola i można ją zmodyfikować, niewykrytych przez obiekt, który jest właścicielem tego pola. Za pomocą [właściwości](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) do hermetyzacji tego pola, można uniemożliwić bezpośredni dostęp do pola.  
  
 Aby utworzyć nową właściwość **Hermetyzuj pole** operacji zmienia modyfikator dostępu dla pola, które mają być hermetyzacji do [prywatnej](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), a następnie generuje [Pobierz](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)i [ustaw](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) metody dostępu dla tego pola. W niektórych przypadkach tylko `get` metody dostępu jest generowany, np. gdy pole jest zadeklarowany jako tylko do odczytu.  
  
 Aparat refaktoryzacji aktualizacji kodu z odwołaniami do nowej właściwości w obszarach, określone w **aktualizacji odwołania** części **Hermetyzuj pole** okno dialogowe.  
  
### <a name="to-create-a-property-from-a-field"></a>Aby utworzyć właściwość z polem  
  
1. Utwórz aplikację konsoli o nazwie `EncapsulateFieldExample`, a następnie zastąp `Program` poniższym przykładowym kodem.  
  
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
  
2. W [Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md), umieść kursor w deklaracji, nazwę pola, które mają do hermetyzacji. W poniższym przykładzie, umieść kursor na słowo `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3. Na **Refaktoryzuj** menu, kliknij przycisk **Hermetyzuj pole**.  
  
     **Hermetyzuj pole** pojawi się okno dialogowe.  
  
     Możesz również wpisać skrótu klawiaturowego CTRL + R, E, aby wyświetlić **Hermetyzuj pole** okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Hermetyzuj pole** do wyświetlenia **Hermetyzuj pole** okno dialogowe.  
  
4. Określ ustawienia.  
  
5. Naciśnij klawisz ENTER lub kliknij przycisk **OK** przycisku.  
  
6. W przypadku wybrania **podgląd zmian odwołania** opcji, a następnie **podgląd zmian odwołania** zostanie otwarte okno. Kliknij przycisk **Zastosuj** przycisku.  
  
     Następujące `get` i `set` kod dostępu jest wyświetlany w pliku źródłowym:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Kod w `Main` dodano także do nowej metody `Width` nazwy właściwości.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Uwagi  
 **Hermetyzuj pole** operacja jest możliwe tylko wtedy, gdy kursor znajduje się w tym samym wierszu co deklaracja pola.  
  
 Dla deklaracji, które deklarują wielu pól **Hermetyzuj pole** używa przecinka jako granicę między polami i inicjuje, Refaktoryzacja dla pola, która jest najbliższym kursor i w tym samym wierszu, co kursor. Można również określić pole, które chcesz hermetyzacji, wybierając nazwę tego pola w deklaracji.  
  
 Kod, który jest generowany przez tę operację refaktoryzacji jest formowana przez funkcję fragmenty kodu hermetyzowania pola. Fragmenty kodu pochodzą można modyfikować. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmenty kodu Visual C#](../ide/visual-csharp-code-snippets.md)