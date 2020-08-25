---
title: 'Przewodnik: tworzenie fragmentu kodu'
ms.date: 03/31/2020
ms.topic: how-to
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
ms.openlocfilehash: 46744decddcc2d50fd05ea86cc6ebfad9d210031
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800505"
---
# <a name="walkthrough-create-a-code-snippet"></a>Przewodnik: tworzenie fragmentu kodu

Można utworzyć fragment kodu zawierający tylko kilka kroków. Wystarczy utworzyć plik XML, wypełnić odpowiednie elementy i dodać do niego swój kod. Opcjonalnie możesz użyć parametrów zastępczych i odwołań do projektu. Zaimportuj fragment kodu do instalacji programu Visual Studio za pomocą przycisku **Importuj** w programie **Code wstaweks Manager** (**Narzędzia**  >  **fragmentów kodu narzędzi Manager**).

## <a name="snippet-template"></a>Szablon fragmentu kodu

Poniższy kod XML jest podstawowym szablonem fragmentu kodu:

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

1. Utwórz nowy plik XML w programie Visual Studio i Dodaj opisany powyżej szablon.

2. Wypełnij tytuł fragmentu w elemencie **title** . Użyj nazwy **głównej kwadratu**tytułu.

3. Wypełnij język fragmentu kodu w atrybucie **Language** elementu **Code** . W języku C# Użyj **CSharp**, aby uzyskać Visual Basic, użyj **języka vb**i języka C++, użyj **CPP**.

   > [!TIP]
   > Aby wyświetlić wszystkie dostępne wartości języka, przejrzyj [sekcję atrybuty elementu kodu](code-snippets-schema-reference.md#attributes) na stronie [Dokumentacja schematu fragmenty kodu](code-snippets-schema-reference.md) .

4. Dodaj kod fragmentu w sekcji **CDATA** wewnątrz elementu **Code** .

   Dla języka C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Lub dla Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Nie można określić, w jaki sposób wiersze kodu w sekcji **CDATA** fragmentu kodu powinny być wcięte lub sformatowane. Po wstawieniu usługa językowa automatycznie sformatuje wstawiony kod.

5. Zapisz fragment kodu jako *SquareRoot. fragment* (możesz go zapisać w dowolnym miejscu).

## <a name="import-a-code-snippet"></a>Importowanie fragmentu kodu

1. Można zaimportować fragment kodu do instalacji programu Visual Studio za pomocą **Menedżera fragmentów kodów**. Otwórz go, wybierając pozycję **Narzędzia**  >  **Wstaw fragmenty kodu**.

2. Kliknij przycisk **Importuj** .

3. Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.

4. Zostanie otwarte okno dialogowe **Importowanie fragmentu kodu** z monitem o wybranie miejsca, w którym można dodać wstawkę z opcji w okienku po prawej stronie. Jednym z opcji powinny być **Moje fragmenty kodu**. Zaznacz go i kliknij przycisk **Zakończ**, a następnie **OK**.

5. Fragment kodu jest kopiowany do jednej z następujących lokalizacji, w zależności od języka kodowego:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017 \ Code Snippets\Visual C# \Moje fragmenty kodu*  
   *%USERPROFILE%\Documents\Visual Studio 2017 \ Code Snippets\Visual Basic\My fragmentów kodu*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019 \ Code Snippets\Visual C# \Moje fragmenty kodu*  
   *%USERPROFILE%\Documents\Visual Studio 2019 \ Code Snippets\Visual Basic\My fragmentów kodu*

   ::: moniker-end

6. Przetestuj fragment kodu, otwierając projekt C# lub Visual Basic. Przy otwartym pliku kodu w edytorze wybierz wstawki **wstawek**  >  **Insert Snippet** z menu dostępnego po kliknięciu prawym przyciskiem myszy, a następnie **Moje fragmenty kodu**. Powinien pojawić się fragment kodu o nazwie **pierwiastek kwadratowy**. Kliknij go dwukrotnie.

   Kod fragmentu kodu zostanie wstawiony do pliku kodu.

## <a name="description-and-shortcut-fields"></a>Opis i pola skrótów

::: moniker range="vs-2017"

1. Pola opisu zawierają więcej informacji na temat fragmentu kodu wyświetlanego w Menedżerze fragmentów kodu. Skrót to tag, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj dodany fragment, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2017 \ fragmenty kodu \\ [Visual C# lub Visual Basic] \Moje kod Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Pola opisu zawierają więcej informacji na temat fragmentu kodu wyświetlanego w Menedżerze fragmentów kodu. Skrót to tag, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj dodany fragment, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2019 \ fragmenty kodu \\ [Visual C# lub Visual Basic] \Moje kod Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Ponieważ edytujesz plik w katalogu, w którym został umieszczony program Visual Studio, nie musisz go ponownie zaimportować do programu Visual Studio.

2. Dodaj elementy **Author** i **Description** do elementu **header** i wypełnij je.

3. Element **header** powinien wyglądać następująco:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Otwórz **Menedżera fragmentów kodu** i wybierz fragment kodu. W okienku po prawej stronie Zwróć uwagę, że pola **Opis** i **autor** są teraz wypełnione.

   ![Opis fragmentu kodu w Menedżerze fragmentów kodu](media/code-snippet-description-author.png)

5. Aby dodać skrót, Dodaj element **skrótu** w elemencie **nagłówka** :

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Zapisz ponownie plik fragmentu kodu.

7. Aby przetestować skrót, Otwórz wcześniej użyty projekt, wpisz **sqrt** w edytorze i naciśnij klawisz **Tab** (raz dla Visual Basic, dwa razy dla języka C#).

   Kod fragmentu kodu zostanie wstawiony.

## <a name="replacement-parameters"></a>Parametry zastępcze

Licencjobiorca może chcieć, aby części fragmentu kodu zostały zastąpione przez użytkownika. Na przykład może zaistnieć potrzeba, aby użytkownik zamienił nazwę zmiennej na jeden w bieżącym projekcie. Można dostarczyć dwa typy zamian: literały i obiekty. Użyj [elementu Literal](code-snippets-schema-reference.md#literal-element) , aby zidentyfikować zamiennik dla fragmentu kodu, który jest całkowicie zawarty w fragmencie, ale prawdopodobnie będzie dostosowany po wstawieniu go do kodu (na przykład ciąg lub wartość liczbowa). Użyj [elementu Object](code-snippets-schema-reference.md#object-element) do identyfikacji elementu, który jest wymagany przez fragment kodu, ale prawdopodobnie zostanie zdefiniowany poza fragmentem (na przykład wystąpieniem obiektu lub kontrolką).

1. Aby umożliwić użytkownikowi łatwe zastępowanie liczby w celu obliczenia wartości pierwiastek kwadratowy, zmodyfikuj element **fragmentu** pliku *SquareRoot. fragment* w następujący sposób:

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

   Zwróć uwagę, że zastąpienie literału ma identyfikator ( `Number` ). Ten identyfikator jest przywoływany w fragmencie kodu, otaczając go `$` znakami:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Zapisz plik fragmentu kodu.

3. Otwórz projekt i Wstaw fragment kodu.

   Fragment kodu został wstawiony, a edytowalny literał jest wyróżniony do zastąpienia. Umieść kursor nad parametrem zastępczym, aby wyświetlić etykietkę narzędzia dla wartości.

   ![Etykietka narzędzia parametru zastąpienia fragmentu kodu w programie Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Jeśli w fragmencie kodu znajduje się więcej niż jeden parametr, który można zmienić, możesz nacisnąć klawisz **Tab** , aby przejść od jednego do drugiego.

## <a name="import-a-namespace"></a>Importowanie przestrzeni nazw

Można użyć fragmentu kodu, aby dodać `using` dyrektywę (C#) lub `Imports` instrukcję (Visual Basic) przez uwzględnienie [elementu Imports](code-snippets-schema-reference.md#imports-element). W przypadku projektów .NET Framework można również dodać odwołanie do projektu za pomocą [elementu References](code-snippets-schema-reference.md#references-element).

W poniższym kodzie XML przedstawiono fragment kodu, który używa metody `File.Exists` w przestrzeni nazw System.IO, w związku z tym definiuje element **Imports** do zaimportowania przestrzeni nazw System.IO.

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
