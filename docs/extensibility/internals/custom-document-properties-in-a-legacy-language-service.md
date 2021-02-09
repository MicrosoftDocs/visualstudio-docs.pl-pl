---
title: Niestandardowe właściwości dokumentu w starszych usługach językowych
description: Dowiedz się, jak utworzyć niestandardowe właściwości dokumentu, które są wyświetlane w programie Visual Studio okno Właściwości w ramach starszej wersji usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a9bd5b41d1c04e52d16ecb2fc327e648d9f81aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902994"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Niestandardowe właściwości dokumentu w starszej wersji usługi językowej
Właściwości dokumentu można wyświetlić w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oknie **Właściwości** . Języki programowania zazwyczaj nie mają właściwości skojarzonych z poszczególnymi plikami źródłowymi. Plik XML obsługuje jednak właściwości dokumentu, które mają wpływ na kodowanie, schemat i arkusz stylów.

## <a name="discussion"></a>Dyskusja
 Jeśli język wymaga niestandardowych właściwości dokumentu, należy utworzyć klasę z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i zaimplementować niezbędne właściwości w klasie pochodnej.

 Ponadto właściwości dokumentu są zwykle przechowywane w samym pliku źródłowym. Wymaga to, aby usługa językowa przeanalizowana informacje o właściwościach z pliku źródłowego, aby były wyświetlane w oknie **Właściwości** i zaktualizować plik źródłowy po dokonaniu zmiany we właściwościach dokumentu w oknie **Właściwości** .

## <a name="customize-the-documentproperties-class"></a>Dostosowywanie klasy DocumentProperties
 Aby zapewnić obsługę właściwości dokumentu niestandardowego, należy utworzyć klasę z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i dodać dowolną liczbę właściwości. Należy również podać atrybuty użytkownika, aby zorganizować je w oknie **Właściwości** . Jeśli właściwość ma tylko `get` metodę dostępu, jest wyświetlana jako tylko do odczytu w oknie **Właściwości** . Jeśli właściwość ma zarówno metody `get` `set` dostępu, jak i, właściwość może być również aktualizowana w oknie **Właściwości** .

### <a name="example"></a>Przykład
 Oto przykładowa Klasa pochodna <xref:Microsoft.VisualStudio.Package.DocumentProperties> , pokazująca dwie właściwości `Filename` i `Description` . Gdy właściwość jest aktualizowana, wywoływana jest metoda niestandardowa <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, aby zapisać właściwość w pliku źródłowym.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>Tworzenie wystąpienia niestandardowej klasy DocumentProperties
 Aby utworzyć wystąpienie klasy niestandardowych właściwości dokumentu, należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metodę w swojej wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, aby zwracało pojedyncze wystąpienie <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy.

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
 Ponieważ właściwości dokumentu są zwykle specyficzne dla pliku źródłowego, wartości są przechowywane w samym pliku źródłowym. Wymaga to od analizatora języka lub skanera, aby zdefiniować te właściwości. Na przykład właściwości dokumentu XML są przechowywane w węźle głównym. Wartości w węźle głównym są modyfikowane, gdy wartości okna **Właściwości** są zmieniane, a węzeł główny zostanie zaktualizowany w edytorze.

### <a name="example"></a>Przykład
 Ten przykład zapisuje właściwości `Filename` i `Description` w pierwszych dwóch wierszach pliku źródłowego osadzony w specjalnym nagłówku komentarza w następujący sposób:

```
//!Filename = file.testext
//!Description = A sample file
```

 Ten przykład pokazuje dwie metody, które są konieczne do pobrania i ustawienia właściwości dokumentu z pierwszych dwóch wierszy pliku źródłowego, a także sposobu aktualizowania właściwości, jeśli użytkownik modyfikuje plik źródłowy bezpośrednio. `SetPropertyValue`Metoda w pokazanym przykładzie jest taka sama jak wywołana z `TestDocumentProperties` klasy, jak pokazano w sekcji *Dostosowywanie klasy DocumentProperties* .

 Ten przykład używa skanera, aby określić typ tokenów w pierwszych dwóch wierszach. Ten przykład służy tylko do celów informacyjnych. Bardziej typowym podejściem do tej sytuacji jest przeanalizowanie pliku źródłowego w postaci drzewa analizowanego, w którym każdy węzeł drzewa zawiera informacje o konkretnym tokenie. Węzeł główny powinien zawierać właściwości dokumentu.

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
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
