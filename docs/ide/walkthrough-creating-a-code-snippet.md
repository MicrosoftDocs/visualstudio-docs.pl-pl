---
title: 'Przewodnik: tworzenie fragmentu kodu'
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f58581a601da59e7ff66a3bae5ddcb7432bf8e3
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836100"
---
# <a name="walkthrough-create-a-code-snippet"></a>Przewodnik: tworzenie fragmentu kodu

Fragment kodu można utworzyć za pomocą tylko kilku krokach. To wszystko, co należy zrobić, Utwórz plik XML, wypełnij odpowiednie elementy i Dodaj swój kod do niego. Opcjonalnie można wprowadzić korzystanie z parametry zamiany oraz odwołania do projektu. Zaimportuj fragment kodu do instalacji programu Visual Studio przy użyciu **importu** znajdujący się w **Menedżera wstawek kodu** (**narzędzia** > **kodu Menedżer fragmentów**).

## <a name="snippet-template"></a>Szablon fragmentu kodu

Następujący kod XML jest podstawowy szablon fragmentu kodu:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>tworzenie fragmentu kodu

1. Utwórz nowy plik XML w programie Visual Studio i Dodaj ukazany powyżej szablon.

2. Wprowadź tytuł wstawki **tytuł** elementu. Użyj tytuł **pierwiastek kwadratowy**.

3. Wprowadź język wstawki w **języka** atrybutu **kodu** elementu. Aby uzyskać C#, użyj **CSharp**i Visual Basic można użyć **VB**.

   > [!TIP]
   > Aby wyświetlić wszystkie wartości z dostępnym językiem, przejdź [kodu sekcję atrybutów elementu](code-snippets-schema-reference.md#attributes) na [odwołanie do schematu fragmentów kodu](code-snippets-schema-reference.md) strony.

4. Dodaj fragment kodu w **CDATA** sekcji wewnątrz **kodu** elementu.

   Dla języka C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Lub dla języka Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

5. Zapisz fragment kodu jako *SquareRoot.snippet* (można zapisać go w dowolnym miejscu).

## <a name="import-a-code-snippet"></a>Zaimportuj fragment kodu

1. Fragment kodu można zaimportować do instalacji programu Visual Studio, za pomocą **Menedżera wstawek kodu**. Otwórz go, wybierając **narzędzia** > **Menedżera wstawek kodu**.

2. Kliknij przycisk **importu** przycisku.

3. Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.

4. **Importowania fragmentu kodu** zostanie otwarte okno dialogowe prośbą o wybranie miejsca dodania fragmentu kodu spośród możliwości w okienku po prawej stronie. Jedną z opcji powinny być **Moje fragmenty kodu**. Zaznacz go i kliknij **Zakończ**, następnie **OK**.

5. Fragment kodu jest kopiowany do jednej z następujących lokalizacji, w zależności od języka kodu:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Przetestuj swój fragment kodu, otwierając C# lub projekcie Visual Basic. Za pomocą pliku z kodem otwarte w edytorze, wybrać **fragmenty** > **Wstaw fragment kodu** z menu kliknij prawym przyciskiem myszy, a następnie **Moje fragmenty kodu**. Powinieneś zobaczyć fragment o nazwie **pierwiastek kwadratowy**. Kliknij go dwukrotnie.

   Fragment kodu dodaje się w pliku kodu.

## <a name="description-and-shortcut-fields"></a>Pola Opis i skrót

::: moniker range="vs-2017"

1. Pola opisów podać więcej informacji na temat fragmentów kodu po wyświetleniu w Menedżerze fragmentów kodu. Skrót jest znacznikiem, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj ten fragment kodu, które zostały dodane, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2017\Code fragmenty\\[Visual C# lub Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Pola opisów podać więcej informacji na temat fragmentów kodu po wyświetleniu w Menedżerze fragmentów kodu. Skrót jest znacznikiem, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj ten fragment kodu, które zostały dodane, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2019\Code fragmenty\\[Visual C# lub Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Ponieważ edycji pliku w katalogu, w których program Visual Studio umieszczenia go, nie musisz ponownie go zaimportować do programu Visual Studio.

2. Dodaj **Autor** i **opis** elementów **nagłówka** elementu i wypełnij je.

3. **Nagłówka** element powinien wyglądać mniej więcej tak:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Otwórz **Menedżera wstawek kodu** i wybierz wstawki kodu. W okienku po prawej stronie, zwróć uwagę, że **opis** i **Autor** teraz zostaną wypełnione pola.

   ![Opis fragmentu kodu w Menedżerze fragmentu kodu](media/code-snippet-description-author.png)

5. Aby dodać skrót, Dodaj **skrótów** elemencie **nagłówka** elementu:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Zapisz ponownie plik fragmentu kodu.

7. Aby przetestować ten skrót, otwórz projekt co użyte wcześniej, wpisz **sqrt** w edytorze i naciśnij klawisz **kartę** (jeden raz dla języka Visual Basic w C#).

   Fragment kodu jest wstawiany.

## <a name="replacement-parameters"></a>Parametry zamiany

Możesz zdecydować o wymianie części fragmentu kodu mają zostać zastąpione przez użytkownika. Na przykład możesz zechcieć użytkownikowi zastąpić nazwę zmiennej w bieżącym projekcie. Można zapewnić dwa rodzaje zamiany: literały i obiekty. Użyj [Literal — element](code-snippets-schema-reference.md#literal-element) do identyfikowania zamiennika fragment kodu, który zawiera się całkowicie we fragmencie, ale prawdopodobnie można dostosować, po jego wstawieniu do kodu (na przykład wartość ciągu lub liczbowe). Użyj [Object element](code-snippets-schema-reference.md#object-element) do identyfikowania elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem (na przykład wystąpienie obiektu lub kontrolki).

1. Aby zezwolić użytkownikom na łatwe zastępowanie numer do obliczania pierwiastek kwadratowy liczby, należy zmodyfikować **fragment** elementu *SquareRoot.snippet* pliku w następujący sposób:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Należy zauważyć, że zastąpienie literału otrzymuje identyfikator (`Number`). Czy identyfikator odwołuje się z w obrębie fragmentu kodu ją za pomocą `$` znaków:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Zapisz plik fragmentu kodu.

3. Otwórz projekt i Wstaw fragment kodu.

   Wstawieniu fragmentu kodu, i można edytować literał zostanie wyróżniona do zastąpienia. Umieść kursor nad parametr zastąpienia, aby wyświetlić etykietkę narzędzia dla wartości.

   ![Etykietka narzędzia parametr zastąpienia fragment kodu w programie Visual Studio Code](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Jeśli istnieje więcej niż jeden parametr replacable fragment kodu, możesz nacisnąć przycisk **kartę** przejść z jednego do drugiego w celu zmiany wartości.

## <a name="import-a-namespace"></a>Importuj przestrzeń nazw

Fragment kodu służy do dodawania `using` — dyrektywa (C#) lub `Imports` — instrukcja (Visual Basic), umieszczając [Imports element](code-snippets-schema-reference.md#imports-element). Dla projektów programu .NET Framework, można dodać odwołanie do projektu przy użyciu [odwołania — element](code-snippets-schema-reference.md#references-element).

Następujący kody XML pokazuje fragment kodu, który używa metody `File.Exists` w przestrzeni nazw System.IO i w związku z tym, **Importy** element, aby zaimportować system.IO — przestrzeń nazw.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)