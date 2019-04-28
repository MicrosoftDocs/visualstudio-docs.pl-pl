---
title: Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdff9237ef30884d5bfaad424edfffec62a8f58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908420"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej
**Autos** oknie wyświetlane są wyrażenia, takie jak zmienne i parametry, które znajdują się w zakresie, gdy program debugowany jest wstrzymany, (albo z powodu punkt przerwania lub wyjątku). Wyrażenie może zawierać zmiennych lokalnych lub globalnych oraz parametry, które zostały zmienione w zakresie lokalnym. **Autos** okna może również obejmować wystąpień klasy, struktury lub innego typu. Wszystko, co może ocenić ewaluatora wyrażeń potencjalnie mogą być wyświetlane w **Autos** okna.

 Środowiska pakietu zarządzanego (MPF) nie zapewnia bezpośrednią obsługę **Autos** okna. Jednak Jeśli zastąpisz <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody, można zwrócić listę wyrażeń, które mają zostać wyświetlone w **Autos** okna.

## <a name="implementing-support-for-the-autos-window"></a>Implementowanie Obsługa okna zmiennych automatycznych
 Wszystko, czego potrzebujesz do obsługi **Autos** okna jest zaimplementowanie <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Należy określić implementacji podanej lokalizacji w pliku źródłowym, które wyrażeń powinny znajdować się w **Autos** okna. Metoda zwraca listę ciągów, w których każdy ciąg reprezentuje pojedyncze wyrażenie. Zwracana wartość wynosząca <xref:Microsoft.VisualStudio.VSConstants.S_OK> wskazuje, że lista zawiera wyrażenia, podczas gdy <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> wskazuje, że nie ma żadnych wyrażeń do wyświetlenia.

 Rzeczywiste wyrażeń, zwracane są nazwy zmiennych i parametrów, które pojawiają się w tej lokalizacji w kodzie. Te nazwy są przekazywane do ewaluatora wyrażenia, aby uzyskać wartości i typów, które następnie są wyświetlane w **Autos** okna.

### <a name="example"></a>Przykład
 W poniższym przykładzie pokazano implementację <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodę, która pobiera listę wyrażeń z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody przy użyciu Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Każdy z wyrażeń opakowaniu jako `TestVsEnumBSTR` implementującej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfejsu.

 Należy pamiętać, że `GetAutoExpressionsCount` i `GetAutoExpression` metody są niestandardowe metody na `TestAuthoringSink` obiektu i zostały dodane do obsługi tego przykładu. Reprezentują one jednym ze sposobów w wyrażeniach, które dodano do `TestAuthoringSink` obiektu przez parser (przez wywołanie metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metody) można uzyskać dostęp poza analizator.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```