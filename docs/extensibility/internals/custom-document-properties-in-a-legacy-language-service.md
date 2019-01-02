---
title: Niestandardowe właściwości dokumentu w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c323b71f67f795cb9a3c6ab7492cbcf77a9b8c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946714"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Niestandardowe właściwości dokumentu w starszej wersji usługi językowej
Właściwości dokumentu mogą być wyświetlane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **właściwości** okna. Języki programowania zwykle nie mają właściwości skojarzone z pojedynczych źródłowych plików. Jednakże XML obsługuje właściwości dokumentu, które wpływają na kodowanie, schemat oraz arkusza stylów.  
  
## <a name="discussion"></a>Dyskusja  
 Jeśli język musi niestandardowe właściwości dokumentu, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i implementuje niezbędne właściwości w klasie pochodnej.  
  
 Ponadto właściwości dokumentu zwykle są przechowywane w samym pliku źródłowego. Wymaga to usługa językowa można przeanalizować informacji z pliku źródłowego do wyświetlenia w **właściwości** okna oraz do aktualizowania pliku źródłowego, w przypadku zmian właściwości dokumentu w  **Właściwości** okna.  
  
## <a name="customize-the-documentproperties-class"></a>Dostosowywanie klasy DocumentProperties  
 Aby zapewnić obsługę niestandardowe właściwości dokumentu, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasę i Dodaj dowolną liczbę właściwości, według potrzeb. Należy również podać atrybuty użytkownika, aby zorganizować je w **właściwości** wyświetlania okna. Jeśli właściwość jest tylko `get` metody dostępu jest on wyświetlany jako tylko do odczytu w **właściwości** okna. Jeśli właściwość ma jednocześnie `get` i `set` metod dostępu, właściwość może też być aktualizowana w **właściwości** okna.  
  
### <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładową klasę pochodną <xref:Microsoft.VisualStudio.Package.DocumentProperties>, którym są wyświetlane dwie właściwości `Filename` i `Description`. Po zaktualizowaniu właściwości, metody niestandardowej na <xref:Microsoft.VisualStudio.Package.LanguageService> klasy jest wywoływana, aby zapisać właściwości do pliku źródłowego.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiate-the-custom-documentproperties-class"></a>Utwórz wystąpienie klasy niestandardowej DocumentProperties  
 Do utworzenia wystąpienia klasy właściwości niestandardowego dokumentu, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metoda w wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy w celu zwracania pojedynczego wystąpienia usługi <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>Właściwości w pliku źródłowym  
 Ponieważ właściwości dokumentu są zazwyczaj specyficzne dla pliku źródłowego, wartości są przechowywane w samym pliku źródłowego. To wymaga obsługi ze analizatora języka lub skaner, aby zdefiniować te właściwości. Na przykład właściwości dokumentu XML są przechowywane w węźle głównym. Wartości w węźle głównym są modyfikowane podczas **właściwości** wartości okna zostaną zmienione i węzeł główny jest aktualizowana w edytorze.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przechowuje właściwości `Filename` i `Description` w pierwsze dwa wiersze pliku źródłowego osadzone w nagłówku specjalne komentarz jako:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 W tym przykładzie przedstawiono dwie metody, które są wymagane do pobierania i ustawiania właściwości dokumentu z pierwsze dwa wiersze w pliku źródłowego, jak również, jak właściwości są aktualizowane, gdy użytkownik modyfikuje plik źródłowy bezpośrednio. `SetPropertyValue` w przykładzie pokazano, w tym miejscu jest taka sama jeden wywołać metody z `TestDocumentProperties` klasy, jak pokazano na *Dostosowywanie klasy DocumentProperties* sekcji.  
  
 W tym przykładzie użyto skaner można ustalić typu tokenów w pierwsze dwa wiersze. Ten przykład dotyczy tylko w celach ilustracyjnych. Jest bardziej typowym podejściem do takiej sytuacji można przeanalizować pliku źródłowego, w którym każdy węzeł drzewa zawiera informacje o dany token tak zwany drzewo analizy. Węzeł główny zawiera właściwości dokumentu.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje usługi starszego języka](../../extensibility/internals/legacy-language-service-features1.md)