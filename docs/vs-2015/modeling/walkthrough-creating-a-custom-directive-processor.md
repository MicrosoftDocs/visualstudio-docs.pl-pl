---
title: 'Przewodnik: Tworzenie niestandardowego procesora dyrektywy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
ms.assetid: b8f35a36-14e1-4467-8f5f-e01402af14d5
caps.latest.revision: 76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 665c59e6881ec2e5924845dfc8dcc130b5044095
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663391"
---
# <a name="walkthrough-creating-a-custom-directive-processor"></a>Przewodnik: Tworzenie niestandardowego procesora dyrektywy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dyrektywa procesorami * pracy, dodając kod do *wygenerowanej klasy przekształcenia*. Jeśli wywołasz *dyrektywy* z *szablonu tekstu*, reszta kodu napisanego w szablonie tekstowym może polegać na funkcjonalności, jaką zapewnia dyrektywa.  

 Można napisać własne niestandardowe procesory dyrektyw. Dzięki temu można dostosowywać szablony tekstowe. Aby utworzyć niestandardowy procesor dyrektywy, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  

 Zadania przedstawione w niniejszym przewodniku to m.in.:  

-   Tworzenie niestandardowego procesora dyrektywy  

-   Rejestrowanie procesora dyrektywy  

-   Testowanie procesora dyrektywy  

## <a name="prerequisites"></a>Wymagania wstępne  
 W celu wykonania instrukcji w tym przewodniku potrzebne są następujące elementy:  

-   Visual Studio 2010  

-   Visual Studio 2010 SDK  

## <a name="creating-a-custom-directive-processor"></a>Tworzenie niestandardowego procesora dyrektywy  
 W tym przewodniku tworzysz niestandardowy procesor dyrektywy. Dodaj niestandardową dyrektywę, który odczytuje plik XML, przechowuje go w <xref:System.Xml.XmlDocument> zmienną i udostępnia go za pośrednictwem właściwości. W sekcji „Testowanie procesora dyrektywy” używasz tej właściwości w szablonie tekstowym w celu dostępu do pliku XML.  

 Wywołanie niestandardowej dyrektywy wygląda następująco:  

 `<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`  

 Niestandardowy procesor dyrektywy dodaje zmienną i właściwość do wygenerowanej klasy przekształcenia. Dyrektywy, że piszesz, stosuje <xref:System.CodeDom> klas do pisania kodu, który aparat dodaje do wygenerowanej klasy przekształcenia. <xref:System.CodeDom> Klasy Tworzenie kodu w Visual C# lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], w zależności od języka określonego w `language` parametru `template` dyrektywy. Język procesora dyrektywy i język szablonu tekstu, który uzyskuje dostęp do procesora dyrektywy, nie muszą sobie odpowiadać.  

 Kod, który tworzy dyrektywa, wygląda następująco:  

```csharp  
private System.Xml.XmlDocument document0Value;  

public virtual System.Xml.XmlDocument Document0  
{  
  get  
  {  
    if ((this.document0Value == null))  
    {  
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);  
    }  
    return this.document0Value;  
  }  
}  
```  

```vb  
Private document0Value As System.Xml.XmlDocument  

Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument  
    Get  
        If (Me.document0Value Is Nothing) Then  
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)  
        End If  
        Return Me.document0Value  
    End Get  
End Property  
```  

#### <a name="to-create-a-custom-directive-processor"></a>Aby utworzyć niestandardowy procesor dyrektywy  

1.  W Visual Studio utwórz projekt biblioteki klas C# lub Visual Basic o nazwie CustomDP.  

    > [!NOTE]
    >  Jeśli chcesz zainstalować procesor dyrektywy na więcej niż jednym komputerze, to lepiej używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia (VSIX) projektu, a następnie dołącz do rozszerzenia plik .pkgdef. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).  

2.  Dodawanie odwołań do następujących zestawów:  

    -   **Microsoft.VisualStudio.TextTemplating.\*.0**  

    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**  

