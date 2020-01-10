---
title: 'Przewodnik: Tworzenie fragmentu kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac188bcf7975b8da1bbc71a90d3b6c34b095d424
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845578"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Wskazówki: tworzenie wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć fragment kodu zawierający tylko kilka kroków. Wystarczy utworzyć plik XML, wypełnić odpowiednie elementy i dodać do niego swój kod. Możesz również dodawać odwołania i parametry zastępujące do kodu. Można dodać fragment kodu do instalacji programu Visual Studio za pomocą przycisku Importuj w Menedżerze fragmentów kodów (**Narzędzia/program fragmentów kodu**).

> [!TIP]
> Aby uzyskać więcej informacji o tym, jak łatwiej pisać fragmenty kodu, Wyszukaj witrynę sieci Web CodePlex dla narzędzi społecznościowych, takich jak [Edytor wstawek](https://snippeteditor.codeplex.com/).

## <a name="snippet-template"></a>Szablon fragmentu kodu
 Oto podstawowy szablon fragmentu kodu:

```
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

### <a name="to-create-a-code-snippet"></a>Aby utworzyć fragment kodu

1. Utwórz nowy plik XML w programie Visual Studio i Dodaj opisany powyżej szablon.

2. Wypełnij tytuł fragmentu kodu, np. "Hello world VB", w elemencie title.

3. Wypełnij język fragmentu kodu w atrybucie Languages elementu Code. Na potrzeby tego przykładu Użyj "VB".

4. Dodaj kod w sekcji CDATA wewnątrz elementu Code, na przykład:

    ```
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>

    ```

5. Zapisz fragment kodu jako VBCodeSnippet. fragment kodu.

### <a name="to-add-a-code-snippet-to-visual-studio"></a>Aby dodać fragment kodu do programu Visual Studio

1. Możesz dodać własne fragmenty kodu do instalacji programu Visual Studio za pomocą Menedżera fragmentów kodów. Otwórz Menedżera fragmentów kodu (**Tools/Code wstaweks Manager**).

2. Kliknij przycisk **Importuj** .

3. Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.

4. Zostanie otwarte okno dialogowe **Importowanie fragmentu kodu** z monitem o wybranie miejsca, w którym można dodać wstawkę z opcji w okienku po prawej stronie. Jednym z opcji powinny być **Moje fragmenty kodu**. Zaznacz go i kliknij przycisk **Zakończ**, a następnie **OK**.

5. Fragment kodu jest kopiowany do następującej lokalizacji:

     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`

6. Przetestuj swój fragment, otwierając projekt Visual Basic i otwierając plik kodu. W pliku kliknij **Wstaw** wstawkę z menu kontekstowego, a następnie **Moje fragmenty kodu**. Powinien pojawić się fragment kodu o nazwie **My Visual Basic**. Kliknij go dwukrotnie.

7. Powinien zostać wyświetlony `Console.WriteLine("Hello, World!")` wstawiony w kodzie.

### <a name="adding-description-and-shortcut-fields"></a>Dodawanie opisu i pól skrótów

1. Pola opisu zawierają więcej informacji na temat fragmentu kodu wyświetlanego w Menedżerze fragmentów kodu. Skrót to tag, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj dodany fragment, otwierając plik `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.

2. Dodaj elementy Author i Description do elementu header i wypełnij je.

3. Element header powinien wyglądać następująco:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>

    ```

4. Otwórz Menedżera fragmentów kodu i wybierz fragment kodu. W prawym okienku należy zobaczyć, że pola Opis i autor są teraz wypełnione.

5. Aby dodać skrót, Dodaj element skrótu obok elementu autor i opis:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>

    ```

6. Zapisz ponownie plik fragmentu kodu.

7. Aby przetestować skrót, Otwórz projekt Visual Basic i Otwórz plik kodu. Wpisz `hello` w pliku i naciśnij klawisz TAB. Należy wstawić kod fragmentu kodu.

### <a name="to-add-references-and-imports"></a>Aby dodać odwołania i Importy

1. Za pomocą fragmentów kodu Visual Basic można dodać odwołanie do projektu przy użyciu elementu References i dodać deklarację Imports za pomocą elementu Imports. (Fragmenty kodu w innych językach nie mają tej funkcji). Na przykład jeśli zmienisz `Console.WriteLine` w przykładzie kodu na `MessageBox.Show`, może być konieczne dodanie zestawu System. Windows. Forms. dll do projektu.

2. Otwórz fragment kodu.

3. Dodaj element References pod elementem fragmentu kodu:

    ```
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>

    ```

4. Dodaj element Importy pod elementem fragmentu kodu:

    ```
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>

    ```

5. Zmień sekcję CDATA na następującą:

    ```
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. Zapisz fragment kodu.

7. Otwórz projekt Visual Basic i Dodaj fragment kodu.

8. Zostanie wyświetlona instrukcja Imports w górnej części pliku kodu:

    ```
    Imports System.Windows.Forms

    ```

9. Przyjrzyj się właściwościom projektu. Karta odwołania zawiera odwołanie do System. Windows. Forms. dll.

### <a name="adding-replacements"></a>Dodawanie zamian

1. Licencjobiorca może chcieć, aby części fragmentów kodu zostały zastąpione przez użytkownika, na przykład jeśli dodasz zmienną i chcesz, aby użytkownik zamienił zmienną na jeden w bieżącym projekcie. Można dostarczyć dwa typy zamian: literały i obiekty. Literały są ciągami niektórych typów (literały ciągów, nazwy zmiennych lub reprezentacje ciągów wartości liczbowych). Obiekty są wystąpieniami niektórych typów innych niż ciąg. W tej procedurze zostanie zadeklarowana wymiana literału i zastąpienie obiektu i zmiana kodu w celu odwoływania się do tych zamian.

2. Otwórz fragment kodu.

3. W tym przykładzie używa parametrów połączenia SQL, dlatego należy zmienić elementy Importy i odwołania, aby dodać odpowiednie odwołania:

    ```
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>

    ```

4. Aby zadeklarować zamianę literału dla parametrów połączenia SQL, Dodaj element deklaracji pod elementem fragmentu kodu, a w nim Dodaj element literału z podelementami dla identyfikatora, etykietki narzędzia i wartości domyślnej dla zastąpienia:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>

    ```

5. Aby zadeklarować zamiennik obiektu dla połączenia SQL, Dodaj element obiektu wewnątrz elementu deklaracji i Dodaj elementy podrzędne dla identyfikatora, typu obiektu, etykietki narzędzia i wartości domyślnej. Element deklaracji powstających powinien wyglądać następująco:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6. W sekcji Code należy odwołać się do zamienników z otaczającymi znakami $, na przykład `$replacement$`:

    ```
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. Zapisz fragment kodu.

8. Otwórz projekt Visual Basic i Dodaj fragment kodu.

9. Kod powinien wyglądać podobnie do poniższego, gdzie zamienniki `SQL connection string` i `dcConnection` są wyróżnione w jasnym kolorze pomarańczowym. Naciśnij klawisz TAB, aby przejść od jednego do drugiego.

    ```
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection

    ```

## <a name="see-also"></a>Zobacz też
 [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)
