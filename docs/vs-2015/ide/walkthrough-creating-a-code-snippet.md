---
title: 'Przewodnik: Tworzenie wstawek kodu | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee4e0c6fd686398ae89b5c079d6efc1297a19f5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109812"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Przewodnik: Tworzenie wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragment kodu można utworzyć za pomocą tylko kilku krokach. To wszystko, co należy zrobić, Utwórz plik XML, wypełnij odpowiednie elementy i Dodaj swój kod do niego. Możesz również dodać parametry odwołań i zastąpień w kodzie. Można dodać fragment kodu do instalacji programu Visual Studio za pomocą przycisku Importuj w Menedżerze fragmentów kodu (**narzędzia/Manager wstawek kodu**).  
  
> [!TIP]
>  Aby uzyskać informacje o tym, jak łatwiej napisać wstawki kodu, wyszukiwanie witrynie CodePlex narzędzi społecznościowe, takiego jak [Edytor wstawek](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
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
  
### <a name="to-create-a-code-snippet"></a>Aby utworzyć wstawkę kodu  
  
1. Utwórz nowy plik XML w programie Visual Studio i Dodaj ukazany powyżej szablon.  
  
2. Wprowadź tytuł wstawki, np. "Hello World VB", w elemencie tytuł.  
  
3. Wprowadź język wstawki w atrybucie języki elementu kodu. W tym przykładzie należy użyć "VB".  
  
4. Dodaj jakiś kod w sekcji CDATA wewnątrz elementu kodu, na przykład:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5. Zapisz fragment kodu jako VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Aby dodać wstawki kodu programu Visual Studio  
  
1. Możesz dodać własne fragmenty kodu do instalacji programu Visual Studio za pomocą Menedżera fragmentów kodu. Otwórz Menedżera wstawek kodu (**narzędzia/Manager wstawek kodu**).  
  
2. Kliknij przycisk **importu** przycisku.  
  
3. Przejdź do lokalizacji, w której zapisano fragment kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.  
  
4. **Importowania fragmentu kodu** zostanie otwarte okno dialogowe prośbą o wybranie miejsca dodania fragmentu kodu spośród możliwości w okienku po prawej stronie. Jedną z opcji powinny być **Moje fragmenty kodu**. Zaznacz go i kliknij **Zakończ**, następnie **OK**.  
  
5. Fragment kodu zostanie skopiowany do następującej lokalizacji:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6. Przetestuj swój fragment kodu, otwierając projekt Visual Basic i otwierania pliku kodu. W pliku kliknij **Wstaw fragment kodu** na menu kontekstowe, a następnie **Moje fragmenty kodu**. Powinieneś zobaczyć fragment o nazwie **Moje wstawki kodu programu Visual Basic**. Kliknij go dwukrotnie.  
  
7. Powinien zostać wyświetlony `Console.WriteLine("Hello, World!")` wstawione w kodzie.  
  
### <a name="adding-description-and-shortcut-fields"></a>Dodawanie pól opis i skrót  
  
1. Pola opisów podać więcej informacji na temat fragmentów kodu po wyświetleniu w Menedżerze fragmentów kodu. Skrót jest znacznikiem, który użytkownicy mogą wpisać w celu wstawienia fragmentu kodu. Edytuj ten fragment kodu, które zostały dodane, otwierając plik `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2. Dodaj elementy autor i opis do elementu nagłówek i wypełnij je.  
  
3. Element nagłówka powinien wyglądać mniej więcej tak:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4. Otwórz Menedżera wstawek kodu i wybierz wstawki kodu. W okienku po prawej stronie powinien zostać wyświetlony, że teraz zostaną wypełnione pola Opis i autor.  
  
5. Aby dodać skrót, Dodaj element skrótu obok autor i opis elementu:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6. Zapisz ponownie plik fragmentu kodu.  
  
7. Aby przetestować ten skrót, otwórz projekt języka Visual Basic i Otwórz plik kodu. Typ `hello` w pliku i naciśnij klawisz TAB. Należy dodać fragment kodu.  
  
### <a name="to-add-references-and-imports"></a>Aby dodać odwołania i Importy  
  
1. Przy użyciu fragmentów kodu w języku Visual Basic można dodać odwołania do projektu przy użyciu elementu odwołania i dodawanie deklaracji Importy za pomocą elementu Importy. (Fragmenty w innych językach nie posiadają tej funkcji.) Na przykład, jeśli zmienisz `Console.WriteLine` w przykładzie kodu, aby `MessageBox.Show`, może być konieczne dodanie zestawu System.Windows.Forms.dll do projektu.  
  
2. Otwórz swoją wstawkę.  
  
3. Dodaj element odwołania pod elementem fragment kodu:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4. Dodaj element Importy pod elementem fragment kodu:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5. Zmień sekcję CDATA do następujących:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6. Zapisz fragment kodu.  
  
7. Otwórz projekt języka Visual Basic i Dodaj fragment kodu.  
  
8. Zostanie wyświetlony zostanie instrukcja Imports u góry pliku kodu:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Sprawdź właściwości projektu. Karta odwołania zawiera odwołanie do pliku System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Dodawanie zamian  
  
1. Możesz zdecydować o wymianie części swoich wstawek kodu mają zostać zastąpione przez użytkownika, na przykład jeśli dodasz zmienną i użytkownik zastąpił ją zmienną w bieżącym projekcie. Można zapewnić dwa rodzaje zamiany: literały i obiekty. Literały są ciągami specjalistycznymi (literały ciągów, nazwy zmiennych lub ciągi znaków reprezentujące wartości liczbowe). Obiekty są wystąpieniami niektórych typów innych niż ciąg. W tej procedurze zostanie zadeklarować zamianę literału i zastąpienie obiektu oraz zmiana kodu, aby odwołać te zmiany.  
  
2. Otwórz swoją wstawkę.  
  
3. W tym przykładzie użyto parametrów połączenia SQL, dlatego należy zmienić elementy Importy i odwołania, aby dodać odpowiednie odwołania:  
  
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
  
4. Aby zadeklarować zamianę literału dla parametrów połączenia SQL, Dodaj element deklaracji pod elementem fragment kodu, a w nim Dodaj element literału z podelementami dla Identyfikatora, etykietki narzędzia i wartość domyślna dla zastąpienia:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5. Aby zadeklarować zamianę obiektu dla połączenia SQL, Dodaj element obiektu wewnątrz elementu deklaracji i Dodaj elementy podrzędne dla Identyfikatora, typu obiektu, wskazówki i wartość domyślną. Wynikowy element Declarations powinien wyglądać następująco:  
  
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
  
6. W sekcji kodu można odwoływać się do zamian z otaczającymi znaków $, na przykład `$replacement$`:  
  
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
  
8. Otwórz projekt języka Visual Basic i Dodaj fragment kodu.  
  
9. Kod powinien wyglądać podobnie do poniższego, gdzie zamiany `SQL connection string` i `dcConnection` są wyróżnione kolorem jasnopomarańczowym. Naciśnij klawisz TAB, aby przejść z jednego do drugiego.  
  
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