3.  Zastąp kod w **klasa1** następującym kodem. Ten kod zawiera definicję klasy CustomDirectiveProcessor, która dziedziczy <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> klasy i implementuje niezbędne metody.  

    ```csharp  
    using System;  
    using System.CodeDom;  
    using System.CodeDom.Compiler;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using Microsoft.VisualStudio.TextTemplating;  

    namespace CustomDP  
    {  
        public class CustomDirectiveProcessor : DirectiveProcessor  
        {  
            //this buffer stores the code that is added to the   
            //generated transformation class after all the processing is done   
            //---------------------------------------------------------------------  
            private StringBuilder codeBuffer;  

            //Using a Code Dom Provider creates code for the   
            //generated transformation class in either Visual Basic or C#.  
            //If you want your directive processor to support only one language, you  
            //can hard code the code you add to the generated transformation class.  
            //In that case, you do not need this field.  
            //--------------------------------------------------------------------------  
            private CodeDomProvider codeDomProvider;  

            //this stores the full contents of the text template that is being processed  
            //--------------------------------------------------------------------------  
            private String templateContents;  

            //These are the errors that occur during processing. The engine passes   
            //the errors to the host, and the host can decide how to display them,  
            //for example the host can display the errors in the UI  
            //or write them to a file.  
            //---------------------------------------------------------------------  
            private CompilerErrorCollection errorsValue;  
            public new CompilerErrorCollection Errors  
            {  
                get { return errorsValue; }  
            }  

            //Each time this directive processor is called, it creates a new property.  
            //We count how many times we are called, and append "n" to each new  
            //property name. The property names are therefore unique.  
            //-----------------------------------------------------------------------------  
            private int directiveCount = 0;  

            public override void Initialize(ITextTemplatingEngineHost host)  
            {  
                //we do not need to do any initialization work  
            }  

            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)  
            {  
                //the engine has passed us the language of the text template  
                //we will use that language to generate code later  
                //----------------------------------------------------------  
                this.codeDomProvider = languageProvider;  
                this.templateContents = templateContents;  
                this.errorsValue = errors;  

                this.codeBuffer = new StringBuilder();  
            }  

            //Before calling the ProcessDirective method for a directive, the   
            //engine calls this function to see whether the directive is supported.  
            //Notice that one directive processor might support many directives.  
            //---------------------------------------------------------------------  
            public override bool IsDirectiveSupported(string directiveName)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                return false;  
            }  

            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    string fileName;  

                    if (!arguments.TryGetValue("FileName", out fileName))  
                    {  
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");  
                    }  

                    if (string.IsNullOrEmpty(fileName))  
                    {  
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");  
                    }  

                    //Now we add code to the generated transformation class.  
                    //This directive supports either Visual Basic or C#, so we must use the  
                    //System.CodeDom to create the code.  
                    //If a directive supports only one language, you can hard code the code.  
                    //--------------------------------------------------------------------------  

                    CodeMemberField documentField = new CodeMemberField();  

                    documentField.Name = "document" + directiveCount + "Value";  
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentField.Attributes = MemberAttributes.Private;  

                    CodeMemberProperty documentProperty = new CodeMemberProperty();  

                    documentProperty.Name = "Document" + directiveCount;  
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentProperty.Attributes = MemberAttributes.Public;  
                    documentProperty.HasSet = false;  
                    documentProperty.HasGet = true;  

                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);  
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));  
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));  
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };  

                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);  
                    documentProperty.GetStatements.Add(ifThen);  

                    CodeStatement s = new CodeMethodReturnStatement(fieldName);  
                    documentProperty.GetStatements.Add(s);  

                    CodeGeneratorOptions options = new CodeGeneratorOptions();  
                    options.BlankLinesBetweenMembers = true;  
                    options.IndentString = "    ";  
                    options.VerbatimOrder = true;  
                    options.BracingStyle = "C";  

                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))  
                    {  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);  
                    }  

                }//end CoolDirective  

                //One directive processor can contain many directives.  
                //If you want to support more directives, the code goes here...  
                //-----------------------------------------------------------------  
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    //code for SuperCoolDirective goes here...  
                }//end SuperCoolDirective  

                //Track how many times the processor has been called.  
                //-----------------------------------------------------------------  
                directiveCount++;  

            }//end ProcessDirective  

            public override void FinishProcessingRun()  
            {  
                this.codeDomProvider = null;  

                //important: do not do this:  
                //the get methods below are called after this method   
                //and the get methods can access this field  
                //-----------------------------------------------------------------  
                //this.codeBuffer = null;  
            }  

            public override string GetPreInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the start of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any pre-initialization, so we will just return "".  
                //-----------------------------------------------------------------  
                //GetPreInitializationCodeForProcessingRun runs before the   
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  

            public override string GetPostInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the end of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any post-initialization, so we will just return "".  
                //------------------------------------------------------------------  
                //GetPostInitializationCodeForProcessingRun runs after the  
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  

            public override string GetClassCodeForProcessingRun()  
            {  
                //Return the code to add to the generated transformation class.  
                //-----------------------------------------------------------------  
                return codeBuffer.ToString();  
            }  

            public override string[] GetReferencesForProcessingRun()  
            {  
                //This returns the references that we want to use when   
                //compiling the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need a reference to this assembly to be able to call   
                //XmlReaderHelper.ReadXml from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    this.GetType().Assembly.Location  
                };  
            }  

            public override string[] GetImportsForProcessingRun()  
            {  
                //This returns the imports or using statements that we want to   
                //add to the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                //from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    "CustomDP"  
                };  
            }  
        }//end class CustomDirectiveProcessor  

        //-------------------------------------------------------------------------  
        // the code that we are adding to the generated transformation class   
        // will call this method  
        //-------------------------------------------------------------------------  
        public static class XmlReaderHelper  
        {  
            public static XmlDocument ReadXml(string fileName)  
            {  
                XmlDocument d = new XmlDocument();  

                using (XmlTextReader reader = new XmlTextReader(fileName))  
                {  
                    try  
                    {  
                        d.Load(reader);  
                    }  
                    catch (System.Xml.XmlException e)  
                    {  
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);  
                    }  
                }  
                return d;  
            }  
        }//end class XmlReaderHelper  
    }//end namespace CustomDP  
    ```  

    ```vb  
    Imports System  
    Imports System.CodeDom  
    Imports System.CodeDom.Compiler  
    Imports System.Collections.Generic  
    Imports System.Globalization  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports Microsoft.VisualStudio.TextTemplating  

    Namespace CustomDP  

        Public Class CustomDirectiveProcessor  
        Inherits DirectiveProcessor  

            'this buffer stores the code that is added to the   
            'generated transformation class after all the processing is done   
            '---------------------------------------------------------------  
            Private codeBuffer As StringBuilder  

            'Using a Code Dom Provider creates code for the  
            'generated transformation class in either Visual Basic or C#.  
            'If you want your directive processor to support only one language, you  
            'can hard code the code you add to the generated transformation class.  
            'In that case, you do not need this field.  
            '--------------------------------------------------------------------------  
            Private codeDomProvider As CodeDomProvider  

            'this stores the full contents of the text template that is being processed  
            '--------------------------------------------------------------------------  
            Private templateContents As String  

            'These are the errors that occur during processing. The engine passes   
            'the errors to the host, and the host can decide how to display them,  
            'for example the host can display the errors in the UI  
            'or write them to a file.  
            '---------------------------------------------------------------------  
            Private errorsValue As CompilerErrorCollection  
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection  
                Get  
                    Return errorsValue  
                End Get  
            End Property  

            'Each time this directive processor is called, it creates a new property.  
            'We count how many times we are called, and append "n" to each new  
            'property name. The property names are therefore unique.  
            '--------------------------------------------------------------------------  
            Private directiveCount As Integer = 0  

            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)  

                'we do not need to do any initialization work  
            End Sub  

            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)  

                'the engine has passed us the language of the text template  
                'we will use that language to generate code later  
                '----------------------------------------------------------  
                Me.codeDomProvider = languageProvider  
                Me.templateContents = templateContents  
                Me.errorsValue = errors  

                Me.codeBuffer = New StringBuilder()  
            End Sub  

            'Before calling the ProcessDirective method for a directive, the   
            'engine calls this function to see whether the directive is supported.  
            'Notice that one directive processor might support many directives.  
            '---------------------------------------------------------------------  
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean  

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  

                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  

                Return False  
            End Function  

            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))  

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  

                    Dim fileName As String  

                    If Not (arguments.TryGetValue("FileName", fileName)) Then  
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")  
                    End If  

                    If String.IsNullOrEmpty(fileName) Then  
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")  
                    End If  

                    'Now we add code to the generated transformation class.  
                    'This directive supports either Visual Basic or C#, so we must use the  
                    'System.CodeDom to create the code.  
                    'If a directive supports only one language, you can hard code the code.  
                    '--------------------------------------------------------------------------  

                    Dim documentField As CodeMemberField = New CodeMemberField()  

                    documentField.Name = "document" & directiveCount & "Value"  
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentField.Attributes = MemberAttributes.Private  

                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()  

                    documentProperty.Name = "Document" & directiveCount  
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentProperty.Attributes = MemberAttributes.Public  
                    documentProperty.HasSet = False  
                    documentProperty.HasGet = True  

                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)  
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))  
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))  
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}  

                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)  
                    documentProperty.GetStatements.Add(ifThen)  

                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)  
                    documentProperty.GetStatements.Add(s)  

                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()  
                    options.BlankLinesBetweenMembers = True  
                    options.IndentString = "    "  
                    options.VerbatimOrder = True  
                    options.BracingStyle = "VB"  

                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)  

                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)  
                    End Using  

                End If  'CoolDirective  

                'One directive processor can contain many directives.  
                'If you want to support more directives, the code goes here...  
                '-----------------------------------------------------------------  
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then  

                    'code for SuperCoolDirective goes here  
                End If 'SuperCoolDirective  

                'Track how many times the processor has been called.  
                '-----------------------------------------------------------------  
                directiveCount += 1  
            End Sub 'ProcessDirective  

            Public Overrides Sub FinishProcessingRun()  

                Me.codeDomProvider = Nothing  

                'important: do not do this:  
                'the get methods below are called after this method   
                'and the get methods can access this field  
                '-----------------------------------------------------------------  
                'Me.codeBuffer = Nothing  
            End Sub  

            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String  

                'Use this method to add code to the start of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any pre-initialization, so we will just return "".  
                '-----------------------------------------------------------------  
                'GetPreInitializationCodeForProcessingRun runs before the   
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  

            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String  

                'Use this method to add code to the end of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any post-initialization, so we will just return "".  
                '------------------------------------------------------------------  
                'GetPostInitializationCodeForProcessingRun runs after the  
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  

            Public Overrides Function GetClassCodeForProcessingRun() As String  

                'Return the code to add to the generated transformation class.  
                '-----------------------------------------------------------------  
                Return codeBuffer.ToString()  
            End Function  

            Public Overrides Function GetReferencesForProcessingRun() As String()  

                'This returns the references that we want to use when   
                'compiling the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need a reference to this assembly to be able to call   
                'XmlReaderHelper.ReadXml from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}  
            End Function  

            Public Overrides Function GetImportsForProcessingRun() As String()  

                'This returns the imports or using statements that we want to   
                'add to the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                'from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", "CustomDP"}  
            End Function  
        End Class 'CustomDirectiveProcessor  

        '--------------------------------------------------------------------------  
        ' the code that we are adding to the generated transformation class   
        ' will call this method  
        '--------------------------------------------------------------------------  
        Public Class XmlReaderHelper  

            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument  

                Dim d As XmlDocument = New XmlDocument()  

                Using reader As XmlTextReader = New XmlTextReader(fileName)  

                    Try  
                        d.Load(reader)  

                    Catch e As System.Xml.XmlException  

                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)  
                    End Try  
                End Using  

                Return d  
            End Function  
        End Class 'XmlReaderHelper  

    End Namespace  
    ```  

