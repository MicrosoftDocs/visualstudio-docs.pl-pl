---
title: 'Przewodnik: tworzenie fragmentu kodu'
ms.date: 10/27/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 27c8237b04b2c4c903d971b1035558b77d4bf2d6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937603"
---
# <a name="walkthrough-create-a-code-snippet"></a>Przewodnik: tworzenie fragmentu kodu
Fragment kodu można utworzyć za pomocą tylko kilku krokach. To wszystko, co należy zrobić, Utwórz plik XML, wypełnij odpowiednie elementy i Dodaj swój kod do niego. Możesz również dodać parametry odwołań i zastąpień w kodzie. Można dodać fragment kodu do instalacji programu Visual Studio przy użyciu **importu** znajdujący się na **Menedżera wstawek kodu** (**narzędzia**  >   **Menedżer fragmentów kodu**).

## <a name="snippet-template"></a>Szablon fragmentu kodu
 Oto podstawowy szablon fragmentu kodu:

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

### <a name="create-a-code-snippet"></a>tworzenie fragmentu kodu

1.  Utwórz nowy plik XML w programie Visual Studio i Dodaj ukazany powyżej szablon.

2.  Wprowadź tytuł wstawki, np. "Witaj świecie VB", w **tytuł** elementu.

3.  Wprowadź język wstawki w **języka** atrybutu **kodu** elementu. W tym przykładzie należy użyć "VB".

4.  Dodaj jakiś kod w **CDATA** sekcji wewnątrz **kodu** elementu, na przykład:

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5.  Zapisz fragment kodu jako *VBCodeSnippet.snippet*.

### <a name="add-a-code-snippet-to-visual-studio"></a>Dodaj fragment kodu do programu Visual Studio

1.  Możesz dodać własne fragmenty kodu do instalacji programu Visual Studio za pomocą Menedżera fragmentów kodu. Otwórz **Menedżera wstawek kodu** (**narzędzia** > **Menedżera wstawek kodu**).

2.  Kliknij przycisk **importu** przycisku.

3.  Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.

4.  **Importowania fragmentu kodu** zostanie otwarte okno dialogowe prośbą o wybranie miejsca dodania fragmentu kodu spośród możliwości w okienku po prawej stronie. Jedną z opcji powinny być **Moje fragmenty kodu**. Zaznacz go i kliknij **Zakończ**, następnie **OK**.

5.  Fragment kodu zostanie skopiowany do następującej lokalizacji:

     *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

6.  Przetestuj swój fragment kodu, otwierając projekt Visual Basic i otwierania pliku kodu. W pliku wybierz **fragmenty** > **Wstaw fragment kodu** z menu kliknij prawym przyciskiem myszy, a następnie **Moje fragmenty kodu**. Powinieneś zobaczyć fragment o nazwie **Moje wstawki kodu programu Visual Basic**. Kliknij go dwukrotnie.

    `Console.WriteLine("Hello, World!")` dodaje się w pliku kodu.

### <a name="add-description-and-shortcut-fields"></a>Dodawanie pól opis i skrót

1.  Pola opisów podać więcej informacji na temat fragmentów kodu po wyświetleniu w Menedżerze fragmentów kodu. Skrót jest znacznikiem, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj ten fragment kodu, które zostały dodane, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet*.

2.  Dodaj **Autor** i **opis** elementów **nagłówka** elementu i wypełnij je.

3.  **Nagłówka** element powinien wyglądać mniej więcej tak:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4.  Otwórz **Menedżera wstawek kodu** i wybierz wstawki kodu. W okienku po prawej stronie powinien zostać wyświetlony, **opis** i **Autor** teraz zostaną wypełnione pola.

5.  Aby dodać skrót, Dodaj **skrótów** element wraz z **Autor** i **opis** elementu:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6.  Zapisz ponownie plik fragmentu kodu.

7.  Aby przetestować ten skrót, otwórz projekt języka Visual Basic i Otwórz plik kodu. Typ `hello` w pliku i naciśnij klawisz **kartę** dwa razy.

    Fragment kodu jest wstawiany.

### <a name="add-references-and-imports"></a>Dodawanie odwołania i Importy

1.  Można dodać odwołania do projektu przy użyciu **odwołania** elementu i dodawanie deklaracji Importy za pomocą **Importy** elementu. (Ta działa dla języka C# oraz.) Na przykład, jeśli zmienisz `Console.WriteLine` w przykładzie kodu, aby `MessageBox.Show`, może być konieczne dodanie *System.Windows.Forms.dll* zestawu do projektu.

2.  Otwórz swoją wstawkę.

3.  Dodaj **odwołania** pod **fragment** elementu:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4.  Dodaj **Importy** pod **fragment** elementu:

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5.  Zmiana **CDATA** sekcji do następującego:

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6.  Zapisz fragment kodu.

7.  Otwórz projekt języka Visual Basic i Dodaj fragment kodu.

8.  Zostanie wyświetlony `Imports` instrukcji na górze pliku kodu:

    ```vb
    Imports System.Windows.Forms
    ```

9. Sprawdź właściwości projektu. **Odwołania** karta zawiera odwołanie do *System.Windows.Forms.dll*.

### <a name="add-replacements"></a>Dodawanie zamian

1.  Możesz zdecydować o wymianie części swoich wstawek kodu mają zostać zastąpione przez użytkownika, na przykład jeśli dodasz zmienną i użytkownik zastąpił ją zmienną w bieżącym projekcie. Można zapewnić dwa rodzaje zamiany: literały i obiekty. Literały są ciągami specjalistycznymi (literały ciągów, nazwy zmiennych lub ciągi znaków reprezentujące wartości liczbowe). Obiekty są wystąpieniami niektórych typów innych niż ciąg. W tej procedurze zostanie zadeklarować zamianę literału i zastąpienie obiektu oraz zmiana kodu, aby odwołać te zmiany.

2.  Otwórz swoją wstawkę.

3.  W tym przykładzie użyto parametrów połączenia SQL, dlatego należy zmienić **Importy** i **odwołania** elementy, aby dodać odpowiednie odwołania:

    ```xml
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

4.  Aby zadeklarować zamianę literału dla parametrów połączenia SQL, Dodaj **deklaracje** elementu w obszarze **fragment kodu** elementu, a w nim Dodaj **literału** element z elementy podrzędne dla Identyfikatora, etykietki narzędzia i wartość domyślna dla zastąpienia:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5.  Aby zadeklarować zamianę obiektu dla połączenia SQL, Dodaj **obiektu** element wewnątrz **deklaracje** element i Dodaj elementy podrzędne dla Identyfikatora typu obiektu, wskazówki i wartość domyślna wartość. Wartość wynikowa **deklaracje** element powinien wyglądać następująco:

    ```xml
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

6.  W sekcji kodu można odwoływać się do zamian z otaczającymi znaków $, na przykład `$replacement$`:

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7.  Zapisz fragment kodu.

8.  Otwórz projekt języka Visual Basic i Dodaj fragment kodu.

9. Kod powinien wyglądać podobnie do poniższego, gdzie zamiany `SQL connection string` i `dcConnection` są wyróżnione kolorem jasnopomarańczowym. Wybierz **kartę** przejść z jednego do drugiego.

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)