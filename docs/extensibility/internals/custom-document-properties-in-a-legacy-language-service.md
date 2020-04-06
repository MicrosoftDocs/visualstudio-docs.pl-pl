---
title: Niestandardowe właściwości dokumentu w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708971"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Niestandardowe właściwości dokumentu w starszej usłudze języka
Właściwości dokumentu mogą być wyświetlane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w oknie **Właściwości.** Języki programowania zazwyczaj nie mają właściwości skojarzonych z poszczególnymi plikami źródłowymi. Jednak XML obsługuje właściwości dokumentu, które wpływają na kodowanie, schemat i arkusz stylów.

## <a name="discussion"></a>Dyskusji
 Jeśli język wymaga właściwości dokumentu niestandardowego, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i zaimplementować niezbędne właściwości w klasie pochodnej.

 Ponadto właściwości dokumentu są zazwyczaj przechowywane w samym pliku źródłowym. Wymaga to usługi języka do analizowania informacji o właściwościach z pliku źródłowego do wyświetlania w oknie **Właściwości** i zaktualizować plik źródłowy po wprowadzeniu zmiany do właściwości dokumentu w oknie **Właściwości.**

## <a name="customize-the-documentproperties-class"></a>Dostosowywanie klasy Właściwości documentproperties
 Aby obsługiwać właściwości dokumentu niestandardowego, należy <xref:Microsoft.VisualStudio.Package.DocumentProperties> wyprowadzić klasę z klasy i dodać tyle właściwości, ile potrzebujesz. Należy również podać atrybuty użytkownika, aby zorganizować je na ekranie okna **Właściwości.** Jeśli właściwość ma `get` tylko akcesor, jest wyświetlany jako tylko do odczytu w **właściwości** okna. Jeśli właściwość `get` ma `set` zarówno i akcesory, właściwość może być również aktualizowana w **właściwości** okna.

### <a name="example"></a>Przykład
 Oto przykład klasy pochodzące <xref:Microsoft.VisualStudio.Package.DocumentProperties>z , pokazując `Filename` `Description`dwie właściwości i . Po zaktualizowaniu właściwości, metoda <xref:Microsoft.VisualStudio.Package.LanguageService> niestandardowa w klasie jest wywoływana do zapisu właściwości do pliku źródłowego.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Tworzenie wystąpienia niestandardowej klasy Właściwości dokumentu
 Aby utworzyć wystąpienia klasy właściwości dokumentu niestandardowego, należy <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> zastąpić metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> wersji klasy, aby <xref:Microsoft.VisualStudio.Package.DocumentProperties> zwrócić pojedyncze wystąpienie klasy.

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
 Ponieważ właściwości dokumentu są zwykle specyficzne dla pliku źródłowego, wartości są przechowywane w samym pliku źródłowym. Wymaga to obsługi z analizatora języka lub skanera do definiowania tych właściwości. Na przykład właściwości dokumentu XML są przechowywane w węźle głównym. Wartości w węźle głównym są modyfikowane po zmianie wartości okna **Właściwości,** a węzeł główny jest aktualizowany w edytorze.

### <a name="example"></a>Przykład
 W tym przykładzie `Filename` `Description` przechowuje właściwości i w pierwszych dwóch wierszach pliku źródłowego, osadzone w specjalnym nagłówku komentarza, jak:

```
//!Filename = file.testext
//!Description = A sample file
```

 W tym przykładzie przedstawiono dwie metody potrzebne do uzyskania i ustawić właściwości dokumentu z pierwszych dwóch wierszy pliku źródłowego, a także jak właściwości są aktualizowane, jeśli użytkownik modyfikuje plik źródłowy bezpośrednio. Metoda `SetPropertyValue` w przykładzie pokazano tutaj jest taka `TestDocumentProperties` sama, o nazwie z klasy, jak pokazano w *Dostosowywanie DocumentProperties sekcji klasy.*

 W tym przykładzie używa skanera do określenia typu tokenów w pierwszych dwóch wierszach. Ten przykład służy wyłącznie do celów ilustracyjnych. Bardziej typowe podejście do tej sytuacji jest przeanalizowanie pliku źródłowego do tego, co nazywa się drzewa analizy, gdzie każdy węzeł drzewa zawiera informacje o określonym tokenie. Węzeł główny będzie zawierać właściwości dokumentu.

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

## <a name="see-also"></a>Zobacz też
- [Starsze funkcje usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
