---
title: Kod reguły wyodrębniania niestandardowego (test wydajności sieci Web)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d29bb2d0bfa1bbea7d0dd8dedbb17f9704a9c66d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810630"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Kod reguły wyodrębniania niestandardowego dla testu wydajności sieci Web

Użytkownicy mogą tworzyć własne reguły wyodrębniania. W tym celu należy utworzyć własne reguły jako pochodne wybranej klasy reguł wyodrębniania. Reguły wyodrębniania pochodzą od klasy bazowej <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> Można również tworzyć niestandardowe reguły sprawdzania poprawności. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Aby utworzyć niestandardową regułę wyodrębniania

1. Otwórz projekt testowy zawierający test wydajności sieci Web.

2. (Opcjonalnie) Utwórz oddzielny projekt Biblioteka klas, w którym będzie przechowywana reguła wyodrębniania.

    > [!IMPORTANT]
    > Klasę można utworzyć w tym samym projekcie, w którym znajdują się testy. Jednak chcąc używać zdefiniowanej reguły do różnych testów, najlepiej utworzyć oddzielny projekt Biblioteki klas i w nim przechowywać regułę. W przypadku utworzenia oddzielnego projektu należy wykonać opcjonalne kroki podane w tej procedurze.

3. (Opcjonalnie) W projekcie Biblioteka klas dodaj odwołanie do biblioteki dll Microsoft.VisualStudio.QualityTools.WebTestFramework.

4. Utwórz klasę pochodną od klasy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Zaimplementuj elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5. (Opcjonalnie) Skompiluj nowy projekt Biblioteka klas.

6. Obowiązkowe W projekcie testowym Dodaj odwołanie do projektu biblioteki klas, który zawiera niestandardową regułę wyodrębniania.

7. W projekcie testowym Otwórz test wydajności sieci Web w **Edytor internetowego testu wydajnościowego**.

8. Aby dodać niestandardową regułę wyodrębniania, kliknij prawym przyciskiem myszy żądanie testu wydajności sieci Web i wybierz polecenie **Dodaj regułę wyodrębniania**.

     Zostanie wyświetlone okno dialogowe **Dodawanie reguły wyodrębniania** . Niestandardowa reguła walidacji zostanie wyświetlona na liście **Wybierz regułę** wraz ze wstępnie zdefiniowanymi regułami walidacji. Wybierz niestandardową regułę wyodrębniania, a następnie wybierz **przycisk OK**.

9. Uruchom test wydajności sieci Web.

## <a name="example"></a>Przykład

Poniższy kod pokazuje implementację niestandardowej reguły wyodrębniania. Ta reguła wyodrębnia wartość ze wskazanego pola wejściowego. Przykładu należy użyć jako punktu wyjścia dla tworzenia własnych niestandardowych reguł wyodrębniania.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

Metoda <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> zawiera podstawowe funkcje reguły wyodrębniania. Metoda <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> w poprzednim przykładzie przyjmuje jako wartość element <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs>, który dostarcza odpowiedzi generowane przez żądanie objęte regułą wyodrębniania. Odpowiedź zawiera element <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>, w którym znajdują się wszystkie znaczniki odpowiedzi. Znaczniki wejściowe są odfiltrowywane z elementu <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>. Każdy tag wejściowy jest sprawdzany pod kątem atrybutu o nazwie `name` , którego wartość jest równa wartości podanej przez użytkownika `Name` właściwości. Jeśli zostanie znaleziony tag z tym pasującym atrybutem, podejmowana jest próba wyodrębnienia wartości zawartej w `value` atrybucie, jeśli istnieje atrybut value. Jeśli istnieje, nazwa i wartość znacznika są wyodrębniane i dodawane do kontekstu testu wydajności sieci Web. Reguła wyodrębniania zadziałała pomyślnie.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Kodowanie niestandardowej reguły walidacji dla testów wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
