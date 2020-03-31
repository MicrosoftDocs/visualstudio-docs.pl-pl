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
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2554729be8f3b9697d1407befd68cbb21fac10dd
ms.sourcegitcommit: 992dd075e65b5f3adefc1ff758975298c47381e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80435037"
---
# <a name="walkthrough-create-a-code-snippet"></a>Przewodnik: tworzenie fragmentu kodu

Fragment kodu można utworzyć za pomocą tylko kilku kroków. Wszystko, co musisz zrobić, to utworzyć plik XML, wypełnić odpowiednie elementy i dodać do niego kod. Opcjonalnie można użyć parametrów zastępczych i odwołań do projektu. Zaimportowanie fragmentu kodu do instalacji programu Visual Studio przy użyciu przycisku **Importuj** w **Menedżerze urywków kodu** **(Menedżer urywków****kodu narzędzi).** > 

## <a name="snippet-template"></a>Szablon fragmentu kodu

Następujący kod XML jest podstawowym szablonem urywka:

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

1. Utwórz nowy plik XML w programie Visual Studio i dodaj szablon pokazany powyżej.

2. Wypełnij tytuł fragmentu kodu w **tytule** elementu. Użyj tytułu **Pierwiastek kwadratowy**.

3. Wypełnij język fragmentu kodu w **language** **atrybutu Code** elementu. W przypadku języka C#należy użyć **klawisza CSharp**, dla języka Visual Basic, użyj **VB**, a w przypadku języka C++, użyj **CPP**.

   > [!TIP]
   > Aby wyświetlić wszystkie dostępne wartości języka, przejrzyj [sekcję Atrybuty elementu Kod](code-snippets-schema-reference.md#attributes) na stronie [Odwołania do schematu fragmentów kodu.](code-snippets-schema-reference.md)

4. Dodaj kod fragmentu kodu w sekcji **CDATA** wewnątrz **Code** elementu.

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

   > [!NOTE]
   > Nie można określić, jak wiersze kodu w sekcji **CDATA** fragmentu kodu powinny być wcięte lub sformatowane. Po wstawieniu usługa językowa automatycznie formatuje wstawiony kod.

5. Zapisz fragment kodu jako *fragment SquareRoot.snippet* (możesz zapisać go w dowolnym miejscu).

## <a name="import-a-code-snippet"></a>Importowanie fragmentu kodu

1. Fragment kodu można zaimportować do instalacji programu Visual Studio przy użyciu **Menedżera urywków kodu**. Otwórz go, wybierając Menedżera**urywków kodu** **narzędzi** > .

2. Kliknij przycisk **Importuj.**

3. Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, wybierz go i kliknij przycisk **Otwórz**.

4. Zostanie otwarte okno dialogowe **Importowanie fragmentu kodu** z prośbą o wybranie miejsca dodania fragmentu kodu z opcji w prawym okienku. Jedną z opcji powinny być **moje fragmenty kodu**. Zaznacz go i kliknij przycisk **Zakończ**, a następnie **OK**.

5. Fragment kodu jest kopiowany do jednej z następujących lokalizacji, w zależności od języka kodu:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Urywki\Visual C#\Moje fragmenty*
   kodu *%USERPROFILE%\Documents\Visual Studio 2017\Code Urywki\Visual Basic\Moje fragmenty kodu*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Urywki\Visual C#\Moje fragmenty*
   kodu *%USERPROFILE%\Documents\Visual Studio 2019\Code Urywki\Visual Basic\Moje fragmenty kodu*

   ::: moniker-end

6. Przetestuj fragment kodu, otwierając projekt języka C# lub Visual Basic. Po otwarciu pliku kodu w edytorze wybierz polecenie **Urywki** > **wstawianie fragmentu** kodu z menu po kliknięciu prawym przyciskiem myszy, a następnie **pozycję Fragmenty kodu .** Powinien zostać wyświetlony fragment kodu o nazwie **Square Root**. Kliknij go dwukrotnie.

   Kod fragmentu kodu zostanie wstawiony do pliku kodu.

## <a name="description-and-shortcut-fields"></a>Pola opisu i skrótów

::: moniker range="vs-2017"

1. Pola opisu podają więcej informacji na temat fragmentu kodu podczas wyświetlania w Menedżerze urywków kodu. Skrót jest tagiem, który użytkownicy mogą wpisywać w celu wstawienia fragmentu kodu. Edytuj dodany fragment kodu, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2017\Code Urywki\\[Visual C# lub Visual Basic]\Mój fragment kodu\SquareRoot.urywek*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Pola opisu podają więcej informacji na temat fragmentu kodu podczas wyświetlania w Menedżerze urywków kodu. Skrót jest tagiem, który użytkownicy mogą wpisywać w celu wstawienia fragmentu kodu. Edytuj dodany fragment kodu, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2019\Code Urywki\\[Visual C# lub Visual Basic]\Mój fragment kodu\SquareRoot.urywek*.

::: moniker-end

   > [!TIP]
   > Ponieważ edytujesz plik w katalogu, w którym visual studio umieścił go, nie trzeba ponownie zaimportować go do programu Visual Studio.

2. Dodaj elementy **Autor** i **Opis** do elementu **Nagłówka** i wypełnij je.

3. Element **nagłówka** powinien wyglądać mniej więcej tak:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Otwórz **Menedżera urywków kodu** i wybierz fragment kodu. W prawym okienku zwróć uwagę, że pola **Opis** i **Autor** są teraz wypełnione.

   ![Opis fragmentu kodu w Menedżerze urywków kodu](media/code-snippet-description-author.png)

5. Aby dodać skrót, dodaj element **skrótu** w **elemencie Nagłówka:**

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Zapisz ponownie plik urywka.

7. Aby przetestować skrót, otwórz poprzednio używany projekt, wpisz **sqrt** w edytorze i naciśnij **klawisz Tab** (raz dla języka Visual Basic, dwa razy dla języka C#).

   Zostanie wstawiony kod fragmentu kodu.

## <a name="replacement-parameters"></a>Parametry zamienne

Możesz chcieć, aby części fragmentu kodu zostały zastąpione przez użytkownika. Na przykład można zastąpić nazwę zmiennej w bieżącym projekcie. Można podać dwa typy zamienników: literały i obiekty. Użyj [Literal element](code-snippets-schema-reference.md#literal-element) do identyfikowania zastąpienia fragmentu kodu, który jest całkowicie zawarty w urywek, ale prawdopodobnie zostaną dostosowane po wstawieniu do kodu (na przykład ciąg lub wartość liczbowa). Użyj [Object element](code-snippets-schema-reference.md#object-element) do identyfikowania elementu, który jest wymagany przez fragment kodu, ale może być zdefiniowany poza fragment kodu się (na przykład wystąpienie obiektu lub formant).

1. Aby umożliwić użytkownikowi łatwe zastąpienie liczby w celu obliczenia pierwiastka kwadratowego, **zmodyfikuj** element Fragment pliku *SquareRoot.snippet* w następujący sposób:

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

   Należy zauważyć, że dosłowne`Number`zastąpienie otrzymuje identyfikator ( ). Ten identyfikator odwołuje się z poziomu fragmentu kodu, `$` otaczając go znakami:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Zapisz plik urywka.

3. Otwórz projekt i wstaw fragment kodu.

   Fragment kodu zostanie wstawiony, a edytowalny literał zostanie podświetlony w celu zastąpienia. Umieść wskaźnik myszy na parametrze zastępczym, aby wyświetlić etykietkę narzędzia dla wartości.

   ![Etykietka narzędzia parametru zastępowania fragmentu kodu w programie Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Jeśli we wemieśni znajduje się więcej niż jeden parametr wielokrotnego rozmieszczenia, możesz nacisnąć **klawisz Tab,** aby przejść z jednego do drugiego, aby zmienić wartości.

## <a name="import-a-namespace"></a>Importowanie obszaru nazw

Fragment kodu służy do dodawania `using` dyrektywy (C#) `Imports` lub instrukcji (Visual Basic) przez [dołączenie importu elementu](code-snippets-schema-reference.md#imports-element). W przypadku projektów programu .NET Framework można również dodać odwołanie do projektu przy użyciu [elementu Odwołania](code-snippets-schema-reference.md#references-element).

Poniższy kod XML przedstawia fragment kodu, który `File.Exists` używa metody w System.IO przestrzeni nazw i w związku z tym definiuje **Imports** element do importowania System.IO obszaru nazw.

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

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