4.  Dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] tylko Otwórz **projektu** menu, a następnie kliknij przycisk **właściwości CustomDP**. Na **aplikacji** na karcie **głównej przestrzeni nazw**, usuń wartość domyślną `CustomDP`.  

5.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  

6.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  

### <a name="build-the-project"></a>Kompilacja projektu  
 Skompiluj projekt. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  

## <a name="registering-the-directive-processor"></a>Rejestrowanie procesora dyrektywy  
 Zanim wywołasz dyrektywę z szablonu tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], należy dodać klucz rejestru dla procesora dyrektywy.  

> [!NOTE]
>  Jeśli chcesz zainstalować procesor dyrektywy na więcej niż jednym komputerze, to lepiej zdefiniować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie (VSIX), który zawiera plik .pkgdef wraz z zestawem. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).  

 Klucze dla procesorów dyrektyw istnieją w rejestrze w następującej lokalizacji:  

```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  

 Lokalizacja w rejestrze dla systemów 64-bitowych:  

```  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  

 W tej sekcji dodajesz klucz dla niestandardowego procesora dyrektywy do rejestru w tej samej lokalizacji.  

> [!CAUTION]
>  Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze wykonaj kopię zapasową wszystkich cennych danych, które znajdują się na komputerze.  

#### <a name="to-add-a-registry-key-for-the-directive-processor"></a>Aby dodać klucz rejestru dla procesora dyrektywy  

