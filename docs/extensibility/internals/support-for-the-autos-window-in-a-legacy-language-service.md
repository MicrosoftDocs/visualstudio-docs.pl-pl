---
title: Obsługa okna Autos w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704882"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej
Okno **Autos** wyświetla wyrażenia, takie jak zmienne i parametry, które znajdują się w zakresie, gdy program jest debugowany jest wstrzymany (z powodu punktu przerwania lub wyjątku). Wyrażenia mogą zawierać zmienne, lokalne lub globalne oraz parametry, które zostały zmienione w zakresie lokalnym. Okno **Autos** może również zawierać wystąpienia klasy, struktury lub innego typu. Wszystko, co oceniający wyrażenie może ocenić, może być potencjalnie wyświetlane w oknie **Autos.**

 Struktura pakietu zarządzanego (MPF) nie zapewnia bezpośredniej obsługi okna **Autos.** Jeśli jednak zostanie zastąpiona <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metoda, można zwrócić listę wyrażeń, które mają być prezentowane w oknie **Autos.**

## <a name="implementing-support-for-the-autos-window"></a>Implementowanie obsługi okna Autos
 Wszystko, co musisz zrobić, aby obsługiwać <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> **autos** okna jest zaimplementowanie metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie. Implementacja musi zdecydować, biorąc pod uwagę lokalizację w pliku źródłowym, które wyrażenia powinny pojawić się w oknie **Autos.** Metoda zwraca listę ciągów, w których każdy ciąg reprezentuje pojedyncze wyrażenie. Zwracana <xref:Microsoft.VisualStudio.VSConstants.S_OK> wartość wskazuje, że lista zawiera <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> wyrażenia, a jednocześnie wskazuje, że nie ma żadnych wyrażeń do wyświetlenia.

 Zwracane rzeczywiste wyrażenia to nazwy zmiennych lub parametrów, które pojawiają się w tej lokalizacji w kodzie. Nazwy te są przekazywane do oceniającego wyrażenie w celu uzyskania wartości i typów, które są następnie wyświetlane w oknie **Autos.**

### <a name="example"></a>Przykład
 W poniższym przykładzie <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> przedstawiono implementację metody, która <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> pobiera listę wyrażeń z metody przy użyciu przyczyny <xref:Microsoft.VisualStudio.Package.ParseReason>analizy . Każde z wyrażeń jest `TestVsEnumBSTR` zawijane <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> jako implementacji interfejsu.

 Należy zauważyć, że `GetAutoExpressionsCount` i `GetAutoExpression` metody `TestAuthoringSink` są metody niestandardowe na obiekcie i zostały dodane do obsługi tego przykładu. Reprezentują one jeden sposób, w `TestAuthoringSink` którym wyrażenia dodane do obiektu <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> przez analizatora (wywołując metodę) można uzyskać dostęp poza analizatorem.

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
