---
title: Kodowanie niestandardowej reguły walidacji dla testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3f26dc7fd69c5190f5ba56985ef2509ddbf87866
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919914"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Kod niestandardowej reguły walidacji dla testów wydajności sieci web

Możesz utworzyć własne reguły sprawdzania poprawności. Aby to zrobić, klasa reguły jest pochodzi od klasy reguł sprawdzania poprawności. Reguły sprawdzania poprawności pochodzić od <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> klasy bazowej.

> [!NOTE]
> Można również utworzyć niestandardowe reguły wyodrębniania. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>Aby utworzyć niestandardowe reguły sprawdzania poprawności

1.  Otwórz projekt Test zawierający test wydajności sieci web.

2.  (Opcjonalnie) Należy utworzyć oddzielny projekt biblioteki klas, w której chcesz przechowywać regułę sprawdzania poprawności.

    > [!IMPORTANT]
    > Klasę można utworzyć w tym samym projekcie, w którym znajdują się testy. Jednak chcąc używać zdefiniowanej reguły do różnych testów, najlepiej utworzyć oddzielny projekt Biblioteki klas i w nim przechowywać regułę. W przypadku utworzenia oddzielnego projektu należy wykonać opcjonalne kroki podane w tej procedurze.

3.  (Opcjonalnie) W projekcie biblioteki klas Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.WebTestFramework.

4.  Utwórz klasę pochodną od klasy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Zaimplementuj elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>.

5.  (Opcjonalnie) Skompiluj nowy projekt Biblioteka klas.

6.  (Opcjonalnie) W projekcie testowym Dodaj odwołanie do projektu Biblioteka klas zawierającego niestandardową regułę poprawności.

7.  W projekcie Test Otwórz test wydajności sieci web, w **edytora testów wydajności sieci Web**.

8.  Aby dodać niestandardową regułę poprawności na żądanie testu wydajności sieci web, kliknij prawym przyciskiem myszy żądanie i wybierz pozycję **Dodaj regułę walidacji**.

     **Dodaj regułę walidacji** pojawi się okno dialogowe. Zostanie wyświetlony swojej niestandardowej reguły walidacji w **wybierz regułę** listy wraz z reguł sprawdzania poprawności wstępnie zdefiniowane. Wybierz swoje niestandardowej reguły walidacji, a następnie wybierz **OK**.

9. Uruchom test wydajności sieci web.

## <a name="example"></a>Przykład

Poniższy kod pokazuje implementację niestandardowej reguły walidacji. Ta reguła walidacji naśladuje zachowanie wstępnie zdefiniowana reguła sprawdzania poprawności wymaganego tagu. Na użytek tego przykładu jako punktu wyjścia własne niestandardowe reguły sprawdzania poprawności.

> [!WARNING]
> Właściwości publiczne w kodzie dla niestandardowego modułu weryfikacji nie może mieć wartości null.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Kodowanie niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)