1. Uruchom `regedit` polecenia przy użyciu Start menu lub wiersza polecenia.  

2. Przejdź do lokalizacji **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**i kliknij węzeł.  

    W systemach 64-bitowych użyj **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  

3. Dodaj nowy klucz o nazwie CustomDirectiveProcessor.  

   > [!NOTE]
   >  Jest to nazwa, która będzie używana w polu Procesor niestandardowych dyrektyw. Ta nazwa nie musi odpowiadać nazwie dyrektywy, nazwie klasy procesora dyrektywy ani przestrzeni nazw procesora dyrektywy.  

4. Dodaj nową wartość ciągu o nazwie Class, która ma wartość CustomDP.CustomDirectiveProcessor dla nazwy nowego ciągu znaków.  

5. Dodaj nową wartość ciągu o nazwie CodeBase, która ma wartość równą ścieżce do biblioteki CustomDP.dll, utworzonej we wcześniejszej części przewodnika.  

    Na przykład ścieżka może wyglądać `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`.  

    Klucz rejestru powinien mieć następujące wartości:  

   |   Nazwa    |  Typ  |                                   Dane                                   |
   |-----------|--------|--------------------------------------------------------------------------|
   | (Domyślnie) | REG_SZ |                             (wartość nieustawiona)                              |
   |   Class   | REG_SZ |                    CustomDP.CustomDirectiveProcessor                     |
   | CodeBase  | REG_SZ | <strong>\<Path to Your Solution></strong>CustomDP\bin\Debug\CustomDP.dll |

    Jeśli zestaw znajduje się w pamięci podręcznej GAC, wartości powinny wyglądać tak:  

   |   Nazwa    |  Typ  |               Dane                |
   |-----------|--------|-----------------------------------|
   | (Domyślnie) | REG_SZ |          (wartość nieustawiona)          |
   |   Class   | REG_SZ | CustomDP.CustomDirectiveProcessor |
   | Zestaw  | REG_SZ |           CustomDP.dll            |

6. Uruchom ponownie program Visual Studio.  

## <a name="testing-the-directive-processor"></a>Testowanie procesora dyrektywy  
 Aby przetestować procesor dyrektywy, należy napisać szablon tekstowy, który ją wywołuje.  

 W tym przykładzie szablon tekstowy wywołuje dyrektywę i przekazuje nazwę pliku XML, który zawiera dokumentację dla pliku klasy. Aby uzyskać więcej informacji, zobacz [komentarze dokumentacji XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  

 Następnie szablon tekstowy używa <xref:System.Xml.XmlDocument> właściwość, którą tworzy dyrektywa, przejdź do pliku XML i wydrukowania komentarzy dokumentacji.  

#### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>Aby utworzyć plik XML używany do testowania procesora dyrektywy  

1.  Utwórz plik tekstowy o nazwie `DocFile.xml` za pomocą dowolnego edytora tekstów (na przykład w Notatniku).  

    > [!NOTE]
    >  Ten plik można utworzyć w dowolnym miejscu (na przykład C:\Test\DocFile.xml).  

2.  Dodaj następującą zawartość do pliku tekstowego:  

    ```  
    <?xml version="1.0"?>  
    <doc>  
        <assembly>  
            <name>xmlsample</name>  
        </assembly>  
        <members>  
            <member name="T:SomeClass">  
                <summary>Class level summary documentation goes here.</summary>  
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>  
            </member>  
            <member name="F:SomeClass.m_Name">  
                <summary>Store for the name property</summary>  
            </member>   
            <member name="M:SomeClass.#ctor">  
                <summary>The class constructor.</summary>   
            </member>  
            <member name="M:SomeClass.SomeMethod(System.String)">  
                <summary>Description for SomeMethod.</summary>  
                <param name="s">Parameter description for s goes here</param>  
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>  
            </member>  
            <member name="M:SomeClass.SomeOtherMethod">  
                <summary>Some other method.</summary>  
                <returns>Return results are described through the returns tag.</returns>  
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>  
            </member>  
            <member name="M:SomeClass.Main(System.String[])">  
                <summary>The entry point for the application.</summary>  
                <param name="args">A list of command line arguments</param>  
            </member>  
            <member name="P:SomeClass.Name">  
                <summary>Name property</summary>  
                <value>A value tag is used to describe the property value</value>  
            </member>  
        </members>  
    </doc>  
    ```  

3.  Zapisz i zamknij plik.  

#### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>Aby utworzyć szablon tekstowy w celu przetestowania procesora dyrektywy  

1.  W Visual Studio utwórz projekt biblioteki klas C# lub Visual Basic o nazwie TemplateTest.  

2.  Dodaj nowy plik szablonu tekstu o nazwie TestDP.tt.  

3.  Upewnij się, że **narzędzie niestandardowe** właściwość TestDP.tt jest ustawiona na `TextTemplatingFileGenerator`.  

4.  Zmień zawartość TestDP.tt na następujący tekst.  

    > [!NOTE]
    >  Pamiętaj zamienić ciąg <`YOUR PATH>` ze ścieżką do pliku DocFile.xml.  

     Język szablonu tekstu nie musi odpowiadać językowi procesora dyrektywy.  

    ```csharp  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".txt" #>  

    <#  //This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  

    <#  //Uncomment this line if you want to see the generated transformation class. #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  

    <#  //This will use the results of the directive processor. #>  
    <#  //The directive processor has read the XML and stored it in Document0. #>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  

        foreach (XmlNode member in node.ChildNodes)  
        {  
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  

            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
            }  
            WriteLine("");  
        }  
    #>  

    <#  //You can call the directive processor again and pass it a different file. #>  
    <# //@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>  

    <#  //To use the results of the second directive call, use Document1. #>  
    <#  
        //XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");  

        //...  
    #>  
    ```  

    ```vb  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".txt" #>  

    <#  'This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  

    <#  'Uncomment this line if you want to see the generated transformation class. #>  
    <#  'System.Diagnostics.Debugger.Break() #>  

    <#  'This will use the results of the directive processor. #>  
    <#  'The directive processor has read the XML and stored it in Document0. #>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  

        Dim member As XmlNode  
        For Each member In node.ChildNodes  

            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  

            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
            Next  

            WriteLine("")  
        Next  
    #>  

    <#  'You can call the directive processor again and pass it a different file. #>  
    <# '@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>  

    <#  'To use the results of the second directive call, use Document1. #>  
    <#  
        'node = Document1.DocumentElement.SelectSingleNode("members")  

        '...  
    #>  
    ```  

    > [!NOTE]
    >  W tym przykładzie wartość `Processor` parametr `CustomDirectiveProcessor`. Wartość `Processor` parametru musi pasować do nazwy klucza rejestru procesora.  

5.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  

#### <a name="to-test-the-directive-processor"></a>Aby przetestować procesor dyrektywy  

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy TestDP.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  

     Aby uzyskać [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] użytkowników, TestDP.txt może nie być widoczna w **Eksploratora rozwiązań** domyślnie. Aby wyświetlić wszystkie pliki przypisane do projektu, otwórz **projektu** menu i kliknij przycisk **Pokaż wszystkie pliki**.  

2.  W **Eksploratora rozwiązań**, rozwiń węzeł TestDP.txt, a następnie kliknij dwukrotnie TestDP.txt, aby otworzyć go w edytorze.  

     Wyświetli się wygenerowany tekst wyjściowy. Dane wyjściowe powinny wyglądać następująco:  

    ```  
       Name:  T:SomeClass  
    summary:  Class level summary documentation goes here.  
    remarks:  Longer comments can be associated with a type or member through the remarks tag  

       Name:  F:SomeClass.m_Name  
    summary:  Store for the name property  

       Name:  M:SomeClass.#ctor  
    summary:  The class constructor.  

       Name:  M:SomeClass.SomeMethod(System.String)  
    summary:  Description for SomeMethod.  
      param:  Parameter description for s goes here  
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.  

       Name:  M:SomeClass.SomeOtherMethod  
    summary:  Some other method.  
    returns:  Return results are described through the returns tag.  
    seealso:  Notice the use of the cref attribute to reference a specific method  

       Name:  M:SomeClass.Main(System.String[])  
    summary:  The entry point for the application.  
      param:  A list of command line arguments  

       Name:  P:SomeClass.Name  
    summary:  Name property  
      value:  A value tag is used to describe the property value  
    ```  

## <a name="adding-html-to-generated-text"></a>Dodawanie HTML do wygenerowanego tekstu  
 Po przetestowaniu niestandardowego procesora dyrektywy możesz dodać kod HTML do wygenerowanego tekstu.  

#### <a name="to-add-html-to-the-generated-text"></a>Aby dodać HTML do wygenerowanego tekstu  

1.  Zastąp kod w TestDP.tt następującym kodem. Kod HTML jest podświetlony. Pamiętaj zamienić ciąg `YOUR PATH` ze ścieżką do pliku DocFile.xml.  

    > [!NOTE]
    >  Otwórz dodatkowe \<# i zamykające #> oddzielają Kod instrukcji od znaczników HTML.  

    ```csharp  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".htm" #>  

    <#  //this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  

    <#  //uncomment this line if you want to see the generated transformation class #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  

    <html><body>  

    <#  //this will use the results of the directive processor #>  
    <#  //the directive processor has read the XML and stored it in Document0#>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  

        foreach (XmlNode member in node.ChildNodes)  
        {  
    #>  
    <h3>  
    <#      
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
    #>  
    </h3>  
    <#  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
    #>  
    <br/>  
    <#  
            }  
        }  
    #>  
    </body></html>  
    ```  

    ```vb  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".htm" #>  

    <#  'this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  

    <#  'uncomment this line if you want to see the generated transformation class #>  
    <#  'System.Diagnostics.Debugger.Break() #>  

    <html><body>  

    <#  'this will use the results of the directive processor #>  
    <#  'the directive processor has read the XML and stored it in Document0#>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  

        Dim member As XmlNode  
        For Each member In node.ChildNodes  
    #>  
    <h3>  
    <#      
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
    #>  
    </h3>  
    <#  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
    #>  
    <br/>  
    <#  
            Next  
        Next  
    #>  
    </body></html>  
    ```  

2.  Na **pliku** menu, kliknij przycisk **Zapisz TestDP.txt**.  

3.  Aby wyświetlić dane wyjściowe w przeglądarce w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy TestDP.htm i kliknij przycisk **Pokaż w przeglądarce**.  

     Dane wyjściowe powinny być takie same, jak oryginalny tekst, z tą różnicą, że mają zastosowany format HTML. Każda nazwa elementu powinna być wyświetlana czcionką pogrubioną.
